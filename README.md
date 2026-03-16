<h1 align="center"> Análise Preditiva de Preços de Laptops com Processamento de Texto </h1>

## Descrição
Projeto desenvolvido para a disciplina de **Projeto Aplicado II** do curso de Banco de Dados da Universidade Presbiteriana Mackenzie, terceiro semestre.  
O foco deste projeto é desenvolver uma análise preditiva de preços de laptops modernos, combinando técnicas de **análise exploratória de dados (EDA)**, **processamento de linguagem natural (NLP)** e **aprendizado de máquina**.  
Os dados utilizados foram extraídos de uma base pública disponível no Kaggle, contendo informações detalhadas sobre especificações técnicas e preços de laptops comercializados em 2024.  

Dataset disponível em: [Modern Laptop Prices and Specifications](https://www.kaggle.com/datasets/sohaibdevv/modern-laptop-prices-and-specifications)

---

## Objetivo Principal
**Pergunta central:**  
É possível melhorar a predição de preços de laptops extraindo features a partir dos campos de texto do dataset (como nome do processador e da GPU), comparado a um modelo que usa apenas dados numéricos?

### a) Aquisição e Preparação dos Dados
- **Preparação dos Dados:**
  - Ingestão do arquivo `.csv` e tratamento de valores ausentes.
  - Normalização de strings (remoção de caracteres especiais, padronização de maiúsculas).
  - Armazenamento em banco relacional **SQLite** com esquema normalizado (tabelas: Laptop, Marca, Processador, GPU).

### b) Processamento de Texto (NLP)
- Extração de features das colunas `Processor`, `GPU` e `Model` via **regex** e **tokenização**.
- Variáveis geradas: fabricante e geração da CPU, se tem GPU dedicada, série da GPU e bag-of-words do nome do modelo (TF-IDF).

### c) Análise Estatística Preditiva
- Distribuição das variáveis e identificação de outliers.
- Testes de hipótese (Kruskal-Wallis) para comparar preço médio entre marcas.
- Regressão linear múltipla como baseline.
- Matriz de correlação entre variáveis numéricas e o preço.

### d) Aprendizado de Máquina
- **Pergunta-chave:** As features textuais extraídas via NLP melhoram a predição de preço?
- **Modelos comparados:**
  - Regressão Linear (baseline)
  - Random Forest Regressor
  - Gradient Boosting (XGBoost)
- **Métricas de avaliação:** RMSE, MAE e R² — com validação cruzada de 5 folds.

---

## Conclusão Esperada
Sintetizar os resultados para determinar como cada fator — **marca**, **geração do processador**, **GPU**, **memória RAM** e **armazenamento** — impacta **individualmente** e **coletivamente** o preço final do laptop, e demonstrar o ganho de performance ao incluir features extraídas de texto no modelo preditivo.

---

## Dataset
- `laptop_prices.csv` (usado)

**Variáveis principais:**

| Coluna | Tipo | Descrição |
|---|---|---|
| `Brand` | Categórico | Marca do fabricante |
| `Model` | Texto livre | Nome comercial do produto |
| `Processor` | Texto semi-estruturado | Nome do processador (fabricante, família, geração) |
| `RAM (GB)` | Numérico | Memória RAM em GB |
| `Storage (GB)` | Numérico | Capacidade de armazenamento em GB |
| `Storage Type` | Categórico | SSD, HDD ou híbrido |
| `Screen Size` | Numérico | Tamanho da tela em polegadas |
| `GPU` | Texto semi-estruturado | Modelo da placa gráfica |
| `Operating System` | Categórico | Sistema operacional |
| `Price (USD)` | Numérico | **Variável-alvo** — preço em dólares |

---

## Referências do Dataset
- **Origem dos Dados:**  
  O conjunto de dados foi obtido por meio da plataforma **Kaggle**, no dataset *Modern Laptop Prices and Specifications* (https://www.kaggle.com/datasets/sohaibdevv/modern-laptop-prices-and-specifications), publicado pelo usuário **sohaibdevv**.

- **Originalidade e Limitações:**  
  Os dados foram coletados via web scraping em varejistas globais de tecnologia durante 2024. Os preços estão em dólares americanos (USD) e podem não refletir variações regionais de mercado.

- **Período da Coleta:**  
  Produtos disponíveis comercialmente em **2024**.

- **Limitações de Uso:**  
  Por se tratar de um dataset público e de fonte secundária, seu uso é destinado a fins acadêmicos e de pesquisa. Os insights devem ser analisados considerando que os dados refletem apenas o catálogo disponível no período de coleta.

---

## Integrantes
Este projeto foi desenvolvido pelos seguintes integrantes:

- Ryan Rodrigues Pereira
- Nour Hussein Barakat
- Guilherme de Araújo Esp. Santo

**Universidade Presbiteriana Mackenzie**  
**Curso Banco de Dados**  
**Projeto Aplicado II - 2º Semestre 2025**
