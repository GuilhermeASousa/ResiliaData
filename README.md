# ResiliaData
Módulo 2 | Projeto Individual | Sistema ResiliaData

# Contexto
Você foi contratado para desenvolver um banco de dados que irá armazenar dados importantes que será utilizado pelo sistema RESILIADATA.

➔ O sistema irá auxiliar na avaliação de quais são as tecnologias que as empresas parceiras estão utilizando e quem são seus colaboradores;

➔ Vamos ter o cadastro de empresas parceiras, cadastro de tecnologias com a opção de selecionar a área (webdev, dados, marketing, etc.), uma tabela para registrar quais tecnologias as empresas estão utilizando e uma tabela para cadastro de colaboradores.

# O que é para fazer?
## Realizar essa modelagem e responder algumas perguntas com nosso modelo:
### 1. Quais são as entidades necessárias?
  - Empresa Parceira
  - Tecnologia
  - Uso de Tecnologia (relacionamento entre Empresa Parceira e Tecnologia)
  - Colaborador

### 2. Quais são os principais campos e seus respectivos tipos?
  - Empresa Parceira:
    - ID (chave primária, numérico)
    - Nome (texto)
    - Setor (texto)
      ```SQL
      CREATE TABLE Empresa_Parceira (
      ID INT PRIMARY KEY,
      Nome VARCHAR(255),
      Setor VARCHAR(255)
      );
      ```
  - Tecnologia:
    - ID (chave primária, numérico)
    - Nome (texto)
    - Área (texto)
      ```SQL
      CREATE TABLE Tecnologia (
      ID INT PRIMARY KEY,
      Nome VARCHAR(255),
      Área VARCHAR(255)
      );
      ```
  - Uso de Tecnologia:
    - ID_Empresa (chave estrangeira referenciando Empresa Parceira, numérico)
    - ID_Tecnologia (chave estrangeira referenciando Tecnologia, numérico)
    - Ano_de_Início (data)
    - Ano_de_Término (data)
      ```SQL
      CREATE TABLE Uso_de_Tecnologia (
      ID_Empresa INT,
      ID_Tecnologia INT,
      Ano_de_Início DATE,
      Ano_de_Término DATE,
      FOREIGN KEY (ID_Empresa) REFERENCES Empresa_Parceira(ID),
      FOREIGN KEY (ID_Tecnologia) REFERENCES Tecnologia(ID)
      );
      ```
  - Colaborador:
    - ID (chave primária, numérico)
    - Nome (texto)
    - Cargo (texto)
    - ID_Empresa (chave estrangeira referenciando Empresa Parceira, numérico)
      ```SQL
      CREATE TABLE Colaborador (
      ID INT PRIMARY KEY,
      Nome VARCHAR(255),
      Cargo VARCHAR(255),
      ID_Empresa INT,
      FOREIGN KEY (ID_Empresa) REFERENCES Empresa_Parceira(ID)
      );
      ```
### 3. Como essas entidades estão relacionadas?
  - A entidade "Uso de Tecnologia" está relacionada com "Empresa Parceira" e "Tecnologia" através das chaves estrangeiras ID_Empresa e ID_Tecnologia, respectivamente.
  - A entidade "Colaborador" está relacionada com "Empresa Parceira" através da chave estrangeira ID_Empresa.

### 4. Simule 2 registros para cada entidade.
  - _Inserindo registros na tabela Empresa Parceira:_
  ```SQL
  INSERT INTO Empresa_Parceira (ID, Nome, Setor)
  VALUES
  (1, 'Empresa A', 'Tecnologia'),
  (2, 'Empresa B', 'Marketing');
  ```
  - _Inserindo registros na tabela Tecnologia:_
  ```SQL
  INSERT INTO Tecnologia (ID, Nome, Área)
  VALUES
  (1, 'Python', 'Webdev'),
  (2, 'SQL', 'Dados');
  ```
  - _Inserindo registros na tabela Uso de Tecnologia:_
  ```SQL
  INSERT INTO Uso_de_Tecnologia (ID_Empresa, ID_Tecnologia, Ano_de_Início, Ano_de_Término)
  VALUES
  (1, 1, '2020-01-01', NULL),
  (2, 2, '2019-01-01', NULL);
  ```
  - _Inserindo registros na tabela Colaborador:_
  ```SQL
  INSERT INTO Colaborador (ID, Nome, Cargo, ID_Empresa)
  VALUES
  (1, 'João', 'Desenvolvedor', 1),
  (2, 'Maria', 'Analista de Dados', 2);
  ```
