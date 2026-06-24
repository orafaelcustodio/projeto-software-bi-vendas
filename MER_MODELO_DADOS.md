# MER - Modelo de Dados do Dashboard de Análise de Vendas

Como o projeto é de BI/análise de dados, a entrega final utiliza um **Modelo Entidade-Relacionamento em formato dimensional**, adequado para análise no Power BI.

## Visão geral

O modelo é composto por uma tabela fato central, `FATO_VENDAS`, e seis tabelas dimensão:

- `DIM_DATA`
- `DIM_PRODUTO`
- `DIM_CATEGORIA`
- `DIM_REGIAO`
- `DIM_CANAL_VENDA`
- `DIM_FORMA_PAGAMENTO`

A tabela fato registra os eventos de venda. As dimensões representam os eixos de análise usados no dashboard.

## Entidades

### FATO_VENDAS
Tabela central do modelo. Cada linha representa uma venda/pedido.

Campos:
- `pedido_id` - chave primária da venda
- `id_data` - chave estrangeira para `DIM_DATA`
- `id_produto` - chave estrangeira para `DIM_PRODUTO`
- `id_regiao` - chave estrangeira para `DIM_REGIAO`
- `id_canal_venda` - chave estrangeira para `DIM_CANAL_VENDA`
- `id_forma_pagamento` - chave estrangeira para `DIM_FORMA_PAGAMENTO`
- `quantidade`
- `preco_unitario`
- `receita_total`

### DIM_DATA
Permite análises temporais.

Campos:
- `id_data`
- `data_venda`
- `ano`
- `mes`
- `nome_mes`
- `ano_mes`

### DIM_CATEGORIA
Classifica os produtos por categoria.

Campos:
- `id_categoria`
- `categoria`

### DIM_PRODUTO
Contém os produtos vendidos.

Campos:
- `id_produto`
- `produto`
- `id_categoria`

### DIM_REGIAO
Permite análise por região.

Campos:
- `id_regiao`
- `regiao`

### DIM_CANAL_VENDA
Permite análise por canal de venda.

Campos:
- `id_canal_venda`
- `canal_venda`

### DIM_FORMA_PAGAMENTO
Permite análise por forma de pagamento.

Campos:
- `id_forma_pagamento`
- `forma_pagamento`

## Relacionamentos

- `DIM_DATA` 1:N `FATO_VENDAS`
- `DIM_PRODUTO` 1:N `FATO_VENDAS`
- `DIM_REGIAO` 1:N `FATO_VENDAS`
- `DIM_CANAL_VENDA` 1:N `FATO_VENDAS`
- `DIM_FORMA_PAGAMENTO` 1:N `FATO_VENDAS`
- `DIM_CATEGORIA` 1:N `DIM_PRODUTO`

## Arquivos gerados

O MER está disponível nos seguintes formatos:

- `diagrams/MER_Dashboard_Analise_Vendas.png`
- `diagrams/MER_Dashboard_Analise_Vendas.svg`
- `diagrams/MER_Dashboard_Analise_Vendas.dot`
- `diagrams/MER_Dashboard_Analise_Vendas.mmd`

Os dados dimensionais também foram materializados em CSV na pasta:

`data/modelo_dimensional/`
