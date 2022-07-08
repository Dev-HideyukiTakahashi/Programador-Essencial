# :gem: Lambda no Java

---

- Os lambdas obedecem o conceito do paradigma funcional, com eles podemos facilitar a legebilidade do nosso código, além disso com a nova API Funcional do Java podemos ter alta produtividade para lidar com objetos.

---

### :books:Interfaces Funcionais

Geralmente as interfaces funcionais possuem uma anotação em nível de classe (@FuncionalInterface), para forçar o compilador a apontar um erro se a interface não estiver de acordo com as regras de uma interface funcional, útil para um futuro programador que for utilizar a classe.

- Exemplo com interface Função:

```JAVA
/*Criando a propria functional interface
 * OBS: Implicitamente o Java reconhece que o método é abstrato,
 * poderia ter também um método DEFAULT, ou um método STATIC
 * mas nunca mais de 1 método abstrato,
 */

package application;

@FunctionalInterface
public interface Calculo {

	//Não podemos ter mais de 1 método na interface funcional
	Integer executar(int a,  int b);

	default String aceitoDefault() {
		return "É aceitável um método DEFAULT em uma @FunctionalInterface";
	}

	static String aceitoStatic() {
		return "É aceitável um método STATIC em uma @FunctionalInterface";
	}
}
```

- Agora que sabemos como se define uma interface funcional, podemos aprender como se define uma lambda.
- Estrutura da Lambda:
  - `InterfaceFuncional nomeVariavel = parametro -> logica`

```JAVA
/* @FunctionalInterface
 * Java Lambda - anotações e estudos
 */


package application;

public class App {
	public static void main(String[] args) {

		/* Criando uma função lambda a partir dos parâmetros
		* do método 'executar' da classe Calculo,
		* Entre parênteses são parâmetros e a arrow function "->", como eles  vão se comportar
		*/
		Calculo somar = (a, b) -> {
			return a + b;
		};

		/*
		 * Como o retorno era só 1 linha, podemos abstrair as chaves e a palavra return
		 */
		Calculo subtrair = (a, b) -> a - b;

		System.out.println(somar.executar(10, 5));
		System.out.println(subtrair.executar(8, 4));
	}
}

```

Output:

```
15
4
```

- Quando uma lambda possui apenas uma instrução no corpo de sua lógica não é necessário o uso de chaves.

- Se a função possui mais de uma instrução devemos utilizar chaves e além disso deve explicitar o retorno se o retorno for diferente de void.
  - As chaves utilizadas para definir o escopo da lambda precisa ser encerradas com ";".
  - Exemplo:
  ```JAVA
  Funcao colocarPrefixoSenhorNaString = valor -> {
      String valorComprefixo = "Sr. " + valor;
      String valorComprefixoEpontoFinal = valorComprefixo + ".";
      return valorComprefixoEpontoFinal;
  };
  ```

---

### :books:Função de alta ordem

- É uma função que retorna uma função ou que recebe uma função como parâmetro.

```Java
public class Principal {
    public static void main(String[] args) {
        Calculo soma = (a,b) -> a+b;
        System.out.println(executarOperacao(soma, 1,3));
        Calculo subtrai = (a,b) -> a-b;
        System.out.println("Subtrai: "+executarOperacao(subtrai,4,2));
    }
    //Função de alta ordem, utiliza outra função como parâmetro
    public static int executarOperacao(Calculo calculo, int a, int b){
        return calculo.calcular(a, b);
    }
}

interface Calculo{
    public int calcular(int a, int b );
}
```

---

## :books:`java.util.function`

---

:floppy_disk: `java.util.function.Consumer;`

- Sintaxe Consumer:

```Java
public interface Consumer<T> {
    void accept (T t);
}
```

- Problema exemplo
  - Fazer um programa que, a partir de uma lista de produtos, aumente o preço dos produtos em 10%.
  - Usando a mesma classe 'Product' em 'Predicate'.

```JAVA
public class PriceUpdate implements Consumer<Product> {

    @Override
    public void accept(Product p) {
        p.setPrice(p.getPrice() * 1.1);
    }
}

```

