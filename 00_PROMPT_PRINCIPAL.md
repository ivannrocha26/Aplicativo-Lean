# Prompt — Aplicativo de Gestão Lean de Obras · Construtora Impacto (v2)

> Leia também o `CLAUDE.md` e a pasta `docs/` (detalhes de cada controle, regras de cálculo, consultoria, checklist, referência MGA e registro de decisões).
>
> Versão construída a partir de: varredura das pastas "Documentação de obra" (Macau Beach) e "Consultoria Lean", LEIA-ME da TM, Procedimento Geral de Implantação Lean v2 + PG-LEAN-01 a 07, Checklist Lean (réguas) e análise do sistema MGA (Macedo Faria), usado como referência funcional — **o app deve ser parecido no propósito, mas não uma cópia**. Itens marcados [ABERTO] ainda dependem de decisão.

---

## 1. Papel e objetivo

Você é um time de produto (PM + arquiteto + dev full-stack + UX de campo). Vai especificar e construir um aplicativo que reúna, em um único lugar, os controles de produção Lean que hoje estão espalhados em dezenas de planilhas Excel por obra, e que acompanhe a implantação do método Lean em cada obra (consultoria interna).

Problemas que o app resolve (constatados nas planilhas atuais):
- Mesma informação com números diferentes em cada arquivo (ex.: 309, 312, 384 e 192 apartamentos na mesma obra).
- Nomenclatura de serviço diferente por controle (código de 4 letras na meta, nome na produtividade, EAP no kanban).
- Fórmulas quebradas, vínculos externos frágeis, abas legadas de outras obras, arquivos copiados mês a mês.
- Causas de não cumprimento da meta e planos de ação quase nunca registrados (PPC com 100% das falhas sem justificativa).
- Análise semanal da TM feita à mão.

## 2. Escopo da versão 1 — núcleo Lean de produção

**Dentro:** cadastro de obra, catálogo de serviços, produtividade (com conferência de entrega obrigatória), TM, meta de curto prazo e PPC, central de planos de ação, checklist Lean mensal, jornada de implantação (encontros), distribuição e presença, controle visual, ficha do pacote / prontidão, macrofluxo, multimomento, mapa do tempo e cruz verde, painéis por perfil.

**Fora (versões futuras):** custo e mão de obra (Análise de MDO, PLANEJAMENTO TOTAL, prêmio de produção, simulação de indireto), contratos e medições, integração Sienge (SC/PC/NF, IEC), concreto, kanban, RH, Asana. A arquitetura deve prever esses módulos sem reescrever o núcleo.

Regra do método que o app respeita: custo e mão de obra só são liberados para uma obra com checklist ≥ 80%.

## 3. Obras e estágio de implantação

| Obra | Situação | Tipo |
|---|---|---|
| Macau Beach | Implantada (acompanhamento por checklist) | Vertical — 3 torres (L, O, R), térreo + 12 pav., 8 aptos/pav. |
| Villa Áurea | Implantada | [ABERTO] |
| Porto Arboreto | Em implantação | Vertical |
| Silvia Fonseca Diniz | Em implantação | [ABERTO] |
| Raízes Jabotiana | Pré-obra | **Horizontal — 164 casas** |
| Mirante, Milano, Villa dos Coqueiros | Concluídas (Milano e Coqueiros não passaram pelo método) | Só histórico/arquivo [ABERTO: importar?] |

O app precisa suportar **obra vertical** (torre → pavimento → apartamento) e **horizontal** (quadra/etapa → casa), com sequência de execução configurável.

## 4. Perfis e permissões

| Perfil | Escopo | Pode |
|---|---|---|
| Diretoria | Todas as obras | Ver painéis e indicadores (somente leitura). |
| Multiplicador Lean (Ivan, Camila) | Todas as obras | Conduzir a jornada de implantação, aplicar e validar o checklist, liberar módulos por obra, configurar catálogo e réguas, ver tudo. |
| Supervisor (várias obras) | Obras atribuídas | Ver indicadores, planos de ação e resultados de checklist; comentar. |
| Gestor da obra | Sua obra | Lançar dados, definir metas, criar e **fechar** planos de ação, justificar a TM. |
| Engenheiro de campo | Sua obra | Mesmo que o gestor. [ABERTO: pode fechar plano de ação?] |
| Assistente / Estagiário | Sua obra | Lançar produtividade (início, fim, equipe, observação), mapa do tempo, cruz verde. |

