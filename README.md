# Credit Score
## Classificador de Pontuação de Crédito 
Este é um projeto de Data Science desenvolvido para classificar a pontuação de crédito das pessoas em bom ou ruim, com base em suas informações financeiras e de crédito.

## Problema a ser resolvido
Você está trabalhando como um cientista de dados em uma empresa financeira global. A empresa coletou ao longo dos anos detalhes básicos do banco e reuniu muitas informações relacionadas a crédito. A gerência deseja construir um sistema inteligente para segmentar as pessoas em faixas de pontuação de crédito para reduzir os esforços manuais.

# Estrutura do Projeto
Este projeto é organizado da seguinte forma:

__input:__ Pasta contendo os dados de entrada.

__src:__ Pasta contendo os códigos-fonte do projeto, dividido em 3 versões, incluindo scripts para pré-processamento de dados, treinamento de modelo e avaliação.

__model:__ Pasta contendo o modelo final salvo em arquivo pickle.

## Dados
Os dados são de uma base do Kaggle (https://www.kaggle.com/datasets/parisrohan/credit-score-classification) e incluem as seguintes informações:

- __ID:__ Identificação única de uma entrada.

- __Customer_ID:__ Identificação única de uma pessoa.
  
- __Month:__ Mês do ano.
  
- __Nome:__ Nome da pessoa.
  
- __Idade:__ Idade da pessoa.
  
- __SSN:__ Número de Seguro Social da pessoa.
  
- __Ocupação:__ Ocupação da pessoa.

- __Renda Anual (Annual_Income):__ Renda anual da pessoa.

- __Salário Líquido Mensal (Monthly_Inhand_Salary):__ Salário mensal líquido da pessoa.
  
- __Número de Contas Bancárias (Num_Bank_Accounts):__ Número de contas bancárias da pessoa.
  
- __Número de Cartões de Crédito (Num_Credit_Card):__ Número de outros cartões de crédito da pessoa.
  
- __Taxa de Juros no Cartão de Crédito (Interest_Rate):__ Taxa de juros no cartão de crédito.
  
- __Número de Empréstimos (Num_of_Loan):__ Número de empréstimos concedidos pelo banco.
  
- __Tipo de Empréstimo (Type_of_Loan):__ Tipos de empréstimo concedidos a uma pessoa.
  
- __Atraso a partir da Data de Vencimento (Delay_from_due_date):__ Número médio de dias de atraso a partir da data de vencimento.
  
- __Número de Pagamentos Atrasados (Num_of_Delayed_Payment):__ Número médio de pagamentos atrasados por pessoa.
  
- __Alteração Percentual no Limite do Cartão de Crédito (Changed_Credit_Limit):__ Alteração percentual no limite do cartão de crédito.
  
- __Número de Consultas de Crédito (Num_Credit_Inquiries):__ Número de consultas de crédito.
  
- __Classificação da Mistura de Créditos (Credit_Mix):__ Classificação da mistura de créditos.
  
- __Dívida Pendente (Outstanding_Debt):__ Dívida pendente a ser paga (em USD).
  
- __Taxa de Utilização do Cartão de Crédito (Credit_Utilization_Ratio):__ Taxa de utilização do cartão de crédito.
  
- __Idade do Histórico de Crédito (Credit_History_Age):__ Idade do histórico de crédito da pessoa.
  
- __Pagamento do Valor Mínimo (Payment_of_Min_Amount):__ Se apenas o valor mínimo foi pago pela pessoa.

- __Pagamentos Mensais de EMI (Total_EMI_per_month):__ Pagamentos mensais de EMI (em USD).
  
- __Valor Investido Mensalmente (Amount_invested_monthly):__ Valor investido mensalmente pelo cliente (em USD).
  
- __Comportamento de Pagamento (Payment_Behaviour):__ Comportamento de pagamento do cliente (em USD).
  
- __Saldo Mensal (Monthly_Balance):__ Saldo mensal do cliente (em USD).
  
- __Pontuação de Crédito (Credit_Score):__ Intervalo de pontuação de crédito (Pobre, Padrão, Bom)

# Limpeza dos dados
Durante o processo de preparação dos dados para modelagem, foram realizadas as seguintes etapas de limpeza:

### Remoção de Underlines em Algumas Respostas
Foi identificado que algumas respostas continham underlines que não eram relevantes para a análise. Para resolver isso, foi desenvolvida uma função que removeu esses underlines das respostas, garantindo a consistência dos dados.

### Ajuste dos Tipos das Colunas
As colunas foram cuidadosamente examinadas para garantir que os tipos de dados estivessem corretos. Isso incluiu a conversão de colunas categóricas para o tipo numéricas.

### Tratamento de Valores Negativos Indesejados
Durante a análise inicial dos dados, foram identificados valores negativos em colunas onde não deveriam existir e que foram ajustados

# Feature engineering

### Expansão da Coluna 'Type of Loan'
A coluna 'Type of Loan' foi expandida para criar colunas binárias indicando cada tipo de empréstimo obtido. Essa abordagem permite que o modelo capture a influência de cada tipo de empréstimo na pontuação de crédito do cliente de forma mais granular.

### Criação de uma Nova Coluna de Histórico de Crédito
Uma nova coluna foi criada para representar o total de meses de histórico de crédito que cada cliente possui. Essa informação pode ser útil para o modelo ao avaliar a estabilidade financeira e o comportamento de pagamento do cliente ao longo do tempo.

### Criação de Novas Variáveis Derivadas
Foram criadas várias novas variáveis derivadas com base em diferentes aspectos financeiros dos clientes, como renda anual, número de contas bancárias, número de cartões de crédito, etc. Essas variáveis fornecem insights adicionais sobre a situação financeira e o comportamento de pagamento dos clientes, ajudando a enriquecer o conjunto de dados e melhorar o desempenho do modelo.

### Redefinição das Categorias de Pontuação de Crédito
Para focar especificamente na diferenciação entre bons e maus pagadores, as categorias de pontuação de crédito "Padrão" e "Boa" foram consolidadas em uma única categoria "Boa". Essa abordagem visa otimizar o desempenho do modelo na identificação de clientes com alto risco de crédito.

# Versões dos Modelos

Versões Testadas do Modelo de Classificação de Crédito
Ao longo do desenvolvimento, testamos três principais versões do modelo para classificar os scores de crédito, cada uma explorando abordagens e técnicas diferentes. Abaixo estão os detalhes de cada versão:

### Versão 1: Seleção e Otimização do Modelo
Inicialmente, realizamos validação cruzada com vários modelos para identificar o mais adequado. Os modelos testados foram:

Decision Tree: DecisionTreeClassifier()

Random Forest: RandomForestClassifier()

Gradient Boosting: GradientBoostingClassifier()

XGBoost: XGBClassifier()

Logistic Regression: LogisticRegression()

O modelo de Random Forest se destacou e foi selecionado para uma otimização de hiperparâmetros detalhada usando a ferramenta Optuna.

### Versão 2: Voting Classifier
Após a otimização do Random Forest, experimentamos um Voting Classifier combinando:

Random Forest: RandomForestClassifier()

Gradient Boosting: GradientBoostingClassifier()

XGBoost: XGBClassifier()

Este approach visava utilizar a força coletiva dos modelos para uma previsão mais estável e robusta.

### Versão 3: Stacking Classifier
Na última iteração, implementamos um Stacking Classifier que utiliza uma estratégia de empilhamento dos modelos anteriores:

Modelos de base: Random Forest, Gradient Boosting, e KNN e SVC
Meta-modelo: LogisticRegression()
Este modelo foi desenhado para capturar e explorar diferentes padrões e relações nos dados que modelos individuais poderiam não captar sozinhos.

Cada versão foi avaliada com base em sua precisão, recall, F1-score e ROC-AUC, permitindo-nos identificar a melhor abordagem para o problema em questão.

Com isso em conta, o melhor modelo foi o da versão 3

# Métricas de Avaliação

Aplicando o modelo 3, tivemos as seguintes métricas:

__Precision:__ 0.9068

A precisão é a proporção de verdadeiros positivos (pessoas classificadas corretamente como bom crédito) em relação ao total de pessoas classificadas como bom crédito pelo modelo. Neste caso, o modelo tem uma precisão de aproximadamente 90.68%, o que indica que quando ele classifica alguém como tendo bom crédito, está correto em cerca de 90.68% das vezes.

__Recall:__ 0.9142

Recall, também conhecido como sensibilidade, é a proporção de verdadeiros positivos em relação ao total de verdadeiros positivos e falsos negativos (pessoas que realmente têm bom crédito, mas foram erroneamente classificadas como tendo crédito ruim). Um recall de aproximadamente 91.59% indica que o modelo identifica corretamente cerca de 91.42% das pessoas com bom crédito.

__F1-score:__ 0.9110

O F1-score é uma métrica que combina precisão e recall em uma única pontuação, calculada como a média harmônica das duas. Ele fornece uma medida mais equilibrada entre precisão e recall. Um F1-score de aproximadamente 91.10% indica um bom equilíbrio entre precisão e recall para o modelo.

__ROC-AUC:__ 0.9303

A área sob a curva ROC (ROC-AUC) é uma métrica que avalia o desempenho geral de um classificador binário. Quanto mais próximo o valor estiver de 1, melhor será o desempenho do modelo em distinguir entre as classes. Com um valor de aproximadamente 93.03%, seu modelo demonstra um bom desempenho na classificação dos dados.

__Matriz de Confusão__
Uma matriz de confusão é uma tabela que mostra a performance de um modelo de classificação em um conjunto de dados, onde as linhas representam as classes reais e as colunas representam as classes previstas pelo modelo.

|            | Previsto Crédito Ruim | Previsto Crédito Bom |
|------------|-----------------------|-----------------------|
| **Crédito Ruim** | 6699                  | 2000                  |
| **Crédito Bom** | 1826                  | 19475                 |

O modelo corretamente classificou 6699 pessoas com bom crédito como tendo bom crédito.
O modelo classificou erroneamente 2000 pessoas com bom crédito como tendo crédito ruim.
O modelo corretamente classificou 19475 pessoas com crédito ruim como tendo crédito ruim.
O modelo classificou erroneamente 1826 pessoas com crédito ruim como tendo bom crédito.
