# COMPILAÇÃO DO HISTÓRICO PROFISSIONAL — Desenvolvimento do aplicativo "Gestão Lean" para as obras da Construtora Impacto

> **Fonte desta compilação:** as quatro conversas anteriores mantidas no Claude Code para o projeto "Aplicativo Lean para Obras", entre **22/10/2026 e 27/10/2026**. Foram lidas todas as mensagens escritas por mim (Ivan), as respostas que dei às perguntas de múltipla escolha e os relatórios do assistente sobre o que foi feito e conferido.
>
> **Limites da fonte:**
> - Os documentos do projeto (`00_PROMPT_PRINCIPAL.md`, `docs/01` a `docs/06`, a análise em Word "Analise do app gestão lean.docx", o "CONTEXTO-NOVO-CHAT.md") **não foram relidos** para esta compilação, por escolha minha. Só entra deles o que aparece citado nas conversas.
> - Imagens e capturas de tela enviadas nas conversas não foram reabertas.
> - Uma chave de API e uma senha apareceram nas conversas e foram omitidas de propósito.
>
> **Como ler a classificação:**
> - **REALIZADA:** declarei ou decidi e foi executado.
> - **ACOMPANHADA:** acompanhei.
> - **RESPONSABILIDADE RECORRENTE:** faz parte das minhas atribuições.
> - **PARTICIPAÇÃO:** participei sem ser o responsável principal.
> - **PROPOSTA OU PLANEJADA:** discutida, sem confirmação de implementação.
> - **CONHECIMENTO TÉCNICO:** conceito discutido, sem evidência de aplicação por mim.
> - **NÃO CONFIRMADA:** a execução ou a minha participação não ficou clara.
>
> **Observação importante sobre autoria técnica:** nas conversas, o código do aplicativo foi escrito e testado pelo assistente de IA (Claude Code) a partir das minhas instruções, decisões e correções. O meu papel registrado foi definir o que construir, tomar as decisões de regra de negócio e de visual, fornecer as planilhas e os dados das obras, revisar as telas e pedir ajustes. A compilação respeita essa divisão.

---

## 1. Identificação e contexto da conversa

- **Assunto principal:** concepção, especificação e acompanhamento do desenvolvimento de um aplicativo único de gestão Lean das obras da **Construtora Impacto**. O nome inicial era "Aplicativo Lean" e o nome final adotado foi **"Gestão Lean"**. O aplicativo reúne controles que hoje ficam espalhados em planilhas Excel por obra: produtividade, TM, metas de curto prazo e PPC, checklist Lean mensal, gestão de compras, planos de ação e jornada de implantação Lean.
- **Período:** 22/10/2026 a 27/10/2026 (quatro sessões).
- **Empresa:** Construtora Impacto (o app usa a marca "Impacto 40 anos").
- **Setor:** pelo contexto das conversas, as decisões partem do setor de **planejamento** / implantação Lean. Eu disse: *"o setor de planejamento faz tudo. tem todo acesso ao aplicativo"*. No app, o meu perfil foi configurado como **"Multiplicador Lean"** (criador/planejamento). Os documentos do projeto citam Ivan e Camila como Multiplicadores Lean.
- **Obras envolvidas:** Macau Beach, Villa Áurea, Porto Arboreto, Silvia Fonseca Diniz, Raízes Jabotiana e Turim.
- **Contexto profissional:**
  - A Impacto já usava o **MGA**, um sistema em HTML de controle de produtividade. Eu disse: *"Esse HTML foi desenvolvido por mim, juntamente com a minha coordenadora"*. O código-fonte original se perdeu: *"foi feito em outro computador da empresa e não conseguimos salvar"*.
  - Também existiam dois apps anteriores: **App Checklist** e **App Gestão de Compras** ("planilha de compras").
  - O objetivo das sessões foi transformar tudo num aplicativo só, com visual moderno ("aspecto inovador e tecnológico", sem "cara de Excel"), com acesso por perfil de cargo e com dados reais das obras.
  - O app roda por enquanto **só no meu computador**: *"eu não tenho como publicar esse aplicativo, a ideia é continuar no meu computador onde eu vou fazendo as melhorias e só no final que eu vou passar para o TI para ele publicar"*.

---

## 2. Atividades profissionais identificadas

### 2.1. Concepção e especificação de um aplicativo de gestão Lean para as obras

- **Classificação:** REALIZADA (concepção, especificação e acompanhamento). A programação foi feita pela IA sob minha orientação.
- **Contextualização:** os controles de obra estavam espalhados em planilhas Excel por obra e em três ferramentas separadas (MGA, App Checklist e App Compras). Já existia na pasta do projeto uma especificação escrita (`00_PROMPT_PRINCIPAL.md`) com escopo da v1, perfis, **15 módulos**, regras de visual, regras de negócio, importação e entregáveis. Também havia seis documentos de apoio (inventário de controles da obra Macau Beach, funcionamento da consultoria Lean, fórmulas da TM e da produtividade, checklist completo, referência do MGA, decisões e pendências).
- **Objetivo:** ter um único aplicativo, usado em campo (celular e tablet) e no escritório, com cálculos derivados dos lançamentos e visões diferentes por cargo.
- **Descrição do desenvolvimento, em ordem cronológica:**
  1. **22/10:** pedi a análise da pasta e o início do aplicativo a partir da "Documentação de obra" da Macau Beach. Foi criado um protótipo (pasta `app/`, em React). A TM foi conferida contra as planilhas reais da Macau.
  2. **22/10:** pedi uma **cópia editável do MGA** ("não um clone, mas uma cópia para fazermos melhorias"). Depois pedi para **juntar o MGA com o aplicativo Lean num só**, apagando o que não fosse mais necessário. O MGA virou a base, e o protótipo React ficou só como referência.
  3. **22–23/10:** pedi que os apps **Checklist** e **Gestão de Compras** entrassem no aplicativo. Compras foi para "Planejamento e produção" e Checklist para "Lean e resultados", com o visual desses dois apps como padrão.
  4. **23/10:** decidi criar uma **"nuvem própria"** local. Também foram feitas a tela "Hoje" por perfil, as permissões por cargo, o painel de resultado das obras, a pré-avaliação do checklist, a retirada do PFE e a integração com o Prevision.
  5. **23/10:** pedi para subir dados reais (checklists e planilhas de compras) e fizemos várias rodadas de ajuste visual: tela de login com fotos das obras, faixas "Obras ativas/concluídas", menu do usuário etc.
  6. **23–26/10:** retirada dos emojis, menu "Configurações", gráficos com visual tecnológico, barra superior, acessos de teste por perfil, painel de Diretor/Supervisor/Planejamento, **Nota de Aderência Lean** e importação das produtividades reais da Macau Beach e da Villa Áurea.
  7. **26/10:** implantação de um sistema de design ("handoff de design Fase 1": temas, barra superior, menu lateral) e da tela **P1 – TM e pacotes**.
  8. **27/10:** pedi para aplicar uma análise que eu tinha em Word ("Analise do app gestão lean.docx"), com ajustes por perfil, metas da semana, checklist e visuais. Também pedi um atalho na área de trabalho para iniciar o app.
