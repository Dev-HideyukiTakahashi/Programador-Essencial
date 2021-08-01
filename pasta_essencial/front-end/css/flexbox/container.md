# :hammer_and_wrench:Flex Container
---
O Flex Container é a tag que envolve os itens flex, ao indicar display: flex, essa tag passa a ser um Flex Container.

---
## :hammer:Display

* Define o elemento como um flex container, tornando os seus filhos flex-itens.
* Os elementos flutuam como se fosse aplicar o comando `float left`, útil para alinhar os elementos em uma fileira.
* O Tamanho do item é exatamente o tamanho do conteúdo.

* `display: flex;`

  
  * Torna o elemento um flex container automaticamente transformando todos os seus filhos diretos em flex itens.

* Exemplo utilizando uma classe flex:
  ```css
  .flex {
    display: flex;
  }
  ```
* `flex-wrap`
  * Utilizado para definir a "quebra" do elemento, útil quando não cabe no container.

* Exemplo utilizando uma classe flex-wrap:

  ```css
  .flex-wrap {
    flex-wrap: wrap;
  }
  ```

* `flex: 1`
  * Utilizado para que os elementos ocupem o tamanho total do container, já que sem essa propriedade cada elemento terá o seu tamanho natural, podendo sobrar espaço indesejado do container.
* Exemplo utilizando uma classe de um item:
```css
.item {
  background: tomato;
  margin: 5px;
  text-align: center;
  font-size: 1.5em;
  flex: 1; /* propriedade para o item se dividir em tamanho proporcional ao container*/
}
```


