# :gem:Properties

---

- O arquivo de propriedade é uma ótima opção para passar configurações para uma determinada aplicação que necessitada de configurações externas e a mesma em si não pode ser alterada. Um exemplo seria um programa que conecta a um banco de dados e precisa de dados para realizar a conexão, sem que o código fonte do mesmo seja alterado. Um outro exemplo seria guardar informações que um determinado arquivo .jar pode vir a utilizar.

---

#### Exemplo

- Foi criado um arquivo na pasta raíz com nome 'db.properties':

```
user=developer
password=1234567
dburl=jdbc:mysql://localhost:3306/coursejdbc
useSSL=false
```

- Utilizando a classe Properties para interagir com esse arquivo:

```java
package application;

import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;

public class Program {

	public static void main(String[] args){

		// Para carregar(load) o arquivo, o método 'load' da classe Properties espera um 'input.stream'
		// Por isso no exemplo utilizamos o FileInputStream que retorna os bytes de cada letra
		// o load converte todos esses bytes para um 'Map'
		try(FileInputStream fs = new FileInputStream("db.properties")){

			// Manipulando arquivos exemplos:
			Properties props = new Properties();
			props.load(fs);

			for(Object key: props.keySet())	{
				System.out.println("Output in forEach : " + key + props.get(key));
			}
			System.out.println();
			System.out.println("toString : " + props);

			String user = props.getProperty("user");
			String url = props.getProperty("dburl");
			System.out.println("User output: " + user);
			System.out.println("Url output: " + url);

		}catch(IOException e) {
			System.out.println(e.getMessage());
		}
	}
}
```

- OUTPUT:

```
Output in forEach : password1234567
Output in forEach : userdeveloper
Output in forEach : dburljdbc:mysql://localhost:3306/coursejdbc
Output in forEach : useSSLfalse

toString : {password=1234567, user=developer, dburl=jdbc:mysql://localhost:3306/coursejdbc, useSSL=false}
User output: developer
Url output: jdbc:mysql://localhost:3306/coursejdbc

```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