- **Ferramentas e sistemas:** Claude Code (IA), MGA (base), Excel (dados de origem), Prevision (planejamento), Git (histórico de versões), navegador (Edge).
- **Minha participação:** defini escopo e prioridades. A ordem foi aparência primeiro e funcionalidades depois: *"vamos continuar por enquanto mexendo na aparência do aplicativo. depois iremos para as funcionalidades"*. Tomei as decisões de regra de negócio, forneci arquivos e caminhos das planilhas, revisei as telas com prints e pedi correções.
- **Importância:** centraliza os controles Lean das obras, padroniza cálculos (sem números digitados) e dá a cada cargo a informação de que precisa.
- **Resultados registrados nas conversas:** aplicativo funcionando localmente em `localhost`; 64 testes automáticos de cálculo passando (eram 44 no protótipo, depois 56, 59 e 64); dados reais de checklist, compras e produtividade de várias obras carregados; decisões registradas de nº 19 a nº 49 no arquivo de decisões do projeto.

### 2.2. Recuperação e reaproveitamento do sistema MGA (controle de produtividade)

- **Classificação:** REALIZADA (decisão e pedido). A autoria original do MGA está em "Pontos que precisam de confirmação".
- **Contextualização:** o MGA ("MGA — Controle de Produtividade.html") existia só como página salva do navegador, num único arquivo de cerca de 4,5 MB. O código-fonte se perdeu.
- **Objetivo:** ter uma cópia editável para melhorar e atualizar com *"outras funcionalidades, outros controles que precisamos atualizar"*.
- **Descrição:**
  - O HTML foi desmontado em arquivos legíveis: o script principal passou de uma linha de 2,3 MB para cerca de 58 mil linhas.
  - Foi escrito um mapa funcional de todas as telas: Login → Empresas → Obras → Painel → 20 módulos. Ele cobre PFE/TM, apropriação de mão de obra, IEC do custo via Sienge, permissões em três camadas e sincronização.
  - Foram aplicadas proteções na cópia de desenvolvimento: nuvem oficial só leitura, dados do navegador isolados e sem atualização automática.
- **Decisões minhas:**
  - Respondi que **temos autorização** para copiar o MGA.
  - Escolhi que **onde MGA e Impacto divergem, vale a regra da Impacto**.
  - Escolhi fazer a junção **por etapas**.
  - Autorizei apagar o MGA original da pasta e a pasta `C:\mga`. O original acabou guardado em `mga/original/` e no histórico Git.
- **Resultado:** o MGA passou a ser a base do aplicativo único, com a marca Impacto (logos, fotos das fachadas das obras, ícone). A marca d'água do MGA foi mantida.

### 2.3. Unificação dos apps Checklist e Gestão de Compras no aplicativo

- **Classificação:** REALIZADA (decisão e pedido). A autoria dos apps antigos é NÃO CONFIRMADA: eu disse que foram "desenvolvidos antes", sem dizer por quem.
- **Decisões minhas:**
  - Checklist: **"unir de verdade"** (telas dentro do app).
  - Compras: **"recriar dentro do Lean"**.
  - Tema padrão **escuro**, como nos apps.
  - Autorizei juntar as telas do checklist: resultado, análises, diretoria, relatórios e fotos.
- **O que entrou (Checklist):**
  - **Preenchimento:** cabeçalho da visita (data, verificador, fase, amostra), filtro Campo/Sistema e apontamentos por item (torre, pavimento, apartamento, local, descrição, fotos).
  - **Resultado:** medidor da nota, radar comparando com o mês anterior e detalhamento pilar → micropilar → itens.
  - **Análises:** mapas de calor obra × micropilar e item × mês, evolução e itens que mais perdem pontos.
  - **Diretoria:** aderência consolidada, obras abaixo da meta, ranking e evolução de 12 meses.
  - **Relatórios:** executivo, diretoria e planilha no layout "teste2.0" com aba de evidências.
- **O que entrou (Compras):**
  - **Cálculo:** a partir da data de início de cada serviço, o app calcula quando **levantar, solicitar e receber**, com alerta vermelho, amarelo ou verde.
  - **Telas:** painel de ações vencidas e a vencer, agenda de 12 semanas, carga por pacote, contratações (Levantado, Solicitado, Entregas, Iniciado), cronograma físico (pacote × lote), catálogo de materiais, prazos e feriados.
  - **Arquivos:** importação da planilha antiga e exportação para Excel com 24 colunas.
- **Ficou de fora naquele momento:** sincronização de Compras com o Prevision, e-mails de aviso, importação da "Ficha de Material", Excel dos relatórios executivo e de diretoria, aba "Melhorias" e criação de novas versões do checklist pelo app.

### 2.4. Definição dos perfis de acesso por cargo (o que cada função vê e edita)

- **Classificação:** REALIZADA (regra de negócio definida por mim e implementada).
- **Contextualização:** o MGA tinha papéis genéricos. Eu quis acesso por cargo da obra e da empresa: *"como vamos ter vários tipos de acesso, o ideal é ter vários acessos, como diretor, supervisor, gestor, engenheiro, assistente, estagiário"*.
- **Regras que defini (23/10):**
  - **Planejamento:** *"faz tudo. Tem todo acesso ao aplicativo"*.
  - **Diretoria:** *"só vê os resultados, como obras com melhor nota no checklist"*. *"Não precisa ver nada sobre gestão de compras (...) isso é irrelevante para diretoria. Para diretoria o que importa é aderência da obra. Uma nota geral que engloba tudo"*. Vê a nota no checklist e nos macropilares e micropilares, *"sem precisar descrever quais foram os itens de cada micropilar que ficou com 0"*.
  - **Supervisores:** indicadores e dashboards mais detalhados, com dados da gestão de compras (quantidade de levantados, solicitados etc.) e a nota de cada item do checklist.
  - **Engenheiro e Gestor:** a nota da própria obra, com dados e dashboards dela. **Assistente:** as mesmas permissões.
  - **Estagiários:** *"só poderão preencher as informações da produtividade"*.
- **Respostas complementares que dei:**
  - Gestão de Compras: veem Planejamento, Supervisor, Gestor e Engenheiro.
  - Gestor, Engenheiro e Assistente **editam**. Supervisor **só vê**.
  - Confirmei três interpretações: (1) "aderência" = nota geral do checklist; (2) o Diretor não vê TM nem planos de ação, só o resultado do checklist; (3) o Assistente vê Compras igual ao Engenheiro.
  - Pedi para criar acessos de teste para **diretor, supervisor, gestor/engenheiro, assistente e estagiário**, com botões na tela de login.
