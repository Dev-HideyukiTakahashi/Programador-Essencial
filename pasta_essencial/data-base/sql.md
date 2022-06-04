# :gem:SQL

---

#### :floppy_disk: Comandos em SQL

---

- Comando **CREATE TABLE**
  - Utilizado para criar tabela, primeiro parâmetro é o nome da tabela, seguido pelos atributos.

**contato**
id | nome | sobrenome | nascimento| peso
--- | --- | --- | --- | ---

**email**
id | email | contato_fk
--- | --- | ---
Os seguintes comandos criam as tabelas respectivamente:

```
CREATE TABLE contato (
  id INT PRIMARY KEY, // define a chave primária
  nome VARCHAR(30) NOT NULL, // 'not null' força o usuário a definir esse campo
  sobrenome VARCHAR(30) NOT NULL,
  nascimento DATE,
  peso DECIMAL(5,2) // argumentos (quantidade de casas, casas após a ',') 5,2 exemplo: 000,00.
);
```

```
CREATE TABLE email(
  id INT PRIMARY KEY,
  email VARCHAR(60) NOT NULL,
  contato_fk INT,
  FOREIGN KEY (contato_fk) REFERENCES contato(id) // o atributo contato_fk dessa tabela está referenciando o id da tabela contato acima, sendo assim sua chave estrangeira
)
```

- Valores NULL e valores padrão:

  - **NOT NULL** não permite valores nulos.
  - **DEFAULT <'valor'>** define um valor paradão para os atributos.
  - Se não for especificado, os valores por padrão aceitam null.

- Valor único:

  - **UNIQUE**
    - Garante que não haja valores repetidos.
    - Como exemplo podemos incluir no atributo 'email' da tabela acima com mesmo nome:
      - `email VARCHAR(60) NOT NULL UNIQUE,`

- Consultas:
  - A expressão básica assume forma de : `SELECT<atributos> FROM <tabelas> WHERE <condições>`
- Exemplos:

  - Selecionar o nome e email de todos contatos cujo sobrenome seja 'Silva':

  ```
  SELECT nome, email
  FROM contato, email
  WHERE contato.id = email.contato_fk
  AND contato.sobrenome = 'Silva';
  ```

  - Selecionar o id do email de todos contatos com peso maior que 70:
    - Nesse exemplo existe ambiguidade, tanto na tabela contato como tabela email existe o campo 'id'. Nesse caso informamos o atributo com o nome de sua tabela.

  ```
  SELECT email.id
  FROM contato, email
  WHERE email.contato_fk = contato.id
  AND contato.peso > 70;
  ```

  - Alias(apelido)
    - No exemplo 1 'n' é um apelido para o campo contato.nome
    - No exemplo 2 o alias foi definido a uma tabela para consulta

  ```
  SELECT contato.nome AS n, email.email AS e
  FROM contato, email
  WHERE contato.id = email.contato_fk
  AND n = 'Maria';
  ```

  ```
  SELECT c.peso
  FROM contato c
  WHERE c.peso < 100;
  ```

- Distinct:
  - Utilizado para eliminar registros repetidos nas consultas

```
SELECT DISTINCT nome
FROM contato;
```

- LIKE:
  - Exemplo 1 selecionando todos emails que comece com 'maria@'
  - Exemplo 2 todos os contatos que nasceram na decada de 80

```
SELECT *
FROM email
WHERE email LIKE 'maria@%'; // '%' indica que pode possuir zero ou mais caracteres posteriores
```

```
SELECT *
FROM contato
WHERE nascimento LIKE '198_-__-__'; // para datas representadas como AAAA-MM-DD
```

- BETWEEN:
  - Selecionando contatos com peso entre 90 e 100

```
SELECT *
FROM contato
WHERE peso BETWEEN 90 AND 100;
```

- ASC / DESC:
  - Selecionando contatos por nome alfabética crescente e descrescente
  * Selecionando nome e sobrenome de todos contatos cujo nome comece com 'A' e ordenar por sobrenome em ordem descrescente e nome em ordem crescente

```
SELECT nome
FROM contato
ORDER BY nome ASC;
```

