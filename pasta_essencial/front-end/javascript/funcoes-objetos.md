# 📋Dicas com funções e objetos:

---

### :gem:Sintaxe exemplo 'Função'

#### Com argumentos:

```
function areaQuadrado(lado) {
  return lado * lado;
}
```

- Outline:

```
areaQuadrado(4) // 16
areaQuadrado(5) // 25
areaQuadrado(2) // 4
```

#### Atribuindo retorno a uma variável:

```javascript
function pi() {
return 3.14;
}

var total = 5 \* pi(); // 15.7
```

#### Retornando condicional:

```javascript
function corFavorita(cor) {
  if (cor === "azul") {
    return "Você gosta do céu";
  } else if (cor === "verde") {
    return "Você gosta de mato";
  } else {
    return "Você não gosta de nada";
  }
}
console.log(corFavorita()); // retorna 'Você não gosta de nada'
```

#### Argumento como função:

```javascript
addEventListener("click", function () {
  console.log("Clicou");
});
// A função possui dois argumentos
// Primeiro é a string 'click'
// Segundo é uma função anônima
```

---

### :gem:Sintaxe exemplo 'Objeto'

```javascript
var pessoa = {
  nome: "João",
  idade: 52,
  profissao: "Engenheiro de obras",
  possuiFaculdade: false,
};

pessoa.nome; // "João"
pessoa.possuiFaculdade; // false
```

#### Objeto com método:

```javascript
var quadrado = {
  lados: 4,
  function(lado) {
    return lado * lado;
  },
  function(lado) {
    return this.lados * lado;
  },
};

quadrado.lados; // 4
quadrado.area(5); // 25
quadrado.perimetro(5); // 20
```

---

**Referência Origamid** :mega:[ https://www.origamid.com/](https://www.origamid.com/)


