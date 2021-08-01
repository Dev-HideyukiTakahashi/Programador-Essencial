# :hammer_and_wrench:Flex Container

---

**O Flex Container é a tag que envolve os itens flex, ao indicar display: flex, essa tag passa a ser um Flex Container.**

---

## :hammer:Display

- Define o elemento como um flex container, tornando os seus filhos flex-itens.
- Os elementos flutuam como se fosse aplicar o comando `float left`, útil para alinhar os elementos em uma fileira.
- O Tamanho do item é exatamente o tamanho do conteúdo.

- `display: flex;`

  - Torna o elemento um flex container automaticamente transformando todos os seus filhos diretos em flex itens.

- Exemplo utilizando uma classe flex:
  ```css
  .flex {
    display: flex;
  }
  ```
- `flex-wrap`

  - Define se os itens devem quebrar ou não a linha. Por padrão eles não quebram linha, isso faz com que os flex itens sejam compactados além do limite do conteúdo.

  - Essa é geralmente uma propriedade que é quase sempre definida como flex-wrap: wrap; Pois assim quando um dos flex itens atinge o limite do conteúdo, o último item passa para a coluna debaixo e assim por diante.

- Exemplo utilizando uma classe flex-wrap:

  ```css
  .flex-wrap {
    flex-wrap: wrap;
  }
  ```

- `flex: 1`
  - Utilizado para que os elementos ocupem o tamanho total do container, já que sem essa propriedade cada elemento terá o seu tamanho natural, podendo sobrar espaço indesejado do container.
- Exemplo utilizando uma classe de um item:
  ```css
  .item {
    background: tomato;
    margin: 5px;
    text-align: center;
    font-size: 1.5em;
    flex: 1; /* propriedade para o item se dividir em tamanho proporcional ao container*/
  }
  ```

---

## :hammer:Flex-direction

- Define a direção dos flex itens. Por padrão ele é row (linha), por isso quando o display: flex; é adicionado, os elementos ficam em linha, um do lado do outro.

- A mudança de row para column geralmente acontece quando estamos definindo os estilos em media queries para o mobile. Assim você garante que o conteúdo seja apresentado em coluna única.

  ```css
  .flex {
    flex-direction: row;
    // Os itens ficam em linha
    flex-direction: row-reverse;
    // Os itens ficam em linha reversa, ou seja 3, 2, 1.
    flex-direction: column;
    // Os itens ficam em uma única coluna, um embaixo do outro.
    flex-direction: column-reverse;
    // Os itens ficam em uma única coluna, um embaixo do outro, porém em ordem reversa: 3, 2 e 1.
  }
  ```

---

## :hammer:Justify-content

- Alinha os itens flex no container de acordo com a direção. A propriedade só funciona se os itens atuais não ocuparem todo o container. Isso significa que ao definir flex: 1; ou algo similar nos itens, a propriedade não terá mais função

- Excelente propriedade para ser usada em casos que você deseja alinhar um item na ponta esquerda e outro na direita, como em um simples header com marca e navegação.

  ```css
  .flex {
    justify-content: flex-start;
    // Alinha os itens ao início do container.
    justify-content: flex-end;
    // Alinha os itens ao final do container.
    justify-content: center;
    // Alinha os itens ao centro do container.
    justify-content: space-between;
    // Cria um espaçamento igual entre os elementos. Mantendo o primeiro grudado no início e o último no final.
    justify-content: space-around;
    // Cria um espaçamento entre os elementos. Os espaçamentos do meio são duas vezes maiores que o inicial e final.
  }
  ```

---

## :hammer:Align-items

- O align-items alinha os flex itens de acordo com o eixo do container. O alinhamento é diferente para quando os itens estão em colunas ou linhas.

- Essa propriedade permite o tão sonhado alinhamento central no eixo vertical, algo que antes só era possível com diferentes hacks.

  ```css
  .flex {
    align-items: stretch;
    // Valor padrão, ele que faz com que os flex itens cresçam igualmente.
    align-items: flex-start;
    // Alinha os itens ao início.
    align-items: flex-end;
    // Alinha os itens ao final.
    align-items: center;
    // Alinha os itens ao centro.
    align-items: baseline;
    // Alinha os itens de acordo com a linha base da tipografia.
  }
  ```

---

## :hammer:align-content

- Alinha as linhas do container em relação ao eixo vertical. A propriedade só funciona se existir mais de uma linha de flex-itens. Para isso o flex-wrap precisa ser wrap.

- Além disso o efeito dela apenas será visualizado caso o container seja maior que a soma das linhas dos itens. Isso significa que se você não definir height para o container, a propriedade não influencia no layout.

  ```css
  .flex {
    align-content: stretch;
    // Valor padrão, ele que faz com que os flex itens cresçam igualmente na vertical.
    align-content: flex-start;
    // Alinha todas as linhas de itens ao início.
    align-content: flex-end;
    // Alinha todas as linhas de itens ao final.
    align-content: center;
    // Alinha todas as linhas de itens ao centro.
    align-content: space-between;
    // Cria um espaçamento igual entre as linhas. Mantendo a primeira grudada no topo e a última no bottom.
    align-content: space-around;
    // Cria um espaçamento entre as linhas. Os espaçamentos do meio são duas vezes maiores que o top e bottom.
  }
  ```
---
Fonte: https://origamid.com/projetos/flexbox-guia-completo/

---
:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
