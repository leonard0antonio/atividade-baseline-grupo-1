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