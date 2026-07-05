# IP por Krigagem---Python
Índice Pluviométrico por no Município de Quixeramobim


🌧️ Krigagem de Índice Pluviométrico (IP)
Script em Python para interpolação espacial de dados pluviométricos utilizando Krigagem Ordinária (Ordinary Kriging), com geração de raster (.tif) e mapa temático da distribuição de chuvas no município de Quixeramobim (CE).
📋 Descrição
Este script realiza a interpolação de dados de postos pluviométricos (pontos) para gerar uma superfície contínua de precipitação, recortada pelos limites do município de interesse. O processo utiliza o método geoestatístico de Krigagem Ordinária através da biblioteca PyKrige, produzindo um raster georreferenciado e um mapa visual do resultado.
⚙️ Funcionalidades

Leitura de shapefiles de pontos pluviométricos e limite municipal (GeoPandas);
Verificação e padronização do Sistema de Referência de Coordenadas (CRS) — SIRGAS 2000 / UTM (EPSG:31984);
Interpolação espacial via Krigagem Ordinária com modelo de variograma esférico (PyKrige);
Geração de grid regular (resolução de 350m) sobre a área de estudo;
Exportação do resultado como raster GeoTIFF (rasterio);
Recorte do raster pelos limites do município (rasterio.mask);
Geração de mapa final com os pontos pluviométricos sobrepostos (matplotlib).

🛠️ Tecnologias e Bibliotecas

PyKrige — Interpolação geoestatística
GeoPandas — Manipulação de dados vetoriais
Rasterio — Manipulação de dados raster
NumPy
Matplotlib

📂 Estrutura de Dados Esperada
Dados da krikagem/
├── chuva.shp          # Pontos pluviométricos (com campo IP_Crpn)
└── quixeramobim.shp   # Limite do município
▶️ Como usar

Instale as dependências:

bashpip install pykrige rasterio geopandas

Ajuste os caminhos dos shapefiles de entrada no script.
Execute o script. Serão gerados:

IP.tif — raster com a interpolação recortada pelo município;
Mapa em .png/.tif com a visualização espacial da chuva interpolada.



📊 Saída
O script gera um raster contínuo representando o Índice Pluviométrico (IP) interpolado, além de um mapa com:

Superfície de chuva (em tons de azul);
Limite do município;
Localização dos postos pluviométricos utilizados.

⚠️ Observações

Originalmente desenvolvido e testado no Google Colab.
O CRS padrão assumido é EPSG:31984 (SIRGAS 2000 / UTM zone 24S).
O modelo de variograma utilizado é o esférico, podendo ser ajustado conforme necessidade (gaussian, exponential, etc).
