<h1 align="center"> Laptops Dataset for prediction of laptop prices </h1>
Descrição
Projeto desenvolvido para a disciplina de Projeto Aplicado II do curso de Banco de Dados da Universidade Presbiteriana Mackenzie, segundo semestre./n
O foco deste projeto é desenvolver uma análise preditiva de preços de laptops, combinando técnicas de análise exploratória de dados (EDA), processamento de linguagem natural (NLP) e aprendizado de máquina.
Os dados utilizados foram extraídos de uma base pública disponível no Kaggle, contendo especificações técnicas detalhadas e preços (em euros) de 1.146 modelos de laptops.
Dataset disponível em: Laptop Prices

Objetivo Principal
Pergunta central:
É possível melhorar a predição de preços de laptops extraindo features a partir dos campos de texto do dataset (como modelo de CPU e GPU), comparado a um modelo que usa apenas dados numéricos?
a) Aquisição e Preparação dos Dados

Preparação dos Dados:

Ingestão do arquivo .csv e remoção da coluna vazia Unnamed: 16.
Conversão da coluna Ram de string (ex.: "8GB") para numérico.
Conversão da coluna Cpu Rate de string (ex.: "2.5GHz") para numérico.
Tratamento de valores ausentes e normalização de strings.
Armazenamento em banco relacional SQLite com esquema normalizado.



b) Processamento de Texto (NLP)

Extração de features das colunas Cpu Model, Gpu Model e ScreenResolution via regex e tokenização.
Variáveis geradas: família e geração da CPU, se tem GPU dedicada (Nvidia/AMD), resolução da tela extraída como numérico, e bag-of-words do Product (TF-IDF).

c) Análise Estatística Preditiva

Distribuição das variáveis e identificação de outliers em Price_euros.
Testes de hipótese (Kruskal-Wallis) para comparar preço médio entre marcas e tipos de laptop.
Regressão linear múltipla como baseline.
Matriz de correlação entre variáveis numéricas e o preço.

d) Aprendizado de Máquina

Pergunta-chave: As features textuais extraídas via NLP melhoram a predição de preço?
Modelos comparados:

Regressão Linear (baseline)
Random Forest Regressor
Gradient Boosting (XGBoost)


Métricas de avaliação: RMSE, MAE e R² — com validação cruzada de 5 folds.


Conclusão Esperada
Sintetizar os resultados para determinar como cada fator — marca, tipo de laptop, CPU, GPU, RAM e armazenamento — impacta individualmente e coletivamente o preço final, e demonstrar o ganho de performance ao incluir features extraídas de texto no modelo preditivo.

Dataset

Laptop-Price.csv (usado)

Variáveis:
ColunaTipoDescriçãoCompanyCategóricoMarca do fabricante (Dell, Lenovo, HP, Asus...)ProductTexto livreNome/modelo do laptopTypeNameCategóricoTipo (Notebook, Ultrabook, Gaming, Workstation...)InchesNuméricoTamanho da tela em polegadasScreenResolutionTextoResolução da tela (ex.: Full HD 1920x1080)RamTexto → NuméricoMemória RAM (ex.: "8GB")OpSysCategóricoSistema operacionalCpu BrandCategóricoFabricante da CPU (Intel, AMD)Cpu ModelTexto semi-estruturadoModelo da CPU — usado no NLPCpu RateTexto → NuméricoClock da CPU em GHz (ex.: "2.5GHz")SSDNuméricoArmazenamento SSD em GBHDDNuméricoArmazenamento HDD em GBFlash StorageNuméricoArmazenamento flash adicional em GBHybridNuméricoArmazenamento híbrido (0/1)Gpu BrandCategóricoFabricante da GPU (Intel, Nvidia, AMD)Gpu ModelTexto semi-estruturadoModelo da GPU — usado no NLPPrice_eurosNuméricoVariável-alvo — preço em euros

Referências do Dataset

Origem dos Dados:
O conjunto de dados foi obtido por meio da plataforma Kaggle, no dataset Laptop Prices (https://www.kaggle.com/datasets/abdelrahmanemad594/laptop-prices/data), publicado pelo usuário abdelrahmanemad594.
Originalidade e Limitações:
O dataset contém 1.146 registros com especificações técnicas detalhadas de laptops. Os preços estão em euros (€) e podem não refletir variações regionais de mercado. Inclui uma coluna vazia (Unnamed: 16) que será descartada no pré-processamento.
Período da Coleta:
Modelos disponíveis comercialmente em 2017–2018.
Limitações de Uso:
Por se tratar de um dataset público e de fonte secundária, seu uso é destinado a fins acadêmicos e de pesquisa.


Integrantes
Este projeto foi desenvolvido pelos seguintes integrantes:

Ryan Rodrigues Pereira
Nour Hussein Barakat
Guilherme de Araújo Esp. Santo

Universidade Presbiteriana Mackenzie
Curso Banco de Dados
Projeto Aplicado II - 2º Semestre 2025
