# :floppy_disk:Conceitos Iniciais

---

* ### :open_file_folder:Tipos_primitivos

  * Boolean: Não é um valor numérico, só admite os valores true ou false e ocupa apenas 1 bit de espaço.
    * Valor padrão para o tipo boolean: **false**
  * Char: Usa o código UNICODE e ocupa cada caractere 16    bits.
  * Inteiros: Diferem nas precisões e podem ser positivos ou negativos.
    - Byte: 1 byte.
    - Short: 2 bytes.
    - Int: 4 bytes.
    - Long: 8 bytes.
  * Reais em ponto flutuante: igual que os inteiros também diferem nas precisões e podem ser positivos ou negativos.
    - Float: 4 bytes.
    - Double: 8 bytes.

---

* Tipos Primitivos: Números inteiros:

Tipo  |	Tamanho (bits)  |  	Faixa  |	Valor Padrão
---|---|--- | ---
byte  |	8  |	-128 a 127|	0
short  |	16  |	-32.768 a 32.767 |	0
int	 | 32  |	-231 a 231 – 1 |	0
long  |	64 |	-263 a 263 -1 |	0L

---

* Tipos Primitivos: Números de Ponto Flutuante:

Tipo  |	Tamanho (bits)  |	Faixa  |	Valor Padrão
---|---|--- | ---
float  |	32  |	IEEE 754 ±1,40129846432481707e-45 a 3,40282346638528860e+38 |	0.0f
double  |	64  |	IEEE 754 ±4,94065645841246544e-324 a 1,79769313486231570e+308	 | 0.0d
* Podemos controlar a quantidade de casas em um número flutuante:
```java
public class controlaFlutuante {
//Controlando o número de casas com número flutuante
  public static void main(String[] args) {
    double n1 = 1.12345;
    double n2 = 1.12345;
    double n3 = 1.12345;
		
    //Com o comando printf (f = formatado)
    //Dentro do printf o comando: "%.<qtdCasas>f",<variávelDeSaída>
    System.out.printf("%.2f%n",n1);
    System.out.printf("%.4f%n", n2);
    System.out.printf("%.5f%n", n3);
    //O comando %n foi apenas para pular uma linha.
  }
}
```
* Para conseguir utilizar ponto ao invés de vírgula, que é o padrão americano com números flutuantes, basta adicionar o comando:
`Locale.setDefault(Locale.US)`

---

* ###  :open_file_folder:Operações

  * Podemos realizar uma série de operações com os dados do tipo inteiro. A tabela seguinte mostra uma lista completa.

Operação | Descrição
--- | ---
`=, +=, -=, *=, /=, %=`	| Operadores de atribuição
`==, !=` |	Operadores de igualdade e diferença
`<, <=, >, >=` |	Operadores de desigualdade
`+, -`	| Operadores unários
`+, -, *, /, %`	| Adição, subtração, multiplicação, divisão e módulo
`+=, -=, *=, /=, %=` |	Operadores de atribuição com adição, subtração, multiplicação, divisão e módulo
`++, --` |	Incremento e decremento
`<<, >>, >>>` |	Operadores de deslocamento de bits
`<<=, >>=, >>>=` |	Operadores de atribuição com deslocamento de bits
`~`	 | Operador lógico de negação
`&&, ^`|	Operadores lógicos E e OU-exclusivo
`&=, ^=,`	| Operadores de atribuição com operação lógica E e Ou - exclusivo.

  * Operador lógico OU = `||`
  * Operadores de atribuição com operação lógica Ou =  `|= `
 
  * Muitas das operações realizáveis com inteiros (porém não todas) têm análogas para números de ponto flutuante. Eis um resumo: 
    * Operadores de atribuição
    * Operadores de igualdade e diferença
    * Operadores de desigualdade
    * Sinais unários
    * Adição, subtração, multiplicação e divisão
    * Operadores de atribuição com adição, subtração, multiplicação e divisão
    * Operadores unários de incremento e decremento

* Operadores de atribuição cumulativa

Operação | Cumulativa
--- | ---
a += b; |  a = a + b;
a -= b; | a = a - b;
a *= b; | a = a * b;
a /= b; | a = a / b;
a %= b; | a = a % b;

---
###  :open_file_folder: Modificadores de Acesso:

* **default, public, private e protected**

* Temos quatro modificadores de acesso: public,
private, protected e default.

  * O modificador default não precisa ser declarado,