```
SELECT nome
FROM contato
ORDER BY nome DESC;
```

```
SELECT nome, sobrenome
FROM contato
WHERE sobrenome LIKE 'A%'
ORDER BY sobrenome DESC, nome ASC; // os critérios são avaliados pela ordem de declaração
```

##### Comando INSERT :

- Utilizado para inserir linhas (registros) em uma tabela.
- A ordem é a mesma definida na criação dos atributos da tabela, nesse exemplo a tabela 'contato' acima.

```
INSERT INTO contato
VALUES(10, 'João', 'Silva', '1990-04-12', 95 );
```

- Populando uma nova tabela com a tabela existente 'contato'

```
CREATE TABLE lista_de_nomes(
  nome varchar(30),
  sobrenome varchar(30)
);
```

```
INSERT INTO lista_de_nomes
SELECT nome, sobrenome
FROM contato
WHERE nascimento > '1980-01-01'
);
```

##### Comando UPDATE :

- Modifica um ou mais valores nas linhas(registros)
- Exempressão básica: `UPDATE <tabela> SET <atributos e valores> WHERE <condições>`

```
UPDATE contato
SET peso = 99, nascimento = '1982-04-25' // podemos modificar mais de um valor separando por vírgulas
WHERE nome = "Joao";

```

##### Comando DELETE :

- Remove linhas(registros) de uma tabela
- - Exempressão básica: `DELETE FROM <tabela> WHERE <condições>`

```
DELETE FROM email
WHERE id = 3
```

##### Comando JOIN:

- Selecionar o nome de todos contatos cujo email começa com 'maria@'
- Exemplo 1 sem Join, exemplo 2 com Join

```
SELECT nome
FROM contato, email
WHERE contato.id = email.contato_fk
AND email.email LIKE 'maria@%';
```

```
SELECT nome
FROM (contato JOIN email ON contato.id = email.contato_FK)
WHERE email.email LIKE 'maria@%';
```

##### Funções de agregação:

- Populares : COUNT, SUM, MAX, MIN e AVG (contagem, soma, valor máximo, valor mínimo e média)
- Exemplo 1, selecionando o peso mínimo e máximo de todos contatos.
- Exemplo 2, número total de contatos cujo peso > 80.

```
SELECT MAX(peso), MIN(peso)
FROM contato;
```

```
SELECT COUNT(*)
FROM contato
WHERE peso > 80;
```

##### Agrupamento

- Selecionando o sobrenome e quantidade de contatos que possuem o mesmo sobrenome:

```
SELECT sobrenome, COUNT(*)
FROM contato
GROUP by sobrenome;

```

##### Comandos de alteração de schema:

- Alterando o nome da coluna na tabela
```
ALTER TABLE tabela_exemplo 
CHANGE id_exemplo novo_id_exemplo integer(5) unsigned; /* é necessário colocar todos atributos referentes ao novo nome */
```

- Removendo um esquema do banco de dados

```
DROP SCHEMA pessoas;
```

- Removendo a tabela email

```
DROP TABLE email;
```

- Adicionando a coluna 'apelido' na tabela 'contato'

```
ALTER TABLE contato
ADD COLUMN apelido VARCHAR(15);
/* OBS de ordem, em default a coluna vai ser adicionada no final da tabela, podemos utilizar o comando 'after' para posicionar após alguma coluna específica, ou 'first' para posicionar no começo da tabela */

```

- Adicionando a coluna 'apelido' um padrão 'senhor' caso não exista uma definição no momento de criação do registro, e alterando o tamanho para 25 caracteres

```
ALTER TABLE contato
ADD COLUMN apelido VARCHAR(25) DEFAULT 'Senhor';
```

- Removendo a coluna apelido

```
ALTER TABLE contato
DROP COLUMN apelido;
```

- Adicionando uma chave primária a coluna caso não tenha

```
ALTER TABLE telefone
ADD PRIMARY KEY(id);
```

- Adicionando uma integridade referencial em uma tabela

```
ALTER TABLE telefone
ADD FOREIGN KEY(contato_fk)
REFERENCES contato(id);
```