- **Supervisores reais cadastrados por pedido meu:**
  - **Silvio:** Villa Áurea e Raízes Jabotiana.
  - **Fabio:** Macau Beach, Porto Arboreto e Silvia Fonseca Diniz.
- **Ajustes posteriores (análise em Word, 27/10):**
  - O **Preenchimento** do checklist fica só com o Planejamento.
  - Gestor, Engenheiro, Assistente e Estagiário só enxergam a própria obra, sem comparação entre obras.
  - Na Jornada, gestor, engenheiro e assistente veem só as etapas feitas e a atual.
  - O estagiário passou a preencher também **Cruz Verde** e **Mapa do Tempo**. O dia lançado fica fechado e só o gestor corrige.
  - O **Fluxo de serviços** não aparece para o estagiário.
- **Importância:** cada nível hierárquico recebe a informação compatível com a sua decisão. Diretoria vê aderência; supervisão vê detalhe; obra executa e lança.

### 2.5. Criação do indicador "Nota de Aderência Lean" por obra

- **Classificação:** REALIZADA (indicador idealizado por mim; os pesos foram escolhidos entre as opções apresentadas).
- **Contextualização:** pedi um painel inicial para Diretor e Supervisor com nota dos últimos checklists, ranking das obras e uma *"nota de aderência lean"*.
- **Como eu descrevi o indicador:** *"faça uma ponderação entre a nota do checklist, uso das produtividades (se estão atualizadas, bem preenchidas), uso da TM (se está com muitos planos de ação, se estão todos com planos de ação preenchidos), ponderação entre os itens controlados na planilha de compras (se tem itens atrasados etc.)"*.
- **Composição adotada (escolhi "Checklist 40%" e "usar a proposta" de medição):**

| Componente | Peso | Medição |
|---|---|---|
| Checklist | 40% | nota do último mês fechado |
| Produtividade | 20% | % dos serviços em andamento com lançamento nos últimos 7 dias e datas coerentes |
| TM | 20% | % dos serviços fora da meta que têm plano de ação (100% se nenhum estiver fora) |
| Compras | 20% | % dos itens sem ação vencida |

- **Regra de cálculo:** componente sem dado sai da conta, e o painel informa sobre qual % dos pesos a nota foi calculada.
- **Painel "Todas as obras":**
  - Indicadores do topo: aderência média, checklist médio, obras abaixo do corte de 80%, planos atrasados, compras vencidas, serviços da TM sem plano.
  - Ranking das obras e mapa de calor obra × componente.
  - Últimos checklists com variação, evolução do checklist e pontos de atenção por obra.
- **Também pedi:**
  - Seletor de obra na barra superior, com "Todas as obras" primeiro. Escolher uma obra abre direto a obra.
  - O mesmo painel para o perfil Planejamento.
- **Resultados observados:**
  - **Macau Beach: 92,6%**, calculada só com checklist (96%) e compras (17 ações vencidas em 119 itens).
  - Depois da importação das produtividades, com metas provisórias de TM, caiu para **73,8%**. Esse valor não representa a obra enquanto as metas reais não forem configuradas.

### 2.6. Checklist mensal de Gestão Lean (avaliação das obras)

- **Classificação:**
  - Uso do checklist como ferramenta de avaliação das obras e regras no app: REALIZADA (decisões).
  - Aplicação do checklist em campo por mim: NÃO CONFIRMADA nas conversas.
- **Características registradas:**
  - **Checklist Impacto 2.0:** 54 itens. Cada opção tem o texto da régua e "como verificar".
  - **Regras de preenchimento:** opção N/A; observação obrigatória quando o item fica com N/A, nota 0 ou nota 1. O mês não fecha enquanto faltar algo.
  - **Faixas da versão 2.0 no app:** 90% / 60%. No cartão "Hoje": verde acima de 90%, âmbar entre 80% e 90%, vermelho abaixo de 80%.
  - **Meta mostrada nas telas:** 80%. É o corte que libera os módulos de custo e mão de obra. O app antigo usava 85%.
  - **Estrutura:** pilares → macropilares → micropilares → itens, com trilhas Campo e Sistema.
  - **Checklists anteriores:** são do modelo antigo do MGA (40 itens) e foram mantidos como "versão anterior".
- **Pré-avaliação automática (autorizei em 23/10):** o app sugere a nota de alguns itens a partir dos dados lançados.
  - 1.1: Mapa do Tempo (ex.: "3 dias úteis sem registro").
  - 1.4: PPC médio do mês.
  - 1.6 e 1.10: planos de meta e de TM atrasados.
  - 1.16: semanas sem meta.
  - 1.25 e 1.26: Cruz Verde.
  - Nada é gravado sem o toque do verificador.
  - Os itens 1.2, 1.5, 1.7, 1.8, 1.9 e 2.4 estão marcados como pré-avaliáveis na especificação, mas a regra de medição deles **ainda não foi definida** (PROPOSTA/PENDENTE).
- **Relatórios (ajuste de 27/10):**
  - **Relatório executivo:** itens pontuados com fotos e observações.
  - **Relatório da diretoria:** compilado entre obras, com notas dos pilares, sem detalhar itens.
- **Notas reais carregadas no app:** ver seções 3 e 7.

### 2.7. Controle de produtividade e TM (ritmo dos serviços)

- **Classificação:**
  - Importação e validação das produtividades reais da Macau Beach e da Villa Áurea: REALIZADA (por pedido meu, executada pela IA).
  - Configuração das metas da TM: PROPOSTA OU PLANEJADA. Eu disse *"eu configuro as metas da TM no app"*, sem confirmação de que já fiz.
- **Contextualização:**
  - As produtividades ficam em planilhas Excel por serviço, uma planilha por serviço (ex.: "NN. Serviço.xlsx"), com uma linha por unidade e datas de início e fim.
  - Na Macau elas ficam em `Documentação de obra/Obra/Produtividade/Barbara`, com 28 planilhas.
  - Eu indiquei o caminho: *"na pasta documentação de obras - obras - produtividade"*. Pedi para começar pela Macau, com cópia do banco antes, e depois fazer a Villa Áurea.
- **Regras de cálculo registradas:**
  - O **fim previsto da TM** é calculado pelo **ritmo médio das últimas 4 semanas**. Escolhi essa opção.
  - A TM mostra o acumulado S1 a S5, o ritmo, o fim previsto, a situação (semáforo) e um diagnóstico. Pacote abaixo da meta gera botão de plano de ação.
  - **Unidade sem data de fim = não concluída.** Nas planilhas antigas o **0** significa "não concluído" e nunca pode virar data.
  - Pacote da TM: Início, Quantidade total e Meta/dia. Sem fim informado, o app calcula por Início + Meta/dia em dias úteis.