O consultor externo (Marcel) não usa o app. Todo registro guarda autor, data e histórico; nada é apagado (inativar / lixeira com restauração).

## 5. Plataforma

- PWA (web responsivo instalável) para celular, tablet e computador, **online e offline**: fila local, sincronização por registro (dois usuários em apartamentos diferentes não conflitam), indicador claro de "pendente de envio".
- Backend real com banco relacional e autenticação individual (sem "arquivo de acessos" importado no navegador).
- Backup automático por obra e exportação para Excel no layout das planilhas atuais (transição).
- Interface em português, pensada para campo: poucos toques, botões grandes, preenchimento em lote (marcar vários apartamentos e aplicar a mesma data).

## 6. Integração Prevision (API)

Ler do Prevision: esteira/sequência de pacotes, datas planejadas, produtividade prevista (capacidade da equipe), restrições, avanço físico previsto × realizado, data de medição. O Prevision substitui a PFE — **o app não terá PFE**. [ABERTO: o app também envia de volta ao Prevision o executado da produtividade?]

## 7. Módulos da v1

### 7.1 Cadastro da obra
Nome, tipo (vertical/horizontal), torres/quadras, pavimentos/etapas, unidades com numeração real (ex.: L1101, chave torre+apto), fase atual, responsáveis, calendário (dias úteis, feriados nacionais/estaduais/municipais), ritmo-alvo da obra (definido a partir do pavimento-tipo; Macau: 8 aptos/semana = 1,6/dia). O cadastro é a **fonte única** de unidades: nenhum outro módulo digita quantidade total.

### 7.2 Catálogo de serviços (pacotes)
Lista padrão da construtora (~45 serviços da esteira: Estrutura, Lixamento, Prumadas, Drywall, Impermeabilização, Contrapiso, Cerâmica, Pintura, Esquadrias, Bancada, Louças e Metais, Revisões…), com código de 4 letras, nome, faixa (Apto, Hall, Cobertura, Fachada, Área comum), ordem na esteira e criticidade padrão (gargalo / flexível). Cada obra ativa e reordena os serviços que usa e define meta/dia por serviço. Um único nome em todo o app.

### 7.3 Produtividade (substitui as ~28 planilhas por serviço)
- Registro por **unidade × serviço**: data de início, data de fim, equipe/empreiteira, servente, observação, campos extras por serviço (ex.: Cerâmica — lote piso, lote revestimento). Estrutura: também por ciclo (1–4) e pavimento.
- Status derivado: Pendente / Em execução (só início) / Finalizado (início e fim) / Com pendência.
- **Todos os serviços da meta têm apontamento por unidade**, inclusive os que hoje não têm planilha (climatização, gás, instalações, serviços de hall, cobertura, fachada, área comum — unidade = hall do pavimento, elevação, etc.).
- **Conferência de entrega obrigatória:** ao lançar a data de fim, abre o checklist de condições de entrega daquele serviço (configurável por serviço). Item reprovado gera pendência com descrição, foto e responsável pela resolução; a unidade fica "Com pendência" até nova conferência aprovada. Só então conta como Finalizado na TM. Relatório de pendências por serviço, pavimento, apartamento e responsável (base da terminalidade).
- Regra do pacote (documento/PDF de como executar o serviço) consultável dentro do serviço.
- Alertas: unidade iniciada há mais de N dias sem fim; inversão de esteira (serviço posterior finalizado com anterior em aberto); serviço sem lançamento há mais de 7 dias.
- Análise por equipe: média/dia, índice de produtividade (média ÷ meta).
- Mapa visual da obra (torre × pavimento × unidade colorido por status) gerado automaticamente.

