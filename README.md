# Panorama de Ocupação Hospitalar COVID-19 (2020–2022)

Painel analítico em HTML para monitoramento da ocupação de leitos de UTI e enfermaria clínica por COVID-19 entre 2020 e 2022.

> **Dashboard Online (GitHub Pages):** https://flavioladislau-tech.github.io/panorama-ocupacao-covid19/

## Visão Geral dos Indicadores

| Indicador | Valor Consolidado |
| --- | --- |
| Total de registros analisados | 432 |
| Unidades Federativas (UFs) | 12 |
| Taxa média de ocupação em UTI | 51,0% |
| Taxa média de ocupação clínica | 43,9% |
| Pico mensal de UTI confirmada | 2.100 (Mar/2021) |
| Óbitos confirmados registrados | 8.521 |
| Altas confirmadas registradas | 51.671 |

## Comparativo Anual (2020–2022)

| Ano | Registros | Ocupação UTI (%) | Ocupação Clínica (%) | Óbitos | Altas |
| --- | ---: | ---: | ---: | ---: | ---: |
| 2020 | 144 | 52,5% | 45,2% | 2.847 | 15.848 |
| 2021 | 144 | 64,0% | 55,0% | 4.934 | 24.653 |
| 2022 | 144 | 31,1% | 26,8% | 740 | 11.170 |

## Estrutura do Repositório

```text
panorama-ocupacao-covid19/
├── index.html                  # Dashboard interativo em HTML + CSS + JS
├── README.md                   # Documentação e resumo estatístico
├── DATA_DICTIONARY.md          # Dicionário de colunas dos arquivos CSV
├── .gitignore
└── data/
    ├── ocupacao_2020.csv
    ├── ocupacao_2021.csv
    └── ocupacao_2022.csv
```

## Arquivos CSV Utilizados

- `data/ocupacao_2020.csv` — Série consolidada de 2020 (144 registros)
- `data/ocupacao_2021.csv` — Série consolidada de 2021 (144 registros)
- `data/ocupacao_2022.csv` — Série consolidada de 2022 (144 registros)

## Como Visualizar Localmente ou Publicar no GitHub Pages

1. **No navegador local:** abra o arquivo `index.html` com um duplo clique.
2. **No GitHub Pages:**
   - Acesse **Settings → Pages** no repositório.
   - Em **Source**, selecione **Deploy from a branch**.
   - Em **Branch**, selecione `main` e `/ (root)` e clique em **Save**.
   - O painel ficará publicado em: `https://flavioladislau-tech.github.io/panorama-ocupacao-covid19/`

## Licença

Distribuído sob a licença **MIT**.
