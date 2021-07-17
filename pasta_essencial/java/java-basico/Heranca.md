# :floppy_disk:Herança

---
A herança é um mecanismo da Orientação a Objeto que permite criar novas classes a partir de classes já existentes, aproveitando-se de todos os dados e comportamentos existentes na classe a ser estendida(super classe).

Os subtipos, além de herdarem todas as características de seus supertipos, também podem adicionar mais características, seja na forma de variáveis e/ou métodos adicionais, bem como reescrever métodos já existentes na superclasse, polimorfismo.

* Vantages de herança

    * Reuso
    * Polimorfismo

* Sintaxe:
    * `class A extends B`

---

### **Upcasting** e **Downcasting**

* Upcasting
    * Casting da subclasse para superclasse
    * Uso comum: polimorfismo

* Downcasting
    * Casting da superclasse para subclasse
    * Palavra `instanceof`
    * Uso comum: métodos que recebem parâmetros genéricos (ex: Equals)

* Exemplo:

```JAVA
package aula;

import entities.Account;
import entities.BusinessAccount;
import entities.SavingsAccount;

public class Main {
	public static void main (String[] args) {
		
		Account acc = new Account(1001, "Alex", 0.0);
		BusinessAccount bacc = new BusinessAccount(1002, "Maria", 0.0, 500.0);
		
		//UPCASTING
		
		Account acc1 = bacc;
		Account acc2 = new BusinessAccount(1003, "Bob", 0.0, 200.0);
		Account acc3 = new SavingsAccount(1004, "Ana", 0.0, 0.01);
		
		//Downcasting
		
		//É necessário um casting da subclasse
		BusinessAccount acc4 = (BusinessAccount)acc2;
		//Chamando um método da classe BusinessAccount, que não era possível no objeto "acc2"
		acc4.loan(100.0);
		
		//Essa chamada de objeto gera um erro, pois a classe é diferente da sub e super, acc3 pertence a "SavingAccount"
		/*BusinessAccount acc5 = (BusinessAccount) acc3;*/
		
		//Instanceof para testar
		
		if(acc3 instanceof BusinessAccount) {
			BusinessAccount acc5 = (BusinessAccount)acc3;
			acc5.loan(200.0);
			System.out.println("BusinessAccount");
			
		}
		if(acc3 instanceof SavingsAccount) {
			SavingsAccount acc5 = (SavingsAccount)acc3;
			acc5.updateBalance();
			System.out.println("SavingAccount");			
		}

		
	}

}
```

---

### Polimorfismo

* Polimorfismo significa "muitas formas", é o termo definido em linguagens orientadas a objeto, como por exemplo Java, C# e C++, que permite ao desenvolvedor usar o mesmo elemento de formas diferentes. Polimorfismo denota uma situação na qual um objeto pode se comportar de maneiras diferentes ao receber uma mensagem. No Polimorfismo temos dois tipos:

    * Polimorfismo Estático ou Sobrecarga


      * O Polimorfismo Estático se dá quando temos a mesma operação implementada várias vezes na mesma classe. A escolha de qual operação será chamada depende da assinatura dos métodos sobrecarregados.

	 * Polimorfismo Dinâmico ou Sobreposição

        * O Polimorfismo Dinâmico acontece na herança, quando a subclasse sobrepõe o método original. Agora o método escolhido se dá em tempo de execução e não mais em tempo de compilação. A escolha de qual método será chamado depende do tipo do objeto que recebe a mensagem. 

---

### Sobrescrita de Métodos e Sobrecarga

* A Sobrescrita de Métodos (Override) pode ser classificada como polimorfismo de inclusão. 
Quando um método sobrescreve um método herdado de uma classe, temos uma sobrescrita de método. 
Este método de sobrescrita tem que ser idêntico ao método da classe herdada, ou seja, eles precisam ter o mesmo nome, valor de retorno e argumentos. Portanto, temos que uma classe filha fornece apenas uma nova implementação para o método herdado e não um novo método. 

Exemplo:
```JAVA
   public class Teste {
       
        public void fazAlgo() {
              System.out.println("Este é o método da super classe");
        }

   }

   public class NovoTeste extends Teste {

        @Override
        public void fazAlgo() {
              System.out.println("Este é o método foi sobrescrito");
        }

   }
```

* O tipo de polimorfismo de Sobrecarga (Overload) permite a existência de vários métodos de mesmo nome, porém com assinaturas levemente diferentes, ou seja, variando no número e tipo de argumentos. Ficaria a cargo do compilador escolher de acordo com as listas de argumentos os procedimentos ou métodos a serem executados.
Sobrecarga de Métodos é comumente usada nos construtores de uma classe Java.
```JAVA
   public class Teste {
       
        public void fazAlgo() {
              System.out.println("Este método não recebe parâmetro);
        }

        public void fazAlgo(String mensagem) {
              System.out.println("Mensagem");
        }

		public void fazAlgo(int n1, int n2, String mensagem){
			this.num1 = n1;
			this.num2 = n2;
			this.msg = mensagem;

		}

   }
```

---
### Classes e métodos `final`

* Palavra chave: `final`
* Para **classe**: evita que a classe seja herdada.
   * Sintaxe:
	```Java
	public final class SavingAccount {
		...
	}
	```
* Para **métodos**: evita que o método seja sobreposto.

---

:coffee:[Voltar Java](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
