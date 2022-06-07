# :gem:JPA

---

O JPA trabalha por padrão criando uma tabela com mesmo nome da classe, com os mesmos nomes de atributos.

---

##### código exemplo:

- main:

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

		// Buscando uma lista de usuarios:

		String jpql = "SELECT u FROM Usuario u"; // Nesse campo passamos o nome do Objeto JAVA
		TypedQuery<Usuario> query = em.createQuery(jpql, Usuario.class);
		query.setMaxResults(5); // limitando para 5 o resultado de usuarios

		List<Usuario> usuarios = query.getResultList();

		for(Usuario u : usuarios) {
			System.out.println(u.getId() + ": " + u.getNome());
		}

		// Atualizando os dados de um usuario

		em.getTransaction().begin();

		Usuario usuario = em.find(Usuario.class, 14L);
		usuario.setNome("Maria Joaquina");
		usuario.setEmail("mariajoaquina@gmail.com");
		em.merge(usuario); // Método para atualizar o usuário

		em.getTransaction().commit();

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

##### código exemplo de DAO:

- Com um DAO genérico podemos instanciar um DAO de qualquer tipo, facilitando reuso

```java
public class DAO<T> {

	private static EntityManagerFactory emf;
	private EntityManager em;
	private Class<T> classe;

	static {
		try {
			emf = Persistence.createEntityManagerFactory("estudo-jpa");
		} catch (Exception e) {

		}
	}

	public DAO(Class<T> classe) {
		this.classe = classe;
		em = emf.createEntityManager();
	}

	public DAO() {
		this(null);
	}

	public DAO<T> abrirT() {
		em.getTransaction().begin();
		return this;
	}

	public DAO<T> fecharT() {
		em.getTransaction().commit();
		return this;
	}

	public DAO<T> incluir(T entidade) {
		em.persist(entidade);
		return this;
	}

	public DAO<T> incluirAtomico(T entidade) {
		return this.abrirT().incluir(entidade).fecharT();
	}

	public List<T> obterTodos(int qtde, int deslocamento){
		if(classe == null) {
			throw new UnsupportedOperationException("Classe nula.");
		}

		String jpql = "SELECT t FROM " + classe.getName() + " t";
		TypedQuery<T> query = em.createQuery(jpql, classe);
		query.setMaxResults(qtde);
		query.setFirstResult(deslocamento);
		return query.getResultList();
	}
}
```

- Herdando DAO

```java
public class ProdutoDAO extends DAO<Produto>{

	public ProdutoDAO() {
		super(Produto.class);
	}
}
```

##### código exemplo de Herança:

- @Inheritance

  - Por padrão a 'strategy' é SINGLE_TABLE
  - No padrão, poderia colocar discriminar os campos da seguinte forma
  - `@DiscriminatorColumn(name="tipo", length=2, discriminatorType=DiscriminatorType.STRING)`
    - É criada uma coluna com nome 'tipo' de tamanho 2, com um valor String
  - Com a notação `@DiscriminatorColumn` em cada coluna eu posso descrever o nome do campo, caso o objeto pertencer aquela classe.
    - `@DiscriminatorValue("AL")` // class Aluno
    - `@DiscriminatorValue("AB")` // class AlunoBolsista
  - Dessa maneira na saída no banco de dados seria uma coluna 'tipo' com valores 'AL' ou 'AB', para diferenciar as classes.

```java

// Classe Aluno
@Entity
@Inheritance(strategy=InheritanceType.TABLE_PER_CLASS) // Essa marcação gera 2 tabelas separadas //
public class Aluno {

	@Id
	private Long matricula;

	private String nome;

	public Aluno() {
	}

// Classe AlunoBolsista
@Entity
public class AlunoBolsista extends Aluno {

	private Double valorBolsa;

	public AlunoBolsista() {
	}
```

##### código exemplo de NamedQuery:

```java
	public List<T> consultar(String nomeConsulta, Object ...params ){
		TypedQuery<T> query = em.createNamedQuery(nomeConsulta, classe);
		// O primeiro argumento é o nome da consulta e o segundo o parametro de comparação
		for (int i = 0; i < params.length; i += 2) {
			query.setParameter(params[i].toString(), params[i+1]);
		}
		return query.getResultList();
	}


	//////////////////////////
	// CLASSE MAIN
		DAO<Filme> dao = new DAO<>(Filme.class);
		List<Filme> filmes = dao.consultar("filmesNotaMaiorQue", "nota", 8.5);

		for(Filme f:  filmes) {
			System.out.println(f.getNome());
		}
```

- Arquivo XML

```xml
	<named-query name="filmesNotaMaiorQue">
	<!--A query é baseada no objeto JAVA e não na tabela SQL, f é o alias  -->
		<query>
			SELECT distinct f from Filme f
			JOIN FETCH f.atores
			WHERE f.nota >= :nota
		</query>
	</named-query>
```

- persistence.xml

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

- @Entity
  - Indica que a classe é uma entidade de domínio que vai corresponder a uma tabela.
- @Id
  - Identificando que o atributo é a chave primária
  - `@GeneratedValue(strategy=GenerationType.IDENTITY)`
    - Geralmente o comando acima é utilzado para informar que o id vai ser implementado automaticamente pelo banco de dados
- @Column
  - Pode ser utilizado para alterar o nome de um atributo:
    - `@Column(name="nomeCompleto")`

---

- No Spring Data:
  - Configura de forma automática o arquivo 'persistence.xml'
  - Instancia o EntityManagerFactory / EntityManager automaticamente
  - Gerencia as transações automaticamente
