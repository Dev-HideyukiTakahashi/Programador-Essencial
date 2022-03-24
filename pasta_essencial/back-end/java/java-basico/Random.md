# :gem: Como gerar um número aleatório em Java

---

* Primeiro você precisa importar a classe `Random` do pacote java.util

   * `import java.util.Random`

* Agora você pode instanciar um objeto da classe Random.

   * `Random random = new Random();`

---

#### Exemplos:

* Gerando números inteiros aleatórios de 0 à 100:
   * Para gerar números aleatórios inteiros de 0 até um determinado valor, basta chamar o método `nextInt` informando o valor máximo. No nosso exemplo o máximo é 100:

      * `int numero = random.nextInt(100);`

* Gerando números reais aleatórios:
   * Números reais são gerados de 0 até 1 com a função `nextDouble`. Logo, se você quiser um número aleatório de 0 até o número que você quiser, basta multiplicar por ele.
    Por exemplo, para gerar um número aleatório de 0 até 100 basta multiplicar o número gerado por 100.
      * `double numero random.nextDouble() * 100; //Número aleatório de 0 à 100`

---
#### Código Exemplo:

```package exemplo;

import java.util.Random;

public class GerarNumeroAleatorio {

    public static void main(String[] args) {

        Random random = new Random();

        int numeroInteiroAleatorio_0_a_100 = random.nextInt(100);
        System.out.println("Número inteiro aleatório de 0 até 100: " + numeroInteiroAleatorio_0_a_100);

        double numeroRealAleatorio_0_a_1 = random.nextDouble();
        System.out.println("Número real aleatório de 0 até 1: " + numeroRealAleatorio_0_a_1);

        double numeroRealAleatorio_0_a_100 = random.nextDouble() * 10;
        System.out.println("Número real aleatório de 0 até 100: " + numeroRealAleatorio_0_a_100);

    }

}
}
```

#### Exemplo de saída:
Número inteiro aleatório de 0 até 100: 43

Número real aleatório de 0 até 1: 0.16296306514069792

Número real aleatório de 0 até 100: 46.890481714549026

---

Fonte: https://dicasdejava.com.br/como-gerar-um-numero-aleatorio-em-java/

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)