```Java
package ex223;

import ex222.application.Product;

import java.util.ArrayList;
import java.util.List;
import java.util.function.Consumer;

public class Program {
    public static void main(String[] args) {

        List<Product> list = new ArrayList<>();
        list.add(new Product("Tv", 900.00));
        list.add(new Product("Mouse", 50.00));
        list.add(new Product("Tablet", 350.50));
        list.add(new Product("HD Case", 80.90));
        //Implementação da interface
        list.forEach(new PriceUpdate());
        //Reference method com método estático
        list.forEach(Product::StaticProductConsumer);
        //Reference method com método não estático
        list.forEach(Product::nonStaticProductConsumer);
        //Expressão lambda declarada
        Consumer<Product> consumer = c -> c.setPrice(c.getPrice() * 1.1);
        list.forEach(consumer);
        //Expressão lambda inline
        list.forEach(c -> c.setPrice(c.getPrice() * 1.1));

        list.forEach(System.out::println);
    }
}

```

- Exemplo 2

```Java
import java.util.function.Consumer;

public class Principal {
    public static void main(String[] args) {
        //O próprio sistema entende que implicitamente existe um parâmetro "frase"
        //não sendo necessário explicitar no código
        Consumer<String> imprimirUmaFrase = System.out::println;
        Consumer<String> imprimirUmaFrase2 = frase -> System.out.println(frase);
        imprimirUmaFrase.accept("Hello World");

    }
}
```

---

:floppy_disk: `java.util.function.Function;`

- Sintaxe Function:

```Java
public interface Function<T, R> {
    R apply (T t);
}
```

- Problema exemplo:
  - Fazer um programa que, a partir de uma lista de produtos, gere uma nova lista contendo os nomes dos produtos em caixa alta.

```Java
public class Program {
    public static void main(String[] args) {

        List<Product> list = new ArrayList<>();
        list.add(new Product("Tv", 900.00));
        list.add(new Product("Mouse", 50.00));
        list.add(new Product("Tablet", 350.50));
        list.add(new Product("HD Case", 80.90));

        //Implementação da interface
        List <String> names = list.stream().map(new UpperCaseName()).collect(Collectors.toList());
        names.forEach(System.out::println);

        //Expressão lambda declarada
        Function<Product, String> func = p -> p.getName().toUpperCase();
        List <String> names2 = list.stream().map(func).collect(Collectors.toList());

        //Expressão lambda inline
        List <String> names3 = list.stream().map(p -> p.getName().toUpperCase()).collect(Collectors.toList());

    }
}

```

```Java
import java.util.function.Function;

public class UpperCaseName implements Function<Product, String> {

    @Override
    public String apply(Product p) {
        return p.getName().toUpperCase();
    }
}

```

- Exemplo 2:

```Java
import java.util.function.Function;

public class Principal {
    public static void main(String[] args) {

        Function<String, String> retornarNomeContrario = text -> new StringBuilder(text).reverse().toString();
        System.out.println(retornarNomeContrario.apply("Nome"));

        Function<String, Integer> converteString = string -> Integer.valueOf(string);
        System.out.println(converteString.apply("20"));

    }
}
```

---

:floppy_disk: `java.util.function.Predicate;`

- Sintaxe da interface Predicate:

```Java
public interface Predicate<T> {
    boolean test (T t);
}
```

- Problema exemplo
  - Fazer um programa que, a partir de uma lista de produtos, remova da lista somente aqueles cujo preço mínimo seja 100.

```Java
package ex222.application;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
import java.util.function.Predicate;

public class Program {
    public static void main(String[] args) {
        //Predicados
        Scanner input = new Scanner(System.in);

        List<Product> list = new ArrayList<>();
        list.add(new Product("Tv", 900.00));
        list.add(new Product("Mouse", 50.00));
        list.add(new Product("Tablet", 350.50));
        list.add(new Product("HD Case", 80.90));

        //Predicado lambda, removendo todos produtos com custo maior ou igual 100
        list.removeIf(p -> p.getPrice() >= 100);

        //Com mesmo resultado utilizando a interface
        //Instanciando a partir da interface ProductPredicate
        list.removeIf(new ProductPredicate());

        //Reference method com método estático
        list.removeIf(Product::StaticProductPredicate);

        //Reference method com método não estático
        list.removeIf(Product::nonStaticProductPredicate);

        //Expressão lambda declarada
        Predicate<Product> pred = p -> p.getPrice() >= 100;
        list.removeIf(pred);

        //Poderia ter recebido um valor que o usuário digitou;
        //Exemplo: Predicate<Product> pred = p -> p.getPrice() >= input.nextIDouble();

        //Expressão lambda inline
        //Como exemplo utilizando uma variável.
        double num = 100;
        list.removeIf(p -> p.getPrice() >= num);

        for (Product p : list) {
            System.out.println(p);
        }
    }
}

```

