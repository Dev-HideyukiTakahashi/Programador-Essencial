# :gem:JDBC (Java Database Connectivity)

---

- **RuntimeException**

```java
package dao;

public class DataBaseException extends RuntimeException {

	// RuntimeException personalizada para não precisar ficar tratando 'try' 'catch'
	// toda hora.

	private static final long serialVersionUID = 1L;

	public DataBaseException(String msg) {
		super(msg);
	}

}
```

---

**Tabelas usadas para o exemplo:**

- Table department:

|  Id |        Name |
| --: | ----------: |
|   1 |   Computers |
|   2 | Electronics |
|   3 |     Fashion |
|   4 |       Books |

- Table seller:

|  Id |        Name | Email            |           BirthData | BaseSalary | DepartmentId |
| --: | ----------: | ---------------- | ------------------: | ---------: | -----------: |
|   1 |   Bob Brown | bob@gmail.com    | 1998-04-21 00:00:00 |       1000 |            1 |
|   2 | Maria Green | maria@gmail.com  | 1979-12-31 00:00:00 |       3500 |            2 |
|   3 |   Alex Grey | alex@gmail.com   | 1988-01-15 00:00:00 |       2200 |            1 |
|   4 |  Martha Red | martha@gmail.com | 1993-11-30 00:00:00 |       3000 |            4 |
|   5 | Donald Blue | donald@gmail.com | 2000-01-09 00:00:00 |       4000 |            3 |
|   6 |   Alex Pink | bob@gmail.com    | 1997-03-04 00:00:00 |       3000 |            2 |

---

- **Classe 'DataSource'**

```java
package dao;

import java.io.FileInputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;

public class DataSource {

	private static Connection connection = null;

	public static Connection getConnection() {
		if (connection == null) {
			try {
				Properties props = loadProperties();
				String url = props.getProperty("dburl");
				connection = DriverManager.getConnection(url, props);
			} catch (SQLException e) {
				throw new DataBaseException(e.getMessage());
			}
		}
		return connection;
	}

	public static void closeConnection() {
		if (connection != null) {
			try {
				connection.close();
			} catch (SQLException e) {
				throw new DataBaseException(e.getMessage());
			}
		}
	}

	private static Properties loadProperties() {
		try (FileInputStream fs = new FileInputStream("db.properties")) {
			Properties props = new Properties();
			props.load(fs);
			return props;
		} catch (IOException e) {
			throw new DataBaseException(e.getMessage());
		}
	}

	public static void closeStatement(Statement statement) {
		if (statement != null) {
			try {
				statement.close();
			} catch (SQLException e) {
				throw new DataBaseException(e.getMessage());
			}
		}
	}

	public static void closeResultSet(ResultSet resultSet) {
		if (resultSet != null) {
			try {
				resultSet.close();
			} catch (SQLException e) {
				throw new DataBaseException(e.getMessage());
			}
		}
	}
}
```

---

### :floppy_disk:CRUD

- (Create, Read, Update, Delete)

---

#### Demo: inserir dados

- API:

  - PreparedStatement
  - executeUpdate
  - Statement.RETURN_GENERATED_KEYS
  - getGeneratedKeys

- **Intput**:

```java
package application;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.text.ParseException;
import java.text.SimpleDateFormat;

import dao.DataSource;

public class Program {

	public static void main(String[] args) {

		// Inserindo um novo seller

		Connection connection = null;
		PreparedStatement st = null;

		try {

			SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
			connection = DataSource.getConnection();

			// O campo id é auto incrementado
			// "?" é umm placeholder, no exemplo são 5 placeholders que representam cada
			// atributo de seller
			st = connection.prepareStatement("INSERT INTO seller "
					+ "(Name, Email, BirthDate, BaseSalary, DepartmentId) VALUES (?, ?, ?, ?, ?) ", Statement.RETURN_GENERATED_KEYS);
    // Statement.RETURN_GENERATED_KEYS é usado para recuperar o ID, é opcional


			// Populando os campos placeholder, sintaxe tipo(posição, valor)
			st.setString(1, "Carl Purple");
			st.setString(2, "carl@gmail.com");
			st.setDate(3, new java.sql.Date(sdf.parse("22/04/1985").getTime()));
			st.setDouble(4, 3000.0);
			st.setInt(5, 4);

      // Retorno para ver quantas linhas foram afetadas, pode ser utilizada em conjunto com Statement.RETURN_GENERATED_KEYS para retornar o ID afetado
			int rowsAffected = st.executeUpdate();
			if(rowsAffected > 0) {
				// O resultset pode retornar mais de 1 valor
				ResultSet rs = st.getGeneratedKeys();
				while(rs.next()) {
					// Passando a primeira coluna que no caso é a coluna Id
					int id = rs.getInt(1);
					System.out.println("Done! ID = " + id);
				}
			}else {
				System.out.println("No rown affected!");
			}

		} catch (SQLException e) {
			e.printStackTrace();
		} catch (ParseException e) {
			e.printStackTrace();
		} finally {
			DataSource.closeStatement(st);
			DataSource.closeConnection();

		}

	}

}

```

