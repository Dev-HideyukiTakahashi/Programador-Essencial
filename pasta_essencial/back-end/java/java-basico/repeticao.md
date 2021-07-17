# :floppy_disk:Estruturas de repetição
---
* As estruturas de repetição também são conhecidas como laços (loops) e são utilizados para executar, repetidamente, uma instrução ou bloco de instrução enquanto determinada condição estiver sendo satisfeita.

* Qualquer que seja a estrutura de repetição, ela contém quatro elementos fundamentais: 
**inicialização**,**condição**, **corpo** e **iteração**. 
   * A inicialização compõe-se de todo código que determina a condição inicial da repetição. 
   * A condição é uma expressão booleana avaliada após cada leitura do corpo e 
   determina se uma nova leitura deve ser feita ou se a estrutura de repetição deve ser encerrada. 
   * O corpo compõe-se de todas as instruções que são executadas repetidamente. 
   * A iteração é a instrução que deve ser executada depois do corpo e antes de uma nova repetição.
---

### :open_file_folder:While

* Uma estrutura de repetição while, que em português significa enquanto, especifica que um sistema ou programa de computador deve repetir uma instrução ou um conjunto de instruções enquanto a condição que é uma expressão booleana permanece verdadeira.

* O exemplo abaixo, escreve no console o nome  “while” enquanto dado número representado pela variável “num” que é inicializado com 0, for menor do que 100.
```java
num = 0;

while (num < 100){
       System.out.println("while");
       num++;
}
```
---
### :open_file_folder:Do…while

* Você já deve imaginar que a estrutura de repetição do…while é uma variação da while. 
A principal diferença entre elas é que, como já dissemos, o while processa uma instrução ou grupo de instrução, zero ou mais vezes, ao passo que o do…while processa uma instrução, obrigatoriamente pelo menos uma vez, e se necessário outras tantas vezes.

* Assim, implica que o corpo da estrutura, ou seja, o bloco de instrução será executado pelo menos uma vez antes que a condição do loop seja testada. Exemplo:
```java
num = 0

do{
   System.out.println("do..while");
   num++;
}while (num < 100);
```
---

### :open_file_folder:FOR
* Lembra que utilizamos uma estrutura de repetição controlado por um contador com o while?
O for que em português significa “para”, não apenas é capaz de implementar esse tipo de repetição como o faz
em uma única linha.

* O for também é uma instrução de repetição que processa uma instrução ou grupo de instrução zero ou mais vezes.
* O que munda é a sintaxe, no caso do for a variável de controle, o valor inicial, o incremento e a condição de 
continuação do loop, são declarados como em uma espécie de cabeçalho, também chamado de cabeçalho da instrução for.

* O formato da sintaxe da instrução de repetição for fica assim:
```java
for(int num = 0; num < 10; num++){
   System.out.println("for");
} 
```
* Detalhando a estrutura acima temos a palavra reservada for, a variável de controle seguida do seu valor de inicialização, e então esse bloco do cabeçalho é separado por um ponto e vírgula, continuando temos a condição de continuação do loop que é uma expressão booleana, o ponto e vírgula e o incremento.

* Geralmente utilizamos o for quando há um número final já definido para o fim do loop.

* Todo laço de repetição escrito obedecendo as regras de sintaxe da estrutura while também pode ser escrito com a sintaxe do for.
---
### :open_file_folder:Enhanced-for
* O enhanced-for foi introduzido a partir do Java 5, e é utilizado para realizar as varreduras em collections. 
Para cada iteração do for, o elemento da iteração é atribuído à variável. Utilizando o enhanced-for, você é obrigado a percorrer um array por exemplo.
Sintaxe:
```java
for(<Tipo> <dado> : <array>) {
    <blocoDeComando>
}
```
```java
* Exemplo
// print array elements 

class Main {
  public static void main(String[] args) {
      
    // create an array
    int[] numbers = {3, 9, 5, -5};
    
    // for each loop 
    for (int number: numbers) {
      System.out.println(number);
    }
  }
}
```

### :open_file_folder:Quebras_de_Laço
* As quebras de laço são utilizadas para interromper o fluxo normal das estruturas de repetição while, do-while e for. Há dois tipos distintos de quebras de laço, representadas pelas palavras reservadas **break** e **continue**.

* Há situações em que é preciso interromper um laço antes que sua condição se torne falsa. 
É para isso que serve o **break;**. Figurando dentro do bloco de instruções de um laço qualquer,essa instrução encerra a estrutura de repetição, desviando a execução do aplicativo para a linha seguinte ao final desse laço.

* Enquanto a instrução **break;** é utilizada para encerrar um laço, a instrução **continue;** serve para iniciar uma nova repetição em que todas as instruções tenham sido executadas. Em laços while e do-while, uma instrução **continue;** desvia o fluxo de execução para a condição. Em um laço for, ela desvia o fluxo de execução para a iteração e, em seguida, a condição é lida novamente.

---

:coffee:[Voltar Java](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)