```JAVA
package ex222.application;

import java.util.function.Predicate;

public class ProductPredicate implements Predicate<Product> {

    @Override
    public boolean test(Product p) {
        return p.getPrice() >= 100;
    }
}
```

```JAVA
package ex222.application;

public class Product {

    private String name;
    private Double price;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Double getPrice() {
        return price;
    }

    public void setPrice(Double price) {
        this.price = price;
    }

    public Product(String name, Double price) {
        this.name = name;
        this.price = price;
    }

    public static boolean StaticProductPredicate(Product p) {
        return p.getPrice() >= 100;
    }

    public boolean nonStaticProductPredicate() {
        return price >= 100;
    }

    @Override
    public String toString() {
        return "Product{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }

}

```

- Outro exemplo

```Java
import java.util.function.Predicate;


public class Principal {
    public static void main(String[] args) {
        //Predicate retorna boolean
        Predicate<String> estaVazio = valor -> valor.isEmpty();
        //String vazia para teste
        System.out.println(estaVazio.test(""));
        //String populada, resulta false
        System.out.println(estaVazio.test("Nome"));
    }
}
```

---

:floppy_disk: `java.util.function.Supplier;`

```Java
import java.util.function.Supplier;

public class Principal {
    public static void main(String[] args) {
        //Não recebe parâmetro
        Supplier<Pessoa> suppliers = () -> new Pessoa();
        System.out.println(suppliers.get());
    }
}
class Pessoa{
    private String nome;
    private Integer idade;

    public Pessoa(){
        nome = "Nome";
        idade = 30;
    }
    @Override
    public String toString() {
        return String.format("Nome : "+nome+" Idade : "+ idade);
    }
}
```

---

:floppy_disk: `Iterações`

```Java
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class Principal {
    public static void main(String[] args) {
        String[] nomes = {"Joao", "Paulo", "Oliveira", "Santos", "Instrutor", "Java"};
        Integer[] numeros = {1, 2, 3, 4, 5};
        imprimirNomesFiltrados(nomes);
        imprimirTodosNomes(nomes);
        dobroDosNumeros(numeros);

    }

    //Método comum para filtrar 1 nome do vetor nomes
    public static void imprimirNomesFiltrados(String[] nomes) {
        String nomesParaImprimir = "";
        for (int i = 0; i < nomes.length; i++) {
            if (nomes[i].equals("Joao")) {
                nomesParaImprimir += " " + nomes[i];
            }
        }

        System.out.println("For: " + nomesParaImprimir);

        //Função stream para fazer o mesmo processo acima
        String nomesParaImprimirLambda = Stream.of(nomes)
                .filter(nome -> nome.equals("Joao"))
                .collect(Collectors.joining());

        System.out.println("Lambda: " + nomesParaImprimirLambda);

    }

    //Método para imprimir todos valores do array
    public static void imprimirTodosNomes(String[] nomes) {
        System.out.println();
        System.out.println("Impressão padrão");
        for (String i : nomes) {
            System.out.println(i);
        }
        System.out.println("-----------------");
        System.out.println("Impressão com lambda");
        //Função stream para fazer o mesmo processo de impressão
        Stream.of(nomes)
                .forEach(System.out::println);
    }

    public static void dobroDosNumeros(Integer[] numeros) {
        System.out.println();
        System.out.println("Imprimindo o dobro dos números com 'for' 1,2,3,4,5");
        for (Integer i : numeros) {
            System.out.println(i * 2);
        }
        //A mesma função de impressão em dobro com stream
        System.out.println("Usando o Stream ");
        Stream.of(numeros).map(numero -> numero * 2)
                .forEach(System.out::println);
    }

}
```

---

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
