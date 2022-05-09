# 📋Dicas Javascript:

---

### :gem:DOM

- É uma interface que representa documentos HTML e XML através de objetos. Com ela é possível manipular a estrutura, estilo e conteúdo destes documentos.

* Ao inspecionar elemento com o Chrome, você está vendo a representação oficial do DOM.

---

#### Seleção de Elementos

- ID

```javascript
// Seleciona pelo ID
const animaisSection = document.getElementById("animais");
const contatoSection = document.getElementById("contato");

// Retorna null caso não exista
const naoExiste = document.getElementById("teste");
```

- CLASSE E TAG

```javascript
// Seleciona pela classe, retorna uma HTMLCollection
const gridSection = document.getElementsByClassName("grid-section");
const contato = document.getElementsByClassName("grid-section contato");

// Seleciona todas as UL's, retorna uma HTMLCollection
const ul = document.getElementsByTagName("ul");

// Retorna o primeiro elemento
console.log(gridSection[0]);
```

- SELETOR GERAL ÚNICO

```javascript
const animais = document.querySelector(".animais");
const contato = document.querySelector("#contato");
const ultimoItem = document.querySelector(".animais-lista li:last-child");
const linkCSS = document.querySelector('[href^="https://"]');
const primeiroUl = document.querySelector("ul");

// Busca dentro do Ul apenas
const navItem = primeiroUl.querySelector("li");
```

- SELETOR GERAL LISTA

  - querySelectorAll retorna todos os elementos compatíveis com o seletor CSS em uma NodeList

```javascript
const gridSection = document.querySelectorAll(".grid-section");
const listas = document.querySelectorAll("ul");
const titulos = document.querySelectorAll(".titulo");
const fotosAnimais = document.querySelectorAll(".animais-lista img");

// Retorna o segundo elemento
console.log(gridSection[1]);
```

- HTMLCOLLECTION VS NODELIST
  - A diferença está nos métodos e propriedades de ambas. Além disso a NodeList retornada com querySelectorAll é estática.

```javascript
const titulo = document.querySelector(".titulo");
const gridSectionHTML = document.getElementsByClassName("grid-section");
const gridSectionNode = document.querySelectorAll(".grid-section");

titulo.classList.add("grid-section");

console.log(gridSectionHTML); // 4 itens
console.log(gridSectionNode); // 3 itens
```

- ARRAY-LIKE

  - HTMLCollection e NodeList são array-like, parecem uma array mas não são. O método de Array forEach() por exemplo, existe apenas em NodeList.

  * É possível transformar array-like em uma Array real, utilizando o método Array.from(gridSection)

```javascript
const gridSection = document.querySelectorAll(".grid-section");

gridSection.forEach(function (gridItem, index, array) {
  gridItem.classList.add("azul");
  console.log(index); // index do item na array
  console.log(array); // a array completa
});
```

---

#### Classes e Atributos

- CLASSLIST
  - Retorna uma lista com as classes do elemento. Permite adicionar, remover e verificar se contém.

```javascript
const menu = document.querySelector(".menu");

menu.className; // string
menu.classList; // lista de classes
menu.classList.add("ativo");
menu.classList.add("ativo", "mobile"); // duas classes
menu.classList.remove("ativo");
menu.classList.toggle("ativo"); // adicionas e não tem/remove a classe se tem
menu.classList.contains("ativo"); // true ou false
menu.classList.replace("ativo", "inativo");
```

- ATTRIBUTES
  - Retorna uma array-like com os atributos do elemento.

```javascript
const animais = document.querySelector(".animais");

animais.attributes; // retorna todos os atributos
animais.attributes[0]; // retorna o primeiro atributo
```

- GETATTRIBUTE E SETATTRIBUTE
  - Métodos que retornam ou definem de acordo com o atributo selecionado

```javascript
const img = document.querySelector("img");

img.getAttribute("src"); // valor do src
img.setAttribute("alt", "Texto Alternativo"); // muda o alt
img.hasAttribute("id"); // true / false
img.removeAttribute("alt"); // remove o alt

img.hasAttributes(); // true / false se tem algum atributo
```

- READ ONLY VS WRITABLE

```javascript
const animais = document.querySelector(".animais");

animais.className; // string com o nome das classes
animais.className = "azul"; // substitui completamente a string
animais.className += " vermelho"; // adiciona vermelho à string

animais.attributes = 'class="ativo"'; // não funciona, read-only
```

---

#### Dimensões e Distâncias

- HEIGHT E WIDTH
  - Mesmos comandos para o Width, clientWidth ...

```javascript
const section = document.querySelector(".animais");

section.clientHeight; // height + padding
section.offsetHeight; // height + padding + border
section.scrollHeight; // height total, mesmo dentro de scroll
```

