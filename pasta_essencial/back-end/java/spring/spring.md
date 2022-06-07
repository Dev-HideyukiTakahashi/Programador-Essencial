# :leaves: Spring

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
