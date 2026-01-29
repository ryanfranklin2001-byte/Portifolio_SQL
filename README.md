![Banner do projeto](Assests/Gemini_Generated_Image_duowzpduowzpduow.png)
# Análise de Dados de E-commerce: Ingestão, Saneamento e Business Intelligence com SQL 📊

Este projeto consiste em uma análise exploratória de dados (EDA) de ponta a ponta utilizando **MySQL**. O foco foi transformar um conjunto de dados brutos (Olist Dataset) em uma base de dados limpa, otimizada e enriquecida com KPIs estratégicos para suporte à tomada de decisão.

## 🎯 Objetivo do Projeto
Transformar dados brutos de e-commerce em informações acionáveis, respondendo a perguntas críticas sobre volume de pedidos, faturamento, eficiência logística e comportamento de clientes.

---

## 🛠️ Tecnologias e Ferramentas
* **Banco de Dados:** MySQL.
* **Linguagem:** SQL (DDL, DML, DQL).
* **Técnicas:** Ingestão de dados (ETL), limpeza de dados (Data Cleaning), análise temporal e integração de tabelas (Joins).

---

## ⚙️ Processos Técnicos Detalhados

### 1. Modelagem e Ingestão de Dados (ETL)
Foi estruturado um banco de dados relacional composto por tabelas integradas. A carga foi realizada via comando `LOAD DATA LOCAL INFILE` para máxima performance.

**Principais tabelas criadas:**
* `olist_pedidos`: Cabeçalho das vendas com timestamps de aprovação e entrega.
* `olist_pedido_itens`: Detalhamento de produtos, preços e fretes por pedido.
* `olist_pedido_pagamentos`: Informações de parcelamento e métodos de pagamento.
* `olist_clientes` e `olist_vendedores`: Dados cadastrais e geográficos.
* `olist_order_avaliacoes`: Feedback e scores dos clientes.

### 2. Limpeza e Integridade de Dados
* Para garantir a confiabilidade das análises, foram aplicadas técnicas de saneamento nos scripts:
* **Tratamento de Nulos:** Conversão de strings vazias para `NULL` em campos de timestamp de resposta.
* **Remoção de Duplicatas:** Identificação de registros duplicados na tabela de avaliações através de colunas auxiliares e `JOINs` internos para manter apenas a entrada mais recente.
* **Otimização:** Criação de índices (`INDEX`) em colunas de busca frequente, como `review_id`, para reduzir a latência das queries.
* **Manutenção:** Limpeza de registros inconsistentes em vendedores sem dados geográficos.

### 3. Enriquecimento e Business Intelligence
A partir dos dados limpos, foram desenvolvidas queries para extrair indicadores de performance (KPIs):

* **Eficiência Logística:** Cálculo do tempo médio de entrega (Lead Time) utilizando `TIMESTAMPDIFF` entre a data de postagem e a entrega ao cliente.
* **Análise de Faturamento:** Consolidação do valor total por pedido (Preço + Frete) e validação com os valores de pagamento.
* **Segmentação de Clientes (RFM):** Classificação dinâmica utilizando `CASE WHEN`:
    * **Cliente Novo:** 1 pedido.
    * **Recorrente:** 2 a 5 pedidos.
    * **Alto Potencial:** Mais de 5 pedidos.
* **Comportamento de Compra:** Identificação de tendências por dia da semana utilizando a função `DAYOFWEEK`.

---

## 📈 Resultados e Impacto
* **KPIs Estratégicos:** Estruturação de métricas de evolução mensal de faturamento e volume de pedidos.
* **Identificação de Sazonalidade:** Descoberta dos dias e meses com maior pico de demanda.
* **Logística:** Mapeamento do tempo médio de entrega para identificação de gargalos operacionais.
* **Base para Dashboards:** Os scripts preparam a base para conexão direta com ferramentas como Power BI ou Tableau.

---

> **Destaque Profissional:** Este projeto reflete a capacidade de conectar processos técnicos de banco de dados (SQL) a necessidades reais de negócio, garantindo que a análise final seja baseada em dados íntegros e otimizados.
