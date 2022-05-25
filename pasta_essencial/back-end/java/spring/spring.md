#:leaves: Spring

---

### :seedling: Entidades (anotações JPA)

---

**@Transient** - O JPA ignora o atributo em questão

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

### :seedling: Spring (anotações mais utilizadas)

---

- **@Bean**

```Java
@Configuration // Anotação de configuração
public class BeanConfig {
	/*
	 * Criando a própria bean...
	 * Nesse caso, na chamada do @Autowired em outra classe, o Spring localiza
	 * essa bean para instanciar um UserRepository.
	 * Pode ser útil dependendo da regra de negócio, pode ser um cálculo,
	 * emissão de nota ou alguma regra adicional necessária no momento de instanciar o objeto.
	 */

	@Bean
	public UserRepository userRepository() {
		return new UserRepository();
	}
}
```

- **@Repository**

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {

	/*
	 * @Repository traz todo essencial do CRUD pronto.
	 * Sintaxe (Nome da classe entidade/Tipo de ID)
	 */
}
```

- **@Service**

```java
/*
 * A classe de serviço faz o meio campo entre o repositório e o controller.
 * Assim o repository conversa com o banco da dados,
 * O serviçe aplica as regras de negócio,
 * O controller efetivamente conversa com a aplicação.
 */
@Service
public class UserService {

	@Autowired  // O Spring instancia o objeto automaticamente quando encontra a classe @Repository
	private UserRepository repository;


	/*
	 * Aplicando uma regra de negócio no serviço antes de enviar a camada controller
	 */
	public List<User> buscaDados(){
		List<User> nomes = repository.findAll();
		for(User devedor : nomes) {
			if(devedor.getName().equals("Devendo no serasa")) {
				return null;
			}
		}
		return nomes;
	}

	public User buscaId(Long id) {
		Optional<User> user = repository.findById(id);
		return user.get();
	}


}
```

**@Controller**

```java
@RestController   // Rest traduz todos os dados para Json
public class UserController {

	/*
	 * Reponsável pela chamada de tela.
	 */

	@Autowired
	private UserService service;

	//Exemplos de request
	@RequestMapping("/rest")
	public List<User> testeRest() {
		return service.buscaDados();
	}

	@RequestMapping(value="/{id}")
	public User buscaId(Long id) {
		return service.buscaId(id);
	}
}

```

---

### :seedling: Configuração para H2-Database (comum em testes)

- Arquivo: **application-test.properties**
  Configurações para utilizar o H2 como banco de dados para testes.

```
spring.datasource.url=jdbc:h2:mem:testdb // criando um banco de dados em memória(mem) com nome de testdb
spring.datasource.username=sa
spring.datasource.password=

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console // caminho no navegador para acesso

spring.jpa.show-sql=true //comando para exibição de comandos sql no console
spring.jpa.properties.hibernate.format_sql=true //
```

---

### :seedling: Configuração de uma classe para testes.

```java
package com.estudo.aula.config;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Profile;

import com.estudo.aula.repositories.UserRepository;

@Configuration
@Profile("test")
public class TestConfig implements CommandLineRunner {

	@Autowired
	private UserRepository userRepository;

	@Override
	public void run(String... args) throws Exception {
		// tudo implementado nesse método será executado quando a aplicação for iniciada

	}

}
```

---