- OFFSETTOP E OFFSETLEFT

const section = document.querySelector('.animais');

```javascript
// Distância entre o topo do elemento e o topo da página
section.offsetTop;

// Distância entre o canto esquerdo do elemento
// e o canto esquerdo da página
section.offsetLeft;
```

- GETBOUNDINGCLIENTRECT()
  - Método que retorna um objeto com valores de width, height, distâncias do elemento e mais.

```javascript
const section = document.querySelector(".animais");

const rect = section.getBoundingClientRect();
rect.height; // height do elemento
rect.width; // width do elemento
rect.top; // distância entre o topo do elemento e o scroll
```

- WINDOW

```javascript
window.innerWidth; // width do janela
window.outerWidth; // soma dev tools também
window.innerHeight; // height do janela
window.outerHeight; // soma a barra de endereço

window.pageYOffset; // distância total do scroll vertical
window.pageXOffset; // distância total do scroll horizontal

if (window.innerWidth < 600) {
  console.log("Tela menor que 600px");
}
//OBS: caso necessário pode usar 'onload' para itens mais 'lentos' de carregar, exemplo imagens que carregam só depois do js carregar e podem retornar valores 0 por esse motivo
window.onload = function () {
  imagens.forEach((img) => {
    console.log(img.offsetWidth);
  });
  //a função só executa depois de carregar todas imagens
};
```

- MATCHMEDIA();

```javascript
const small = window.matchMedia("(max-width: 600px)");

if (small.matches) {
  console.log("Tela menor que 600px");
} else {
  console.log("Tela maior que 600px");
}
```

---

#### Eventos

- ADDEVENTLISTENER

  - Adiciona uma função ao elemento, esta chamada de callback, que será ativada assim que certo evento ocorrer neste elemento.
  - O terceiro parâmetro é opcional.

```javascript
const img = document.querySelector("img");

// elemento.addEventListener(event, callback, options)
img.addEventListener("click", function () {
  console.log("Clicou");
});
```

- CALLBACK
  - É boa prática separar a função de callback do addEventListener, ou seja, declarar uma função ao invés de passar diretamente uma função anônima

```javascript
const img = document.querySelector("img");
function callback() {
  console.log("Clicou");
}

img.addEventListener("click", callback); // 🚀
img.addEventListener("click", callback()); // undefined
img.addEventListener("click", function () {
  console.log("Clicou");
});
img.addEventListener("click", () => {
  console.log("Clicou");
});
```

- Events

```javascript
animaisLista.addEventListener("click", (event) => {
  const currentTarget = event.currentTarget; // this
  const target = event.target; // onde o clique ocorreu
  const type = event.type; // tipo de evento
  const path = event.path;
  console.log(currentTarget, target, type, path);
});
```

- DIFERENTES EVENTOS

```javascript
const h1 = document.querySelector("h1");

function callback(event) {
  console.log(event.type, event);
}

h1.addEventListener("click", callback);
h1.addEventListener("mouseenter", callback);
window.addEventListener("scroll", callback);
window.addEventListener("resize", callback);
window.addEventListener("keydown", callback);
```

KEYBOARD

- Você pode adicionar atalhos para facilitar a navegação no seu site, através de eventos do keyboard.

```javascript
window.addEventListener("keydown", (event) => {
  if (event.key == "f") {
    document.body.classList.toggle("fullscream");
    // ao apertar 'f' no teclado adiciona a classe fullscream no body caso não exista caso contrário remove
  }
});
```

---

#### Exemplos:

```javascript
console.log(window);
// window é o objeto global do browser
// possui diferentes métodos e propriedades

window.innerHeight; // retorna a altura do browser

const url = window.location.href; // retorna a url da página

window.alert("Isso é um alerta"); // window é o objeto global
alert("Isso é um alerta"); // Funciona
```

- Toda tag html é representada pelo objeto Element e por isso herda os seus métodos e propriedades.

```html
<!--código html-->
<h1 class="titulo-principal">Esse é o título</h1>
<p class="ativo">Sou da class ativo</p>
```

```javascript
const classeSelecionada = document.querySelector(".ativo"); // busca a primeira classe que contenha 'ativo'
console.log(classeSelecionada); // p.ativo

const titulo = document.querySelector("h1");

titulo.innerText; // retorna o texto;
titulo.classList; // retorna as classes;
titulo.id; // retorna o id;
titulo.offsetHeight; // retorna a altura do elemento;

function callback() {
  console.log("clicou em mim");
}

titulo.addEventListener("click", callback);
// ativa a função callback ao click no titulo
```

---

**Referência Origamid** :mega:[ https://www.origamid.com/](https://www.origamid.com/)
