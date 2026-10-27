# ADR-0001: CV como código com RenderCV

## Status

Aceito.

## Data

Decidido em 2026-09-30, registrado em 2026-10-27.

## Contexto

O CV precisa mudar com frequência para vagas diferentes, manter histórico de
alterações e gerar um PDF que passe por ATS. Editar PDF ou documento visual à
mão torna diff, revisão e versão por vaga impossíveis.

## Decisão

Manter o conteúdo e o design em um único YAML versionado, renderizado pelo
RenderCV com Typst. O PDF é artefato de build, não fonte. A saída fica em
`rendercv_output/`, ignorada pelo git. O release publica o PDF mais recente.

## Alternativas consideradas

### Word ou Google Docs

- Prós: edição visual simples.
- Contras: diff ruim, versão por vaga frágil, layout quebra ao editar texto.
- Rejeitado: o histórico e a revisão por commit são parte do objetivo.

### HTML próprio com Puppeteer

- Prós: controle total do layout e do CSS.
- Contras: mais código para manter, mais chance de regressão de página.
- Rejeitado: o RenderCV já resolve tipografia, ATS e página.

### Canva ou editor visual

- Prós: rápido para um currículo único.
- Contras: sem diff, sem versão, exporta PDF com texto inconsistente.
- Rejeitado: não atende ao uso por vaga nem à revisão por agente.

## Consequências

- Toda mudança passa por YAML e render.
- O PDF é reconstruível a qualquer momento.
- A página é o limite rígido: conteúdo novo exige corte.
- O repositório pode ser público sem telefone nem pretensão salarial.