- **Validação da TM da Macau Beach:**
  - **Protótipo:** bateu em **24 dos 26** serviços de apartamento. Regularização de Teto e Regularização de Parede diferiram só na última semana, porque as planilhas foram editadas depois do último salvamento da TM. A linha "Metais e Carenagens" apontava, por erro, para a planilha de Guarda-Corpo.
  - **Após a importação (corte 18/10):** 20 serviços iguais em todas as semanas, 2 iguais nas 4 primeiras semanas e 3 diferenças causadas por planilhas alteradas depois de 22/10 (ver seção 5).
- **Tela P1 "TM e pacotes" (26/10):** os números na Villa Áurea estão na seção 3.
- **Explicação técnica recebida (27/10):** "TM e pacotes" é o painel do ritmo de cada serviço e onde se cadastram os pacotes. "TM semanal" é a planilha no formato da Impacto, com diagnóstico por pacote e botão de plano de ação. As duas usam o mesmo cálculo.

### 2.8. Planejamento de curto prazo: metas da semana e PPC

- **Classificação:** REALIZADA (regras aplicadas no app por pedido meu). Uso em obra por mim: NÃO CONFIRMADO.
- **Regras da Impacto adotadas no app:**
  - **PPC mínimo de 90%** (o MGA usava 80%).
  - Meta não cumprida **não passa** para a semana seguinte.
  - **Causas padronizadas** e aviso de "meta sem causa".
- **Regras aplicadas da análise de 27/10 ("Analise do app gestão lean.docx"):**
  - Botão "Criar meta da semana" para assistente, engenheiro, gestor e planejamento.
  - Dia de criação da meta configurável por obra (padrão: **sexta-feira**).
  - A meta nasce em **rascunho** e o **gestor valida**. Depois de validada, o planejamento trava. Só gestor ou planejamento alteram, informando o motivo, que vai para um histórico. O realizado e as causas continuam livres.
  - **Alertas:** lembrete no dia. Passado o dia, gestor, engenheiro e assistente são cobrados, e supervisor e planejamento são avisados.
  - Botão **Vincular meta** no Controle Visual: mostra a meta da semana e o atraso da semana anterior. Os apartamentos escolhidos na meta pintam o visual de rosa ("planejado no mês").
- **Indicador registrado:** PPC da semana 1 de outubro na Macau = **93,48% (43 de 46)**, igual à planilha.

### 2.9. Gestão de compras / suprimentos das obras

- **Classificação:** REALIZADA (fornecimento das planilhas e decisão de carga dos dados reais). Uso operacional da planilha de compras por mim: NÃO CONFIRMADO.
- **Contextualização:** eu disse: *"estou mandando os checklists das obras e as planilhas de compras para você subir no aplicativo e começarmos a ter dados reais para ver como ficam os dashboards"*. Coloquei as planilhas na pasta do projeto.
- **Lógica do controle:** a partir do início de cada serviço (cronograma físico pacote × lote), calculam-se as datas de **levantamento, solicitação e entrega**. Cada item tem as etapas Levantado, Solicitado, Entregue e Iniciado.
- **Resultado da carga:** ver tabela na seção 7, com as linhas não lidas por inconsistência.
- **Problema apontado:** linhas cujo pacote ou lote não existe no cronograma da própria planilha (ver seção 5).

### 2.10. Planejamento a partir do Prevision e retirada do PFE

- **Classificação:** REALIZADA (decisão e fornecimento do acesso à API).
- **Decisões:**
  - Tirar o PFE do planejamento e usar o Prevision.
  - **Esconder a PFE do menu sem apagar.**
  - Informei que tinha a documentação e a chave da API e passei o link da documentação (api-docs.prevision.com.br).
  - O app **só lê** do Prevision, sem devolver o executado.
- **Funcionamento registrado:**
  - **Cartão "Planejamento (Prevision)" na tela Hoje:** avanço físico previsto e realizado, fim previsto, atraso e **IDP** (índice de prazo do Prevision).
  - **"Ver esteira":** lista de serviços com início, fim, locais concluídos, % previsto e % realizado. Serviço atrasado mais de 5 pontos percentuais fica em vermelho.
  - **Vínculo com as obras:** cada obra se liga ao projeto do Prevision pelo nome. Só a Macau foi conferida.
  - **Uso da API:** a primeira consulta leva cerca de 30 segundos e o resultado fica guardado por 6 horas. O Prevision pede cargas grandes antes das 8h e depois das 19h.
- **Números da Macau:** previsto 38,5%, realizado 40,2%, fim 01/09/2027, última medição 16/10/2026. Batem com o painel do Prevision.
- **Ainda propostos:** avanço físico de todas as obras no painel de Diretoria e Supervisor e uso das datas planejadas do Prevision na TM e na meta semanal (PROPOSTA OU PLANEJADA).

### 2.11. Jornada de implantação Lean e Central de planos de ação

- **Classificação:** REALIZADA (módulos levados ao app a partir das regras da Impacto). A situação da Jornada de cada obra está **pendente de definição por mim**.
- **Jornada de implantação:**
  - Mostra o estágio da obra, de "Pré-obra 1" até "Acompanhamento", com a pauta e o critério para avançar de cada encontro.
  - Permite registrar os encontros.
  - O botão "Aplicar na obra" libera os módulos daquele estágio. **Custo e mão de obra só são liberados com checklist ≥ 80%.**
- **Central de planos de ação:**
  - Reúne numa lista os planos da TM, as tarefas de Comunicação, Qualidade, Segurança, Almoxarifado, RH e Custo, e os planos novos.
  - Os atrasados aparecem primeiro e o **prazo original nunca muda**.
  - No protótipo, o quadro tinha as colunas A fazer, Fazendo, Para validar e Concluído, e só o gestor fecha um plano.
- **Caminhos de implantação:** citados nas conversas como "caminhos A, B e Multiplicação", com encontros, papéis e controles exigidos. O detalhamento está no documento de consultoria, que não foi relido.

### 2.12. Estruturação do ambiente de dados (nuvem própria local) e cuidados com dados reais

- **Classificação:** REALIZADA (decisão minha; execução técnica pela IA).
- **Decisões:**
  - "Servidor local simples".
  - Uso por enquanto "só eu, para testar".
  - Dados "só neste computador, por enquanto".
  - Publicação final pelo TI, num projeto Supabase da Impacto.
- **Pedidos relacionados:**
  - Retirar o logout automático por inatividade (antes eram 5 minutos).
  - Criar um atalho na área de trabalho para iniciar o app depois que o servidor caiu.
  - Autorizei a correção da base local depois de um teste que apagou a empresa cadastrada (ver seção 5).

