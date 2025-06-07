# 📦 Projeto Banco de Dados: E-commerce

Este projeto implementa um banco de dados MySQL para um cenário de e-commerce, com foco em:

- Criação de **tabelas relacionais completas**
- **Views personalizadas** para controle de acesso
- **Triggers** para consistência de dados
- **Controle de permissões** por tipo de usuário (Gerente e Funcionário)

---

## 🧱 Estrutura do Banco

O banco `ecommerce` contém as seguintes tabelas principais:

- `clients`: informações de clientes
- `products`: catálogo de produtos
- `orders`: pedidos realizados
- `payments`: formas de pagamento
- `sellers`, `suppliers`: vendedores e fornecedores
- Tabelas de relacionamento: `productOrder`, `productSeller`, `productSupplier`, etc.

---

## 👁️ Views Criadas

As views foram desenvolvidas para facilitar o acesso a dados conforme a função do usuário:

| View                    | Descrição                                                                 |
|-------------------------|---------------------------------------------------------------------------|
| `view_clients_by_orders` | Lista de clientes e seus pedidos com status                              |
| `view_full_orders`       | Produtos com avaliação ajustada e valor total de frete                   |

---

## 🔐 Permissões e Usuários

Dois usuários com permissões diferentes são criados:

- **gerente**  
  - Acesso total às views
  - Usuário: `gerente`  
  - Senha: `senha123`

- **funcionario**  
  - Acesso apenas à view de clientes e pedidos  
  - Usuário: `funcionario`  
  - Senha: `senha456`

### 🔧 Comandos utilizados:
```sql
CREATE USER 'gerente'@'localhost' IDENTIFIED BY 'senha123';
GRANT SELECT ON ecommerce.view_full_orders TO 'gerente'@'localhost';
GRANT SELECT ON ecommerce.view_clients_by_orders TO 'gerente'@'localhost';
