

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
