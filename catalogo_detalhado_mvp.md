
## 3.2. Catálogo de Dados

---

### A. Tabela de Fatos `silver.fato_vendas`:

1. `InvoiceNo` (PK): Número único da fatura. Texto alfanumérico.
2. `StockCode` (FK): Código do produto. Referencia `dim_produto.StockCode`.
3. `CustomerID` (FK): Identificador do cliente. Referencia `dim_cliente.CustomerID`.
4. `InvoiceDate`: Data e hora da transação.
5. `Quantity`: Quantidade vendida. Esperado: valores positivos e negativos (em caso de devolução).
6. `UnitPrice`: Preço unitário em libras esterlinas. Esperado: valores ≥ 0.
7. `ValorTotal`: Quantity * UnitPrice. Representa o total da linha da venda.

---

### B. Tabela de Dimensão `silver.dim_produto`:

1. `StockCode` (PK): Código do produto.
2. `Description`: Descrição textual do produto.

---

### C. Tabela de Dimensão `silver.dim_cliente`:

1. `CustomerID` (PK): Identificador do cliente.
2. `Country`: País de origem do cliente (Ex: United Kingdom, Germany, France...).

---

### D. Tabela de Dimensão `silver.dim_tempo`:

1. `InvoiceDate` (PK): Data da transação.
2. `Ano`: Ano extraído de InvoiceDate.
3. `Mes`: Mês numérico (1 a 12).
4. `Dia`: Dia do mês (1 a 31).
5. `DiaSemana`: Dia da semana (1 = Domingo até 7 = Sábado).

---

### E. Tabela Gold `gold.vendas_flat`:

Tabela final com a junção de todas as dimensões. Contém os seguintes campos:

- Todos os campos da `fato_vendas`.
- `Description` do produto.
- `Country` do cliente.
- Colunas temporais (`Ano`, `Mes`, `Dia`, `DiaSemana`).
