# :gem: Strings
---
## A classe String e algumas funções.
```Java
public class Principal {
    public static void main(String[] args) {

        //Como declarar uma String:
        String nome = "Maria";
        String sobrenome = "Santos";

        //Concatenação com Strings:
        System.out.println(nome + " " + sobrenome);

        String nomeCompleto = nome +" "+sobrenome;
        System.out.println(nomeCompleto);

        //Buscando uma letra dentro da String com charAt(n):
        System.out.println("Letra na posição 3: " + nome.charAt(2));

        //Identificando o tamanho da string:
        System.out.println("Tamanho da String Maria: "+ nome.length());

        //Deixando as letras em minúsculo:
        System.out.println("Lowercase:" + nome.toLowerCase());

        //Deixando as letras em maiúsculo:
        System.out.println("Upercase:" + nome.toUpperCase());

        //Verificando se contém alguma letra na String:
        System.out.println("Contém M? : " + nome.contains("M"));

        //Comparando Strings:
        System.out.println("Equals: " + nome.equals("Maria"));
        //Ignorando case sensitive:
        System.out.println("Equals: " + nome.equalsIgnoreCase("maria"));

        //Pegando um valor de uma determinada posição:
        System.out.println("Substring Maria de 0 até 2 : " + nome.substring(0, 2));
        System.out.println("Substring Maria a partir da 2 : " + nome.substring(2));

        //Utilzando String format para formatar números reais, útil com valores:
        double valor = 2.75;

        System.out.println("Sem formatação: " + valor);
        System.out.println("Com formatação: " + String.format("%.2f", valor));

        //Removendo os "espaços" nos cantos da String com "trim":
        String testeTrim = "Mensagem com espaço em branco no final        ";
        String trim2 = "  - demarcação para ver o resultado  ";
        System.out.println(testeTrim.trim() + trim2.trim());

        //Substituir letras:
        String nome2 = "Joao";
        System.out.println("Joao, substituindo 'o' por 'u' : "+nome2.replace('o', 'u'));
        //Substituir substrings:
        String texto = "Vosse sabe, vosse sabe.";
        System.out.println("Substituir o texto : " + texto +" \nOnde contém 'ss'  substituir por 'c' : " + texto.replace("ss","c"));

        //Função pare recortar uma String com Split:
        String s = "potato apple lemon";
        String[] vect = s.split(" ");
        System.out.println("Utilizando String[] vect = s.split(\" \"), na String s : " + s);
        System.out.println(vect[0]);
        System.out.println(vect[1]);
        System.out.println(vect[2]);
    }
}
```
#### Output:

```
> Task :Principal.main()
Maria Santos
Maria Santos
Letra na posição 3: r
Tamanho da String Maria: 5
Lowercase:maria
Upercase:MARIA
Contém M? : true
Equals: true
Equals: true
Substring Maria de 0 até 2 : Ma
Substring Maria a partir da 2 : ria
Sem formatação: 2.75
Com formatação: 2,75
Mensagem com espaço em branco no final- demarcação para ver o resultado
Joao, substituindo 'o' por 'u' : Juau
Substituir o texto : Vosse sabe, vosse sabe. 
Onde contém 'ss'  substituir por 'c' : Voce sabe, voce sabe.
Utilizando String[] vect = s.split(" "), na String s : potato apple lemon
potato
apple
lemon
```


---

## Estrutura para criar um limpador de buffer para String.

* Após ler um valor não alfanumérico(números, por exemplo), onde o valor é armazenado na variável, mas o ENTER continua no buffer.

* É necessário verificar se esse ENTER está presente e removê-lo. Para isso crie uma função que receba o objeto Scanner por parâmetro e faça os devidos procedimentos. 

* Estrutura:
```java
private static void clearBuffer(Scanner scanner) {
    if(scanner.hasNextLine()) {
        scanner.nextLine();
    }
}
```
   * Depois disto basta chamar o método:
   `clearBuffer(<nomeScanner>);`
---

* Exemplo:
```java
package curso_java;

import java.util.Scanner;

public class LimpaBuffer {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		System.out.println("Informe um número: ");
		int n = input.nextInt();
		//Chamada do método para limpar o "input"(objeto Scanner)
		//Sem essa chamada não seria possível ler a String
		clearBuffer(input);
		System.out.println("Informe um nome: ");
		String nome = input.nextLine();
		
		System.out.println(n+" "+nome);
	}
	//Método criado para limpar o buffer após um alfanumérico.
	private static void clearBuffer(Scanner scanner) {
	    if(scanner.hasNextLine()) {
	        scanner.nextLine();
	    }
	}

}
```
* Esse é apenas um exemplo para um código mais legível, poderiamos simplesmente incluir um `input.nextLine()`, funcionaria da mesma forma.

---


## StringBuilder 

* Abaixo são apresentados os métodos principais e mais utilizados.

    * `length` - Retorna o número de caracteres atualmente em um StringBuilder;

    * `capacity` – Retorna o número de caracteres que pode ser armazenado em um StringBuilder sem alocar mais memória;

    * `ensureCapacity` – Garante que um StringBuilder tenha pelo menos a capacidade especificada;

    * `setLength` – Aumenta ou diminui o comprimento de uma StringBuilder;

    * `charAt` – Aceita um argumento inteiro que representa o índice e retorna o caractere nessa posição no StringBuilder;

	 * `setCharAt` – Copia caracteres de um StringBuilder no array de caracteres passado como um argumento, tendo aceitação de até 4 argumentos;

   		 * o índice inicial a partir do qual os caractere(s) devem ser copiados do StringBuilder;
   		 * o índice um a mais do último caractere que será copiado a partir do StringBuilder;
  		  * o array de caracteres para onde os caracteres serão copiados;
  		  * localização inicial no array de caracteres em que o primeiro caractere deve ser colocado;

 	* `getChars` – Retorna o caractere especificado;

	* `reverse` – Retorna os caracteres invertidos;

### Exemplo de String Builder com toString():

```Java
   @Override
    public String toString() {
        StringBuilder sbuilder = new StringBuilder();
        //Concatenação de Strings com método append
        sbuilder.append("Exemplo com um texto");
        sbuilder.append(exemploVariavel);
        sbuilder.append("Exemplo com um nome");
        for(exemploLista i: algumaLista){
            sbuilder.append(i.getTexto());
        }
        sbuilder.append(exemploVariavel2);
        if(condição){
            sbuilder.append("Texto Qualquer");
        }
        return sbuilder.toString();
    }
```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)