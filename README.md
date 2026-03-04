# Classificador de Imagens de Satélite Sentinel-2 com Vision Transformer (ViT)

Este projeto é um exemplo que  implementa uma arquitetura **Vision Transformer (ViT)** utilizando TensorFlow e Keras para classificar imagens de satélite do conjunto de dados **EuroSAT** (Sentinel-2). O modelo é capaz de identificar 10 categorias diferentes de uso do solo e cobertura terrestre.

## Visão Geral

Ao contrário das Redes Neurais Convolucionais (CNNs) tradicionais, este modelo utiliza o mecanismo de **Atenção (Self-Attention)** para processar imagens como sequências de patches (pedaços). Esta abordagem permite capturar relações de longo alcance entre diferentes partes da imagem de satélite.

### Categorias de Classificação

O modelo classifica as imagens em 10 classes:

- Annual Crop (Plantação Anual)
- Forest (Floresta)
- Herbaceous Vegetation (Vegetação Herbácea)
- Highway (Rodovia)
- Industrial (Industrial)
- Pasture (Pastagem)
- Permanent Crop (Plantação Permanente)
- Residential (Residencial)
- River (Rio)
- Sea Lake (Mar e Lago)

## Tecnologias Utilizadas

- **Python 3.12**
- **TensorFlow / Keras**: Construção e treinamento do modelo.
- **KaggleHub**: Download automatizado do dataset.
- **OpenCV**: Processamento de imagens.
- **Scikit-learn**: Divisão e embaralhamento dos dados.

## Arquitetura do Modelo

O modelo segue a estrutura clássica do Vision Transformer:

- **Patch Embedding**: A imagem de 64x64 é dividida em patches de 16x16, que são achatados (flatten) e projetados linearmente.
- **Positional Encoding**: Adição de informações sobre a posição de cada patch.
- **Class Token**: Um token aprendível adicionado ao início da sequência para agregar o contexto global.
- **Transformer Encoders**: 6 camadas de codificação contendo Multi-Head Attention e MLP (Multi-Layer Perceptron).
- **MLP Head**: Uma camada densa final com ativação Softmax para a classificação.

## ⚙️ Configuração e Hiperparâmetros

| **Parâmetro** | **Valor** |
| --- | --- |
| Tamanho da Imagem | 64x64 (RGB) |
| --- | --- |
| Tamanho do Patch | 16x16 |
| --- | --- |
| Dimensão Oculta | 256 |
| --- | --- |
| Cabeças de Atenção | 4   |
| --- | --- |
| Camadas de Transformer | 6   |
| --- | --- |
| Batch Size | 16  |
| --- | --- |
| Taxa de Aprendizado | 1e-4 |
| --- | --- |
| Épocas | 10 |
| --- | --- |

##  Como Executar

- **Instalação de Dependências**:  
    pip install tensorflow opencv-python patchify matplotlib scikit-learn kagglehub  

- **Dataset**:  
    O script utiliza o kagglehub para baixar automaticamente o dataset gallo33henrique/sentinel-2-satellite-imagery. Certifique-se de ter espaço em disco disponível.
- **Treinamento**:  
    Execute o script para iniciar o carregamento dos dados, pré-processamento e treinamento. O modelo salvo será armazenado em files/model.h5.
- **Predição**:  
    O script inclui funções para realizar predições em imagens de teste.


## Licença

Este projeto é para fins educacionais. O dataset EuroSAT original é fornecido pela equipe do DFKI.