### 7.4 Teste de Metas (TM) — sempre calculada, nunca digitada
Por serviço, com data de corte explícita: acumulado das últimas 5 semanas, executado por semana, % executado, meta/dia, executado real/dia (última semana), ritmo médio de 4 semanas, ritmo necessário para cumprir o prazo, **fim previsto calculado**, dias úteis sem produção, dias não trabalhados da semana (do Mapa do Tempo e feriados), semáforo (ok / Plano de Ação). Faixas separadas (Apto, Hall, Cobertura, Fachada). Gráfico de vales (oscilação semanal por serviço).

**Diagnóstico semanal assistido** (hoje feito à mão toda semana): para cada serviço em Plano de Ação, cruzar semáforo × ritmo de 4 semanas × dias parado; exigir justificativa; se vazia, mostrar a observação da produtividade; classificar o motivo (crítico / simples / programado / não identificado) e a criticidade (gargalo / flexível); gerar o relatório semanal em PDF para supervisor e diretoria. [ABERTO: alguém revisa antes de enviar?]

### 7.5 Meta de curto prazo e PPC
- Meta semanal por linha: local, pacote, atividade, responsável (encarregado/ADM), data, unidade, quantidade. Pode ser pré-preenchida a partir da TM/Prevision.
- Status: Finalizado / Não finalizado. **PPC = metas finalizadas ÷ metas da semana.** Meta parcialmente cumprida conta como não finalizada. **Meta atrasada não entra no PPC da semana seguinte.**
- Causa obrigatória em lista padronizada quando não finalizada (ex.: mão de obra, material, equipamento, serviço anterior, projeto, chuva, outro) [ABERTO: lista oficial]; PPC < 90% exige plano de ação em até 2 dias úteis.
- PPC por semana, por responsável e por causa (Pareto). Impressão da meta por equipe para o quadro.

### 7.6 Central de planos de ação (única)
Todo plano tem: origem (TM, Meta/PPC, Checklist, Encontro, Reunião de setor), obra, serviço/assunto, descrição, responsável, prazo original, prioridade, status em quadro (A fazer / Fazendo / Para validar / Concluído), data de conclusão, evidência. **Fechamento pelo gestor da obra.** Atrasado = vencido sem data de conclusão (prazo original, inclusive de meses anteriores). Visão consolidada por obra para supervisor e diretoria. Preparado para sincronizar com Asana no futuro.

### 7.7 Checklist Lean mensal
Seguir integralmente a especificação de `docs/04_checklist_lean.md` (itens versionados, régua de falhas 2/1/0 por opção — nota nunca digitada —, N/A com justificativa, amostra da visita, trilhas campo × sistema, OBS obrigatória em nota 0/1, fotos, offline, aderência por macro/micropilar, faixas ≥ 90% / 60–89% / < 60%, corte de 80%, escalonamento à diretoria, tendência e mapa de calor obra × micropilar). Itens do checklist que podem ser **pré-avaliados com dados do próprio app** (ex.: 1.1 mapa de chuva, 1.5/1.6 planos da meta, 1.7 produtividade, 1.8 TM, 1.9/1.10 planos da TM, 1.25 cruz verde) devem vir sugeridos, com o verificador confirmando.

### 7.8 Jornada de implantação Lean
Para cada obra: caminho (A — obra em andamento; B — obra a iniciar; Multiplicação), fase (Entendimento / Estabilização / Melhoria / Acompanhamento), encontro atual (Pré-obra 1 e 2, Encontros 1 a 5). Cada encontro tem pauta, participantes, dinâmicas aplicadas, tarefas até o próximo encontro, critério para avançar e lições. **Os módulos de controle são liberados para a obra conforme a jornada avança** (ex.: produtividade e TM a partir do Encontro 1; ficha de pacote no Encontro 2; meta e reuniões no 3; checklist no 4; multimomento no 5; custo e mão de obra com checklist ≥ 80%). Atas no formato padrão: objetivo, temas com encaminhamento, evolução em relação à ata anterior, tarefas (responsável e prazo) — as tarefas viram planos de ação.

