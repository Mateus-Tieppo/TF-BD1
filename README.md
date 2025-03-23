## 📌 Descrição do Projeto
Este projeto define a estrutura de um banco de dados relacional para um sistema de vendas. Ele gerencia informações de pessoas (clientes e fornecedores), produtos, vendas e promoções. O modelo foi projetado para garantir integridade e facilitar consultas e operações entre as tabelas.

## 📁 Estrutura do Banco de Dados
O banco de dados é composto pelas seguintes tabelas:

### 1. **Pessoas**
- `codigo`: Identificador único da pessoa (8 caracteres).
- `nome`: Nome da pessoa (até 150 caracteres).

### 2. **Clientes**
- `codigo`: Identificador da pessoa vinculada (8 caracteres).
- `cpf`: Cadastro de Pessoa Física (11 caracteres).

**Relacionamento:**
- `codigo` é chave estrangeira referenciando `Pessoas(codigo)`.

### 3. **Fornecedores**
- `codigo`: Identificador da pessoa vinculada (8 caracteres).
- `cnpj`: Cadastro Nacional da Pessoa Jurídica (18 caracteres).

**Relacionamento:**
- `codigo` é chave estrangeira referenciando `Pessoas(codigo)`.

### 4. **Vendas**
- `nota_fiscal`: Número da nota fiscal (10 dígitos).
- `data_venda`: Data da venda.
- `codigo`: Código do cliente (8 caracteres).

**Relacionamento:**
- `codigo` é chave estrangeira referenciando `Clientes(codigo)`.

### 5. **Produtos**
- `cod_prod`: Código único do produto (5 dígitos).
- `descricao`: Descrição do produto (até 200 caracteres).
- `codigo`: Código do fornecedor (8 caracteres).
- `qtd_estoque`: Quantidade disponível em estoque (4 dígitos).
- `preco`: Preço unitário do produto (10 dígitos, 2 casas decimais).

**Relacionamento:**
- `codigo` é chave estrangeira referenciando `Fornecedores(codigo)`.

### 6. **Itens_Vendidos**
- `nota_fiscal`: Nota fiscal da venda vinculada.
- `cod_prod`: Código do produto vendido.
- `quantidade`: Quantidade de itens vendidos (4 dígitos).
- `desconto`: Percentual de desconto aplicado (3 dígitos).
- `preco`: Preço final após desconto (10 dígitos, 2 casas decimais).

**Relacionamentos:**
- `nota_fiscal` referencia `Vendas(nota_fiscal)`.
- `cod_prod` referencia `Produtos(cod_prod)`.

### 7. **Promocoes**
- `cod_promo`: Código da promoção (8 dígitos).
- `nome_promo`: Nome da promoção (50 caracteres).
- `data_ini`: Data de início da promoção.
- `data_fim`: Data de término da promoção.

### 8. **Itens_Promo**
- `cod_promo`: Código da promoção associada.
- `cod_prod`: Código do produto em promoção.
- `desconto`: Percentual de desconto aplicado (3 dígitos).
- `cod_promo_0`: Código de outra promoção relacionada.
- `cod_prod_0`: Código de outro produto vinculado à promoção.

**Relacionamentos:**
- `cod_promo` referencia `Promocoes(cod_promo)`.
- `cod_prod` referencia `Produtos(cod_prod)`.
- `cod_promo_0` e `cod_prod_0` criam uma relação cruzada para promoções combinadas.

## 🔧 Requisitos para Implementação
- SGBD compatível com SQL padrão (MySQL, PostgreSQL, SQLite, etc.).
- Editor de SQL (DBeaver, Workbench, ou outro de preferência).

## 🚀 Como Executar
1. Crie um banco de dados novo no SGBD.
2. Copie e execute o script SQL fornecido.
3. Verifique a criação das tabelas e seus relacionamentos.
4. Insira dados de teste para validar o funcionamento.

## 🔍 Possíveis Melhorias Futuras
- Adicionar controle de usuários e permissões.
- Incluir histórico de alterações de estoque.
- Implementar gatilhos para atualização automática de descontos e preços finais.

---
