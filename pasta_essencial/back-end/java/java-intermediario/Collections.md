# :gem: Collections em Java

---
1. :open_book:`java.util.List`
2. :open_book:`java.util.Queue`
3. :open_book:`java.util.Set`
4. :open_book:`java.util.Map`
5. :open_book:`Comparators e Comparables`
6. :open_book:`Optionals`
---

Sugestões para utilizar collections
* Se for necessário manter elementos duplicados, usar Lista! Contudo, se for necessário fazer muita pesquisa, evite o uso de Lista!
* Se não for necessário manter elementos duplicados e nem usar chaves, usar Conjunto! Contudo, se for necessário o uso de chaves, usar Mapa!
* Qual a implementação de Lista que deverá ser escolhida?
	* Usar ArrayList sefor necessário acessar os elementos por índice(ex. pesquisa binária);
	* Usar LinkedList sefor necessário inserir ou removerelementos do meio da Lista com frequência.
* Qual a implementação de Conjunto que deverá ser escolhida?
	* Usar HashSet senãofor necessário obter um conjuntoordenado;
	* Usar TreeSet se for necessário obter um conjuntoordenado.
* Qual a implementação de Mapa que deverá ser escolhida?
	* Usar HashMap senãofor necessário obter um mapaordenado;
	* Usar TreeMap se for necessário obter um mapaordenado.

---

## 1. :floppy_disk: `java.util.List`

* Implementações mais comuns:
    * `java.util.ArrayList`
    * `java.util.Vector`
* Garante ordem de inserção.
* Permite adição, atualização, leitura e remoção sem regras adicionais.
* Permite ordenação através de comparators. 

---

### :books:`java.util.ArrayList`


* Sintaxe:
`List<tipoDado><obj> = new ArrayList<>()`
   * Exemplo:
   `List<Integer> lista = new ArrayList<>()`

* Comandos para utilizar com ArrayList:
   * Tamanho da lista: `size()`
   * Inserir elemento na lista: `add(obj)`, `add(int, obj)`
   * Remover elementos da lista: `remove(obj)`, `remove(int)`, `removeIf(predicado)`
   * Encontrar posição de elemento: `indexOf(obj)`, `lastIndexOf(obj)`

Exemplo de utilização lista:
```java
package curso_java;

import java.util.ArrayList;
import java.util.List;

public class Principal {

	public static void main(String[] args) {
		
		List<String> list = new ArrayList<>();
		
		//Adicionando na lista "list.add(args)"
		list.add("Maria");
		list.add("Alex");
		list.add("Ana");
		list.add("Bob");
		//Adicionando em determinada posição na lista "list.add(pos, args)"
		list.add(2, "Marco");		
                //Atualizando um valor da lista
                list.set(2, "Joana");

                //Buscando um valor na lista
                //Retorna o valor "Ana"
                System.out.println(list.get(2))

                //Comando Contains:
                boolean contemMaria = list.contains("Maria");
                System.out.println(contemMaria);
                //OUTPUT : True


                //Comando para verificar uma condição de lista vazia
                list.isEmpty();

                //Método para limpar a lista ou remover toda a lista
                list.clear();




		//Comando para ver o tamanho da lista "list.size()"

		System.out.println("Tamanho lista: "+list.size());
		
                //Comando para ordernar em ordem alfabética
                Collections.sort(list);


		
		//Comando "for each".
		for(String i: list) {
			System.out.println(i);
		}
		System.out.println("---------------------------------------");
		
		//Removendo na lista "list.remove(args)
		list.remove("Ana");
		
		//Removendo a posição da lista "list.remove(pos)"
		list.remove(1);
		
		
		//Estrutura comum para percorrer uma lista
		for(String i: list) {
			System.out.println(i);
		}
		System.out.println("---------------------------------------");
		
		//Removendo com uma condição "list.removeIf(args)"
		list.removeIf(i -> i.charAt(0) == 'M');
		
		for(String i: list) {
			System.out.println(i);
		}
		
		System.out.println("---------------------------------------");
		
		list.add("Maria");
		list.add("Alex");
		list.add("Ana");
		
		for(String i: list) {
			System.out.println(i);
		}
		
		//Comando para ver a posição na lista "list.indexOf(args)"
		System.out.println("Posição de Alex: " + list.indexOf("Alex"));
		//Quando não há elementos na posição retorna como -1
		System.out.println("Posição vazia: " + list.indexOf("Marco"));
		
		System.out.println("---------------------------------------");
```
---