### 7.9 Mapa do Tempo e Cruz Verde
Mapa do Tempo: dia × manhã/tarde/noite × Bom / Nublado / Chuva / Impraticável + observação; alimenta os dias não trabalhados da TM e o item 1.2 do checklist (datas de chuva do PPC precisam constar no mapa). Cruz Verde: dia sem acidente / com acidente (ASA, ACA, dias de afastamento), análise de causa obrigatória, dias sem acidente.

### 7.10 Distribuição e presença
Colaboradores (matrícula como chave, nome, função padronizada, ADM responsável/encarregado, status), equipes por pacote (equipe e equipe de suporte) com meta/dia, presença diária marcada pelo encarregado em poucos toques (presente / falta / atestado / férias), pendência de quem não marcou, resumo pacote × função, homem-dia por serviço. As equipes alimentam a produtividade (quem executou) e o índice de produtividade.

### 7.11 Controle visual
Gerado automaticamente da produtividade: prédio (torre × pavimento × unidade) ou planta de casas colorida por status de cada serviço; resumo da esteira (onde cada serviço está, distância entre eles, folga de 2 pavimentos para terceirizados). Versão para TV/impressão para gestão à vista.

### 7.12 Ficha do pacote / prontidão
Para pacotes que começam em até 3 meses (data do Prevision): mão de obra (seleção, cotação, contrato, própria/terceirizada), materiais por pavimento/casa no fluxo levantado → solicitado → pedido → entregue → abastecido, ferramentas e EPI/EPC no mesmo fluxo. Alertas de antecedência. Frente só liberada com prontidão 100%. Impressão A4 para o quadro.

### 7.13 Macrofluxo
Desenho da esteira em raias (Apto, Hall, Fachada, Cobertura…) com post-its por serviço, cores para terceirizados e aproveitamento de equipe, "pontos verdes" de avanço; ligado ao catálogo de serviços da obra; exportação em imagem/PDF para a parede.

### 7.14 Multimomento
Aplicação por serviço: rodadas de observação classificadas em valor agregado (VA), desperdício oculto (DO) e desperdício evidente (DE), por colaborador; meta de VA configurável (referência 40%); histórico por serviço para comparar antes e depois de cada melhoria; gera plano de ação.

### 7.15 Painéis
- **Diretoria:** todas as obras lado a lado — estágio da jornada, avanço físico (Prevision), PPC das últimas 4 semanas, nota do checklist e tendência, planos de ação abertos/atrasados, serviços-gargalo parados, fim previsto × meta de entrega.
- **Supervisor:** o mesmo para suas obras, com detalhe de planos de ação e checklist.
- **Obra:** TM da semana, alertas, metas da semana, pendências de lançamento (quem não lançou hoje).
- **Multiplicador:** jornada de todas as obras, próximos encontros, tarefas pendentes por obra.

## 8. Experiência e visual — requisito central

Principal crítica ao sistema de referência (MGA): com muitos controles, a informação ficou **pesada, tumultuada e com cara de Excel**. O app da Impacto deve ser o oposto:
1. **Cada perfil abre na sua tela "Hoje"**, com só o que precisa agir agora (estagiário: unidades para lançar; encarregado: presença e meta do dia; gestor: alertas da TM, planos vencendo, pendências; diretoria: cartões por obra). Os módulos ficam um nível abaixo, não numa grade de 20 cartões.
2. **Navegação por poucas áreas**, não por dezenas de pastas: Produção (produtividade, TM, visual), Planejamento (meta/PPC, ficha do pacote, macrofluxo), Ação (planos de ação, pendências), Lean (checklist, jornada, multimomento), Rotina (presença, tempo, cruz verde).
3. **Cartões, listas e gráficos antes de tabelas.** Tabela larga só como visão "detalhe", opcional. Em campo, lançamento por toque (escolher torre → pavimento → apartamentos → data), nunca digitando em grade.
4. **Exceção primeiro:** destacar o que está fora (serviço parado, PPC baixo, plano atrasado); o que está ok fica discreto.
5. **Uma ação por tela**, botões grandes, contraste para uso ao sol, poucas cores com significado fixo (verde ok, âmbar atenção, vermelho crítico).
6. Linguagem simples, sem siglas não explicadas; cada número com "de onde vem" ao tocar.
7. Identidade visual própria da Impacto.

