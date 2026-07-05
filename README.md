# IP por Krigagem---Python
Índice Pluviométrico por no Município de Quixeramobim

🌧️ Krigagem do Índice Pluviométrico (IP) — Vulnerabilidade Ambiental (Crepani et al., 2001)
Script em Python para interpolação espacial do Índice Pluviométrico (IP), um dos componentes utilizados na análise de Vulnerabilidade à Perda de Solos (Ecodinâmica), conforme a metodologia proposta por Crepani et al. (2001). A interpolação é feita via Krigagem Ordinária, gerando um raster contínuo e um mapa temático recortado para o município de Quixeramobim (CE).
📋 Descrição
O Índice Pluviométrico (IP) é uma das variáveis utilizadas na metodologia de Vulnerabilidade das Unidades Territoriais Básicas (UTBs) proposta por Crepani et al. (2001), amplamente empregada em estudos de Zoneamento Ecológico-Econômico (ZEE). Essa metodologia classifica o território em uma escala de vulnerabilidade que varia entre:

1,0 a 1,4 → Unidades Estáveis
1,5 a 2,4 → Unidades de Vulnerabilidade Intermediária
2,5 a 3,0 → Unidades Vulneráveis

O IP, calculado a partir de dados de precipitação de postos pluviométricos, é um dos parâmetros ponderados junto a outras variáveis (como relevo, solo e cobertura vegetal) na análise integrada da fragilidade ambiental.
Este script realiza a interpolação espacial dos valores de IP a partir de pontos amostrais (postos pluviométricos), utilizando o método geoestatístico de Krigagem Ordinária, com posterior recorte e visualização para a área de estudo (Quixeramobim/CE).
⚙️ Funcionalidades

Leitura de shapefiles de pontos pluviométricos (com valores de IP já calculados) e limite municipal (GeoPandas);
Padronização do Sistema de Referência de Coordenadas (CRS) — SIRGAS 2000 / UTM (EPSG:31984);
Interpolação espacial via Krigagem Ordinária (modelo de variograma esférico) com PyKrige;
Geração de grid regular (resolução de 350m) sobre a área de estudo;
Exportação do raster interpolado em formato GeoTIFF (rasterio);
Recorte do raster pelos limites do município;
Geração de mapa temático com os pontos pluviométricos sobrepostos (matplotlib).

🛠️ Tecnologias e Bibliotecas

PyKrige — Interpolação geoestatística
GeoPandas — Manipulação de dados vetoriais
Rasterio — Manipulação de dados raster
NumPy
Matplotlib

📂 Estrutura de Dados Esperada
Dados da krikagem/
├── chuva.shp          # Pontos pluviométricos (campo IP_Crpn com valores calculados)
└── quixeramobim.shp   # Limite do município (área de estudo)

Observação: o campo IP_Crpn deve conter os valores do Índice Pluviométrico já calculados conforme a metodologia de Crepani et al. (2001), previamente à interpolação.

▶️ Como usar

Instale as dependências:

bashpip install pykrige rasterio geopandas

Ajuste os caminhos dos shapefiles de entrada no script.
Execute o script. Serão gerados:

IP.tif — raster do Índice Pluviométrico interpolado e recortado pelo município;
Mapa (.png) com a visualização espacial do IP e localização dos postos utilizados.



📊 Saída

Raster contínuo representando a distribuição espacial do Índice Pluviométrico (IP);
Mapa temático com:

Superfície interpolada do IP (tons de azul);
Limite do município;
Localização dos postos pluviométricos.



📚 Referência
CREPANI, E.; MEDEIROS, J. S.; HERNANDEZ FILHO, P.; FLORENZANO, T. G.; DUARTE, V.; BARBOSA, C. C. F. Sensoriamento remoto e geoprocessamento aplicados ao zoneamento ecológico-econômico e ao ordenamento territorial. São José dos Campos: INPE, 2001.
⚠️ Observações

Originalmente desenvolvido e testado no Google Colab.
CRS padrão assumido: EPSG:31984 (SIRGAS 2000 / UTM zone 24S).
Modelo de variograma: esférico (ajustável conforme necessidade: gaussian, exponential, etc).
O IP é um dos componentes da vulnerabilidade ambiental — este script trata apenas da etapa de interpolação espacial, não do cálculo do índice em si.
