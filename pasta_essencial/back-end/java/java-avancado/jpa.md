# :gem:JPA
---
O JPA trabalha por padrão criando uma tabela com mesmo nome da classe, com os mesmos nomes de atributos.

---

##### código exemplo:
* main:
```java
package aplicacao;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;

import dominio.Pessoa;

public class Programa {
	public static void main(String[] args) {

		Pessoa p1 = new Pessoa(null, "Carlos da Silva", "carlos@gmail.com");
		Pessoa p2 = new Pessoa(null, "Joaquim Torres", "joaquim@gmail.com");
		Pessoa p3 = new Pessoa(null, "Ana Maria", "ana@gmail.com");				 

		// Comando necessário para criar uma conexão com o banco de dados
		// Busca a informação na pasta/arquivo META-INF/persistence.xml
		// 	<persistence-unit name="exemplo-jpa"
		EntityManagerFactory emf = Persistence.createEntityManagerFactory("exemplo-jpa");
		EntityManager em = emf.createEntityManager();

		// O JPA precisa iniciar uma transação, caso comando não seja apenas
		// leitura com banco de dados
		
		// No exemplo abaixo estamos inserindo novas pessoas na tabela

		em.getTransaction().begin();
		em.persist(p1);
		em.persist(p2);
		em.persist(p3);						
		
		// commit para confirmar as alterações
	 	em.getTransaction().commit();  				
		
		System.out.println("Pronto");

		// Buscando um objeto no banco de dados pelo ID
		// sintaxe ( coluna / id )
		Pessoa p = em.find(Pessoa.class, 2);
		System.out.println(p);
		
		// Apagando um objeto no banco de dados
		em.getTransaction().begin();
		em.remove(p);
		em.getTransaction().commit();
		System.out.println("Apagou");
				
		em.close();
		emf.close();

	}
}

```

* persistence.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence
http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd"
	version="2.1">
	<persistence-unit name="exemplo-jpa"
		transaction-type="RESOURCE_LOCAL">
		<properties>
		<!-- Configuração da url de conexão com o banco de dados, no caso MySQL  -->
			<property name="javax.persistence.jdbc.url"
				value="jdbc:mysql://localhost/aulajpa?useSSL=false&amp;serverTimezone=UTC" />
			<property name="javax.persistence.jdbc.driver"
				value="com.mysql.jdbc.Driver" />
				<!-- Configurando usuário e senha para acesso ao MySQL  -->
			<property name="javax.persistence.jdbc.user" value="root" />
			<property name="javax.persistence.jdbc.password" value="1234567" />
			<property name="hibernate.hbm2ddl.auto" value="update" />
			<!-- https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/dialect/package-summary.html -->
			<property name="hibernate.dialect"
				value="org.hibernate.dialect.MySQL8Dialect" />
		</properties>
	</persistence-unit>
</persistence>
```
---
#### Anotações:
* @Entity
  * Indica que a classe é uma entidade de domínio que vai corresponder a uma tabela.
* @Id
  * Identificando que o atributo é a chave primária
  * `@GeneratedValue(strategy=GenerationType.IDENTITY)`
    * Geralmente o comando acima é utilzado para informar que o id vai ser implementado automaticamente pelo banco de dados
* @Column
  * Pode ser utilizado para alterar o nome de um atributo:
    * ``` @Column(name="nomeCompleto") ```

---
* No Spring Data:
  * Configura de forma automática o arquivo 'persistence.xml'
  * Instancia o EntityManagerFactory / EntityManager automaticamente
  * Gerencia as transações automaticamente