### 2.13. Padronização visual e de usabilidade do aplicativo

- **Classificação:** REALIZADA (requisitos e revisões definidos por mim).
- **Princípio que estabeleci:** *"em todo o site mantenha o aspecto inovador e tecnológico e sempre buscando agrupar funcionalidades iguais, evitando ter muitos botões soltos pelo site poluindo o visual"*. Também: *"temos muitos gráficos que trazem um aspecto de velho, de Excel"*.
- **Pedidos registrados:**
  - **Sem emojis em todo o app** (cerca de 2.850 retirados).
  - Botões soltos (importar, exportar, relatórios, regras do pacote, ZIP) agrupados num menu **Configurações** por grupo (Importação, Exportação, Relatórios e regras, Manutenção), em todas as telas.
  - Gráficos com aparência tecnológica: barras com degradê e meta em filete ciano, medidor segmentado, radar e linhas suaves.
  - **Menu lateral e telas:**
    - Menu lateral no estilo do App Checklist, sem ícones de manual e sem o símbolo do MGA.
    - Botão "← Voltar".
    - Tela inicial sem a etapa "Empresas", com **Obras ativas / Obras concluídas** "como na tela do Prevision".
    - Obra aberta sem botões e painéis poluindo a tela.
  - **Login:**
    - Tela de entrada **"Gestão Lean"** com fotos das obras passando, logo da empresa e frases.
    - Transições lentas e suaves: foto 9,5 s, frase 7 s.
  - **Barra superior e menu do usuário:**
    - Menu do usuário com o grupo **Backup** unificado e sem símbolos.
    - Barra superior com usuário e botão claro/escuro à direita e nome da obra no centro.
    - Para Diretor, Supervisor e Planejamento, seletor de obra no centro da barra.
  - **Sistema de design (handoff Fase 1, 26/10):**
    - Temas escuro (padrão) e claro, barra superior de 60 px e menu lateral de 248 px, recolhível para 72 px.
    - Por pedido meu, o fundo voltou ao tom azul anterior com o grafismo da marca: escuro #08113A, claro #EEF3FB.
  - **Correções de telas apontadas por mim:**
    - Texto ilegível no "dash da semana em análise".
    - Botões de renomear, desativar e clonar sobrepostos ao nome do serviço no modo lista da Produtividade.
    - Botão de tema e menu do usuário sumindo dentro dos módulos.
    - Espaços brancos na janela de pastas da obra.
- **Importância:** a principal crítica ao MGA era ser pesado, tumultuado e com cara de Excel. Visual leve é tratado como requisito do projeto.

### 2.14. Conferência e saneamento de dados das planilhas de obra

- **Classificação:** PARTICIPAÇÃO. Eu pedi e forneci as planilhas; as divergências foram levantadas pela IA. Os pontos estão como **"para conferir com a obra"**, sem confirmação de que conferi.
- **Achados:** ver seção 5 (Acabamento Elétrico, Guarda Corpo, Louças e Metais, datas de fim anteriores às de início, cópias vazias de serviços, linhas de compras sem pacote).

### 2.15. Tentativa de integração e uso de ferramentas de IA no trabalho de engenharia

- **Classificação:** REALIZADA.
- **Descrição:**
  - Usei o Claude Code para o desenvolvimento.
  - Pedi um arquivo de contexto para continuar o trabalho em outra conversa ("CONTEXTO-NOVO-CHAT.md").
  - Preparei pedidos de redesenho para o Claude Design: `docs/09_prompt_claude_design_app_completo.md` e `docs/09_prompt_claude_design_tm_produtividade.md`, com capturas das telas "TM e pacotes" e "Controle de Produtividade".
  - Depois adicionei a pasta do handoff de design ao projeto.

---

## 3. Obras e empreendimentos mencionados

> A situação de implantação Lean de cada obra (implantada, em implantação, pré-obra) aparece nas conversas como informação do arquivo de instruções do projeto. Na Jornada do app essa situação ficou **em branco**, para eu definir.

### 3.1. Macau Beach
- **Empresa:** Construtora Impacto.
- **Tipo:** edifício residencial com **torres**. Aparecem torres L, I, O e R; a quantidade de torres não está confirmada.
- **Unidades:** **312**, com 8 no térreo, conforme respondi.
  - Divergência registrada: o Caderno de Abastecimento indica 7 aptos no térreo, o que daria 309 = 3 × (7 + 12 × 8).
  - A planilha de produtividade tem 8 colunas no térreo, o que dá 312.
  - A torre L tem 103 linhas na Cerâmica (7 + 96).
- **Situação Lean:** implantada.
- **Produtividade:**
  - 28 serviços × 312 unidades = **8.736 unidades** importadas.
  - Planilhas em `Produtividade/Barbara`.
  - Na Estrutura existem duas bases: "Base (NOVO)" com 312 unidades e a antiga com 160. A oficial não está definida.
  - Instalação de Esquadria soma duas produtividades na TM da planilha: "25. Portas de Alumínio" e "31. Instalação de Esquadria".
- **TM:** 28 pacotes criados com meta provisória de 1 unidade/dia; 11 serviços apareceram "fora da meta" por causa disso. A validação da TM e o PPC estão na seção 2.7 e 2.8.
- **Checklist:** mar/26 86,7%, abr/26 78,9%, jul/26 87,2%, ago/26 **96,1%** (▲ 6,9 pp). Setembro em diante em branco.
- **Compras:** 119 itens; 9 linhas não lidas; 17 ações vencidas.
- **Prevision:** previsto 38,5%, realizado 40,2%, fim 01/09/2027, última medição 16/10/2026.
- **Nota de Aderência Lean:** 92,6% (checklist + compras) e depois 73,8% (com TM provisória).
- **Supervisor:** Fabio.
- **Obra auxiliar "Macau Beach – Gráfico de Vales":** cadastro vazio, criado em 15/10/2026 e vindo do MGA. Mandei apagar.

### 3.2. Villa Áurea
- **Tipo:** edifício residencial em **blocos**: 368 apartamentos, 92 itens de hall, 322–330 panos de fachada, 23 blocos.
- **Situação Lean:** implantada.
- **Produtividade:**
  - 48 serviços, **11.896 unidades**, 48 pacotes da TM, 185 equipes, 74 suportes, 48 visuais.
  - Serviços por pavimento (hall, prumadas, sistema de incêndio, corrimão) usam o pavimento como unidade ("TÉRREO", "1º PAV").
  - A produtividade aparece em **17%** no painel: poucos serviços em andamento com lançamento nos últimos 7 dias.
