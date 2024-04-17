# Credit_score
## Classificador de Pontuação de Crédito
Este é um projeto de Data Science desenvolvido para classificar a pontuação de crédito das pessoas em bom ou ruim, com base em suas informações financeiras e de crédito.

## Problema a ser resolvido
Você está trabalhando como um cientista de dados em uma empresa financeira global. A empresa coletou ao longo dos anos detalhes básicos do banco e reuniu muitas informações relacionadas a crédito. A gerência deseja construir um sistema inteligente para segmentar as pessoas em faixas de pontuação de crédito para reduzir os esforços manuais.

## Dados
Os dados são de uma base do Kaggle (https://www.kaggle.com/datasets/parisrohan/credit-score-classification) e incluem as seguintes informações:

ID: Identificação única de uma entrada.
Customer_ID: Identificação única de uma pessoa.
Month: Mês do ano.
Nome: Nome da pessoa.
Idade: Idade da pessoa.
SSN: Número de Seguro Social da pessoa.
Ocupação: Ocupação da pessoa.
Renda Anual (Annual_Income): Renda anual da pessoa.
Salário Líquido Mensal (Monthly_Inhand_Salary): Salário mensal líquido da pessoa.
Número de Contas Bancárias (Num_Bank_Accounts): Número de contas bancárias da pessoa.
Número de Cartões de Crédito (Num_Credit_Card): Número de outros cartões de crédito da pessoa.
Taxa de Juros no Cartão de Crédito (Interest_Rate): Taxa de juros no cartão de crédito.
Número de Empréstimos (Num_of_Loan): Número de empréstimos concedidos pelo banco.
Tipo de Empréstimo (Type_of_Loan): Tipos de empréstimo concedidos a uma pessoa.
Atraso a partir da Data de Vencimento (Delay_from_due_date): Número médio de dias de atraso a partir da data de vencimento.
Número de Pagamentos Atrasados (Num_of_Delayed_Payment): Número médio de pagamentos atrasados por pessoa.
Alteração Percentual no Limite do Cartão de Crédito (Changed_Credit_Limit): Alteração percentual no limite do cartão de crédito.
Número de Consultas de Crédito (Num_Credit_Inquiries): Número de consultas de crédito.
Classificação da Mistura de Créditos (Credit_Mix): Classificação da mistura de créditos.
Dívida Pendente (Outstanding_Debt): Dívida pendente a ser paga (em USD).
Taxa de Utilização do Cartão de Crédito (Credit_Utilization_Ratio): Taxa de utilização do cartão de crédito.
Idade do Histórico de Crédito (Credit_History_Age): Idade do histórico de crédito da pessoa.
Pagamento do Valor Mínimo (Payment_of_Min_Amount): Se apenas o valor mínimo foi pago pela pessoa.
Pagamentos Mensais de EMI (Total_EMI_per_month): Pagamentos mensais de EMI (em USD).
Valor Investido Mensalmente (Amount_invested_monthly): Valor investido mensalmente pelo cliente (em USD).
Comportamento de Pagamento (Payment_Behaviour): Comportamento de pagamento do cliente (em USD).
Saldo Mensal (Monthly_Balance): Saldo mensal do cliente (em USD).
Pontuação de Crédito (Credit_Score): Intervalo de pontuação de crédito (Pobre, Padrão, Bom).
Modelo
A versão final do modelo escolhido foi um ensemble usando a técnica de stacking, composto por:

Random Forest Classifier
Gradient Boosting Classifier
XGBoost Classifier
com uma regressão logística como modelo final do stacking.

Estrutura do Projeto
Este projeto é organizado da seguinte forma:

input: Pasta contendo os dados de entrada.
src: Pasta contendo os códigos-fonte do projeto, incluindo scripts para pré-processamento de dados, treinamento de modelo e avaliação.
model: Pasta contendo o modelo final salvo em arquivo pickle.