### :books:`java.util.Vector`

```Java
import java.util.List;
import java.util.Vector;

public class Principal {
    public static void main(String[] args){
        List<String> esportes = new Vector<>();



        //Adicionando 4 esportes no vetor:
        esportes.add("Futebol");
        esportes.add("Basquete");
        esportes.add("Tenis de mesa");
        esportes.add("Handebol");

        //Imprimindo todo vetor
        System.out.println(esportes);

        //Altera o valor da posição 2
        esportes.set(2, "Ping pong");

        //Remove o esporte da posição 2
        esportes.remove(2);

        //Remove o esporte Handebol
        esportes.remove("Handebol");

        //Retona um valor com o get
        System.out.println("Primeiro esporte: "+esportes.get(0));

        //Navegando pelo vetor
        for(String e: esportes){
            System.out.println(e);
        }
    }
}
```

---
## 2. :floppy_disk:`java.util.Queue`
* Implementação mais comum:
    * `java.util.LinkedList`
* Muito utilizada em filas.
* Garante ordem de inserção.
* Permite adição, leitura e remoção considerando a regra básica de uma fila: primeiro entra, primeiro sai(First in, first out).    
* Não permite mudança de ordenação.
* Não permite alteração do elemento. Precisa remover, alterar e implantar novamente, ocupando uma nova posição na fila.

---

### :books:`java.util.LinkedList`

```Java
import java.util.LinkedList;
import java.util.NoSuchElementException;
import java.util.Queue;

public class Principal {
    public static void main(String[] args){
        Queue<String> filaBanco = new LinkedList<>();

        //Adicionando elementos na fila do banco
        filaBanco.add("Pamela");
        filaBanco.add("Patricia");
        filaBanco.add("Roberto");
        filaBanco.add("Flávio");
        filaBanco.add("Anderson");

        //Imprimindo todos elementos da fila
        System.out.println("Clientes na fila: "+ filaBanco);

        //poll() retorna e remove o primeiro elemento da fila,
        // retorna null se a fila estiver vazia
        System.out.println();
        String proximoCliente = filaBanco.poll();
        System.out.println("Próximo cliente: "+proximoCliente);
        System.out.println("Clientes na fila: "+ filaBanco);

        //peek() retorna mas não remove o primeiro elemento da fila,
        // retorna null se a fila estiver vazia
        System.out.println();
        String primeiroCliente = filaBanco.peek();
        System.out.println("Primeiro cliente na fila: "+primeiroCliente);
        System.out.println("Clientes na fila: "+ filaBanco);


        //element() retorna o primeiro elemento da fila,
        //retorna uma exceção se a fila estiver vazia
        //NoSuchElementException
        System.out.println();
        filaBanco.clear();
        try{
            String primeiroClienteOuErro = filaBanco.element();
            System.out.println(primeiroClienteOuErro);
        }catch(NoSuchElementException e){
            System.out.println("Erro fila vazia! " + e.getMessage());
        }finally{
            System.out.println("Clientes na fila: "+ filaBanco);
        }
    }
}
```

---
## 3. :floppy_disk:`java.util.Set`
* Implementações mais comuns:
        * `java.util.HashSet`
        * `java.util.LinkedHashSet`
        * `java.util.TreeSet`
        
* Por padrão, não garante ordem.
* Não permite itens repetidos
* Permite adição e remoção normalmente.
* Não possui busca por índice e atualização para leitura, apenas navegação.
* Não permite mudança de ordenação.

   |      | Quando Utilizar  |  Ordenação |  Performance |
   | --- | --- | --- | ---
   | HashSet | Quando não é necessário manter uma ordenação | Não é ordenado, e não permite valores repetidos | Por não ter repetição de valores e não ser ordenado, é a implementação mais performática |
   |LinkedHashSet| Quando é necessário manter a ordem de inserção dos elementos| Mantém a ordem de inserção dos elementos|É a implementação mais lenta por ser necessária manter a ordem|
   |TreeSet|Quando é necessário alterar a ordem através do uso de comparators|Mantém a ordem e pode ser reordenado|É performático para leitura. Para modificação tem a necessidade de reordenar, sendo mais lento que o LinkedHashSet

---

### :books:`java.util.HashSet`

