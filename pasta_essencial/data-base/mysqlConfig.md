# :gem:Configurando mySQL no eclipse:
---

* Fazer o download do conector:
  * https://dev.mysql.com/downloads/connector/j/
  * Selecionar "Platform Independent"
* Caso ainda não exista, criar uma User Library contendo o arquivo .jar do driver do MySQL
  * Window -> Preferences -> Java -> Build path -> User Libraries
  * Dê o nome da User Library de MySQLConnector
  * Add external JARs -> (localize o arquivo jar)

* Exemplo de 'properties':
  * Na pasta raiz do projeto, criar um arquivo "db.properties" contendo os dados de conexão:
    * user=developer
    * password=1234567
    * dburl=jdbc:mysql://localhost:3306/coursejdbc
    * useSSL=false

**burl=jdbc:mysql://localhost:3306/coursejdbc**
  * Essa são as mesmas configurações que estão no MySQL, coursejdbc do exemplo é o nome do banco de dados criado no Workbench








---
:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)