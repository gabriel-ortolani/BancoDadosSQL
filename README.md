# Passo a passo: Criação de um banco de dados
Tutorial de como criar um banco de dados SQL que organiza as informações de 'livros', 'ditora', 'autora' e 'assuntos'.
Esse guia sera dividido em etapas para demonstrar desde a crição de tabelas, chaves e até manipulação/consulta de dados.

## Resumo de uma estrutura SQL
* __CREATE__ para criar 'Banco de dados' ou 'tabelas'
* __ALTER__ para adicionar ou modificar colunas
* __DROP__ para remover 'Banco de dados' ou 'Tabelas'
* __INSERT__ para adicionar registros na tabela
* __UPDATE__ para atualizar os registros 
* __DELETE__ para remover os registros
* __SELECT__ para consultar e visualizar dados

## Passo 1: criação do Banco de Dados e das Tabelas
#### 1.1 Criando o DB

```SQL
CREAT DATABASE biblioteca;
USE biblioteca;
```

#### 1.2 Criando a tabela 'editora'
```SQL
CREATE TABLE editora (
    id_editora INT AUTO_INCREMENT PRIMARY KEY,
    nome_editora VARCHAR(100) NOT NULL,
    pais VARCHAR(50)
);
```

#### 1.3 Criando a tabela 'autor'
```SQL
CREATE TABLE autor (
    id_autor INT AUTO_INCREMENT PRIMARY KEY,
    nome_autor VARCHAR(100) NOT NULL,
    data_nascimento DATE
);
```

#### 1.4 Criando a tabela 'assunto'
```SQL
CREATE TABLE assunto (
    id_assunto INT AUTO_INCREMENT PRIMARY KEY,
    descricao_assunto VARCHAR(300) NOT NULL
);
```

#### 1.5 Criando a tabela 'livro'
```SQL
CREATE TABLE livro (
    id_livro INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(150) NOT NULL,
    ano_publicacao YEAR,
    FOREING KEY(id_editora) REFERENCES editora(id_editora),
    FOREING KEY(id_autor) REFERENCES autor(id_autor),
    FOREING KEY(id_assunto) REFERENCES assunto(id_assunto)
);
```

#### 1.6 Criando uma tabela EXTRA
A tabela EXTRA vai servir para exemplificar a exclusão

```SQL
CREATE TABLE extra(
    id INT PRIMARY KEY AUTO_INCREMENT,
    produtos VARCHAR(50),
    quantidade INT(20),
    preco DOUBLE NOT NULL
);
```

## Passo 2: editar tabelas usando 'ALTER'
Após a criação da tabela, podemos adicionar novos campos. Vamos adicionar uma coluna 'email' na tabela 'autor'

```SQL
ALTER TABLE autor
ADD COLUMN email VARCHAR(100);
```