- **Output**
  - Tabela do banco de dados MySQL é gerado um novo 'seller'

|  Id |        Name | Email          |           BirthData | BaseSalary | DepartmentId |
| --: | ----------: | -------------- | ------------------: | ---------: | -----------: |
|   7 | Carl Purple | carl@gmail.com | 1985-04-22 00:00:00 |       3000 |            4 |

---

#### Demo: recuperar dados

API:

- Statement
- ResultSet

  - first() [move para posição 1, se houver]
  - beforeFirst() [move para posição 0]
  - next() [move para o próximo, retorna false se já estiver no último]
  - absolute(int) [move para a posição dada, lembrando que dados reais começam em 1]

- **Intput**:

```java
package application;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import dao.DataSource;

public class Program {

	public static void main(String[] args) {

		Connection connection = null;
		Statement st = null;
		ResultSet rs = null;

		try {
			connection = DataSource.getConnection();
			st = connection.createStatement();
			rs = st.executeQuery("select * from department");

			while (rs.next()) {
				System.out.println(rs.getInt("Id") + ", " + rs.getString("Name"));
			}
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			DataSource.closeStatement(st);
			DataSource.closeResultSet(rs);
      // Fechar a conexão sempre ao final
      DataSource.closeConnection();
		}
	}
}

```

- **Output**:

```
1, Computers
2, Electronics
3, Fashion
4, Books
```

---

#### Demo: atualizar dados

```java
package application;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import dao.DataSource;

public class Program {

	public static void main(String[] args) {

		// Atualizando salario de um 'seller'

		Connection connection = null;
		PreparedStatement st = null;

		try {

			connection = DataSource.getConnection();
			// Nesse caso somando o salário que já estava atribuído com + um placeholder
			// Seria apenas o placeholder para um novo salário
			st = connection.prepareStatement(
					"UPDATE seller " +
					"SET BaseSalary = BaseSalary + ? " +
					"WHERE (DepartmentId = ?)");
			st.setDouble(1, 200.0);
			st.setInt(2, 2);

			int rowsAffected = st.executeUpdate();
			System.out.println("Done! " + rowsAffected + " rows affected.");

		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			DataSource.closeStatement(st);
			DataSource.closeConnection();
		}
	}
}

```

---

#### Demo: deletar dados

```java
package application;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import dao.DataSource;

public class Program {

	public static void main(String[] args) {

		Connection connection = null;
		PreparedStatement st = null;

		try {

			connection = DataSource.getConnection();

			st = connection.prepareStatement(
					"DELETE FROM department "+
					"WHERE " +
					"Id = ?");
			st.setInt(1, 5);

			int rowsAffected = st.executeUpdate();
			System.out.println("Done! " + rowsAffected + " rows affected.");

		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			DataSource.closeStatement(st);
			DataSource.closeConnection();
		}
	}
}

```

---

#### Demo: transações

- Garantir a integridade do banco de dados

- API:
  - setAutoCommit(false)
  - commit()
  - rollback()

* **Input**:

```java
package application;

import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

import dao.DataBaseException;
import dao.DataSource;

public class Program {

	public static void main(String[] args) {

		Connection connection = null;
		Statement st = null;

		try {

			connection = DataSource.getConnection();

			// Comando para setar o comit para manual
			connection.setAutoCommit(false);

			st = connection.createStatement();

			int rows1 = st.executeUpdate("UPDATE seller SET BaseSalary = 2090 WHERE DepartmentId = 1");

			// fake exception no meio da transação, executa apenas o que está antes do algoritmo 'if'
			int x = 1;
			if(x < 2) {
				throw new SQLException("Fake error");
			}

			int rows2 = st.executeUpdate("UPDATE seller SET BaseSalary = 3090 WHERE DepartmentId = 2");


			// comando para comitar, garantindo que todos os blocos serão executados
			connection.commit();

			System.out.println("rows1: " + rows1);
			System.out.println("rows2: " + rows1);



		} catch (SQLException e) {
			//caso não conseguir chegar no commit manual, cai em uma exception, podendo receber um rollback
			// e não executar nada, mantendo a integridade
			try {
				connection.rollback();
				throw new DataBaseException("Transaction rolled back! Caused by : " + e.getMessage());
			} catch (SQLException e1) {
				throw new DataBaseException("Error trying to rollback! Caused by : " + e1.getMessage());
			}
		} finally {
			DataSource.closeStatement(st);
			DataSource.closeConnection();
		}
	}
}


```

- **Output**:

```
Exception in thread "main" dao.DataBaseException: Transaction rolled back! Caused by : Fake error
	at application.Program.main(Program.java:50)
```

---

**Referência DevSuperior** :mega:[ https://learn.devsuperior.com/](https://learn.devsuperior.com/)

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