```Java
import java.util.HashSet;
import java.util.Set;

public class Principal {
    public static void main(String[] args) {

        Set<Double> notasAlunos = new HashSet<>();

        notasAlunos.add(5.8);
        notasAlunos.add(9.3);
        notasAlunos.add(6.5);
        notasAlunos.add(10.0);
        notasAlunos.add(5.4);
        notasAlunos.add(7.3);
        notasAlunos.add(3.8);
        notasAlunos.add(4.0);

        System.out.println(notasAlunos);

        //Remove a nota do set
        notasAlunos.remove(3.8);
        System.out.println(notasAlunos);

        //Retorna a quantidade de itens do set
        System.out.println("Tamanho do set: "+notasAlunos.size());

        //Navega em todos itens do set
        for(Double i: notasAlunos){
            System.out.println(i);
        }

        //Remove todos elementos em que x é menor ou igual a 5
        notasAlunos.removeIf(x -> x <= 5);

        //Limpando a lista
        notasAlunos.clear();

        //Verificando se está vazio
        System.out.println("Está vazio?: "+notasAlunos.isEmpty());

    }
}
```
---
### :books:`java.util.LinkedHashSet`

```Java
import java.util.LinkedHashSet;

public class Principal {
    public static void main(String[] args) {

        LinkedHashSet<Integer> sequenciaNumerica = new LinkedHashSet<>();

        //Adiciona os números no set
        sequenciaNumerica.add(1);
        sequenciaNumerica.add(2);
        sequenciaNumerica.add(4);
        sequenciaNumerica.add(8);
        sequenciaNumerica.add(16);

        System.out.println(sequenciaNumerica);

        //Remove o número do set
        sequenciaNumerica.remove(4);
        System.out.println(sequenciaNumerica);

        //Retorna a quantidade de itens:
        System.out.println("Tamanho do set: "+sequenciaNumerica.size());

        //Navegando no set
        for(Integer i: sequenciaNumerica){
            System.out.println(i);
        }

    }
}
```

---

### :books:`java.util.TreeSet`

```JAVA
import java.util.TreeSet;

public class Principal {
    public static void main(String[] args) {
        TreeSet<String> capitais = new TreeSet<>();

        //Monta a árvore com as cidades capitais
        capitais.add("Porto Alegre");
        capitais.add("Florianópolis");
        capitais.add("Curitiba");
        capitais.add("São Paulo");
        capitais.add("Rio de Janeiro");
        capitais.add("Belo horizonte");

        System.out.println(capitais);

        //Retorna a primeira capital no topo da árvore
        System.out.println("Primeira capital: "+capitais.first());

        //Retorna a última capital na árvore
        System.out.println("Última capital: "+capitais.last());

        //Retorna a primeira capital do topo, removendo o set
        System.out.println("Exibe e remove: "+capitais.pollFirst());

        //Retorna a última capital no final, removendo o set
        System.out.println("Exibe e remove: "+capitais.pollLast());

        System.out.println(capitais);

        //Percorrendo as capitais
        for(String i: capitais){
            System.out.println(i);
        }
    }
}
```
* Exemplo com união, interseção e diferença:
```Java
Set<Integer> a = new TreeSet<>(Arrays.asList(0,2,4,5,6,8,10));
Set<Integer> b = new TreeSet<>(Arrays.asList(5,6,7,8,9,10));
//union
Set<Integer> c = new TreeSet<>(a);
c.addAll(b);
System.out.println(c);
//intersection
Set<Integer> d = new TreeSet<>(a);
d.retainAll(b);
System.out.println(d);
//difference
Set<Integer> e = new TreeSet<>(a);
e.removeAll(b);
System.out.println(e);
```

---
## 4. :floppy_disk:`java.util.Map`

* Implementações comuns:
    * `java.util.HashMap`
    * `java.util.TreeMap`
* Entrada de chave e valor
* Permite valores repetidos, mas não permite repetição de chave
* Permite adição, busca por chave ou valor, atualização, remoção e navegação
* Pode ser ordenado
* Não implementa a classe Collections

* Alguns métodos importantes
    * put(key, value), remove(key), containsKey(key), get(key)
        * Baseado em equals e hashCode
        * Se equals e hashCode não existir, é usada comparação de ponteiros
    * clear() - limpa a lista
    * size() - tamanho da lista
    * keySet() - retorna um Set<K> (retorna as chaves)
    * values() - retorna um Collection<V> (retorna os valores)
    * entrySet() - retorna a associação<K, V>

---

### :books:`java.util.HashMap`

