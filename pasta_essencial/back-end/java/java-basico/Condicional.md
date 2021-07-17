# :floppy_disk:Estruturas de decisão
---

## As estruturas de decisão são utilizadas para controlar o fluxo de execução dos aplicativos,possibilitando que a leitura das instruções siga caminhos alternativos em função da análise de determinadas condições. 

---
### :open_file_folder:Estrutura_if
* A estrutura de decisão if é utilizada para impor uma ou mais condições que deverão ser satisfeitas para 
a execução de uma instrução ou bloco de instruções. A sua forma geral é a seguinte:

   `If(<condição>){<instrução ou bloco>;}`
   * A condição sempre irá figurar entre parênteses, após a palavra reservada if, 
e deve ser uma expressão booleana que resulte em um valor true ou false. 

   * A instrução ou o bloco de instruções somente será executado caso o resultado dessa expressão seja true.
Caso o resultado seja false, o fluxo de execução será desviado e a instrução ou o bloco de instruções 
não será executado.
---
### :open_file_folder:Estrutura_if-else
* A estrutura de decisão if-else é uma variação da estrutura if. 
Ela é utilizada para impor uma ou mais condições que deverão ser satisfeitas para a execução de uma 
instrução ou bloco de instruções e possibilita a definição de uma instrução ou bloco de instruções a 
serem executados caso as condições não sejam satisfeitas. A sua forma geral é a seguinte:

   `If(<Condição>){<instrução ou bloco>;}`

   `else {<instrução ou bloco>;}`


   * A condição sempre irá figurar entre parênteses, após a palavra reservada if, e deve ser
uma expressão booleana que resulte em um valor true ou false. A primeira instrução ou o bloco de
instruções somente será executado caso o resultado dessa expressão seja true. Caso o resultado seja false,
o fluxo de execução será desviado e a instrução ou o bloco posterior ao else será executado.

* Exemplo:
```java
public class EstruturaCondicional{
    public static void main(String[] args){	
        int n1 = 10;
        int n2 = 25;
        int n3 = 65;

        System.out.println("Informe sua idade");
        //If é a condicional "SE"
        if(idade < 18){
            System.out.println("Menor de idade.");
            //else if é o mesmo que "SENÃO SE"
            //podemos combinar os operadores lógicos para verificar a condição
            //nessa caso foi utilizado "&&" que é o mesmo que "AND"
        }else if(idade > 18 && idade < 65){
            System.out.println("Maior de idade.");
            //else é o mesmo que "SENÃO"
        }else{
            System.out.println("Idoso");	
        }
    }
}
```
---

### :open_file_folder:Equals
* O método equals é usado para a comparação. A classe String e as classes Wrapper sobrescrevem o equals para garantir que dois objetos desses tipos, com o mesmo conteúdo, possam ser considerados iguais.

  * Para descobrir se as referências são iguais, deve-se utilizar o   “ == ”,
  * Para que seja comparado os bits das variáveis ou seja seu valor, utiliza-se equals.

* Exemplo:

   `String teste1 = “igual”;`

   `String teste2 = “igual”;`

   `teste1.equals(teste2);`

---

### :open_file_folder:Operador_ternário
* Esse código trata-se de um operador matemático, com um condicional.
Em alguns casos, ambos podem ter comportamento um pouco diferente. 
Lembrando também que o ternário sempre deve retornar valor, e o valor será sempre do mesmo tipo, para ambos os lados da expressão.
* Sintaxe:
   * `(condição) ? valor_se_verdadeiro : valor_se_falso`

* Exemplo:
```java
  if (a > 0)
      b = 1;
   else
      b = 2;

   //com o ternário ficaria:

    b = (a > 0) ? 1 : 2;
```
---

### :open_file_folder:SWITCH

* A estrutura de decisão switch-case, ou simplesmente switch, é uma forma simples para se definir diversos desvios no código a partir de uma única variável ou expressão.
Havendo uma variável com diversos valores possíveis e sendo necessário um tratamento específico para cada um deles, o uso da estrutura if-else se torna confuso e dificulta a leitura do código. Nesse caso, a clareza e a facilidade 
estão do lado da estrutura switch.

* A sintaxe geral da estrutura switch é a seguinte:
```java
   switch (variável) {
     case valor1:
       código se variável = valor1;
       break;
     case valor2:
       código se variável = valor2;
       break;
     case valorN:
       código se variável = valorN;
       break;
     default:
       código se variável diferente de todos os valores;
}
```

* A palavra reservada break é utilizada na estrutura switch para promover um desvio da execução para a linha posterior ao final de seu bloco. Geralmente, ele é utilizado como a última instrução de cada declaração case.

* A palavra default indica que caso nenhum dos cases seja utilizado, a instrução que se encontra no default será 
executada.

* Exemplo:
```java
package condicional;

import java.util.Scanner;
public class Switch {
    public static void main(String[] args){
        Scanner entrada = new Scanner(System.in);
        int teste;
        //criacao da variavel teste
        
        System.out.println("Digite o mês em número inteiro");
        teste = entrada.nextInt();
        //entrada de dados
        
        switch(teste){
            case 1:
                System.out.println("Janeiro");
                break;
            case 2:
                System.out.println("Fevereiro");
                break;
            case 3:
                System.out.println("Março");
                break;
            case 4:
                System.out.println("Abril");
                break;
                
            default:
                System.out.println("Digite SOMENTE números entre 1 e 4");
                break;
        }
    }
}
```
---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)



