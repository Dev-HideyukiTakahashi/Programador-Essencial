# :gem:Algoritmos

---

<details>
<summary><strong>Gerar número aleatório</strong></summary>

- Primeiro você precisa importar a classe `Random` do pacote java.util

  - `import java.util.Random`

- Agora você pode instanciar um objeto da classe Random.

  - `Random random = new Random();`

#### Exemplos:

- Gerando números inteiros aleatórios de 0 à 100:

  - Para gerar números aleatórios inteiros de 0 até um determinado valor, basta chamar o método `nextInt` informando o valor máximo. No nosso exemplo o máximo é 100:

    - `int numero = random.nextInt(100);`

- Gerando números reais aleatórios:
  - Números reais são gerados de 0 até 1 com a função `nextDouble`. Logo, se você quiser um número aleatório de 0 até o número que você quiser, basta multiplicar por ele.
    Por exemplo, para gerar um número aleatório de 0 até 100 basta multiplicar o número gerado por 100.
    - `double numero random.nextDouble() * 100; //Número aleatório de 0 à 100`

---

#### Código Exemplo:

```Java
package exemplo;

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
```

#### Exemplo de saída:

Número inteiro aleatório de 0 até 100: 43

Número real aleatório de 0 até 1: 0.16296306514069792

Número real aleatório de 0 até 100: 46.890481714549026

</details>

<details>
<summary><strong>Formatar valor no padrão de moeda local</strong></summary>

- OBS: o caractere "**¤**" serve para exibir o Label monetário, no caso do Brasil exibe o R$.
- Exemplo de código:

```JAVA
NumberFormat nf = new DecimalFormat("¤ ###,###,##0.00",
			new DecimalFormatSymbols(new Locale("pt","BR")));

System.out.println((nf.format(1788.00)));
```

`R$ 1.788,00`

- Para criar um método em uma classe retornando o valor formatado, é preciso um método de String formatado para Double, pois o método só retorna uma String, exemplo:

```Java
public static NumberFormat nf = new DecimalFormat("¤ ###,###,##0.00",
      new DecimalFormatSymbols(new Locale("pt", "BR"));

public static String formataMoeda(Double valor) {
   return nf.format(valor);
}


/////Na chamada(application):
   double preco = 1788.00;
   System.out.println(formataMoeda(preco));

```

`Saída:$ 1,788.00`

---

- NumberFormat

```java
   NumberFormat nf = NumberFormat.getCurrencyInstance(new Locale("pt", "BR"));

   Double preco = 2000.00;
   System.out.println("Preço unitário: ");
	System.out.println(nf.format(preco));
```

`Saída: Preço unitário: R$ 2.000,00`

</details>

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