```JAVA
import java.util.HashMap;
import java.util.Map;

public class Principal {
    public static void main(String[] args) {

        //O primeiro tipo é a chave
        //O segundo tipo é o valor
        Map<String, Integer> campeoesFifa = new HashMap<>();

        //Adicionando os times no mapa e seus títulos
        campeoesFifa.put("Brasil", 5);
        campeoesFifa.put("Alemana", 4);
        campeoesFifa.put("Itália", 4);
        campeoesFifa.put("Uruguai", 2);
        campeoesFifa.put("Argentina", 2);
        campeoesFifa.put("França", 2);
        campeoesFifa.put("Inglaterra", 1);
        campeoesFifa.put("Espanha", 1);

        System.out.println(campeoesFifa);

        //Atualiza o valor da chave Brasil
        campeoesFifa.put("Brasil", 6);
        System.out.println(campeoesFifa);

        //Retorna Argentina
        System.out.println("Títulos de Argetina: "+campeoesFifa.get("Argentina"));

        //Retorna se existe ou não o time França
        System.out.println("Contém França?: "+campeoesFifa.containsKey("França"));

        //Remove o time França
        campeoesFifa.remove("França");
        System.out.println(campeoesFifa);

        System.out.println("Contém França após remover?: "+campeoesFifa.containsKey("França"));

        //Retorna se existe ou não alguma seleção hexa
        System.out.println("Alguem é hexa(6)? :"+campeoesFifa.containsValue(6));

        //Retorna o tamanho do mapa
        System.out.println("Tamanho do mapa: "+campeoesFifa.size());

        //Navega nos registros do mapa através da chave
        for(String key: campeoesFifa.keySet()){
            //key = retorna o nome do time **** get(key) = retorna os títulos
            System.out.println(key + "---" + campeoesFifa.get(key));
        }

        System.out.println(campeoesFifa);

    }
}
```
### :books:`java.util.TreeMap`
```Java
import java.util.Map;
import java.util.TreeMap;

public class Program {

    public static void main(String[] args) {
        //Passando os tipos, primeiro a chave e depois o valor.
        Map<String, String> cookies = new TreeMap<>();

        //Adicionando elementos, primeiro a chave e depois o valor.
        cookies.put("username", "Maria");
        cookies.put("email", "maria@gmail.com");
        cookies.put("fone", "99584574");
        //removendo um elemento através da chave
        cookies.remove("email");
        //Quando passamos um valor em uma chave que já existe, o valor é sobrescrito
        cookies.put("fone", "97548475");

        //Verificando se o campo fone existe
        System.out.println("Contains 'fone' : " + cookies.containsKey("fone"));
        //Acessando um valor da chave fone
        System.out.println("Fone number : " + cookies.get("fone"));
        //Quando elemento não existe retorna null
        System.out.println("Email: " + cookies.get("email"));

        //Acessando todos elementos do map
        System.out.println("ALL COKIES");
        //Acessando a chave do mapa, keySet() - retorna um Set<K>
        for (String key : cookies.keySet()) {
            //Imprime a chave, acessa a chave para pegar o valor
            System.out.println(key + ": " + cookies.get(key));
        }

    }
}

```
### :books:`java.util.HashMap`
* Exemplo 2:
```JAva

import java.util.HashMap;
import java.util.Map;

public class Program {
    public static void main(String[] args) {

        //Inserindo a chave e depois o valor.
        Map<Product, Double> stock = new HashMap<>();

        //Instanciando os objetos da classe product
        Product p1 = new Product("Tv", 900.0);
        Product p2 = new Product("Notebook", 1200.0);
        Product p3 = new Product("Tablet", 400.0);

        //Instanciando o mapa stock com o obj da classe produto e a quantidade
        stock.put(p1, 10000.0);
        stock.put(p2, 20000.0);
        stock.put(p3, 15000.0);

        //Imprimindo um Set<K> (toString)
        System.out.println("Stock toString() : " + stock.keySet());

        //Imprimindo o stock (key (Product.name, Product.Price), value)
        System.out.println("Stock data: " + stock);



        //Instanciando outro obj Product para verificar se existe
        Product ps = new Product("Tv", 900.0);
        //Verificando se o obs 'ps' está contido no mapa 'stock'
        //OBS: ESSE VALOR RETORNA TRUE SOMENTE SE FOR IMPLANTADO O ...
        //EQUALS e HASHCODE NA CLASSE PRODUCT
        System.out.println("Contains 'ps' key: " + stock.containsKey(ps));

        //Apesar do obj 'ps' não estar na lista, o map compara com a classe Product
        // e retorna o valor no mapa (no caso quantidade ness exemplo)
        System.out.println("Obj 'ps' get(): " + stock.get(ps));

        //Comparando 'ps' com algum elemento do mapa.
        for(Product p: stock.keySet()){
            if(p.equals(ps)){
                System.out.println("Equals 'ps' :  " + p.equals(ps));
                System.out.println(p);
            }
        }


    }
}

public class Product{

    private String name;
    private Double price;

    public Product(String name, Double price) {
        this.name = name;
        this.price = price;
    }

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

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Product product = (Product) o;
        return Objects.equals(name, product.name) && Objects.equals(price, product.price);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, price);
    }

    public String toString() {
        return name + " - " + price;
    }
}


```
---

