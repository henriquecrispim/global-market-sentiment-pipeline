# Multiregional Media Sentiment Pipeline: Ingestão de Big Data e PLN Corporativo 🌍🤖

Este repositório armazena o meu portfólio de Engenharia de Dados e Processamento de Linguagem Natural (PLN) aplicado ao Mercado Financeiro. O sistema consiste em um pipeline robusto e assíncrono que realiza o Web Scraping automatizado de **19 canais oficiais de feeds RSS** das maiores agências de notícias econômicas do Brasil e do mundo, normalizando dados textuais não estruturados e aplicando modelos lógicos de inteligência artificial para quantificar a atenção e o humor macro-financeiro global.

---

## 🎯 Abordagem de Negócio e Finanças Quantitativas

No mercado financeiro moderno, a velocidade de difusão de dados molda a dinâmica dos preços. Variáveis como a **Atenção do Investidor** e o **Sentimento da Mídia** atuam diretamente na precificação de ativos de risco e na mensuração do prêmio de risco implícito das ações (*Implicit Equity Risk Premium - ERP*). Notícias de teor pessimista geram aversão ao risco (*Risk-Off*), provocando fluxos de venda massivos, enquanto manchetes otimistas impulsionam mercados de alta (*Risk-On*).

Este ecossistema resolve o desafio de monitorar esse fluxo contínuo ao atuar como uma plataforma de **Inteligência Quantitativa de Mídia**, mapeando a assimetria informacional e permitindo que analistas e gestores avaliem o humor político-econômico nacional (focado no risco fiscal e Copom) em paralelo com o sentimento macro global (Wall Street, FED e geopolítica).

---

## 🧠 Engenharia de Dados e IA: Fluxo do Pipeline

O pipeline foi projetado seguindo as melhores práticas de arquitetura distribuída, operando de ponta a ponta sem interferência manual:

1. **Camada de Ingestão Massiva (Big Data Layer):** O motor varre assincronamente 19 servidores XML/RSS públicos de grandes players mundiais (*Yahoo Finance, Reuters, CNBC, Wall Street Journal, Bloomberg fallbacks, Financial Times tickers*) e nacionais (*Valor Econômico, InfoMoney, Estadão, Exame, G1*), extraindo até 25 manchetes em tempo real por veículo, o que confere uma capacidade de análise elástica de até **475 manchetes concorrentes por ciclo**.
2. **Classificação Geográfica Automatizada:** Os metadados textuais passam por um filtro algorítmico que particiona os registros nativamente entre *Nacional (Brasil)* e *Internacional (Global)*, blindando a integridade estatística das análises cruzadas.
3. **Mecanismo Léxico de IA (VADER Engine):** O ecossistema adota o classificador **VADER (Valence Aware Dictionary and sEntiment Reasoner)** da biblioteca NLTK. O modelo calcula o peso semântico das sentenças, mapeando a intensidade das palavras para computar o `Compound Score` em uma escala matemática contínua que varia de $-1.0000$ (pânico/estresse máximo) a $+1.0000$ (euforia/otimismo máximo).
4. **Zonas de Corte de Volatilidade e Agrupamento:** Através do método `.cut()` do Pandas, os scores numéricos são segmentados em classes discretas (*Otimista/Bullish*, *Pessimista/Bearish*, *Neutro*), alimentando as queries de agregação relacional matricial (`groupby`).

---

## 📉 Resultados e Análise Visual do Dashboard

O pipeline consolida os volumes e plota um dashboard multiregional comparativo utilizando gráficos facetados (*Facet Columns*), permitindo traçar paralelos imediatos entre a psicologia do mercado brasileiro e o comportamento internacional.

### 📊 Formalização Matemática dos Índices Corporativos
O pipeline calcula os índices macros através da média vetorial contínua:

$$\text{Índice Macro Regional} = \frac{1}{N} \sum_{i=1}^{N} \text{Compound Score}_i$$

* **Índice Nacional (Brasil):** Concentra o pulso da mídia local sobre política monetária, reformas fiscais e balanços da B3.
* **Índice Internacional (Global):** Reflete a direção macroeconômica global, decisões sobre taxas de juros americanas (FOMC) e cadeias de suprimentos globais.

### 🌐 Demonstração Interativa (Web)
O front-end gráfico foi totalmente encapsulado em HTML interativo com suporte a tooltips informativos e isolamento de elementos.

👉 **[ABRIR DASHBOARD INTERATIVO EM TELA CHEIA](https://henriquecrispim.github.io/global-market-sentiment-pipeline/dashboard_sentimento_massivo.html)**

---

## 🛠️ Tecnologias Utilizadas
* **Python 3**
* **Feedparser:** Biblioteca especializada no consumo e parsing de payloads XML/RSS de infraestrutura web de notícias.
* **NLTK (Natural Language Toolkit):** Implementação de Machine Learning léxico via algoritmo preditivo *VADER*.
* **Pandas & NumPy:** Engenharia de features, tratamento de strings, manipulação vetorial e particionamento matricial.
* **Plotly Express:** Mecanismo gráfico sênior para renderização interativa e geração de dashboards de negócios em alta definição.

---

## 🚀 Como Executar o Projeto

Para rodar este ecossistema automatizado de Big Data e Inteligência Artificial, siga o passo a passo abaixo:

1. **Abertura Direta:** Abra o arquivo `.ipynb` deste repositório diretamente no seu **Google Colab** (você pode utilizar o botão "Open in Colab" inserido no topo deste repositório).
2. **Execução em Lote:** Execute todas as células do notebook em sequência pressionando o atalho `Ctrl + F9` (ou acessando o menu superior *Ambiente de Execução > Executar tudo*).
3. **Extração de Artefatos:** Após o processamento do pipeline, os seguintes arquivos de inteligência e governança corporativa serão gravados e disponibilizados para download imediato na barra lateral de arquivos do ambiente:
   * `dashboard_sentimento_massivo.html`: O painel interativo facetado multiregional para consumo em navegadores web.
