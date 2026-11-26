# PENDÊNCIAS — Estudo-SOLID-Principio-Inversao-Dependencia-Java

Este documento rastreia o status de validação, o backlog técnico e os requisitos de compilação do projeto comparativo sobre o Princípio da Inversão de Dependência (DIP).

---

## 1. ✅ Escopo Validado e Concluído
- **Comparativo Arquitetural Completo:**
  - Módulo `before`: Demonstração da violação do DIP onde o caso de uso de alto nível (`FinalizarPedido`) instancia e depende diretamente de implementações concretas de baixo nível (`MySqlPedidoRepository` e `SmtpEmailService`), gerando acoplamento rígido com banco de dados e bibliotecas externas.
  - Módulo `after`: Aplicação estrita do DIP onde os módulos de alto nível dependem apenas de abstrações (`PedidoRepository` e `NotificadorDePedido`) que pertencem à camada de aplicação/domínio. Os detalhes de infraestrutura (implementação em arquivo, MySQL, SMTP) passam a implementar tais abstrações, invertendo o fluxo de dependências do código-fonte.
- **Testes de Fronteira & Arquitetura:**
  - `DependenciasCamadasTest`: Teste automatizado validando a barreira de isolamento arquitetural para impedir que classes de domínio/aplicação importem pacotes de `infra`.
- **Suíte Total de Testes:** **6/6 testes aprovados** no JUnit 5 (testes de caso de uso com mocks, repositório em arquivo e testes de aceitação comportamental).
- **Compatibilidade Multi-JDK:** Configurado o plugin compilador com `<release>17</release>`, garantindo compilação limpa em JDK 17 e JDK 21.
- **Esteira de CI/CD Completa:** Workflow do GitHub Actions configurado (`.github/workflows/ci.yml`) validando o build e todos os testes a cada push.

---

## 2. 📋 Backlog de Engenharia (Próximas Melhorias Opcionais)
- [ ] Adicionar regras ArchUnit para governança contínua da regra de dependência das camadas.

---

## 3. ⚙️ Infraestrutura e Dependências Externas (Requer Ação do Desenvolvedor)
- **Compilador e Ferramental:** JDK 17 ou superior e Apache Maven 3.9+ configurados no ambiente.