- **Checklist:** mar/26 68,8%, abr/26 73,0%, mai/26 87,4%, ago/26 **89,9%**.
- **Compras:** 277 itens; 191 levantados, 188 solicitados, 144 entregues, 109 iniciados; 40 linhas não lidas. É a obra que mais precisa de revisão da planilha.
- **TM (tela P1, semana 19 a 25/10/2026):**
  - 24 de 48 serviços em plano de ação.
  - 18 parados há mais de 7 dias úteis.
  - 24 planos sem justificativa.
  - Fim previsto pelo Prevision em 22/06/2027, **atrasado 29 dias**.
- **Supervisor:** Silvio.

### 3.3. Porto Arboreto
- **Situação Lean:** em implantação.
- **Compras:** 89 itens, 116 pacotes e 91 lotes. Foi a primeira planilha usada para testar a importação.
- **Supervisor:** Fabio.

### 3.4. Silvia Fonseca Diniz
- **Situação Lean:** em implantação.
- **Compras:** 104 itens; 2 linhas não lidas.
- **Supervisor:** Fabio.

### 3.5. Raízes Jabotiana
- **Tipo:** **obra horizontal, 164 casas**. Cadastrada como "obra de casas". O mapa da obra ainda não estava ajustado para casas numa fileira só.
- **Situação:** pré-obra.
- **Compras:** a planilha tinha só o cronograma de pacotes e lotes, sem contratações (0 itens); 3 linhas não lidas.
- **Supervisor:** Silvio.

### 3.6. Turim
- Aparece entre as obras cadastradas, com foto, mas não está na lista de obras do arquivo de instruções do projeto. Ficou só com nome e foto. Não há outras informações.

---

## 4. Ferramentas, softwares e metodologias

| Ferramenta / método | Uso registrado nas conversas |
|---|---|
| **Planilhas Excel de obra** | Fonte dos dados reais. Uma planilha de produtividade por serviço (aba "Base" com estrutura torre/pavimento/unidade e datas), planilha da TM, planilha de meta, planilha de compras (cronograma pacote × lote, contratações) e checklist mensal ("Checklist - Macau 2.0 (réguas).xlsx", layout "teste2.0"). |
| **MGA (controle de produtividade)** | Sistema em HTML usado pela Impacto. Módulos: produtividade, PFE/TM, meta de curto prazo, macrofluxo, multimomento, controle visual, qualidade, segurança, RH, almoxarifado, comunicação, concreto e massas, simulação de indireto, diário de obra. Virou a base do novo app. |
| **App Checklist** e **App Gestão de Compras** | Apps anteriores da Impacto (azul Impacto com degradê ciano, fontes Saira e Barlow, tema escuro). Foram incorporados ao app. |
| **Prevision** | Software de planejamento. Fonte do planejamento no lugar do PFE. Avanço físico previsto/realizado, fim previsto, IDP, "esteira" de serviços, medições. Integração via API, só leitura. |
| **Sienge** | Citado no MGA (IEC do custo via Sienge) e como integração futura. Uso por mim não descrito. |
| **Asana** | Citado como integração futura (contexto do projeto). |
| **TM** | Controle semanal de ritmo dos serviços por pacote: acumulado S1–S5, ritmo das 4 semanas, real/dia, meta/dia, fim previsto, semáforo, diagnóstico, justificativa e plano de ação. Organizada em "faixas" (grupos de serviços por etapa). No app aparece o cartão "Teste de Metas" — significado da sigla a confirmar. |
| **PFE** | Planejamento legado das planilhas. Escondido do app; não deve ser lido nem reproduzido. Significado da sigla não registrado. |
| **Meta de curto prazo / PPC** | Planejamento semanal com PPC (percentual de metas concluídas), causas padronizadas de não cumprimento, mínimo de 90%. |
| **Checklist de Gestão Lean** | Avaliação mensal da aderência das obras ao método (54 itens, réguas, pilares/macropilares/micropilares). |
| **Mapa do Tempo** | Registro diário (ex.: dias impraticáveis por chuva). Alimenta a pré-avaliação do item 1.1 e o desconto de dias na TM. Lançado também pelo estagiário. |
| **Cruz Verde** | Controle diário citado nos itens 1.25 e 1.26 do checklist. Lançado também pelo estagiário. Conteúdo do controle não detalhado. |
| **Controle Visual** | Grade torre × pavimento por serviço. Cores: cinza não iniciado, azul em execução, verde concluído, vermelho pendência, rosa planejado na meta. |
| **Gráfico de vales** | Gráfico do MGA dentro do controle de produtividade. |
| **Macrofluxo / Fluxo de serviços** | Sequência de serviços e ordem de execução dos pavimentos. |
| **Linha de balanço (Fachadas)** | Cronograma por pavimento das fachadas. Módulo novo, desligado por padrão. |
| **Multimomento** | Citado como módulo do MGA e como consolidações na pasta da Villa Áurea. |
| **Kanban e caderno de abastecimento** | Citados como fora da v1, com dependência no item 2.12 do checklist e na ficha do pacote. |
| **Gargalo / flexível** | Classificação dos serviços usada para ordenar a lista da TM (gargalo antes de flexível). Os códigos dos serviços eram provisórios. |
| **Jornada de implantação Lean** | Estágios de Pré-obra a Acompanhamento, encontros, liberação de módulos. |
| **Claude Code / Claude Design** | IA usada para programar o app e para pedir redesenho de telas. |
| **Git** | Histórico de versões do código, sem planilhas com dados pessoais. |
| **Supabase** | Banco e login previstos para a publicação pelo TI. Hoje há uma "nuvem própria" local que imita o Supabase. |

---

## 5. Problemas identificados e soluções discutidas

