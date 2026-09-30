# Gustavo Muniz — CV

Oi, sou o Gustavo. Desenvolvedor web desde 2018, tecnólogo em Análise e
Desenvolvimento de Sistemas e fundador da [Agência Upgrade](https://agenciaupgrade.com.br),
em São Paulo.

Construo aplicações em **React e Next.js com Payload CMS**, sistemas em
**Laravel** e sites em **Astro** (Cloudflare Workers) e **WordPress/Bricks**.
Comecei no suporte e na infraestrutura de TI, então costumo conduzir o projeto
inteiro: escopo, arquitetura, código, hospedagem e manutenção.

Alguns números de projetos recentes:

- E-commerce B2B reconstruído do zero: carregamento de **15 s para menos de 2 s**
  e plugins ativos de **43 para 12**.
- Site corporativo com **100 no PageSpeed Insights** numa hospedagem limitada,
  sem troca de servidor.
- Sistema de cantina digital (PDV + app) com **mais de 5.000 usuários**, que
  tirou o dinheiro físico da cantina de um colégio.
- [Canopy](https://github.com/Agencia-Upgrade/Canopy): boilerplate WordPress
  open source com Bedrock, Timber 2, PHPStan e CI/CD, com meta de WCAG 2.2 AA.

Hoje estou na Multiverso das Letras, cuidando das plataformas em React/Next.js
e de mais de 20 sites do grupo. Topo **CLT, PJ ou freelance**, remoto, híbrido
ou presencial.

**Contato:** [gustavomunix98@gmail.com](mailto:gustavomunix98@gmail.com) ·
[LinkedIn](https://www.linkedin.com/in/gustavomunix)

---

## O que é este repositório

Meu currículo escrito como código. Todo o conteúdo e o design ficam em um
único arquivo, [`Gustavo_Muniz_CV.yaml`](Gustavo_Muniz_CV.yaml), e o PDF é
gerado pelo [RenderCV](https://rendercv.com) (Typst por baixo). Ninguém edita
o PDF à mão.

Por que assim:

- **Histórico:** cada mudança no CV vira um commit, com diff legível.
- **Consistência:** o layout é declarado uma vez e não quebra quando o texto
  muda.
- **Versões por vaga:** uma cópia do YAML gera um recorte sob medida sem mexer
  no principal.
- **ATS:** o PDF sai com texto selecionável, sem tabelas, colunas ou imagens,
  e passa em leitor automático.

## Gerar o PDF

Requisitos: Python 3.12+ e RenderCV 2.8+.

```bash
uv tool install "rendercv[full]"
rendercv render Gustavo_Muniz_CV.yaml
```

A saída vai para `rendercv_output/` (PDF, PNG, Typst, Markdown e HTML). A pasta
é ignorada pelo git, porque tudo se reconstrói a partir do YAML.

O telefone não fica no repositório, que é público. Para o PDF que vai ser
enviado, passe o número na hora de renderizar:

```bash
rendercv render Gustavo_Muniz_CV.yaml --cv.phone "+55..."
```

Durante a edição, o modo watch re-renderiza a cada save:

```bash
rendercv render Gustavo_Muniz_CV.yaml --watch
```

## Estrutura do YAML

| Bloco | O que controla |
| --- | --- |
| `cv` | Nome, contatos e seções (resumo, experiência, formação, competências, disponibilidade) |
| `design` | Tema `classic` em A4, margens, cores, tipografia e espaçamentos |
| `locale` | `portuguese`: nomes de meses e termos como "presente" |

O alvo é **uma página A4**. Se o render gerar `Gustavo_Muniz_CV_2.png`, o texto
passou do limite. Corte texto primeiro e só depois mexa em
`typography.font_size.body` ou `typography.line_spacing`.

## Armadilhas do formato

- **Dois-pontos em texto livre precisa de aspas.** `summary: Assumi o projeto:
  reorganizei` é YAML inválido. Envolva o valor em `"..."`.
- **Nunca use ` - ` no meio de um highlight.** O renderizador trata o hífen
  cercado de espaços como início de um novo item e parte o bullet em dois.
  Use `:` ou vírgula.
- **Unidades usam espaço não separável** (`2 s`, com U+00A0), para o número
  não ficar numa linha e a unidade na outra.

## Versões derivadas

Sob medida para uma vaga, sem editar o principal:

```bash
cp Gustavo_Muniz_CV.yaml vagas/nome-da-empresa.yaml
rendercv render vagas/nome-da-empresa.yaml -o rendercv_output/nome-da-empresa
```

Reordenar bullets costuma dar mais resultado que reescrevê-los, porque o topo de cada
experiência é o que o recrutador lê.

Em inglês: troque `locale.language` para `english`, traduza o bloco `cv` e
mantenha em paralelo como `Gustavo_Muniz_CV_EN.yaml`.
