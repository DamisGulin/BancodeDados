# Conceito do Código SQL

O código SQL apresentado é um script para criar e gerenciar um banco de dados chamado `muriel`. O objetivo principal desse banco de dados é armazenar informações sobre usuários, seus contatos, endereços, produtos e compras. Vamos explorar cada parte do script.

## 1. Criação do Banco de Dados

```sql
CREATE DATABASE muriel;
USE muriel;
```

O script começa com a criação do banco de dados muriel e seleciona esse banco para uso em operações subsequentes.

## 2. Criação das Tabelas

```sql
CREATE TABLE USUARIOS(
	CPF BIGINT (11) UNSIGNED NOT NULL PRIMARY KEY AUTO_INCREMENT, 
	NOME VARCHAR (150) NOT NULL,
	SEXO VARCHAR (1),
	SALARIO DECIMAL (10,2),
	DATA_NASCIMENTO DATE,
	CREATED_AT TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP()
);
```

Descrição: Armazena informações sobre os usuários.
Campos:
    CPF: Identificador único do usuário (chave primária).
    NOME: Nome do usuário.
    SEXO: Gênero do usuário.
    SALARIO: Salário do usuário.
    DATA_NASCIMENTO: Data de nascimento.
    CREATED_AT: Data de criação do registro.

```sql
CREATE TABLE endereco(
	USER_CPF BIGINT(11) UNSIGNED NOT NULL DEFAULT'0',
	NOME VARCHAR (150) NOT NULL,
	NUMERO BIGINT (5) NOT NULL,
	CEP BIGINT (8) UNSIGNED NOT NULL,
	CREATED_AT TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP(),
	PRIMARY KEY (USER_CPF)
);
```
Descrição: Armazena informações de endereço dos usuários.
Campos:
    USER_CPF: Referência ao CPF do usuário (chave primária).
    NOME: Nome da rua.
    NUMERO: Número do endereço.
    CEP: Código postal.
    CREATED_AT: Data de criação do registro.

```sql
CREATE TABLE produto(
	cod_produto BIGINT (5) UNSIGNED NOT NULL PRIMARY KEY AUTO_INCREMENT,
	nome_produto VARCHAR (30) NOT NULL,
	preco_produto FLOAT (5) NOT NULL,
	nota_fiscal_num BIGINT (7) NOT NULL,
	CREATED_AT TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP()
);
```
Descrição: Armazena informações sobre os produtos disponíveis.
Campos:
    cod_produto: Identificador único do produto (chave primária).
    nome_produto: Nome do produto.
    preco_produto: Preço do produto.
    nota_fiscal_num: Número da nota fiscal associada.
    CREATED_AT: Data de criação do registro.

```sql
CREATE TABLE compra(
	cod_compra BIGINT (5) UNSIGNED NOT NULL PRIMARY KEY AUTO_INCREMENT,
	data_compra DATE NOT NULL,
	usuarios_CPF BIGINT(11) UNSIGNED NOT NULL DEFAULT'0',
	nota_fiscal_num BIGINT (7) NOT NULL
);
```
Descrição: Registra as compras feitas pelos usuários.
Campos:
    cod_compra: Identificador único da compra (chave primária).
    data_compra: Data da compra.
    usuarios_CPF: Referência ao CPF do usuário que fez a compra.
    nota_fiscal_num: Número da nota fiscal associada.

```sql
CREATE TABLE nota_fiscal(
	num_nota_fiscal BIGINT (7) UNSIGNED NOT NULL PRIMARY KEY AUTO_INCREMENT,
	compra_cod BIGINT (5) NOT NULL,
	data_nota_fiscal DATE NOT NULL,
	CREATED_AT TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP()
);
```

Descrição: Armazena informações sobre as notas fiscais geradas.
Campos:
    num_nota_fiscal: Identificador único da nota fiscal (chave primária).
    compra_cod: Referência ao código da compra associada.
    data_nota_fiscal: Data da nota fiscal.
    CREATED_AT: Data de criação do registro.

## 3. Inserção de Dados

O código inclui inserções de dados nas tabelas:
    USUARIOS: Adiciona três usuários com informações detalhadas.
    TELEFONES: Adiciona números de telefone associados a cada usuário.
    ENDEREÇO: Adiciona endereços para os usuários.
    PRODUTO: Adiciona um produto com preço e número da nota fiscal.
    COMPRA: Registra uma compra com data e referência ao usuário e nota fiscal.
    NOTA FISCAL: Adiciona informações sobre a nota fiscal relacionada à compra.

## 4. Considerações Finais

Este script SQL define uma estrutura básica para gerenciar um sistema de usuários e suas interações com produtos, compras e contatos. A modelagem de dados é feita de forma a permitir um relacionamento eficiente entre as entidades, garantindo integridade e acesso rápido às informações.