| # | Problema | Como foi identificado / causa | Solução | Situação |
|---|---|---|---|---|
| 1 | Controles espalhados em planilhas e 3 apps diferentes | Contexto do projeto | Aplicativo único a partir do MGA | **Implementada** (em desenvolvimento) |
| 2 | Código-fonte do MGA perdido | Relatado por mim | Cópia desmontada em arquivos editáveis, com histórico Git | **Implementada** |
| 3 | Visual pesado, "cara de Excel", muitos botões soltos | Avaliação minha | Sem emojis, menu Configurações, gráficos tecnológicos, sistema de design | **Implementada** |
| 4 | Diretoria recebendo informação irrelevante (compras) | Avaliação minha | Perfis de acesso por cargo, Nota de Aderência Lean | **Implementada** |
| 5 | Regras divergentes entre MGA e Impacto (PPC 80% × 90%, régua do checklist, PFE) | Comparação feita na junção | Vale a regra da Impacto | **Implementada** |
| 6 | **0 nas planilhas virava data** (00/01/1900), marcando unidade como concluída | Teste do importador | Qualquer número < 1 tratado como "sem data" | **Implementada** |
| 7 | Serviços por pavimento perdiam unidades (hall de 92 para 23 itens na Villa Áurea) | Conferência da importação | Importador passou a reconhecer a coluna de pavimento | **Implementada** |
| 8 | Código interno repetido sobrescrevia unidade (Suporte Ar Condicionado) | Conferência da importação | Código gerado maior; 2 unidades corrigidas | **Implementada** |
| 9 | **Acabamento Elétrico (Macau):** 16 unidades concluídas até 16/10; hoje só 8, todas com fim em 23/10 | Comparação da TM com gabarito de 22/10 | Conferir com a obra (provável perda de dado) | **Pendente** |
| 10 | **Guarda Corpo (Macau):** de nenhuma concluída para 48, oito toda sexta desde 18/09 | Idem | Conferir com a obra (provável preenchimento em lote) | **Pendente** |
| 11 | **Louças e Metais (Macau):** de 93 para 100 | Idem | Conferir com a obra | **Pendente** |
| 12 | Linha "Metais e Carenagens" da TM (Macau) apontava para a planilha de Guarda-Corpo | Validação da TM | Excluída do teste | Registrada |
| 13 | Datas de fim anteriores às de início (Villa Áurea): Metais e Carenagens 16, Emassamento 6, Tratamento de Fissuras Internas 6, Regularização interna 5 | Importação | Conferir com a obra | **Pendente** |
| 14 | Cópias vazias de serviços repetidos (Villa Áurea: "00. Acabamentos Elétricos" e "Gledson e Vitória/06. Metais e Carenagens") | Importação | Usadas as cópias com dados; confirmar que as vazias são sobras | **Pendente** |
| 15 | Linhas de compras com pacote ou lote fora do cronograma: Macau 9, Raízes 3, Silvia 2, Villa Áurea 40 | Carga das planilhas | Corrigir na origem | **Pendente** |
| 16 | Metas da TM provisórias (1 un./dia) distorcendo TM e Aderência | Após importação | Eu configuro as metas reais no módulo "TM e pacotes" | **Planejada** |
| 17 | Itens 1.2, 1.5, 1.7, 1.8, 1.9 e 2.4 do checklist sem regra de pré-avaliação | Implantação da pré-avaliação | Definir como medir cada um | **Pendente** |
| 18 | Itens do checklist que perdem sentido no app (ex.: 1.8 pergunta se a planilha da TM está atualizada; 1.5, 1.6 e 1.10 citam "planilha de metas/TM") | Análise da especificação | Nova versão do checklist voltada ao app | **Proposta** |
| 19 | Teste gravou empresa falsa na base local e apagou a empresa cadastrada | Tela em branco relatada por mim | Autorizei a correção: dados de teste marcados como excluídos e empresa recriada | **Implementada** |
| 20 | Obras repetidas e "Macau Beach – Gráfico de Vales" no seletor | Relatado por mim | Obra apagada; limpeza automática da lista do navegador | Implementada; **não confirmada na minha máquina** |
| 21 | Servidor do app caía e o site não abria | Relatado por mim | Atalho "Gestao Lean" na área de trabalho | **Implementada** |
| 22 | Logout automático após 5 min parado | Pedido meu | Removido | **Implementada** |

---

## 6. Conhecimentos técnicos relevantes

- **Princípio "cálculos nunca digitados":** TM, fim previsto, PPC, semáforo e notas do checklist são sempre derivados dos lançamentos. *(Regra do projeto aplicada no app.)*
- **Fim previsto pela TM:** (quantidade total − executado) ÷ ritmo, com o ritmo médio das 4 semanas, em dias úteis.
  - Ficaram para confirmar: descontar ou não feriados no ritmo de 4 semanas (na semana de 12/10 a planilha divide por 20 dias e o app por 19) e descontar dias marcados como "impraticável" de manhã e à tarde no Mapa do Tempo.
- **Unidade sem data de fim = não concluída.** O 0 das planilhas antigas é "não concluído".
- **Estrutura de unidades:** torre → pavimento → apartamento. Há serviços cuja unidade é o pavimento (hall, prumadas, incêndio, corrimão) ou o pano de fachada.
- **Faixas da TM:** agrupamento de serviços por etapa da obra. Serviço sem faixa aparece como "— sem faixa —" no Controle Visual.
- **PPC:** percentual de metas semanais concluídas. Mínimo de 90% na Impacto; causa obrigatória para meta não cumprida; meta não cumprida não migra para a semana seguinte.
- **Compras:** a partir da data de início do serviço no cronograma físico, retroage-se para obter levantamento, solicitação e entrega, com semáforo de vencimento.
- **Checklist:** régua por item, N/A, observação obrigatória nas notas baixas, fechamento mensal bloqueado se faltar algo, nota consolidada por pilar e micropilar, trilhas Campo e Sistema.
  - Divergência nas faixas: o manual do consultor usa verde 8–10, amarelo 6–8 e crítico abaixo de 6; o documento do checklist usa ≥ 90%, 60–89% e < 60%.
  - Divergência sobre quem edita o checklist: a Qualidade (documento de consultoria) ou o Multiplicador (especificação).
  - Plano concluído depois do prazo conta como atrasado no checklist (decisão do protótipo, a confirmar).
- **Liberação de módulos:** custo e mão de obra só com checklist ≥ 80%.
- **Prevision:** IDP = índice de prazo; avanço físico previsto × realizado por medição.

---

## 7. Indicadores, números e informações quantitativas

