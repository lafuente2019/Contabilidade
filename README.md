# Sistema de Cálculo de Custos e Margem Bruta no Padrão Lakehouse (Databricks)

## Visão Geral

Este projeto implementa um sistema completo para **cálculo de custos,
formação de preços e análise de margem bruta de produtos** utilizando o
padrão Lakehouse (**Bronze → Silver → Gold**) no Databricks.

A solução atende negócios alimentícios que precisam calcular de forma
precisa: - custo real por produto, - margem bruta, - produtos lucrativos
ou deficitários, - preço ideal para atingir margens desejadas, - impacto
de alterações de custos.

------------------------------------------------------------------------

## Objetivos do Projeto

-   Calcular custo unitário e mensal.
-   Distribuir custos fixos proporcionalmente ao consumo.
-   Gerar margem bruta (R\$ e %).
-   Detectar produtos com prejuízo.
-   Determinar markup.
-   Simular alterações de custo.
-   Criar ranking dos produtos mais lucrativos.
-   Organizar todo fluxo em Bronze/Silver/Gold.

------------------------------------------------------------------------

## Arquitetura Medalhão

    /mnt/datalake/margens/
        ├── bronze/
        │       ├── gastosProducao/
        │       └── produtos/
        │
        ├── silver/
        │       ├── config_normalizada/
        │       └── produtos_calculados/
        │
        ├── gold/
        │       ├── resumo_clientes/
        │       ├── ranking_produtos/
        │       ├── produtos_de_risco/
        │       ├── produtos_completos/
        │       └── simulacoes/

------------------------------------------------------------------------

## Bronze Layer -- Dados Crus

Contém arquivos enviados pelo cliente: - `config_clientes.xlsx` -
`produtos_clientes.xlsx`

------------------------------------------------------------------------

## Silver Layer -- Transformações

-   Normalização dos custos.
-   União config × produtos.
-   Cálculos de:
    -   custos proporcionais,
    -   custo total unitário,
    -   custo mensal total,
    -   margem bruta,
    -   markup.

------------------------------------------------------------------------

## Gold Layer -- Relatórios e Indicadores

Inclui: - markup por produto, - preço ideal para margens de 30%, 40%,
50%, - ranking top 10 produtos lucrativos, - produtos deficitários, -
participação de cada custo no total, - simulações de impacto, - tabela
final completa.

------------------------------------------------------------------------

## Arquivos Fake Incluídos

-   `config_clientes_fake.xlsx`
-   `produtos_clientes_fake.xlsx`

------------------------------------------------------------------------

## Tecnologias

-   Databricks Lakehouse
-   PySpark
-   Delta Lake
-   Python
-   DBFS
-   Power BI / Databricks SQL (opcional)

------------------------------------------------------------------------

## Evoluções Futuras

-   Dashboard automatizado