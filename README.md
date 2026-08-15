# 📂 Atividade Prática: Baseline e Gerência de Configuração

## Histórico da Evolução da Configuração
*   **v1.0** → Baseline inicial aprovada
*   **RFC-001** → Solicitação de mudança para atualização do banco de dados
*   **Alteração do MySQL** → Implementação da versão 9.0
*   **Testes** → Validação das consultas da aplicação
*   **Aprovação** → Aceite formal da mudança
*   **v1.1** → Nova baseline estabelecida

---

## Desafio 2 - Análise da Mudança Não Autorizada
1.  **A baseline foi alterada? Por quê?** Não. A baseline é um documento/estado aprovado. O que foi alterado foi o ambiente de produção físico, gerando uma divergência técnica entre o que está rodando e a baseline v1.0 oficial.
2.  **Qual Item de Configuração (IC) foi modificado?** O Banco de dados (MySQL).
3.  **Essa alteração deveria ter sido realizada diretamente em produção?** Não.
4.  **Qual processo deveria ter sido executado antes da alteração?** A criação de uma Solicitação de Mudança (RFC), seguida por avaliação de impacto, aprovação e testes em ambiente seguro antes de ir para produção.
5.  **O que deve acontecer com a baseline após uma mudança aprovada?** Ela deve ser atualizada, gerando uma nova versão (ex: v1.1), registrando o novo estado oficial.

---

## Desafio 5 - Configuration Drift

| Situação | É mudança controlada? | Está na baseline? |
| :--- | :--- | :--- |
| Desenvolvedor altera o código e realiza um novo commit. | Não (se não houver RFC/processo) | Não |
| Administrador altera manualmente uma configuração em produção. | Não | Não |
| Mudança aprovada e documentada gera a baseline v1.1. | Sim | Sim |

*   **Explicação:** Se alguém alterar manualmente o servidor após a baseline v1.1, ocorrerá o fenômeno de "Configuration Drift" (desvio de configuração). O ambiente real deixará de ser um espelho confiável do estado documentado e aprovado, trazendo riscos de instabilidade e dificultando futuras manutenções ou auditorias.

---

## 🚀 Pergunta Final
A baseline é fundamental para uma equipe DevOps pois funciona como a "fonte da verdade" do sistema, garantindo que todos saibam exatamente quais versões e configurações estão estáveis. Quando alterações ocorrem sem controle, surgem problemas como o *Configuration Drift*, falhas em cascata (como erros no banco afetando a aplicação), perda de rastreabilidade de quem fez o quê e a impossibilidade de realizar um *rollback* seguro em caso de incidentes.