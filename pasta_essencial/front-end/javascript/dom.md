# 📋Dicas DOCUMENT OBJECT MODEL (DOM):

---

### :gem:DOM

- É uma interface que representa documentos HTML e XML através de objetos. Com ela é possível manipular a estrutura, estilo e conteúdo destes documentos.

* Ao inspecionar elemento com o Chrome, você está vendo a representação oficial do DOM.

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