## 9. Regras de negócio transversais
1. Toda análise mostra a data de corte.
2. Unidade sem data de fim = não concluída; nunca tratar ausência ou zero como data.
3. Fim previsto, PPC, aderência e semáforo são sempre calculados.
4. Mudança em itens do checklist, catálogo ou parâmetros da obra gera nova versão; histórico mantém a versão original.
5. Nenhum dado de outra obra pode aparecer em uma obra (isolamento por obra).
6. Dados pessoais (nomes, salários) só para perfis autorizados.

## 10. Importação das planilhas atuais (transição)
- Produtividade: arquivos "NN. Serviço.xlsx", aba `Base` — colunas Torre, Chave (Torre&Apto), Apto, Profissional, Servente, Data Início, Data Fim, Validação, OBS, OBS2; Estrutura usa `Base (NOVO)` com Pavimento e Ciclo.
- Meta: `Meta Atual_*.xlsx`, abas Meta S1–S5 — Local, Pacote, Atividade, Responsável, Data, Unidade, Quantidade, Status, Problemas, Plano de Ação.
- TM: só para conferência dos cálculos (não importar a PFE nem abas legadas).
- Checklist: aba `teste2.0` do arquivo de réguas.
- Mapa do Tempo (`Quadro do Tempo.xlsx`) e Cruz Verde (`Cruz Verde.xlsx`).
- Importador com mapeamento de colunas, pré-visualização, normalização de nomes de local/pacote e relatório do que foi ignorado.

## 11. Referência MGA — o que aproveitar e o que fazer diferente
Aproveitar a ideia de: módulos liberados por etapa da consultoria, produtividade com preenchimento em lote, conferência de entrega com pendências, TM com faixas e gráfico de vales, meta pré-preenchida a partir da TM, mapa do tempo e cruz verde integrados ao painel.

Fazer diferente:
- **Sem PFE** — planejamento vem do Prevision via API.
- **Multi-obra de verdade**, com visão consolidada da diretoria e do supervisor (no MGA o foco é a obra).
- **Jornada de implantação como eixo** (encontros, critérios de avanço, atas) — não só módulos liberados.
- **Uma central de planos de ação** para todas as origens, em vez de um plano por pasta.
- **Diagnóstico semanal da TM e relatório automático** com classificação de motivo e criticidade.
- **Checklist com a régua de falhas da Impacto** e pré-avaliação automática pelos dados do app.
- **Causas padronizadas obrigatórias** no PPC.
- Backend com login individual; sem arquivo de acessos nem dependência do navegador.
- **Visual leve e organizado por perfil** (seção 8), em vez de muitos controles com cara de planilha.
- Identidade visual própria da Impacto; não reproduzir layout, textos, código ou marca do MGA.

## 12. Entregáveis esperados
1. Modelo de dados (entidades, relacionamentos, chaves).
2. Mapa de telas por perfil e fluxos principais (lançamento de produtividade em campo, fechamento semanal da TM, meta e PPC, aplicação do checklist, registro de encontro).
3. Regras de cálculo com testes que reproduzam os números da TM e do checklist do Macau Beach.
4. Plano de MVP em fases (v1 núcleo Lean → v2 custo/MDO e Sienge → v3 Asana e demais módulos).
5. Protótipo navegável da v1.

## 13. Pontos ainda abertos
- Quem faz a conferência de entrega (engenheiro, qualidade, encarregado?) e quais condições por serviço.
- Lista oficial de causas do PPC.
- Engenheiro de campo fecha plano de ação?
- Relatório semanal da TM: envio automático ou com revisão?
- Envio de dados de volta ao Prevision.
- Importação das obras concluídas.
- Tipo e estrutura de Villa Áurea e Silvia Fonseca Diniz.