| Dado | Valor | Contexto |
|---|---|---|
| Unidades Macau Beach | 312 (8 no térreo) | Resposta minha; alternativa 309 em aberto |
| Serviços de produtividade Macau | 28 | Planilhas em `Produtividade/Barbara` |
| Unidades importadas Macau | 8.736 | 28 × 312 |
| Validação TM Macau (protótipo) | 24 de 26 serviços de apartamento | 2 diferenças com causa conhecida |
| Validação TM Macau (após importação, corte 18/10) | 20 iguais; 2 iguais nas 4 primeiras semanas; 3 divergentes | Planilhas alteradas depois de 22/10 |
| PPC Macau, semana 1 de outubro | 93,48% (43 de 46) | Igual à planilha |
| Checklist Macau | mar 86,7%; abr 78,9%; jul 87,2%; ago 96,1% | 2026 |
| Checklist Villa Áurea | mar 68,8%; abr 73,0%; mai 87,4%; ago 89,9% | 2026 |
| Média do painel (Macau + Villa) | 92,9% | Último checklist fechado |
| Itens de compras | Macau 119; Porto Arboreto 89; Silvia 104; Villa Áurea 277; Raízes 0 | Carga de 23/10 |
| Villa Áurea, etapas de compras | 191 levantados; 188 solicitados; 144 entregues; 109 iniciados | Cartão Hoje |
| Porto Arboreto, cronograma de compras | 116 pacotes; 91 lotes | — |
| Prevision Macau | previsto 38,5%; realizado 40,2%; fim 01/09/2027; medição 16/10/2026 | — |
| Prevision Villa Áurea | fim 22/06/2027; atraso 29 dias | — |
| Villa Áurea, produtividade | 48 serviços; 11.896 unidades; 368 aptos; 92 hall; 322–330 panos; 23 blocos | — |
| Villa Áurea, TM (19–25/10/2026) | 24/48 em plano de ação; 18 parados > 7 dias úteis; 24 planos sem justificativa | Tela P1 |
| Nota de Aderência Lean, pesos | Checklist 40%; Produtividade 20%; TM 20%; Compras 20% | Escolha minha |
| Aderência Macau | 92,6% → 73,8% | Antes e depois da TM provisória |
| Produtividade atualizada | Macau 91% dos serviços em andamento; Villa Áurea 17% | Lançamento nos últimos 7 dias |
| PPC mínimo | 90% (Impacto) × 80% (MGA) | Vale o da Impacto |
| Corte do checklist | 80% libera custo e mão de obra (app antigo 85%) | — |
| Faixas do checklist 2.0 | 90% / 60% | — |
| Checklist Impacto 2.0 | 54 itens (modelo antigo do MGA: 40) | — |
| Raízes Jabotiana | 164 casas | Obra horizontal |
| Testes automáticos | 44 → 56 → 59 → 64 | Evolução nas sessões |

---

## 8. Projetos, melhorias e contribuições profissionais

1. **Idealização e condução do aplicativo "Gestão Lean"**, unindo MGA, App Checklist, App Gestão de Compras e as regras Lean da Impacto num só sistema, com marca e visual próprios.
2. **Recuperação de uma ferramenta interna (MGA) sem código-fonte**, transformada em base editável e versionada.
3. **Definição da matriz de acesso por cargo** (Planejamento, Diretor, Supervisor, Gestor, Engenheiro, Assistente, Estagiário), com a lógica de que cada nível vê o que precisa para decidir.
4. **Criação do indicador composto "Nota de Aderência Lean"** (checklist, produtividade, TM e compras) e do painel geral com ranking das obras.
5. **Pré-avaliação automática de itens do checklist** a partir dos dados do app, sempre com confirmação do verificador.
6. **Carga de dados reais das obras:** checklists, compras de 5 obras e produtividades da Macau Beach e da Villa Áurea, com validação da TM contra as planilhas.
7. **Substituição do PFE pelo Prevision** como fonte do planejamento, com integração só leitura.
8. **Regras de meta semanal** com validação do gestor, trava do planejamento, histórico de alterações e alertas de cobrança.
9. **Padronização visual** com foco em leveza e agrupamento de funções.
10. **Registro das decisões** de nº 19 a 49 no arquivo de decisões do projeto.

---

## 9. Informações complementares

- **Pessoas citadas:**
  - Minha **coordenadora**, coautora do MGA segundo eu disse; nome não citado.
  - **Camila** (Multiplicadora Lean, segundo o contexto do projeto; tinha acesso no app).
  - **Romário** (tinha acesso no app; função não informada).
  - Supervisores **Silvio** e **Fabio**.
  - O consultor do MGA é citado como **Marcel (Macedo Faria)**.
- **Uso previsto do app:** em campo, no celular e tablet, online e offline.
- **Situação técnica no fim do período:**
  - O app roda em `localhost` no meu computador e é iniciado pelo atalho "Gestao Lean".
  - Várias mudanças das sessões de 23 a 27/10 **ainda não estavam commitadas** no Git. Eu disse: *"ainda não commite; vou olhar as telas primeiro"*.
  - A publicação ficou para o TI, com um projeto Supabase da Impacto.
- **Segurança:** a chave da API do Prevision foi colada numa conversa. Foi recomendado gerar uma chave nova.
- **Recomendação registrada sem resposta minha:** guardar o código fora do OneDrive por causa da sincronização da pasta `node_modules`.

---

## 10. Pontos que precisam de confirmação

1. **Autoria do MGA.** Eu disse que o HTML *"foi desenvolvido por mim, juntamente com a minha coordenadora"*. Os documentos do projeto e o código citam o MGA como sistema do consultor **Marcel (Macedo Faria)**, com criadores "Kawê e Marcel" e marca d'água do consultor. Respondi que "temos autorização" para copiar. Antes de usar isso num relatório, é preciso esclarecer qual foi a minha participação no MGA original.
2. **Autoria dos apps Checklist e Gestão de Compras:** citados como "desenvolvidos antes", sem dizer por quem.
3. **Meu cargo formal:** nas conversas aparecem "Multiplicador Lean" (perfil no app e documentos) e "setor de planejamento". O cargo exato e se sou estagiário, engenheiro ou analista não foram declarados.
4. **Aplicação do checklist em campo por mim:** não declarada. Também não está claro quem fez as avaliações cujas notas foram carregadas.
5. **Configuração das metas da TM:** eu disse que faria; não há confirmação de que fiz.
6. **Significado das siglas TM e PFE:** não registrado. O app usa o cartão "Teste de Metas", o que sugere que TM = Teste de Metas.
7. **Unidades da Macau Beach:** 312 (resposta minha) ou 309 (Caderno de Abastecimento).
8. **Base oficial da Estrutura da Macau:** "Base (NOVO)" com 312 ou a antiga com 160.
9. **Divergências das planilhas da Macau** (Acabamento Elétrico, Guarda Corpo, Louças e Metais) e **da Villa Áurea** (datas de fim anteriores às de início, cópias vazias): não confirmadas com as obras.
10. **"164 ações de compra vencidas":** apareceu como exemplo da faixa "Atenção agora" da tela Hoje, sem indicação de qual obra. Não confundir com as 17 ações vencidas da Macau usadas na Nota de Aderência.
11. **Regras pendentes:**
    - Pré-avaliação dos itens 1.2, 1.5, 1.7, 1.8, 1.9 e 2.4.
    - Desconto de feriados e chuva na TM.
    - "Plano concluído depois do prazo conta como atrasado".
    - Faixas do checklist (manual × documento).
    - Quem edita o checklist (Qualidade × Multiplicador).
12. **Estágio da Jornada de cada obra:** ficou em branco no app, para eu definir.
13. **Obra Turim:** cadastrada no app, sem informações sobre tipo ou situação.
14. **Conteúdo da análise "Analise do app gestão lean.docx":** conhecido só pelo resumo do que foi aplicado. Um trecho ficou sem entendimento: *"as metas cadastradas então na TM. Nos visuais."*
15. **Quantidade de torres da Macau Beach:** aparecem torres L, I, O e R; o número total não foi confirmado.
