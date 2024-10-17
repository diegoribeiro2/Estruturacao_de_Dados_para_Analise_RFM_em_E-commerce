# Estudo de Caso: Estruturação de Dados para Análise RFM em E-commerce

## Introdução

Neste projeto, fui contratado por uma empresa do ramo de e-commerce para levantar os indicadores de Recência, Frequência e Ticket Médio (RFM) de seus clientes. A metodologia RFM é uma técnica amplamente utilizada para segmentar clientes e analisar seu comportamento de compra:

- **R (Recency)**: Tempo desde a última compra do cliente (em dias).
- **F (Frequency)**: Quantidade de compras realizadas pelo cliente.
- **M (Monetary)**: Valor do ticket médio gasto pelo cliente, calculado como a média do total gasto por pedido.

## Dados Utilizados

Recebi um arquivo CSV contendo informações de compras de um e-commerce em 37 países. As colunas do dataset incluem:

- **CustomerID**: Código de identificação do cliente
- **Description**: Descrição do produto
- **InvoiceNo**: Código da fatura
- **StockCode**: Código de estoque do produto
- **Quantity**: Quantidade do produto
- **InvoiceDate**: Data do faturamento (compra)
- **UnitPrice**: Preço unitário do produto
- **Country**: País da compra

## Etapas de Desenvolvimento

### Etapa 01: Leitura e Inspeção dos Dados

Iniciei o projeto lendo o arquivo CSV e inspecionando os dados com a biblioteca Pandas. Utilize o método `describe` para entender a distribuição das variáveis e verificar os tipos de dados presentes no conjunto.

### Etapa 02: Tratamento de Valores Faltantes

Verifiquei se havia valores nulos na identificação do cliente utilizando `isna` e somando os nulos. Removi essas observações para garantir a integridade dos dados.

### Etapa 03: Filtragem de Preços e Quantidades

Realizei filtros para remover entradas com preços unitários ou quantidades iguais ou inferiores a zero. Esse passo foi crucial para eliminar dados inconsistentes que poderiam impactar as análises.

### Etapa 04: Remoção de Duplicatas

Utilizei a função `duplicated` para verificar e remover linhas duplicadas, uma vez que não faz sentido ter a mesma compra registrada mais de uma vez.

### Etapa 05: Correção dos Tipos de Dados

Corrigi os tipos de dados nas colunas relevantes, como `CustomerID` e `InvoiceDate`, para garantir que fossem apropriados para análise.

### Etapa 06: Tratamento de Outliers

Identifiquei e removi outliers extremos, considerando valores com quantidade superior a 10.000 ou preços unitários maiores que 5.000 como erros.

### Etapa 07: Cálculo do Preço Total

Criei uma nova coluna com o preço total da compra, multiplicando as colunas `Quantity` e `UnitPrice`.

### Etapa 08: Cálculo da Última Data de Compra

Utilizei a função `max()` para calcular a data da última compra registrada no dataset, que serviu como referência para o cálculo da recência.

### Etapa 09: Visualizações

Desenvolvi gráficos para analisar:
- Os 10 países com maior valor em vendas
- Os 10 produtos mais vendidos
- O valor de venda total por mês e por país (considerando apenas os 10 principais)

### Etapa 10: Cálculo do RFM

Por fim, agrupei os dados por cliente e fatura para obter a data e o preço total do pedido. Calculei o RFM da seguinte forma:
- **R**: Diferença em dias entre a última compra do cliente e a última compra no conjunto de dados.
- **F**: Quantidade total de compras feitas pelo cliente.
- **M**: Média das compras realizadas pelo cliente.

Esse processo resultou em um dataset estruturado e pronto para a análise, permitindo à empresa entender melhor o comportamento de seus clientes e direcionar suas estratégias de marketing.
