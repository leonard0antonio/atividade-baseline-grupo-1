# 📂 Atividade Prática: Baseline e Gerência de Configuração

![Ilustração do Projeto](demo.jpg)

**Equipe:** André Chagas, Lucas Emanuel, Gabriela Pires e Leonardo Antonio

## 📜 Histórico da Evolução da Configuração
*   **v1.0** → Baseline inicial aprovada
*   **RFC-001** → Solicitação de mudança para atualização do banco de dados
*   **Alteração do MySQL** → Implementação da versão 9.0
*   **Testes** → Validação das consultas da aplicação
*   **Aprovação** → Aceite formal da mudança
*   **v1.1** → Nova baseline estabelecida

## Desafio 1  – Criar a Baseline

# Baseline v1.0 - Sistema de Pedidos

## Identificação da Baseline

* **Baseline:** v1.0
* **Sistema:** Sistema de Pedidos - Versão 1.0
* **Data de criação:** 15/08/2026
* **Responsável pela aprovação:** Equipe Técnica
* **Branch:** `main`
* **Commit de referência:** `abc123`

# Objetivo da Baseline

Registrar o estado oficial, estável, testado e aprovado do Sistema de Pedidos, servindo como referência para o ambiente e para futuras alterações de configuração.

A baseline representa o conjunto dos Itens de Configuração aprovados neste momento, e não apenas o número da versão do sistema.

# Itens de Configuração (ICs)

#  Aplicação

* **Node.js:** 22
* **Express:** 5.1
* **Porta:** 3000

# Banco de Dados

* **SGBD:** MySQL
* **Versão:** 8.4
* **Banco:** `pedidos`
* **Porta:** 3306

# Infraestrutura

* **Sistema Operacional:** Ubuntu Server 24.04
* **Memória RAM:** 4 GB
* **Processamento:** 2 vCPUs

# Código

* **Branch:** `main`
* **Commit:** `abc123`

# Status da Baseline

A configuração registrada nesta baseline foi validada e aprovada pela equipe técnica.

A **Baseline v1.0** representa, portanto, o estado oficial do Sistema de Pedidos antes da alteração da versão do MySQL.

## Desafio 2 – Mudança não autorizada

1. **A baseline foi alterada? Por quê?** Não. A baseline não foi alterada porque ela representa um conjunto definido e aprovado de Itens de Configuração. O que foi alterado foi o servidor de produção real, gerando divergência.
2. **Qual Item de Configuração (IC) foi modificado?** O Banco de dados (atualizado para MySQL 9.0).
3. **Essa alteração deveria ter sido realizada diretamente em produção?** Não.
4. **Qual processo deveria ter sido executado antes da alteração?** O fluxo formal de mudança: Solicitar → Avaliar impacto → Aprovar/Rejeitar → Implementar/Testar → Verificar/Encerrar.
5. **O que deve acontecer com a baseline após uma mudança aprovada?** Deve ser registrada a evolução, gerando um novo documento de baseline (ex: v1.1) contendo a nova configuração aprovada.

## Desafio 3 – Criar uma RFC

# Solicitação de Mudança: RFC-001

* **IC afetado:** Banco de dados (MySQL)
* **Versão atual:** MySQL 8.4
* **Versão proposta:** MySQL 9.0
* **Motivo da mudança:** Problemas de desempenho identificados no servidor de produção utilizando a versão 8.4.
* **Riscos:** Incompatibilidade de queries existentes com a nova versão do MySQL, podendo gerar erros nas consultas da aplicação e indisponibilidade temporária durante a atualização.
* **Impacto na aplicação:** Alto. O Sistema de Pedidos depende diretamente do banco `pedidos`; falhas nas consultas podem indisponibilizar o sistema para os usuários.
* **Ambientes afetados:** Produção.
* **Testes necessários:** Testes de carga e validação de todas as consultas SQL utilizadas pela aplicação Node.js/Express contra a versão 9.0, em ambiente de homologação, antes da liberação em produção.
* **Plano de implementação:**
  1. Comunicar a janela de manutenção à equipe.
  2. Realizar backup completo do banco `pedidos`.
  3. Atualizar o pacote do MySQL no Ubuntu Server de 8.4 para 9.0.
  4. Restaurar os dados e validar a integridade do banco.
  5. Executar os testes de regressão nas consultas da aplicação.
* **Plano de rollback:** Caso os testes falhem ou ocorram erros em produção, desinstalar o MySQL 9.0, reinstalar o MySQL 8.4 e restaurar o backup do banco gerado antes da mudança, retornando o sistema ao estado da baseline v1.0.
* **Responsável:** Gabriela Pires
* **Aprovação:** Pendente

---

**Fluxo de referência:** Solicitar → Avaliar impacto → Aprovar/Rejeitar → Implementar/Testar → Verificar/Encerrar

## Desafio 4 – Criar uma nova Baseline

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

## Desafio 5 Configuration Drift

| Situação | É mudança controlada? | Está na baseline? | Justificativa |
| :--- | :--- | :--- | :--- |
| **Desenvolvedor altera o código e realiza um novo commit.** | **Sim** | **Não** | A alteração está sendo registrada por meio de um novo commit, permitindo rastreabilidade. Porém, como a baseline atual continua representando a configuração aprovada anteriormente, o novo código ainda não faz parte dela. |
| **Administrador altera manualmente uma configuração em produção.** | **Não** | **Não** | A alteração foi realizada diretamente no ambiente de produção, sem passar pelo processo de solicitação, avaliação, aprovação, implementação e testes. Portanto, o estado real do ambiente fica diferente do estado definido pela baseline. |
| **Mudança aprovada e documentada gera a baseline v1.1.** | **Sim** | **Sim** | A mudança passou pelo processo de controle e foi aprovada, implementada e testada com sucesso. Por isso, a nova configuração passa a ser oficialmente registrada na baseline v1.1. |

---
### Pergunta: Se alguém alterar manualmente o servidor depois da baseline v1.1, o que aconteceu com a configuração do ambiente?

### Resposta: Ocorrerá um Configuration Drift. Isso significa que a configuração real do ambiente ficará diferente da configuração oficialmente registrada na baseline.
