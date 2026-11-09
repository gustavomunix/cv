# Spec: CV do Gustavo Muniz

## Status

Aceita em 2026-10-27. Dono: Gustavo Muniz.

## Objetivo

Manter um currículo de uma página para vagas CLT ou PJ de desenvolvedor full
stack no Brasil, com foco em React/Next.js, PHP/Laravel e WordPress. O leitor
principal é recrutador técnico e hiring manager. O sucesso é uma leitura rápida
que leve a entrevista, não uma peça de portfólio.

## Fora de escopo

- Site da agência, portfólio e apresentações comerciais.
- Pretensão salarial e telefone no repositório público. O telefone entra só na
  hora de renderizar o PDF de envio.
- Vaga focada em mobile.
- Fato que exista só na versão em inglês. Os dois YAMLs contam a mesma coisa.

## Versão em inglês

Arquivo separado: `Gustavo_Muniz_CV_EN.yaml`. Traduz o YAML em português. Não
acrescenta cliente, número, data, cargo, tecnologia ou link.

- `locale.language` é `english`, para meses e "present" saírem em inglês.
- Chaves de seção em inglês: `summary`, `experience`, `projects`, `education`,
  `skills`.
- `degree_width` fica maior que no arquivo em português para "Technologist"
  não encostar no nome da instituição. O resto do design é o mesmo.
- Os caminhos de saída usam o nome `Gustavo_Muniz_CV_EN`, para o render não
  sobrescrever o PDF em português.
- Nomes próprios ficam como no original: Multiverso das Letras, Agência
  Upgrade, Prêmio Multiverso, Canopy, Cabekla, UNICV e os demais.
- A Multiverso das Letras não é cliente da Agência Upgrade.
- Mudou um fato num arquivo, atualize o outro no mesmo commit.

## Premissas

1. O CV é público, então todo cliente citado precisa de autorização.
2. O PDF precisa passar por ATS: texto selecionável, sem tabela, coluna ou
   imagem no corpo.
3. Uma página A4 é limite rígido. Conteúdo novo exige corte de conteúdo antigo.
4. Os fatos valem para a data da última revisão. Mudança de cargo, cliente ou
   resultado exige atualização da spec de conteúdo antes do YAML.

## Stack

- RenderCV 2.8 com Typst.
- Tema `classic`. Locale `portuguese` no YAML principal e `english` no YAML em inglês.
- Python 3.12 ou superior apenas para o RenderCV.

## Comandos

```bash
# Instalar
pipx install "rendercv[full]"

# Renderizar
rendercv render Gustavo_Muniz_CV.yaml
rendercv render Gustavo_Muniz_CV_EN.yaml

# Re-renderizar a cada save
rendercv render Gustavo_Muniz_CV.yaml --watch

# Gerar o PDF de envio com telefone
rendercv render Gustavo_Muniz_CV.yaml --cv.phone "+55..."
rendercv render Gustavo_Muniz_CV_EN.yaml --cv.phone "+55..."

# Conferir se ficou em uma página
mdls -name kMDItemNumberOfPages rendercv_output/Gustavo_Muniz_CV.pdf
mdls -name kMDItemNumberOfPages rendercv_output/Gustavo_Muniz_CV_EN.pdf
```

## Estrutura do projeto

```
Gustavo_Muniz_CV.yaml     conteúdo e design do CV em português
Gustavo_Muniz_CV_EN.yaml  os mesmos fatos, em inglês
docs/specs/               regras editoriais e de design
docs/decisions/           decisões que não mudam com frequência
rendercv_output/          saída do render, ignorada pelo git
vagas/                    variantes por vaga, ignoradas pelo git
```

## Estilo do YAML

- No YAML em português, chaves de seção em português: `resumo`, `experiência`,
  `projetos`, `formação`, `competências`.
- No YAML em inglês, chaves de seção em inglês: `summary`, `experience`,
  `projects`, `education`, `skills`.
- Datas em `YYYY-MM` ou `YYYY`. Não misture formatos dentro da mesma entrada.
- Dois-pontos em texto livre exige aspas no valor.
- Nunca use ` - ` no meio de um highlight. O RenderCV trata o hífen cercado de
  espaços como novo item.
- Unidades levam espaço não separável, como em `16 TB`.
- Nome de tecnologia fica como o projeto escreve: `Next.js`, `Payload CMS`,
  `Timber/Twig`, `WooCommerce`.

## Conteúdo

A fonte de verdade é a spec de conteúdo local, fora do repositório público. Em
resumo:

- Cada bullet abre com o resultado ou o escopo, não com a tecnologia.
- Nenhum número, data, cliente ou resultado sem registro na spec.
- Cliente só entra com autorização.
- Termos proibidos ficam fora.

## Design

A fonte de verdade é [`design.md`](design.md). Em resumo:

- A4, uma página, tema `classic`.
- Corpo em 10 pt. O limite é a página, não a fonte.
- Texto justificado sem hifenização.
- Sem imagem, tabela ou coluna no corpo.

## Verificação

Antes de considerar a mudança pronta:

1. `rendercv render` termina sem erro nos dois YAMLs.
2. Existem `Gustavo_Muniz_CV_1.png` e `Gustavo_Muniz_CV_EN_1.png`, e nenhum
   `*_2.png`, em `rendercv_output/`.
3. `mdls` informa `kMDItemNumberOfPages = 1` nos dois PDFs.
4. O texto não contém termo da lista proibida da spec de conteúdo.
5. Cargo, datas, clientes e números batem com a spec de conteúdo.
6. O PNG foi conferido visualmente: sem linha órfã, sem bullet partido, sem
   espaço vazio no topo ou no fim.
7. O diff do YAML foi revisado antes de propor commit.

## Boundaries

**Sempre:**

- Atualizar a spec antes de mudar um fato.
- Atualizar os dois YAMLs quando um fato mudar.
- Rodar o render e conferir a página dos dois PDFs.
- Manter o tom definido na spec de conteúdo.
- Preservar nomes de tecnologia e caminhos.

**Perguntar antes:**

- Citar cliente novo ou resultado novo.
- Mudar a ordem das seções.
- Mexer em `typography`, margens ou cores.
- Criar variante do CV para uma vaga.

**Nunca:**

- Inventar número, data, cliente ou resultado.
- Publicar telefone, salário ou endereço completo.
- Fazer push sem confirmação, porque o push dispara release público.
- Remover um teste ou uma verificação para fazer a página caber.
