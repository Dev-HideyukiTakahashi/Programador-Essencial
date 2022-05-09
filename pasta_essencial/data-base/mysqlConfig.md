# :gem:Configurando mySQL no eclipse:

---

- Fazer o download do conector:
  - https://dev.mysql.com/downloads/connector/j/
  - Selecionar "Platform Independent"
- Caso ainda não exista, criar uma User Library contendo o arquivo .jar do driver do MySQL

  - Window -> Preferences -> Java -> Build path -> User Libraries
  - Dê o nome da User Library de MySQLConnector
  - Add external JARs -> (localize o arquivo jar)

- Exemplo de 'properties':
  - Na pasta raiz do projeto, criar um arquivo "db.properties" contendo os dados de conexão:
    - user=developer
    - password=1234567
    - dburl=jdbc:mysql://localhost:3306/coursejdbc
    - useSSL=false

**burl=jdbc:mysql://localhost:3306/coursejdbc**

- Essa são as mesmas configurações que estão no MySQL, coursejdbc do exemplo é o nome do banco de dados criado no Workbench

- Exemplo de código para abrir e fechar uma conexão com banco de dados

```java
package db;

import java.io.FileInputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

public class DB {
	/*
	 * Classe com métodos para gerar uma conexão com o banco de dados
	 */

	// Conectando com o banco de dados no JDBC

	private static Connection conn = null;

	public static Connection getConnection() {
		if(conn == null) {
			try {
				Properties props = loadProperties();
				String url = props.getProperty("dburl");
				conn = DriverManager.getConnection(url, props);
			}catch(SQLException e) {
				throw new DbException(e.getMessage());
			}
		}
		return conn;
	}

	// Método para fechar a conexão com o banco de dados
	public static void closeConnection() {
		if(conn != null) {
			try {
				conn.close();
			} catch (SQLException e) {
				throw new DbException(e.getMessage());
			}
		}
	}
	// Método auxiliar para carregar os dados do arquivo db.properties
	private static Properties loadProperties() {
		try(FileInputStream fs = new FileInputStream("db.properties")){
			Properties props = new Properties();
			props.load(fs);
			return props;
		}catch(IOException e) {
			throw new DbException(e.getMessage());
		}
	}
}
```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
