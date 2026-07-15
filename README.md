## Justificativa de Escolha do Banco de Dados: PostgreSQL

### 1. Robustez Relacional e Integridade de Dados
Banco relacional do PostgreSQL garante integridade através de chaves estrangeiras. Isso impede anomalias graves, como deletar um veículo que possui uma ordem de serviço vinculada.

### 2. Integração Perfeita com o Ecossistema Python/Django
O back-end do MVP utiliza o framework Django. O PostgreSQL é o banco de dados historicamente recomendado pela comunidade Django, oferecendo máxima compatibilidade com o Django ORM, estabilidade nas migrações de dados (`migrate`) e desempenho otimizado com o driver nativo `psycopg`.

### 5. Custo Zero e Escalabilidade Enterprise
Sendo uma ferramenta de código aberto de alta performance, o PostgreSQL elimina custos com licenças comerciais para a oficina. Ao mesmo tempo, caso o negócio se expanda, o banco suporta replicação e alta concorrência de múltiplos usuários (como atendentes, mecânicos e clientes via API).

---

## 📊 Análise Comparativa de Mercado

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
