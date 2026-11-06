# Contexto para continuar em um novo chat — Aplicativo Lean (Construtora Impacto)

> Cole este arquivo (ou peça para o novo chat lê-lo) no início da conversa.
> Pasta do projeto: `C:\Users\ivan\OneDrive - IMPACTO CONSTRUÇÕES\Aplicativo Lean para Obras`
> Situação em 23/10/2026. Usuário: Ivan Rocha (Multiplicador Lean, Construtora Impacto). Fala português; prefere explicações simples, sem jargão de TI.

## 1. O que é
Um único **Aplicativo Lean** para a gestão Lean das obras da Impacto. Ele junta quatro coisas que existiam separadas:
1. **MGA** (sistema do consultor Marcel/Macedo Faria, uso autorizado — decisão 19): é a **base** do app. Veio de uma página HTML salva do navegador (v457); o código-fonte original se perdeu.
2. **App Lean** (React, pasta `app/`): suas regras foram levadas para dentro do Aplicativo Lean. A pasta `app/` ficou só como referência (o Ivan não autorizou apagar).
3. **App Checklist Lean** (`..\app checklist`, React): telas unidas ao módulo Checklist.
4. **App Gestão de Compras** (`..\app gestão de compras`, Next.js + Postgres): recriado dentro do app.

Regra geral: **onde MGA e Impacto divergem, vale a regra da Impacto** (decisão 22).

## 2. Leia primeiro (no projeto)
- `CLAUDE.md` — regras de trabalho (obrigatório).
- `docs/06_decisoes_e_pendencias.md` — decisões 1–30 e pendências. **Decisão registrada prevalece.**
- `aplicativo-lean/LEIA-ME.md` — estrutura dos arquivos e como rodar.
- `aplicativo-lean/ANALISE-FUNCIONAL.md` — todas as telas/regras herdadas do MGA.
- `00_PROMPT_PRINCIPAL.md` e `docs/01..05` — especificação original.

## 3. Como o código está organizado (`aplicativo-lean/`)
App de **arquivo único**: o `ferramentas/build.mjs` junta `src/` em `dist/AplicativoLean-dev.html`.
- `src/index.template.html` — HTML com marcadores `<!--@inline:arquivo-->`; o build também troca `@dataurl:caminho` por imagens/arquivos embutidos.
- `src/js/04-app.js` — código principal herdado do MGA (≈58 mil linhas, formatado). Edições pontuais e com cuidado.
- Arquivos novos (preferir criar arquivo novo a mexer no 04):
  - `00-ambiente-dev.js` — **proteção**: dados do navegador isolados (prefixo `MGA_DEV::`) e **nuvem só leitura** (gravações bloqueadas). `99-ajustes-dev.js` desliga a auto-atualização.
  - `00-marca-dados.js`, `06-marca-impacto.js`, `css/12` — marca Impacto (logos de `LOGOS/`, fotos de `OBRAS/`; regerar com `npm run marca`).
  - `07-regras-impacto.js` — regras da Impacto (TM no formato da planilha, PPC 90%, planos, checklist 2.0, jornada) em `window.LeanImpacto`.
  - `08-modulos-impacto.js` — módulos Jornada de implantação, Central de planos de ação, TM semanal.
  - `09-compras.js` + `css/14` — Gestão de Compras (`window.ComprasImpacto`, dados em `DB.compras`).
  - `10..13-checklist-*.js` + `css/16..19` — Checklist: base comum (`window.ChkLean`, gráficos SVG, fotos em `DB.checklistFotos`), Resultado + apontamentos com fotos, Análises + Diretoria (várias obras), Relatórios (PDF executivo/diretoria e planilha teste2.0 a partir de `src/modelos/modelo-checklist.xlsx`).
  - `14-menu-lateral.js` + `css/20` — menu lateral e botões no padrão do app Checklist.
  - `15-dados-iniciais*.js` — obras e dados iniciais (gerados por `ferramentas/gerar-dados-iniciais.mjs`).
  - `css/15-tema-lean.css` — tema (tokens `--lean-*`, escuro padrão, fontes Saira/Barlow, azul `#2E4190` → ciano `#12A7DE`).
- Testes: `testes/` (59 testes: regras + números reais do Macau, compras, planilha teste2.0) — `npm test`.

## 4. Como rodar
Dentro de `aplicativo-lean`: `npm install` (uma vez), depois `npm run dev` → **http://localhost:5501** (ou `npm run build` e abrir `dist/AplicativoLean-dev.html`). Login com o usuário real do MGA; a nuvem é **só leitura**.

## 5. O que já foi feito (commits no Git)
1. Cópia editável do MGA, marca Impacto.
2. Etapa 1 da junção: regras Impacto, checklist 2.0 (54 itens, régua por opção, N/A, observação obrigatória, faixas 90/60, corte 80%), PPC mínimo 90%, meta não cumprida não passa de semana, causas padronizadas; módulos Jornada, Central de planos, TM semanal.
3. Nome "Aplicativo Lean", visual dos apps Checklist/Compras (escuro padrão), Gestão de Compras recriada.
4. Checklist unido: Resultado, Análises, Diretoria, Relatórios, apontamentos com fotos.
5. Menu lateral no padrão do app Checklist; sem ícones de manual; sem o anel do MGA; botão "← Voltar".
6. Obras e dados iniciais **só neste computador** (decisão 30): Villa Áurea, Porto Arboreto, Silvia Fonseca Diniz, Raízes Jabotiana (casas), Turim; checklists antigos (Macau 4 meses, Villa Áurea 4 meses) e compras do Porto Arboreto (89 itens).

## 6. Pendências principais (próximos passos sugeridos)
- **Nuvem própria do Aplicativo Lean** (projeto Supabase separado, recomendado) — hoje nada é gravado na nuvem; os dados novos ficam só no navegador do Ivan.
- **Etapa 2 da junção:** tela "Hoje" por perfil, visual mais leve, pré-avaliação do checklist com os dados do app, PFE fora do planejamento (Prevision).
- Sincronização com o **Prevision** (precisa guardar a chave no servidor).
- Abrir no Excel uma planilha teste2.0 gerada e conferir.
- Definir o estágio da Jornada de cada obra; decidir se a pasta `app/` pode ser apagada.
- O Ivan precisa apagar manualmente a pasta `C:\mga` (temporária; tudo dela já está no projeto).
- Pendências de negócio 1–25 em `docs/06` (seção "Pendências").

## 7. Cuidados (não quebrar)
- **Nunca** mudar `MGA_DEV.nuvem` para `"livre"` sem pedido explícito: grava no MGA em produção do consultor.
- **Não remover** a marca d'água do MGA (`window.__mgaWm`).
- Não versionar planilhas com dados pessoais (`*.xlsx` estão no `.gitignore`; exceção só para o modelo vazio).
- Perguntar antes de inventar regra de negócio; registrar decisões novas em `docs/06`.
- Testar no navegador com dados de teste num **endereço separado** (outra porta, ex. 5504) para não misturar com o login do Ivan; apagar os dados de teste no fim.
- Commits em português, terminando com a linha `Co-Authored-By` indicada pelo ambiente.
