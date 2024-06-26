# :leaves: Spring Data

---

### :seedling: Entidades (anotações JPA)

---

**@Transient** - O JPA ignora o atributo/método em questão

**@OneToOne**

```Java



public class Order{
	@OneToOne
	@JoinColumn(name="client_id")  // Escolhemos colocar a coluna em apenas 1 entidade
	private User client;
}

public class Client{
	// poderia ter  depois de "client" cascade=CascadeType.ALL para compartilhar o mesmo ID entre as classes
	@OneToOne(mappedBy = "client") // relacionando a chave estrangeira
	private Order order;
}

```

**@ManyToOne**

```java
	@ManyToOne // muitos para um
	@JoinColumn(name="client_id") // criamos uma nova coluna no banco de dados para identificar a chave estrangeira
	private User client;
```

-Exemplo de método para garantir a relação bidirecional e evitar dados duplicados

- Classe Filme

```java
	public void addAtor(Ator ator) {
		if(ator != null && !getAtores().contains(ator)) {
			getAtores().add(ator);

			if(!ator.getFilmes().contains(this))
			ator.getFilmes().add(this);
		}
```

**@OneToMany**

```java
	@JsonIgnore // Adicionamos essa anotação para não entrar em loop infinito, geralmente na entidade mais fraca
	@OneToMany(mappedBy = "client") // Mapeando a chave estangeira para conversar com a outra entidade
	private List<Order> orders = new ArrayList<>();
```

**@ManyToMany** - JoinTable

```java
public class Order{
	@ManyToMany
	//É necessário uma tabela intermediária de associação em uma relação muitos para muitos, pode ser criada uma nova, ou utilizar uma já existente
	@JoinTable(name = "client_order", // esse campo poderia ser uma tabela de associação já existente, com dados adicionais por exemplo
		joinColumns   = @JoinColumn(name="order_id"),
		inverseJoinColumns = @JoinColumn (name = "client_id"))
	private List<Client> clients = new ArrayList<>();
}

public class Client{
	@ManyToMany(mappedBy = "clients")
	private List<Order> orders = new ArrayList<>();
}
```

**@ManyToMany** - Com dados extras

Classe OrderItemPK

```java
//Criando uma classe adicional que tem as referências das classes associadas

@Embeddable // declarando que uma classe será incorporada por outras entidades
public class OrderItemPK implements Serializable {

	private static final long serialVersionUID = 1L;

	@ManyToOne
	@JoinColumn(name="order_id")
	private Order order;

	@ManyToOne
	@JoinColumn(name="product_id")
	private Product product;

	... get/sets..

}

```

Classe OrderItem

```java
@Entity
@Table(name="tb_order_item")
public class OrderItem implements Serializable {

	private static final long serialVersionUID = 1L;

	@EmbeddedId
	private OrderItemPK id = new OrderItemPK();// Sempre que criar uma classe auxiliar com id composto é necessário instanciar

	private Integer quantity;
	private Double price;

	public OrderItem() {
	}

	public OrderItem(Order Order, Product product,Integer quantity, Double price) {
		id.setOrder(Order);
		id.setProduct(product);
		this.quantity = quantity;
		this.price = price;
	}

	@JsonIgnore  // O java leva em consideração o "get" caso não tenha uma instância direta da associação
	public Order getOrder() {
		return id.getOrder();
	}

	public void setOrder(Order order) {
		id.setOrder(order);
	}
	@JsonIgnore
	public Product getProduct() {
		return id.getProduct();
	}

	public void setProduct(Product product) {
		id.setProduct(product);
	}

	public Integer getQuantity() {
		return quantity;
	}

	public void setQuantity(Integer quantity) {
		this.quantity = quantity;
	}

	public Double getPrice() {
		return price;
	}

	public void setPrice(Double price) {
		this.price = price;
	}
```

Classe Order

```java
@Entity
@Table(name = "tb_order")
public class Order implements Serializable {

	private static final long serialVersionUID = 1L;
 	// pegando a referência de id da classe OrderItem e order da classe OrderItemPK
	@OneToMany(mappedBy="id.order")
	private Set<OrderItem> items = new HashSet<>();

		... codes
```

Classe Product

```java
@Entity
@Table(name = "tb_product")
public class Product implements Serializable {

	private static final long serialVersionUID = 1L;
 	// pegando a referência de id da classe OrderItem e product da classe OrderItemPK
	@OneToMany(mappedBy = "id.product")
	private Set<OrderItem> items = new HashSet<>();

		... codes
```

**@JsonFormat**

```java
/* Algumas formatações com json */

//ISO 8601(Padrão de data/hora mundial)
@JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "yyyy-MM-dd'T'HH:mm:ss'Z'", timezone = "GMT")

//Padrão data/Horas Brasil
@JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "dd-MM-yyyy HH:mm:ss", timezone="GMT-3")
private Date date;


```

---

### :seedling: Configuração para H2-Database (comum em testes)

- Arquivo: **application-test.properties**
  Configurações para utilizar o H2 como banco de dados para testes.

```
#criando um banco de dados em memória(mem) com nome de testdb
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

spring.h2.console.enabled=true
#caminho no navegador para acesso
spring.h2.console.path=/h2-console

#comando para exibição do código sql no console
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

- Spring 3.0
```
# DATASOURCE
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=
# H2 CLIENT
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
# JPA, SQL
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.defer-datasource-initialization=true
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

```

---

### :seedling: PostgreSQL Database

```
spring.datasource.url=jdbc:postgresql://localhost:5432/database
spring.datasource.username=postgres
spring.datasource.password=1234567

spring.datasource.driver-class-name=org.postgresql.Driver

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.hibernate.ddl-auto=update
```

---
