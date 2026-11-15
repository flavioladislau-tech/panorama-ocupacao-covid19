# Panorama de Ocupação Hospitalar COVID-19 (2020–2022)

Painel analítico em HTML para monitoramento da ocupação de leitos de UTI e enfermaria clínica por COVID-19 entre 2020 e 2022.

> **Dashboard Online (GitHub Pages):** https://flavioladislau-tech.github.io/panorama-ocupacao-covid19/


O ponto de partida do projeto é o modelo público de Registro de Ocupação Hospitalar COVID-19 (padrão OpenDataSUS / e-SUS Notifica do Ministério da Saúde), cobrindo três ciclos distintos da pandemia no Brasil:
2020 (ocupacao_2020.csv): início da pandemia, expansão gradual da rede e primeira onda.
2021 (ocupacao_2021.csv): período de maior pressão hospitalar (pico da variante Gama entre março e maio).
2022 (ocupacao_2022.csv): onda Ômicron no início do ano seguida de queda sustentada na ocupação de leitos.

Para que os três anos conversassem entre si sem erros, todas as bases foram padronizadas em 15 colunas (documentadas no DATA_DICTIONARY.md):
- Identificação temporal e geográfica: dataNotificacao, ano, mes, uf, estado, municipio, estabelecimento.
- Leitos ocupados: ocupacaoConfirmadoUti, ocupacaoSuspeitoUti, ocupacaoConfirmadoCli, ocupacaoSuspeitoCli.
- Capacidade instalada: ofertaUti e ofertaCli.
- Desfechos clínicos: obitosConfirmados e altasConfirmadas.


 Tratamento e Normalização dos Arquivos CSV
 
Arquivos CSV públicos costumam vir com diferenças de formatação. A etapa de preparação resolveu quatro problemas comuns:
- Delimitadores variados: detecção automática de separador por vírgula (,), ponto e vírgula (;) ou tabulação (TAB).
- Codificação de caracteres: leitura compatível com UTF-8 e ISO-8859-1 / Windows-1252 (muito comum em planilhas governamentais brasileiras, preservando acentos como São Paulo e Óbitos).
- Padronização de datas e UFs: conversão de datas tanto no formato brasileiro (DD/MM/AAAA) quanto ISO (AAAA-MM-DD), além de normalização dos nomes dos estados para siglas de 2 letras (SP, RJ, MG, etc.).
- Limpeza numérica: conversão segura de valores vazios ou textuais para 0, evitando falhas nas médias e somatórios.


Cálculo dos Indicadores Epidemiológicos

Com os dados limpos na memória, definimos as fórmulas principais que alimentam o painel:

- Total de Ocupação em UTI:
- Taxa de Ocupação em UTI (%):
- Taxa de Ocupação Clínica (%):
- Classificação de Pressão Hospitalar (Limiar Clínico):
- Estável: abaixo de 65% (verde)
- Atenção: entre 65% e 84,9% (âmbar)
- Crítico: igual ou acima de 85% (vermelho)

Agregações geradas:

- Mensal por ano: agrupa os 12 meses (Jan a Dez) de 2020, 2021 e 2022 para comparação sazonal lado a lado.
- Por Estado (UF): soma oferta, ocupação, óbitos e altas por UF para montar o ranking e a tabela analítica.
- Pico mensal: identifica automaticamente o mês/ano com maior volume de casos confirmados em UTI.

 Construção da Visão em HTML (index.html)
 
Todo o painel foi projetado em um único arquivo index.html autocontido (HTML5 + CSS3 + JavaScript puro), sem depender de servidor ou instalação de bibliotecas externas para rodar no navegador ou no GitHub Pages.

 Estrutura Semântica (HTML)
 
A página foi dividida em cinco blocos funcionais:

- Barra superior (<header>): título do projeto, atalhos de âncora (Indicadores, Série Histórica, Resumo Anual, Estados), botão para carregar novos CSVs locais e link direto para o repositório no GitHub.

- Cabeçalho editorial e barra de filtros: filtro segmentado por ano (2020–2022, 2020, 2021, 2022), seletor de UF, alternância entre Leitos de UTI e Leitos Clínicos e campo de busca textual.

- Grade de KPIs (4 cartões): Taxa Média de Ocupação, Pico Mensal Confirmado, Leitos Ocupados (Acumulado) e Desfechos Registrados (Altas e Óbitos).
Área visual de gráficos: comparativo mensal multi-ano à esquerda e ranking de pressão por estado à direita, seguidos pelos 3 cards anuais (2020, 2021, 2022).
- Tabela analítica (<table>): detalhamento completo por estado com cabeçalhos clicáveis para ordenação. 

Identidade Visual e Design System (CSS) 

- Paleta 60-30-10: fundo neutro claro (#f8fafc), cartões brancos (#ffffff) com bordas finas de 1px (#e2e8f0) e cor de destaque clínica em verde-petróleo (#0f766e).
- Tipografia hierárquica: Plus Jakarta Sans nos títulos, Public Sans nos textos e JetBrains Mono com font-variant-numeric: tabular-nums em todos os números e percentuais (mantendo as colunas perfeitamente alinhadas).
- Layout responsivo: uso de CSS Grid e Flexbox para adaptar os 4 KPIs e os 2 gráficos de telas largas (desktop) até celulares.
- Motor Interativo e Gráficos (JavaScript + SVG)
- Dados híbridos: o HTML já traz os dados consolidados embutidos em JSON (para abrir instantaneamente até sem internet) e também possui um parser CSV embutido que lê arquivos enviados pelo botão Carregar CSV Local.
- Gráfico de linhas em SVG puro: o JavaScript calcula as coordenadas (x, y) de cada mês (Jan a Dez) proporcionalmente ao eixo percentual, desenha a linha tracejada do Limiar Crítico de 85%, gera os caminhos <path> de 2020, 2021 e 2022 e posiciona colunas invisíveis de captura para exibir o tooltip dinâmico ao passar o mouse.
Reatividade instantânea: toda alteração nos filtros de ano, estado, tipo de leito ou busca recalcula os KPIs, redesenha o SVG, atualiza as barras dos estados e reordena a tabela em milissegundos no próprio navegador.
  
Estruturação e Publicação no GitHub Pages

Por fim, o projeto foi empacotado seguindo boas práticas de portfólio e ciência de dados aberta:

- index.html: ponto de entrada do site estático.
- README.md: documentação do projeto com tabela resumo de indicadores e comparativo anual.
- DATA_DICTIONARY.md: especificação técnica de cada coluna dos CSVs.
ocupacao_2020.csv, ocupacao_2021.csv, ocupacao_2022.csv: as bases históricas utilizadas.
- gitignore: lista de arquivos temporários ignorados no controle de versão.
- Hospedagem gratuita (GitHub Pages): ativada em Settings → Pages apontando para a branch main na pasta / (root), transformando o arquivo index.html em uma aplicação web acessível publicamente por URL.
