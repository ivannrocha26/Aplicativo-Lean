# CLAUDE.md — Aplicativo Lean para Obras (Construtora Impacto)

Este repositório é o ponto de partida para construir o aplicativo de gestão Lean das obras da Construtora Impacto. Ele reúne num só lugar os controles que hoje estão espalhados em planilhas Excel por obra, e acompanha a implantação do método Lean (consultoria interna).

## Leia nesta ordem antes de qualquer código

1. `00_PROMPT_PRINCIPAL.md` — o que construir: escopo da v1, perfis, módulos, visual, regras, entregáveis. **É a especificação principal.**
2. `docs/06_decisoes_e_pendencias.md` — decisões já tomadas pelo usuário (Ivan) e o que ainda está aberto. Decisão registrada aqui prevalece sobre qualquer suposição.
3. `docs/03_regras_tm_produtividade.md` — como a TM e a produtividade funcionam hoje, fórmulas e armadilhas. Base das regras de cálculo.
4. `docs/04_checklist_lean.md` — especificação completa do checklist mensal (itens, réguas, cálculo, modelo de app).
5. `docs/02_consultoria_lean.md` — como funciona a implantação Lean (caminhos, encontros, controles exigidos, papéis).
6. `docs/01_inventario_documentacao_obra.md` — inventário de todos os controles existentes na pasta "Documentação de obra" (Macau Beach), com estrutura de colunas e problemas.
7. `docs/05_referencia_mga.md` — sistema MGA (Macedo Faria): referência funcional.
8. `aplicativo-lean/LEIA-ME.md` e `aplicativo-lean/ANALISE-FUNCIONAL.md` — cópia editável do MGA (v457), com autorização de uso (decisão 19).

## Regras de trabalho

- **Idioma:** toda a interface, mensagens, documentação e comentários de negócio em português do Brasil.
- **Pergunte antes de inventar regra de negócio.** Se algo não está nos documentos ou está marcado [ABERTO], pergunte ao usuário em vez de presumir. Registre cada nova decisão em `docs/06_decisoes_e_pendencias.md`.
- **Um aplicativo só: o Aplicativo Lean (`aplicativo-lean/`), feito a partir do MGA** (decisões 22 e 25). Os apps Checklist (`../app checklist`) e Gestão de Compras (`../app gestão de compras`) estão sendo unidos a ele (decisões 26 e 27); os dois antigos ficam só como referência. Visual = o do handoff de design Fase 1 (`docs/design_handoff_gestao_lean_fase1/`, decisão 48), escuro como padrão. As regras do app Lean foram levadas para dentro dele: `aplicativo-lean/src/js/07-regras-impacto.js` (TM, PPC, checklist 2.0, jornada, planos — testadas em `aplicativo-lean/testes`, `npm --prefix aplicativo-lean test`) e `aplicativo-lean/src/js/08-modulos-impacto.js` (Jornada, Central de planos de ação, TM semanal). Onde MGA e Impacto divergem, **vale a regra da Impacto**. A pasta `app/` (React) ficou só como referência até decidirem apagá-la; não desenvolver nela. A marca no MGA é a da Impacto (logos em `LOGOS/`, fotos em `OBRAS/`, gerar com `npm --prefix aplicativo-lean run marca`). Não remover a marca d'água do MGA (`window.__mgaWm`).
- **MGA dev nunca grava na nuvem oficial:** `aplicativo-lean/src/js/00-ambiente-dev.js` deixa a nuvem só leitura e isola os dados do navegador. Não mudar para `"livre"` sem pedido explícito.
- **Visual leve é requisito, não detalhe** (seção 8 do prompt): a principal crítica ao MGA é ser pesado, tumultuado e com cara de Excel.
- **Sem PFE.** O planejamento vem do Prevision (API). A aba PFE das planilhas é legado e não deve ser lida nem reproduzida.
- **Cálculos nunca digitados:** TM, fim previsto, PPC, semáforo e notas do checklist são sempre derivados dos lançamentos.
- **Unidade sem data de fim = não concluída.** Nas planilhas antigas o valor 0 significa "não concluído" — nunca tratar como data.
- **Dados reais das obras** ficam no SharePoint/OneDrive da Impacto (caminhos em `docs/01`). Não versionar planilhas com nomes, salários ou dados pessoais neste repositório; para testes, usar dados anonimizados.
- **Validação dos cálculos:** reproduzir os números da TM e do checklist da obra Macau Beach (ver `docs/03` e `docs/04`) em testes automatizados.

## Contexto rápido

- Obras: Macau Beach e Villa Áurea (implantadas), Porto Arboreto e Silvia Fonseca Diniz (em implantação), Raízes Jabotiana (pré-obra, 164 casas — obra horizontal).
- Perfis: Diretoria, Multiplicador Lean (Ivan e Camila), Supervisor de várias obras, Gestor da obra, Engenheiro de campo, Assistente/Estagiário.
- Uso em campo: celular e tablet, online e offline.
- Integração na v1: Prevision (API). Futuro: Asana, Sienge.
