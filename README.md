# Credit Score
## Classificador de Pontuação de Crédito
Este é um projeto de Data Science desenvolvido para classificar a pontuação de crédito das pessoas em bom ou ruim, com base em suas informações financeiras e de crédito.

## Problema a ser resolvido
Você está trabalhando como um cientista de dados em uma empresa financeira global. A empresa coletou ao longo dos anos detalhes básicos do banco e reuniu muitas informações relacionadas a crédito. A gerência deseja construir um sistema inteligente para segmentar as pessoas em faixas de pontuação de crédito para reduzir os esforços manuais.

# Estrutura do Projeto
Este projeto é organizado da seguinte forma:

__input:__ Pasta contendo os dados de entrada.

__src:__ Pasta contendo os códigos-fonte do projeto, incluindo scripts para pré-processamento de dados, treinamento de modelo e avaliação.

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

# Modelo
A versão final do modelo escolhido foi um ensemble usando a técnica de stacking, composto por:

Random Forest Classifier
Gradient Boosting Classifier
XGBoost Classifier
com uma regressão logística como modelo final do stacking.

# Métricas de Avaliação
__Precision:__ 0.9066

A precisão é a proporção de verdadeiros positivos (pessoas classificadas corretamente como bom crédito) em relação ao total de pessoas classificadas como bom crédito pelo modelo. Neste caso, o modelo tem uma precisão de aproximadamente 90.66%, o que indica que quando ele classifica alguém como tendo bom crédito, está correto em cerca de 90.66% das vezes.

__Recall:__ 0.9159

Recall, também conhecido como sensibilidade, é a proporção de verdadeiros positivos em relação ao total de verdadeiros positivos e falsos negativos (pessoas que realmente têm bom crédito, mas foram erroneamente classificadas como tendo crédito ruim). Um recall de aproximadamente 91.59% indica que o modelo identifica corretamente cerca de 91.59% das pessoas com bom crédito.

__F1-score:__ 0.9113

O F1-score é uma métrica que combina precisão e recall em uma única pontuação, calculada como a média harmônica das duas. Ele fornece uma medida mais equilibrada entre precisão e recall. Um F1-score de aproximadamente 91.13% indica um bom equilíbrio entre precisão e recall para o modelo.

__ROC-AUC:__ 0.9308

A área sob a curva ROC (ROC-AUC) é uma métrica que avalia o desempenho geral de um classificador binário. Quanto mais próximo o valor estiver de 1, melhor será o desempenho do modelo em distinguir entre as classes. Com um valor de aproximadamente 93.08%, seu modelo demonstra um bom desempenho na classificação dos dados.

__Matriz de Confusão__
Uma matriz de confusão é uma tabela que mostra a performance de um modelo de classificação em um conjunto de dados, onde as linhas representam as classes reais e as colunas representam as classes previstas pelo modelo.

|            | Previsto Crédito Ruim | Previsto Crédito Bom |
|------------|-----------------------|-----------------------|
| **Crédito Ruim** | 6689                  | 2010                  |
| **Crédito Bom** | 1790                  | 19511                 |

O modelo corretamente classificou 6689 pessoas com bom crédito como tendo bom crédito.
O modelo classificou erroneamente 2010 pessoas com bom crédito como tendo crédito ruim.
O modelo corretamente classificou 19511 pessoas com crédito ruim como tendo crédito ruim.
O modelo classificou erroneamente 1790 pessoas com crédito ruim como tendo bom crédito.
