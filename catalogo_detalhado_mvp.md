

# Catálogo de Dados - MVP E-commerce

| Tabela           | Coluna       | Tipo         | Descrição                                                       |
|------------------|--------------|--------------|-----------------------------------------------------------------|
| fato_vendas      | InvoiceNo    | String       | Número único da fatura (PK)                                     |
| fato_vendas      | StockCode    | String       | Código do produto (FK para dim_produto)                         |
| fato_vendas      | CustomerID   | String       | Identificador do cliente (FK para dim_cliente)                 |
| fato_vendas      | InvoiceDate  | Timestamp    | Data e hora da transação                                        |
| fato_vendas      | Quantity     | Integer      | Quantidade vendida (pode ser negativa em devoluções)           |
| fato_vendas      | UnitPrice    | Decimal(10,2)| Preço unitário                                                  |
| fato_vendas      | ValorTotal   | Decimal(10,2)| Quantity * UnitPrice                                            |
| dim_produto      | StockCode    | String       | Código do produto (PK)                                          |
| dim_produto      | Description  | String       | Descrição do produto                                            |
| dim_cliente      | CustomerID   | String       | Identificador do cliente (PK)                                   |
| dim_cliente      | Country      | String       | País do cliente                                                 |
| dim_tempo        | InvoiceDate  | Timestamp    | Data original da transação (PK)                                 |
| dim_tempo        | Ano          | Integer      | Ano da compra                                                   |
| dim_tempo        | Mes          | Integer      | Mês da compra                                                   |
| dim_tempo        | Dia          | Integer      | Dia da compra                                                   |
| dim_tempo        | DiaSemana    | Integer      | Dia da semana (1=Domingo a 7=Sábado)                            |
| vendas_flat      | *            | Diversos     | Junção de fato com todas as dimensões


# Linhagem dos Dados
A EXT foi feita do repositório do KAGGLE (https://www.kaggle.com/datasets/jihyeseo/online-retail-data-set-from-uci-ml-repo?resource=download). 
É uma base de uma loja de E-Commerce localizada no Reino Unido com as suas vendas durante os anos de 2010 e 2011. 

### Técnicas de modelagem e transformação aplicadas:
- ** Camada Bronze: Ingestão direta dos dados, sem tratamento e diagnóstico do que necessitaria de uma transformação na próxima camada.
- ** Camada Silver: Transformações, e criação das tbls de dimensão ('dim_produto', 'dim_cliente' e 'dim_tempo') e da tabela 'fato_vendas'. 
- ** Camada Ouro: Criação da tabela 'vendas_flat', a partir da junção da tabela fato com as tabelas de dimensão para fazermos as análises voltadas ao negócio. 
