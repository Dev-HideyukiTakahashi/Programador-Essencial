# :hammer_and_wrench:Principais Tags
---
* Site recomendado para output dos códigos: https://codepen.io/pen/
---
## :hammer:Tags para textos:

```html
<!--Cabeçalhos-->
<h1>Cabeçalho principal</h1>
<h2>Cabeçalho nível 2</h2>
<h3>Cabeçalho nível 2</h3>
<h4>Cabeçalho nível 2</h4>
<h5>Cabeçalho nível 2</h5>
<h6>Cabeçalho nível 2</h6>

<!--Negrito e Itálico-->
<p>Texto em <b>Negrito</b> e <i>itálico</i></p>

<!--Parágrafo-->
<p>
    O Lorem Ipsum é um texto modelo da indústria tipográfica e de impressão. O Lorem Ipsum tem vindo a ser o texto padrão usado por estas indústrias desde o ano de 1500, quando uma misturou os caracteres de um texto para criar um espécime de livro.
</p>

<!--Sobrescrito e Subscrito-->
<p>2<sup>2</sup> = 4 e H<sub>2</sub>O = Água</p>
<p><sup>r$</sup>29,90</p>

<!--Quebra de linha-->
<p>Isso está <br> em uma nova linha</p>

<!--Quebra temática-->
<p>Segue abaixo uma quebra de linha</p>
<hr>
<p>Separado pela quebra de linha</p>

<!--Abreviações (passando o mouse em cima da palavra para aparecer a referência)-->
<p>
    <abbr title="Professor">Prof</abbr> Fulano em seu livro
    <cite>Livro legal</cite> disse alguma coisa.
</p>   

```
---
## :hammer:Tags para listas:

```html
<!--Lista Ordenada-->
<h2>Aprovados</h2>
<ol>
    <li>João</li>
    <li>Ana</li>
    <li>Maria</li>
    <li>Pedro</li>
</ol>

<!--Lista Não Ordenada-->
<h2>Lista de compras</h2>
<ul>
    <li>Quejo</li>
    <li>Presunto</li>
    <li>Pão</li>
    <li>Arroz</li>
</ul>
```
---
## :hammer:Tags para links:

```html
<!--URL absoluta-->
<a href="http://www.google.com.br">Google na mesma página</a>
<a href="http://www.google.com.br" target="_blank">Google em uma nova página</a>

<!--Navegando na mesma página-->
<div id="noticia" style="position: absolute; top: 2000px">
    <h1>Notícia bomba</h1>
</div>

```
---

## :hammer:Tags para tabelas:

```html
<!--Tabela-->
<table border="1">
<!--caption = título da tabela-->
<caption>Produtos</caption>
<!--thead = cabeçalho da tabela-->
<thead>
    <!--tr = table row / linha da tabela -->
    <tr>
    <!--th = colunas da linha da tabela-->
    <th>Produto</th>
    <th>Preco</th>
    <th>Quantidade</th>
    <th>Total</th>
    </tr>
</thead>
<!--Corpo da tabela-->
<tbody>
    <tr>
    <!--Table data, dado da tabela na mesma ordem-->
    <td>iPad</td>
    <td>3289,0</td>
    <td>5</td>
    <td>16445,00</td>
    </tr>
    <tr>
    <!--Table data, dado da tabela na mesma ordem-->
    <td>Sansung S9</td>
    <td>2649,00</td>
    <td>8</td>
    <td>21192,00</td>
    </tr>
</tbody>
<!--tfoot = corpo final da tabela-->
<tfoot>
    <tr>
    <!--colspan = tamanho em colunas que esse td vai ter-->
    <!--rowspan = tamanho em linhas que esse td vai ter-->
    <td colspan="3">Total</td>
    <td>37637,00</td>
    </tr>
</tfoot>
```
---

## :hammer:Tags para formulário:
```html
<!--Formulário-->
<form action="enviar.php" method="POST" name="form">
    <div>
        <label for="nome">Nome</label>
        <input type="text" id="nome" required >
    </div>
    <div>
        <label for="email">Email</label>
        <input type="text" id="email" required >
    </div>
    <div>
        <label for="mensagem">Mensagem</label>
        <textarea name="mensagem" id="mensagem" cols="30" rows="10" required>Digite o texto aqui</textarea>
        <button id="enviar" name="enviar" type="submit">Solicitar orçamento</button>
    </div>
</form>
```

---

## :hammer:Tags para img:
```html
<!--Imagens // Absoluta e relativa-->
<img src="https://https://www.google.com.br/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Google">
<img src="imagem-teste.png" alt="Imagem de alguma pasta no projeto">
```

---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)