ou seja, atributos ou métodos que não têm a declaração de um modificador de
acesso são considerados default (que do inglês significa “padrão”).

  * Atributos e métodos públicos (**public**) podem ser acessados e modificados de
qualquer classe do projeto a partir da instância do objeto, ou seja, até de outros
pacotes é possível ter acesso a atributos/métodos do tipo public de forma direta.

  * Já atributos e métodos privados (**private**)  só podem ser acessados pela própria classe, ou seja, eles não são visíveis e nem acessados
  por outros objetos.

  * Outro modificador de acesso não tão comumente utilizado é o modificador **protected**
(protegido em português), este tipo de modificador funciona como um
modificador público para elementos que estão no mesmo pacote, e em outros
pacotes ele só é visível para classes que herdam a classe que possui o atributo
protegido.

MODIFICADOR | NA PRÓPRIA CLASSE |EM OUTRO PACOTE | NO MESMO PACOTE | HERANÇA (EM PACOTE DIFERENTE)
--- | --- | --- | --- | --- 
public | Acessível | Acessível | Acessível |Acessível
private | Acessível | Não | Não |  Não
protected | Acessível | Não | Acessível| Acessível
default | Acessível |  Não | Acessível | Não


* Além dos modificadores de acesso, o JAVA permite a utilização de outros
modificadores, são eles: **static, final e abstract.**

  * O modificador static pode ser aplicado a variáveis e métodos, e a principal característica
dele é que se tratando de atributos, todos os objetos compartilham do
mesmo espaço de memória, e se tratando de método, este pode ser acessado sem
a necessidade de instância do objeto.

  * Os modificadores final restringem ainda mais o acesso aos elementos de uma
classe, para atributos, ele faz com que o atributo não possa ser modificado em
tempo de execução, ou seja, cria-se uma variável que terá um valor constante
do início ao término da execução da aplicação.
Para Classes, indica que esta não
poderá ser herdada (não poderá ter filhos) e para métodos, indica que o mesmo
não poderá ser sobrescrito (usar técnicas de polimorfimo).

  * O modificador abstract é aplicado somente a métodos e a classes, métodos abstratos
não fornecem implementações e em classes abstratas não é possível a criação
de objetos da classe, e normalmente possuem um ou mais métodos abstratos.
O objetivo de criação de classes abstratas é fornecer uma superclasse apropriada
a partir da qual outras classes podem herdar e assim poder compartilhar
um design comum.
---
### :open_file_folder: Scanner: ler dados digitados pelo usuário no console.

* Para invocar a classe **Scanner**, precisamos importar a seguinte biblioteca:
    * `java.util.Scanner`

* Podemos comparar com a função `scanf()` da linguagem **C**

* Cria-se um objeto do tipo Scanner, que passa como argumento o objeto System.in dentro construtor.

* Para cada um dos primitivos existe uma chamada do método para retornar o valor especificado na entrada de dados, sempre seguindo o formato `nextTipoDado()`
* Scanner também é utilizado para manipular arquivos.
```java
    //Criando o objeto do tipo Scanner:
    Scanner input = new Scanner(System.in);

    //Chamada de metódo para retornar o valor em cada tipo:
    float n = input.nextFloat();
    int n = input.nextInt();
    byte bt = input.nextByte();
    long lg = input.nextLong();
    boolean bl = input.nextBoolean();
    double d = input.nextDouble();
    //Para ler a linha inteira
    String s = input.nextLine();
    //Para ler apenas uma palavra
    String s = input.next();
    char c = input.next().chartAt(0);
 ```
* Exemplo prático da utilização:
```java
    public class lendoDados {
      public static void main (String[] args){
          int a;
       
         //Definindo o nome do objeto da classe Scanner, nesse caso eu chamei de "input".   
         Scanner input = new Scanner(System.in);
       
          System.out.println("\nInforme um número: ");
          //A variável "a" recebe o objeto "input" criado acima a partir da classe Scanner, seguido por "nextTipoDado", 
          //nesse caso usei um tipo int, portanto nextInt.
         a = input.nextInt();
         System.out.println("\nO número é: " + a);
        }
    }
    //Comando para encerrar objeto
    input.close();
```

* Podemos utilizar o `<nomeDado>.close()` para fechar o escaneamento de leitura.
* Geralmente útil para fechar arquivos, pois  o scanner também é utilizado em para abrir e fechar arquivos.

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)



