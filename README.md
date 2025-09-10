# FarmTech_na_era_da_cloud_computing
**FarmTech Solutions - Análise de Dados Agrícolas e Computação em Nuvem**

Este projeto foi desenvolvido como parte das atividades da Fase 5 do curso de IA da FIAP, abrangendo **Machine Learning** e **Computação em Nuvem** para uma fazenda de médio porte (200 hectares). O objetivo foi analisar dados históricos para prever o rendimento de safras e propor uma solução de hospedagem em nuvem para o modelo preditivo.

## 👥 Informações do Grupo

- **Nome**: Ricardo De Paiva Melo
    
- **RM**: 565522
    
- **Nome**: Nicolas Lemos Ribeiro
    
- **RM**: 553273
    
- **Nome**: Luiz Felipe Alves Gomes
    
- **RM**: 565151
    
- **Nome**: Artur de Carvalho
    
- **RM**: 558646
    
- **Nome**: Caíque de Souza maulen
    
- **RM**: 560700
    

## 🎯 Objetivos do Projeto

### 📊 **Entrega 1: Machine Learning**

Análise completa do dataset `crop_yield.csv` para prever rendimento de safras através de:

1. **Análise Exploratória de Dados (EDA)** - Familiarização com os dados.
    
2. **Clusterização** - Identificação de tendências e outliers usando algoritmos não supervisionados.
    
3. **Modelagem Preditiva** - Desenvolvimento de cinco modelos de regressão distintos.
    
4. **Avaliação e Seleção** - Comparação de desempenho usando métricas adequadas para selecionar o melhor modelo.
    

### ☁️ **Entrega 2: Computação em Nuvem**

Análise de custos para hospedagem da solução de ML na AWS:

1. **Estimativa de Custos** - Comparação entre as regiões de São Paulo (BR) e Virgínia do Norte (EUA).
    
2. **Configuração Específica** - 2 CPUs, 1 GiB RAM, 5 Gbps rede, 50 GB HD.
    
3. **Justificativa Técnica** - Consideração de latência, soberania de dados e restrições legais.
    

## 📈 **ENTREGA 1: RESULTADOS DA ANÁLISE DE MACHINE LEARNING**

### 🔍 Análise Exploratória dos Dados

O dataset `crop_yield.csv` contém **156 registros** com as seguintes variáveis:

- **Crop**: Tipo de cultura (4 categorias: Cocoa beans, Oil palm fruit, Rice paddy, Rubber natural).
    
- **Precipitation**: Precipitação em mm/dia.
    
- **Specific_Humidity**: Umidade específica a 2m (g/kg).
    
- **Relative_Humidity**: Umidade relativa a 2m (%).
    
- **Temperature**: Temperatura a 2m (°C).
    
- **Yield**: Rendimento (variável alvo).
    

**Principais Descobertas da EDA:**

- O dataset é perfeitamente balanceado, com 39 registros para cada uma das 4 culturas.
    
- A variável `Crop` mostrou-se o **fator mais preditivo** do rendimento, com a cultura "Oil palm fruit" apresentando valores de `Yield` ordens de magnitude maiores que as demais.
    
- As correlações lineares entre as variáveis climáticas e o `Yield` no dataset completo são quase nulas, pois o efeito do tipo de cultura anula essas relações.
    

### 🔢 Clusterização (K-Means e DBSCAN)

- A aplicação do algoritmo K-Means, guiada pelo Método do Cotovelo, identificou **4 clusters** ideais, confirmando os agrupamentos naturais por tipo de cultura.
    
- O algoritmo DBSCAN, com parâmetros padrão, classificou **43 pontos** como outliers. A análise revelou que não se tratavam de erros, mas de pontos nas bordas dos clusters densos, destacando a sensibilidade do algoritmo aos seus hiperparâmetros.
    

### 🤖 Modelos de Regressão Desenvolvidos

A performance dos cinco modelos de regressão foi avaliada, e os resultados estão compilados abaixo:

|   |   |   |   |   |
|---|---|---|---|---|
|**Modelo**|**MAE**|**RMSE**|**R² Score**|**Tempo Treinamento**|
|**Regressão Linear**|**3,132.80**|**4,394.17**|**0.9950**|**< 0.1s**|
|Random Forest|2,797.35|4,878.30|0.9939|< 0.5s|
|Árvore de Decisão|3,142.53|5,316.35|0.9927|< 0.1s|
|XGBoost|4,082.62|6,728.47|0.9883|< 0.2s|
|SVR|38,971.97|71,312.00|-0.3110|< 0.1s|

**🏆 Modelo Selecionado: Regressão Linear**

- **R² Score**: 0.9950 (explica 99.5% da variância do rendimento).
    
- **Justificativa**: Apresentou o melhor R² Score, combinado com alta interpretabilidade e eficiência computacional. O sucesso do modelo se deveu à técnica de **One-Hot Encoding** na variável `Crop`, que permitiu capturar o impacto de cada cultura no rendimento de forma linear.
    

### 📋 Pontos Fortes e Limitações

**Pontos Fortes:**

- Excelente performance preditiva (R² > 0.99) para os modelos bem-sucedidos.
    
- Dataset de alta qualidade, balanceado e sem valores faltantes.
    
- O modelo selecionado (Regressão Linear) é altamente interpretável e leve, ideal para produção.
    

**Limitações:**

- O dataset é relativamente pequeno, o que pode limitar a generalização do modelo para fazendas com perfis climáticos muito diferentes.
    
- A forte dependência da variável `Crop` pode mascarar efeitos secundários das variáveis climáticas.
    
