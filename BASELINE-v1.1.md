#  Baseline v1.1 - Sistema de Pedidos

# Identificação da Baseline

* **Baseline:** v1.1
* **Sistema:** Sistema de Pedidos - Versão 1.0
* **Data de criação:** 15/08/2026
* **Baseline anterior:** v1.0
* **Mudança relacionada:** RFC-001
* **Responsável pela aprovação:** Equipe Técnica

# Objetivo da Baseline

Registrar o novo estado oficial, estável, testado e aprovado do Sistema de Pedidos após a atualização do banco de dados de **MySQL 8.4 para MySQL 9.0**.

# Evolução da Configuração

* **Baseline anterior:** v1.0
* **Mudança aprovada:** MySQL 8.4 → MySQL 9.0
* **RFC relacionada:** RFC-001
* **Nova baseline:** v1.1

# Itens de Configuração (ICs)

# Aplicação

* **Node.js:** 22
* **Express:** 5.1
* **Porta:** 3000

# Banco de Dados

* **SGBD:** MySQL
* **Versão:** 9.0
* **Banco:** `pedidos`
* **Porta:** 3306

# Infraestrutura

* **Sistema Operacional:** Ubuntu Server 24.04
* **Memória RAM:** 4 GB
* **Processamento:** 2 vCPUs

# Código

* **Branch:** `main`
* **Commit:** `abc123`

# Alteração em Relação à Baseline v1.0

O único Item de Configuração alterado foi o banco de dados:

**MySQL 8.4 → MySQL 9.0**

As configurações da aplicação, infraestrutura e código permaneceram inalteradas.

A mudança foi solicitada por meio da **RFC-001**, avaliada, aprovada, implementada e testada antes da definição da nova baseline.

# Status da Baseline

A nova configuração foi validada e aprovada.

A **Baseline v1.1** passa a representar o novo estado oficial do Sistema de Pedidos.
