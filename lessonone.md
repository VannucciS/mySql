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

ALTER TABLE - adiciona um novo campo na tabela




