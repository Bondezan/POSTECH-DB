# Tech Challenge - Sistema Integrado de Atendimento e Execução de Serviços

Este projeto consiste na primeira versão (MVP) do back-end de um Sistema Integrado de Atendimento e Execução de Serviços para uma oficina mecânica de médio porte. O objetivo é mitigar problemas de desorganização operacional, automatizar o fluxo de ordens de serviço (OS), controlar insumos e permitir o acompanhamento de status em tempo real pelos clientes.

O sistema foi desenvolvido seguindo os princípios de **Domain-Driven Design (DDD)** e estruturado em uma **arquitetura monolítica em camadas**.

---

## 🛠️ Justificativa de Escolha do Banco de Dados: PostgreSQL

Conforme os requisitos técnicos estabelecidos para a Fase 1, a escolha do banco de dados é livre mediante justificativa. Optou-se pelo **PostgreSQL** pelos seguintes fatores estratégicos e de arquitetura:

### 1. Robustez Relacional e Integridade de Dados
Como o sistema exige um controle rígido e amarrado de CRUDs de clientes, veículos, serviços e controle de estoque de peças, o modelo relacional do PostgreSQL garante consistência estrita através de chaves estrangeiras. Isso impede anomalias graves, como deletar um veículo que possui uma ordem de serviço vinculada.

### 2. Suporte Nativo a JSONB para Histórico Dinâmico
O PostgreSQL lida com o tipo de dado `JSONB` de forma otimizada. Esse recurso é ideal para persistir logs de auditoria, históricos de status da OS (Recebida, Em diagnóstico, Em execução, etc.) ou checklists de vistorias iniciais que possuem campos altamente dinâmicos por modelo de veículo.

### 3. Integração Perfeita com o Ecossistema Python/Django
O back-end do MVP utiliza o framework Django. O PostgreSQL é o banco de dados historicamente recomendado pela comunidade Django, oferecendo máxima compatibilidade com o Django ORM, estabilidade nas migrações de dados (`migrate`) e desempenho otimizado com o driver nativo `psycopg`.

### 4. Prontidão para Conteinerização (Docker & DevOps)
A infraestrutura do PostgreSQL possui imagens oficiais leves e maduras no Docker Hub. Isso facilita o cumprimento do requisito de entrega que exige um arquivo `docker-compose.yml` para orquestrar o ambiente completo da aplicação local de forma simples.

### 5. Custo Zero e Escalabilidade Enterprise
Sendo uma ferramenta de código aberto de alta performance, o PostgreSQL elimina custos com licenças comerciais para a oficina. Ao mesmo tempo, caso o negócio se expanda, o banco suporta replicação e alta concorrência de múltiplos usuários (como atendentes, mecânicos e clientes via API).

---

## 📊 Análise Comparativa de Mercado

A matriz abaixo detalha a superioridade técnica do PostgreSQL frente a outros bancos para as necessidades específicas do escopo desta oficina:

```text
=========================================================================================
      TABELA COMPARATIVA: POSTGRESQL VS OUTROS BANCOS (PARA OFICINA MECÂNICA)
=========================================================================================
Critério            | PostgreSQL  | MySQL       | SQLite      | MongoDB     | SQL Server
--------------------+-------------+-------------+-------------+-------------+------------
Custo de Licença    | Grátis      | Grátis      | Grátis      | Grátis*     | Muito Caro
Consultas Complexas | Excelente   | Média       | Ruim        | Muito Ruim  | Excelente
Vários Usuários     | Excelente   | Excelente   | Péssimo     | Excelente   | Excelente
Dados JSON (Check)  | Excelente   | Limitado    | Não tem     | Excelente   | Excelente
Conexão com Django  | Perfeita    | Boa         | Apenas Teste| Ruim        | Complexa
=========================================================================================
* Nota: O MongoDB possui versão gratuita, mas o suporte escalável em nuvem é pago.
```

*   **Por que não o SQLite?** Apesar de prático, o SQLite possui sérias restrições de concorrência, travando o arquivo de banco de dados caso múltiplos usuários tentem atualizar ordens de serviço simultaneamente.
*   **Por que não o MongoDB?** Por ser NoSQL, ele carece de mecanismos nativos eficientes para garantir a consistência relacional exigida entre tabelas cruciais do domínio (Cliente ➡️ Veículo ➡️ Peças ➡️ OS).

---

## 🚀 Tecnologias e Arquitetura

*   **Backend:** Python / Django Framework
*   **Banco de Dados:** PostgreSQL (SGBDR Open-source)
*   **Arquitetura:** Monolito em Camadas orientado a Domain-Driven Design (DDD)
*   **Segurança:** Autenticação via JWT para APIs Administrativas
*   **Orquestração:** Docker e Docker Compose
