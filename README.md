# Sistema de Oficina Mecânica

Este projeto consiste em um sistema de gerenciamento para uma oficina mecânica de pequeno porte, desenvolvido como parte de um trabalho acadêmico. O sistema foi projetado para otimizar processos do dia a dia, como o controle de ordens de serviço, gerenciamento de estoque de peças e cadastro de clientes e veículos.

---

## 🛠️ Escolha da Infraestrutura de Banco de Dados: PostgreSQL

Para o armazenamento e gerenciamento dos dados do sistema, a tecnologia escolhida foi o **PostgreSQL**. A decisão baseou-se em critérios técnicos de estabilidade, compatibilidade e custo-benefício para o cenário do modelo de negócio proposto.

### Principais Justificativas para a Escolha:

*   **Modelo Relacional e Integridade de Dados:** Sendo um banco de dados relacional (SGBDR), o PostgreSQL garante a consistência total dos dados por meio de chaves estrangeiras e restrições (*constraints*). Isso impede falhas graves, como a exclusão acidental de um cliente que possui uma ordem de serviço em aberto ou a venda de uma peça inexistente no estoque.
*   **Ferramenta Open-Source Inteligente:** O PostgreSQL é 100% gratuito e de código aberto. Ele se destaca como a escolha ideal para cenários de média complexidade que não exigem o estresse ou o custo de licenças corporativas proprietárias.
*   **Fácil Escalabilidade:** Caso a oficina mecânica cresça ou se expanda para uma rede de franquias no futuro, o banco está preparado para lidar com volumes massivos de dados e replicação sem perda de performance.
*   **Ecossistema com IDEs Gratuitas:** O desenvolvimento e monitoramento das tabelas e consultas são facilitados pelo uso de ferramentas visuais gratuitas e robustas do mercado, como o [DBeaver](https://dbeaver.io) ou o pgAdmin.
*   **Integração Nativa com o Django (Python):** O ecossistema de backend do projeto utiliza o framework Django. O PostgreSQL é historicamente o banco oficial recomendado pela comunidade Django. Essa união fornece suporte total ao Django ORM e acesso a recursos avançados e otimizados, como mapeamento nativo de campos complexos e migrações totalmente estáveis.

---

## 📊 Análise Comparativa de Mercado

Para validar a escolha do PostgreSQL diante de outras soluções do mercado, foi elaborada a seguinte matriz comparativa focada nos requisitos do sistema da oficina mecânica:

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

### Conclusão Teórica do Comparativo:
O **SQLite** mostrou-se inviável devido ao travamento de escrita em acessos simultâneos na oficina. O **MongoDB** falha na amarração rígida das relações entre carros e clientes. Já o **MySQL** possui limitações no tratamento do Django e de dados dinâmicos em formato JSON se comparado ao Postgres. Por fim, bancos corporativos como o **SQL Server** entregariam recursos semelhantes, porém sob custos de licenciamento comercial proibitivos para o modelo de negócios de uma oficina de pequeno porte.

---

## 🚀 Tecnologias Utilizadas no Projeto

*   **Backend:** Python com o framework [Django](https://djangoproject.com)
*   **Banco de Dados:** [PostgreSQL](https://postgresql.org)
*   **Gerenciador do Banco:** DBeaver Community Edition