## 5. :floppy_disk: Comparators e Comparables

* Interfaces comuns:
    * `java.util.Comparator` - Interface para definir classe com regra de ordenação
    * `java.util.Comparable` - Interface para definir regra de ordenação em uma classe de domínio
* Algoritmos de ordenação
* Utilizado primariamente em `java.util.List`
* Permite a ordenação de objetos complexos (criados pelo usuário)

---


### :books:`java.util.Comparable`
```Java
public class Estudante implements Comparable<Estudante> {

    private final String nome;
    private final int idade;

    public Estudante(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    public String getNome() {
        return nome;
    }

    public int getIdade() {
        return idade;
    }

    @Override
    public String toString() {
        return nome +" - "+ idade;
    }

    //Ordenando as idades de forma ascendente, comparando
    //a idade atual com a idade passada por argumento
    @Override
    public int compareTo(Estudante o) {
        return this.getIdade() - o.getIdade();
    }

}
```
### :books:`java.util.Comparator`
```JAVA
import java.util.Comparator;

public class EstudanteComparators implements Comparator<Estudante> {

    //Ordenando de forma ascendente com Comparator
    //Utilizando a classe Estudante criada com Comparable anteriormente
    @Override
    public int compare(Estudante o1, Estudante o2) {
        return o1.getIdade() - o2.getIdade();
    }
}
```
#### :books:Exemplo na classe main:
```JAVA
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Principal {
    public static void main(String[] args) {
        List<Estudante> estudantes = new ArrayList<>();

        estudantes.add(new Estudante("Pedro", 19));
        estudantes.add(new Estudante("Carlos", 23));
        estudantes.add(new Estudante("Mariana", 21));
        estudantes.add(new Estudante("João", 18));
        estudantes.add(new Estudante("Thiago", 20));
        estudantes.add(new Estudante("George", 22));
        estudantes.add(new Estudante("Larissa", 21));

        //Imprimindo a lista desordenada
        System.out.println("---Ordem de inserção---");
        System.out.println(estudantes);

        System.out.println();

        //Organizando a lista pela idade
        estudantes.sort((first, second) -> (first.getIdade() - second.getIdade()));

        System.out.println("---Ordem natural dos números(idade)---");
        System.out.println(estudantes);
        System.out.println();

        //Organizando a lista de forma decrescente pela idade
        System.out.println("---Ordem decrescente dos números(idade)---");
        estudantes.sort((first, second) -> second.getIdade() - first.getIdade());
        System.out.println(estudantes);
        System.out.println();

        //Ordenando com comparator
        estudantes.sort(Comparator.comparingInt(Estudante::getIdade));
        System.out.println("--Ordem natural dos números por idade com comparator--");
        System.out.println(estudantes);
        System.out.println();

        //Ordenando de forma reversa
        estudantes.sort(Comparator.comparingInt(Estudante::getIdade).reversed());
        System.out.println("--Ordem reversa dos números por idade com comparator--");
        System.out.println(estudantes);
        System.out.println();

        //Ordendando com Collection
        //OBS: O obj instanciado lista, obrigatóriamente precisa ter o tipo
        //de uma classe que implementa de Comparable
        //Nesse caso o tipo do obj é do tipo "Estudante", que implements Comparable
        Collections.sort(estudantes);
        System.out.println("--Ordem natural dos números por idade com Collection--");
        System.out.println(estudantes);

    }
}

```

---
## 6. :floppy_disk: Optionals

* Tratamento para valores que podem ser nulos
* Possui 2 estados
    * Presente
    * Vazio
* Permite que você execute operações em valores que podem ser nulos sem preocupação com NullPointerException

