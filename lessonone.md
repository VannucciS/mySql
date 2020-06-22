arquivos de programas / mysql / mysql server /bin mysql.exe -h localhost -u root -p

**COMANDOS DDL**

```
CREATE DATABASE curso_dba; - cria um banco de dados
DROP DATABASE curso_dba; - destrói um banco de dados
SHOW DATABASES; - mostra os bancos de dados do servidor
USE curso_dba; - seleciona um banco de dados para uso
SHOW TABLES curso_dba; - lista as tabelas de um banco de dados
CREATE TABLE <nomeDaTabela> (<campo1 tipo>)
```
**Tipos de dados**

* tinyint - -128 a 127 (signed)
* integer / int
* bigint
* bool / boolean / bit
* float (m,d)
* char(m) - caso o espaço não seja preenchido com o que foi digitado o sistema preenche os dados
* varchar(m) - semelhante ao char, mas sem o preenchimento (versão mais econômica do anterior)
* text/blob
* tinytext / tinyblob - string
* mediumtext / mediumblob - string
* enum - lista (máximo de 65.535 itens)
* date - datas

DESCRIBE - mostra a composição da tabela

DROP TABLE - destrói a tabela

ALTER TABLE <nome da tabela> ADD <campo adicionar> <tipo> - adiciona um novo campo na tabela

ALTER TABLE <> MODIFY<> - modifica um campo da tabela

ALTER TABLE <> CHANGE <> - renomear o nome de um campo e tipo

ALTER TABLE <> DROP COLUMN <> - apaga a coluna/ campo

ALTER TABLE <> RENAME <> - renomeia o nome da tabela



**Comandos DML**

* inserção de dados

INSERT INTO alunos (id, matricula, nome, email) VALUES (1, 123456, Jose, asdf@gmail.com);

* alteração de dados

* atualização de dados
```
UPDATE <tabela> SET email <(o que deve ser alterado>,
  where <campo> = 'alguma coisa';
  ```
* remoção de dados

```
DELETE  FROM <> WHERE <> = <>;

```

```
TRUNKATE
ALTER TABLE 
```
**Consulta de dados - SELECT**
* select concat  ( campo 1 , "-", campo3) from planilha;

**código para fazer backup**
```
mysqldump -u root -h localhost -p <nome do dba>  > c:\backup\backup_nome.sql
  
mysqldump -u [USERNAME] -p[PASSWORD] [DATABASE-NAME] > dumpfilename.sql

```

**código para restaurar**
```
mysqldump -u root -h localhost -p area_comercial < C:\Users\Aprendiz\Downloads\backup_area_comercial.sql

mysql -u [USERNAME] -p[PASSWORD] [DATABASE-NAME] < dumpfilename.sql
```
**OU**

Dentro do prompt do SQL

```
USE area_comercial;

SOURCE C:\Users\Aprendiz\Downloads\backup_area_comercial.sql

```
**Consultas com SELECT**
  
  ```
  SELECT <one.nomedocampo, one.nomedocampo2, two.nomedocampo, two.nomedocampo2>
  FROM tabela1 AS one
  INNER JOIN tabela2 AS two on id.one = id.two
  WHERE 
  
  
  SELECT e.matricula, e.nome, e.data_adminissao, c.nome AS cargo, d.sigla AS sigla_departamento, d.nome AS departamento, 
  FROM empregados e
  INNER JOIN cargos c ON c.id = e.cargo_id
  INNER JOIN departamentos d on d.id = e.cargo_id;
  
```
**TRIGGERS**

```
  CREATE TRIGGER calcular_preco_produtos BEFORE INSERT ON produtos FOR EACH ROW SET NEW.preco = NEW.CUSTO + (NEW.custo * 0.5);
  
  SHOW TRIGGERS; -  mostra as triggers
  
  CREATE TRIGGER remover_produtos_da_familia_excluida BEFORE DELETE ON familias_produtos FOR EACH ROW DELETE FROM produtos  where fk_codigo_familia = OLD.codigo;
  
  DROP TRIGGER <nome da trigger>;
  
  
  
  ```
  ```
  DELIMITER //
  CREATE TRIGGER
  BEGIN 
  
  END //
  DELIMITER;
  ```
**STORED PROCEDURES**


```
DELIMITER $$
CREATE PROCEDURE nome_procedure (parametros)
BEGIN
DECLARE <variaveis>;
...
<instruções>
...
END$$
DELIMITER;

```
**STORED PROCEDURES**

```
CREATE PROCEDURE retorna_se_e_caixa()
BEGIN
DECLARE vCodigo INT DEFAULT 104;
DECLARE vNomeBanco VARCHAR (44);
SELECT nome INTO vNomeBanco FROM bancos WHERE codigo = vCodigo;
IF vNomeBanco = 'Caixa Economica' THEN
SELECT 'É banco caixa' AS resultado;
ELSE
SLEECT 'Não é banco caixa' AS resultado;
END IF;
END $$ DELIMITER;


CALL retorna_se_e_caixa$$
```

**STORED PROCEDURES (LOOP)**

```
CREATE PROCEDURE realiza_loop()
BEGIN
DECLARE vInicial INT DEFAULT 1;
DECLARE vFinal INT DEFAULT 10;
WHILE vInicial ,+ vFinal DO
SELECT vInicial AS contador;
SET vInicial = vInicial + 10
