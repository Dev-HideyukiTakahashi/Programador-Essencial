# :floppy_disk:Exceções
---
* Uma exceção é qualquer condição de erro ou comportamento
inesperado encontrado por um programa em execução
* Em Java, uma exceção é um objeto herdado da classe:
   * java.lang.Exception - o compilador obriga a tratar ou propagar
   * java.lang.RuntimeException - o compilador não obriga a tratar ou propagar
* Quando lançada, uma exceção é propagada na pilha de chamadas de métodos em execução, até que seja capturada (tratada) ou o
programa seja encerrado
---

Hierarquia de exceções do Java:

![](https://github.com/Dev-HideyukiTakahashi/Essencial/blob/master/pasta_essencial/java/java-intermediario/img/hierarquia.jpg)

---

### Por que exceções?
* O modelo de tratamento de exceções permite que erros sejam
tratados de forma consistente e flexível, usando boas práticas
* Vantagens:
   * Delega a lógica do erro para a classe responsável por conhecer as regras que
podem ocasionar o erro
   * Trata de forma organizada (inclusive hierárquica) exceções de tipos diferentes
   * A exceção pode carregar dados quaisquer

---

### Estrutura try-catch
* Bloco try
   * Contém o código que representa a execução normal do trecho de código que
pode acarretar em uma exceção
* Bloco catch
   * Contém o código a ser executado caso uma exceção ocorra
* Deve ser especificado o tipo da exceção a ser tratada (upcasting é permitido)
* Sintaxe:
```JAVA
try {
}
catch (ExceptionType e) {
}
catch (ExceptionType e) {
}
catch (ExceptionType e) {
```
* Exemplos:
```Java
package application;
import java.util.InputMismatchException;
import java.util.Scanner;
public class Program {
   public static void main(String[] args) {
      Scanner sc = new Scanner(System.in);
      try {
         String[] vect = sc.nextLine().split(" ");
         int position = sc.nextInt();
         System.out.println(vect[position]);
      }
      catch (ArrayIndexOutOfBoundsException e) {
         System.out.println("Invalid position!");
      }
      catch (InputMismatchException e) {
       System.out.println("Input error");
      }
      System.out.println("End of program");
      sc.close();
   }
}
```

---
### Pilha de chamadas de métodos
```Java
package application;
import java.util.InputMismatchException;
import java.util.Scanner;
public class Program {
   public static void main(String[] args) {
      method1();  
      System.out.println("End of program");
   }
   public static void method1() {
      System.out.println("***METHOD1 START***");
      method2();
      System.out.println("***METHOD1 END***");
   }
   public static void method2() {
      System.out.println("***METHOD2 START***");
      Scanner sc = new Scanner(System.in);
      try {
         String[] vect = sc.nextLine().split(" ");
         int position = sc.nextInt();
         System.out.println(vect[position]);
      }
   catch (ArrayIndexOutOfBoundsException e) {
      System.out.println("Invalid position!");
      e.printStackTrace();
      sc.next();
   }
   catch (InputMismatchException e) {
    System.out.println("Input error");
   }
   sc.close();
   System.out.println("***METHOD2 END***");
   }
}
```

---
### Bloco finally
* É um bloco que contém código a ser executado independentemente de ter
ocorrido ou não uma exceção.
* Exemplo clássico: fechar um arquivo, conexão de banco de dados, ou outro
recurso específico ao final do processamento.
* Sintaxe:
```Java

try {
}
catch (ExceptionType e) {
}
finally {
}
```
* Exemplo:
```Java
package application;
import java.io.File;
import java.io.IOException;
import java.util.Scanner;
public class Program {
   public static void main(String[] args) {
      File file = new File("C:\\temp\\in.txt");
      Scanner sc = null;
      try {
         sc = new Scanner(file);
         while (sc.hasNextLine()) {
         System.out.println(sc.nextLine());
         }
      }
      catch (IOException e) {
         System.out.println("Error opening file: " + e.getMessage());
      }
      finally {
         if (sc != null) {
         sc.close();
         }
      }
   }
}
```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)