---
```JAVA
import java.util.Optional;

public class Principal {
    public static void main(String[] args) {

        Optional<String> optionalString = Optional.of("Valor presente");

        System.out.println("Valor opcional que está presente");
        optionalString.ifPresentOrElse(System.out::println, () -> System.out.println("Não está presente"));


        Optional<String> optionalNull = Optional.ofNullable(null);

        System.out.println("Valor opcional que não está presente");
        optionalNull.ifPresentOrElse(System.out::println, () -> System.out.println("null = não está presente"));


        Optional<String> optionalEmpty = Optional.empty();

        System.out.println("Valor opcional que não está presente");
        optionalEmpty.ifPresentOrElse(System.out::println, () -> System.out.println("Empty = não está presente"));


       // Optional<String> optionalNullErro = Optional.of(null);

       // System.out.println("Valor opcional que lança um erro NullPointerException");

        optionalString = Optional.of("Valor opcional");
        System.out.println(optionalString.isEmpty());
        System.out.println(optionalString.isPresent());

        optionalString.ifPresent(System.out::println);

        optionalString.ifPresentOrElse(System.out::println,() -> System.out.println("Valor não está presente"));

        if(optionalString.isPresent()){
            String valor = optionalString.get();

            System.out.println(valor);
        }

    }
}
```
---

## 6. :floppy_disk: Stream API

* Manipulação de coleções com o paradigma funcional de forma paralela
* Imutável - Não altera a coleção origem, sempre cria uma nova coleção
* Principais funcionalidades
    * Mapping - Retorna uma coleção com mesmo tamanho da origem com os elementos alterados
    * Filtering - Retorna uma coleção igual ou menor que a coleção origem, com elementos intactos
    * ForEach - Executa uma determinada lógica para cada elemento, retornando nada
    * Peek - Executa uma determinada lógica para cada elemento, retornando a própria coleção
    * Counting - Retorna um inteiro que representa a contagem dos elementos
    * Grouping - Retorna uma coleção agrupada de acordo com a regra definida

---
```JAVA
import java.util.*;
import java.util.stream.Collectors;

public class Principal {
    public static void main(String[] args) {

        //Cria a coleção de estudantes
        List<String> estudantes = new ArrayList<>();

        //Adicionando estudantes para coleção
        estudantes.add("Pedro");
        estudantes.add("Thayse");
        estudantes.add("Marcelo");
        estudantes.add("Carla");
        estudantes.add("Juliana");
        estudantes.add("Thiago");
        estudantes.add("Rafael");

        //Retorna a contagem de elementos do stream
        System.out.println("Contagem: " + estudantes.stream().count());

        //Retorna o elemento com maior número de letras
        System.out.println("Maior nº de letras: "+estudantes.stream().max(Comparator.comparingInt(String::length)));

        //Retorna o elemento com menor número de letras
        System.out.println("Menor nº de letras: "+estudantes.stream().min(Comparator.comparingInt(String::length)));

        //Retorna elementos que tem a letra R no nome
        System.out.println("Nomes com a letra 'R': "+estudantes.stream().filter((estudante) -> estudante.toLowerCase().contains("r")).collect(Collectors.toList()));

        //Retorna os 3 primeiros elementos da coleção
        System.out.println("3 primeiros elementos: "+estudantes.stream().limit(3).collect(Collectors.toList()));
        System.out.println();
        //Retorna cada elemento da coleção, sem retornar outra coleção
        System.out.println("Retornando com forEach(), sem retornar a coleção no final: ");
        estudantes.stream().forEach(System.out::println);

        //Retorna cada elemento da coleção e depois retorna a mesma coleção
        System.out.println();
        System.out.println("Retorna cada elemento e depois retorna a coleção com peek()");
        System.out.println(estudantes.stream().peek(System.out::println).collect(Collectors.toList()));

        //Retorna true se todos elementos da coleção comportarem a condicional
        System.out.println();
        System.out.println("Todos elementos possuem 'W'? : "+estudantes.stream().allMatch((elemento) -> elemento.contains("W")));

        //Retorna true se algum elemento tiver a letra minúscula
        System.out.println();
        System.out.println("Algum elemento com a letra minúscula no nome?: "+
                estudantes.stream().anyMatch((elemento) -> elemento.contains("a")));

        //Retorna o primeiro elemento
        System.out.println();
        System.out.println("Primeiro elemento da coleção");
        estudantes.stream().findFirst().ifPresent(System.out::println);
    }
}
```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
