# Documentação do CV

O currículo vive em `Gustavo_Muniz_CV.yaml` e é renderizado com RenderCV. Esta
pasta guarda as specs que definem o que entra no arquivo e por quê.

## Ordem de verdade

1. `docs/specs/`: escopo, regras editoriais e decisões de design.
2. `Gustavo_Muniz_CV.yaml`: conteúdo e layout em vigor.
3. `README.md`: apresentação pública do repositório.

Se o YAML contradisser uma spec, a spec vence. Corrija o YAML.

## Mapa

| Arquivo | O que define |
| --- | --- |
| [`specs/cv.md`](specs/cv.md) | Objetivo, escopo, comandos, estrutura e critérios de aceite |
| [`specs/design.md`](specs/design.md) | A4, tipografia, ATS, ordem das seções e orçamento de página |
| [`decisions/0001-cv-as-code.md`](decisions/0001-cv-as-code.md) | Por que RenderCV e YAML versionado |

## Como renderizar

```bash
rendercv render Gustavo_Muniz_CV.yaml
```

O PDF, o PNG, o Markdown e o HTML saem em `rendercv_output/`, que também está no
`.gitignore`. A saída é reconstruída a partir do YAML, então nada dessa pasta
entra em commit.
