# Currículo de Gustavo Muniz

Oi, sou o Gustavo. Desenvolvedor full stack desde 2018, tecnólogo em Análise e
Desenvolvimento de Sistemas e fundador da Agência Upgrade, em São Paulo.

Construo aplicações em **React e Next.js com Payload CMS**, sistemas em
**Laravel** e sites em **Astro** (Cloudflare Workers) e **WordPress/Bricks**.

Projetos recentes:

- E-commerce B2B da Cabekla, reconstruído sobre o Canopy, com WooCommerce,
  painel administrativo próprio, preço por perfil de cliente e checkout em
  etapas. A equipe do cliente passou a atualizar a loja sozinha no primeiro dia
  após o treinamento.
- Sistema de cantina digital (PDV e app) usado por mais de 5 mil pessoas, que
  tirou o dinheiro físico da cantina de um colégio.
- [Canopy](https://github.com/Agencia-Upgrade/Canopy): boilerplate WordPress
  open source com Bedrock, Timber 2, PHPStan e CI/CD, com meta de WCAG 2.2 AA.
  Roda em produção na Cabekla.

Hoje estou na Multiverso das Letras, cuidando das plataformas em React/Next.js
e de mais de 20 sites do grupo. Topo **CLT ou PJ**, remoto, híbrido
ou presencial.

**Contato:** [gustavomunix98@gmail.com](mailto:gustavomunix98@gmail.com) ·
[LinkedIn](https://www.linkedin.com/in/gustavomunix)

**[Baixar o CV em PDF](https://github.com/gustavomunix/cv/releases/latest/download/Gustavo_Muniz_CV.pdf)**

---

## O que é este repositório

Meu currículo escrito como código. Todo o conteúdo e o design ficam em um
único arquivo, [`Gustavo_Muniz_CV.yaml`](Gustavo_Muniz_CV.yaml), e o PDF é
gerado pelo [RenderCV](https://rendercv.com) (Typst por baixo). Ninguém edita
o PDF à mão.

Cada mudança no CV vira um commit com diff legível, e o layout, declarado uma
vez, não quebra quando o texto muda. Uma cópia do YAML gera a versão para uma
vaga sem mexer no principal.

## Gerar o PDF

Requisitos: Python 3.12+ e RenderCV 2.8+.

```bash
pipx install "rendercv[full]"
rendercv render Gustavo_Muniz_CV.yaml
```

A saída vai para `rendercv_output/` (PDF, PNG, Typst, Markdown e HTML). A pasta
é ignorada pelo git, porque tudo se reconstrói a partir do YAML.

O telefone não fica no repositório, que é público. Para o PDF que vai ser
enviado, passe o número na hora de renderizar:

```bash
rendercv render Gustavo_Muniz_CV.yaml --cv.phone "+55..."
```

A cada push em `main` que altere o YAML, a action
[`release-pdf.yml`](.github/workflows/release-pdf.yml) renderiza o PDF (sem
telefone), falha se passar de uma página e publica um release novo. O link de
download acima sempre aponta para o último.

Durante a edição, o modo watch re-renderiza a cada save:

```bash
rendercv render Gustavo_Muniz_CV.yaml --watch
```

## Estrutura do YAML

| Bloco | O que controla |
| --- | --- |
| `cv` | Nome, contatos e seções (resumo, experiência, projetos, formação, competências) |
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
- **Unidades usam espaço não separável** (`16 TB`, com U+00A0), para o número
  não ficar numa linha e a unidade na outra.

## Versões derivadas

Sob medida para uma vaga, sem editar o principal:

```bash
mkdir -p vagas
cp Gustavo_Muniz_CV.yaml vagas/nome-da-empresa.yaml
rendercv render vagas/nome-da-empresa.yaml -o rendercv_output/nome-da-empresa
```

A pasta `vagas/` fica fora do git.

Em inglês: troque `locale.language` para `english`, traduza o bloco `cv` e
mantenha em paralelo como `Gustavo_Muniz_CV_EN.yaml`.
