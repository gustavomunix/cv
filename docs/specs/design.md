# Spec: design do CV

## Página

| Campo | Valor |
| --- | --- |
| Tamanho | A4 |
| Margem superior | 1,1 cm |
| Margem inferior | 1,1 cm |
| Margem esquerda | 1,3 cm |
| Margem direita | 1,3 cm |
| Rodapé | Desligado |
| Nota de topo | Desligada |

## Tipografia

| Elemento | Valor |
| --- | --- |
| Tema | `classic` |
| Corpo | 10 pt |
| Nome | 24 pt |
| Headline | 9,5 pt |
| Conexões | 8,5 pt |
| Títulos de seção | 1,2 em |
| Entrelinha | 0,6 em |
| Alinhamento | `justified-with-no-hyphenation` |

O alinhamento sem hifenização evita quebra de palavra no meio. Se a página
estourar, corte texto. Só depois reduza o corpo ou a entrelinha.

## Cores

| Elemento | Valor |
| --- | --- |
| Nome e títulos | `rgb(17, 45, 78)` |
| Headline | `rgb(70, 70, 70)` |
| Conexões | `rgb(40, 40, 40)` |
| Links | `rgb(17, 45, 78)` |

## Header

- Nome, headline e conexões centralizados.
- Conexões com URLs completas, para o ATS ler o destino.
- Separador `·`.
- LinkedIn e GitHub sempre presentes.

## Ordem das seções

1. Resumo
2. Experiência
3. Projetos
4. Formação
5. Competências

Experiência em ordem cronológica inversa. Dentro de cada empresa, o bullet mais
forte vem primeiro.

## Orçamento de página

- Uma página, sempre.
- O resumo ocupa no máximo 6 linhas.
- Cada experiência tem no máximo 4 bullets, exceto a atual.
- Competências em no máximo 4 entradas.
- Se o render gerar `Gustavo_Muniz_CV_2.png`, a mudança não passou.

## ATS

- Texto selecionável, sem rasterização.
- Sem tabela, coluna, ícone ou imagem no corpo.
- Cabeçalhos de seção em texto normal, não em imagem.
- Datas em formato consistente.
- Empresa e cargo na mesma linha, separados por vírgula, como o tema faz.
- Sem hifenização automática.
- Sem caractere decorativo que atrapalhe a leitura por parser.

## Verificação visual

1. Abrir `rendercv_output/Gustavo_Muniz_CV_1.png`.
2. Conferir se nenhum bullet quebrou em duas colunas.
3. Conferir se nenhuma linha ficou órfã no fim de uma seção.
4. Conferir se o header não tem conexão solta.
5. Conferir se o fim da página não tem espaço vazio maior que uma linha.

## O que não muda sem decisão

- Tema, tamanho de página e margens.
- Paleta de cores.
- Ordem das seções.
- Alinhamento sem hifenização.
- Uma página.
