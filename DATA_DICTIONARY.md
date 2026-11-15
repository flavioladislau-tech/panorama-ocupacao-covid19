# Dicionário de Dados · Ocupação Hospitalar COVID-19

Estrutura das colunas nos arquivos `data/ocupacao_2020.csv`, `data/ocupacao_2021.csv` e `data/ocupacao_2022.csv`:

| Coluna | Tipo | Descrição |
| --- | --- | --- |
| `dataNotificacao` | Date (YYYY-MM-DD) | Data de referência da notificação hospitalar |
| `ano` | Integer | Ano epidemiológico (2020, 2021 ou 2022) |
| `mes` | Integer | Mês numérico (1 a 12) |
| `uf` | String (2) | Sigla da Unidade Federativa (ex.: SP, RJ, MG) |
| `estado` | String | Nome completo do estado |
| `municipio` | String | Nome do município do estabelecimento |
| `estabelecimento` | String | Nome da unidade hospitalar ou código CNES |
| `ocupacaoConfirmadoUti` | Number | Leitos de UTI ocupados por casos confirmados |
| `ocupacaoSuspeitoUti` | Number | Leitos de UTI ocupados por casos suspeitos |
| `ocupacaoConfirmadoCli` | Number | Leitos clínicos ocupados por casos confirmados |
| `ocupacaoSuspeitoCli` | Number | Leitos clínicos ocupados por casos suspeitos |
| `ofertaUti` | Number | Capacidade total de leitos de UTI declarada |
| `ofertaCli` | Number | Capacidade total de leitos clínicos declarada |
| `obitosConfirmados` | Number | Óbitos confirmados no período |
| `altasConfirmadas` | Number | Altas hospitalares confirmadas no período |