- O modelo SVR teve um desempenho muito ruim, indicando a necessidade de um ajuste fino de hiperparâmetros que não estava no escopo do projeto.
    

## ☁️ **ENTREGA 2: ANÁLISE DE CUSTOS AWS**

### 💰 Estimativa de Custos (Calculadora AWS)

**Configuração Analisada:**

- **Tipo de Instância**: Linux, On-Demand (100% de utilização)
    
- **CPU**: 2 vCPUs
    
- **Memória**: 1 GiB
    
- **Rede**: Até 5 Gbps
    
- **Armazenamento**: 50 GB (EBS General Purpose)
    

#### Comparação de Regiões:
<img width="756" height="360" alt="Imagem1" src="https://github.com/user-attachments/assets/d9da66b8-d3c7-493a-a531-97f84b8e74a7" />
<img width="756" height="357" alt="Imagem2" src="https://github.com/user-attachments/assets/858bb26d-3c77-4d85-80c8-68d4ededd755" />

_Estimativa de custos para região São Paulo (sa-east-1)_

_Estimativa de custos para região Virgínia do Norte (us-east-1)_

### 🎯 Decisão e Justificativa Técnica

**Região Escolhida: São Paulo (sa-east-1)**

**Justificativas:**

1. **✅ Soberania de Dados e Compliance Legal**: A principal razão para a escolha é a conformidade com a Lei Geral de Proteção de Dados (LGPD) e outras regulamentações brasileiras que podem exigir que dados sensíveis (como os de sensores agrícolas) permaneçam em território nacional.
    
2. **⚡ Baixa Latência e Performance**: A proximidade geográfica com a fazenda (localizada no Brasil) minimiza o tempo de resposta da API (<50ms), o que é crucial para aplicações que podem evoluir para a coleta de dados em tempo real.
    
3. **💼 Aspectos Operacionais**: Embora o custo seja idêntico ao da Virgínia do Norte para esta configuração, a escolha por São Paulo facilita o suporte técnico em português e o alinhamento com o horário comercial brasileiro.
    

## 🚀 Como Executar a Solução (API com Docker)

Para interagir com o modelo de Regressão Linear selecionado, foi criada uma API com Flask, containerizada com Docker.

### Pré-requisitos

- Docker Desktop instalado e em execução.
    

### Passos para Execução

1. Construa a imagem Docker:
    
    Navegue até o diretório raiz do projeto e execute o comando:
    
    ```
    docker build -t previsao-safra-api .
    ```
    
2. **Execute o container:**
    
    ```
    docker run -p 5000:5000 previsao-safra-api
    ```
    
    A API estará disponível em `http://127.0.0.1:5000`.
    

### ☁️ Documentação da API

- **Endpoint:** `/predict`
    
- **Método:** `POST`
    
- **Exemplo de `curl`:**
    
    ```
    curl -X POST [http://127.0.0.1:5000/predict](http://127.0.0.1:5000/predict) \
    -H "Content-Type: application/json" \
    -d '{
          "Crop": "Rice, paddy",
          "Precipitation": 2600.5,
          "Specific_Humidity": 18.1,
          "Relative_Humidity": 83.5,
          "Temperature": 26.5
        }'
    ```
    

## 📁 Arquivos do Projeto

```
projeto-farmtech/
├── api/
│   ├── app.py
│   ├── model.pkl
│   └── scaler.pkl
├── data/
│   └── crop_yield.csv
├── imagens/
│   ├── aws_sao_paulo.png
│   └── aws_virginia.png
├── Dockerfile
├── requirements.txt
├── RicardoDePaivaMelo_rm565522_pbl_fase4.ipynb
└── README.md
```

## 🔗 Links Importantes

### 📊 **Análise Completa (Entrega 1)**

📓 Notebook (Google Colab):

Para visualizar e executar a análise de dados, acesse o notebook no Google Colab ou visualize o arquivo diretamente no repositório.

- [**Abrir no Google Colab**](https://colab.research.google.com/drive/1MsMjjU9YuPQruPQ2BV52XXqm78Dbj6tI#scrollTo=NK838cpfEGTW) _(Substitua pelo link compartilhável do seu notebook)_
    
- [**Visualizar no Repositório**](https://github.com/ricardopaivamelo/FarmTech_na_era_da_cloud_computing/blob/main/RicardoDePaivaMelo_rm565522_pbl_fase4.ipynb)
    

🎥 Vídeo Demonstrativo - Machine Learning (5min):

(https://youtu.be/dsBe2aDLVik)

> _Demonstração da análise exploratória, clusterização e comparação dos 5 modelos de regressão._

### ☁️ **Análise de Custos AWS (Entrega 2)**

🎥 Vídeo Demonstrativo - AWS Calculator (5min):

(https://youtu.be/UK9Mw1R_4zw)

> _Demonstração prática da comparação de custos usando a calculadora AWS._

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**: Linguagem principal
    
- **Pandas & NumPy**: Manipulação e análise de dados
    
- **Scikit-learn**: Algoritmos de ML e avaliação de modelos
    
- **XGBoost**: Modelo de boosting
    
- **Matplotlib & Seaborn**: Visualização de dados
    
- **Google Colab / Jupyter Notebook**: Ambiente de desenvolvimento para análise
    
- **Flask**: Framework para API web
    
- **Docker**: Containerização da aplicação
    
- **AWS Calculator**: Estimativa de custos em nuvem
    

_Projeto desenvolvido para a Fase 5 - FIAP Pós-Graduação em Artificial Intelligence & Machine Learning_
