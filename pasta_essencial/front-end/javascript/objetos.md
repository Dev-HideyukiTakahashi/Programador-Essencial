# 📋Dicas com objetos :

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

#### Construtores:

- Sintaxe

```javascript
function Carro() {
  this.marca = "Marca"; // atributo público
  this.preco = 0; // atributo público
}

const honda = new Carro();
honda.marca = "Honda";
honda.preco = 4000;

console.log(honda);
//Carro {marca: 'Honda', preco: 4000}
```

- Parâmetros

```javascript
function Dom(seletor) {
  const element = document.querySelector(seletor);
  this.ativo = function (classe) {
    element.classList.add(classe);
  };
}

const lista = new Dom("ul");
lista.ativo("ativo");

const lastLi = new Dom("li:last-child");
lastLi.ativo("ativo");
```

---

### :gem:Getter/Setter

```javascript
const sequencia = {
  _valor: 1, // convenção usar o underline para explicitar o acesso apenas interno
  get valor() {
    return this._valor++;
  },
  set valor(valor) {
    this._valor = valor;
  },
};

console.log(sequencia.valor, sequencia.valor); // utilizando getter
// Output: 1 2
sequencia.valor = 10; // utilizando setter
console.log(sequencia.valor, sequencia.valor); // utilizando getter
```

- Por conveção o js entende que ao acessar o método é um get e ao atribuir é um set.

---

### :gem:ForEach

- Sintaxe exemplo:
  - É possível passar nos argumentos (item, index, array).

```javascript
const imagens = document.querySelectorAll("img"); // seleciona todas 'img' que estão no html

imgs.forEach(function (item) {
  console.log(item);
}); // imprime cada item(nome genérico) da 'lista'

imgs.forEach((item) => {
  console.log(item);
}); // mesma função com programação funcional
```

---

### :gem:Classes

```javascript
//Sintaxe
class objeto {
  constructor(nome = "generico", valor = 0) {
    this.nome = nome;
    this.valor = valor;
  }
  descricao() {
    return console.log(`Nome: ${this.nome} Valor: ${this.valor}`);
  }
}

const produto = new objeto("carro", 200000);
console.log(produto);
produto.descricao();

//Output: objeto { nome: 'carro', valor: 200000 }
//Output: Nome: carro Valor: 200000

//Herança

class Avo {
  constructor(sobrenome) {
    this.sobrenome = sobrenome;
  }
}

class Pai extends Avo {
  constructor(sobrenome, profissao = "Professor") {
    super(sobrenome);
    this.profissao = profissao;
  }
}

class Filho extends Pai {
  constructor() {
    super("Silva");
  }
}

const filho = new Filho();
console.log(filho);

// Output: Filho { sobrenome: 'Silva', profissao: 'Professor' }
```

---

**Referência Origamid** :mega:[ https://www.origamid.com/](https://www.origamid.com/)
**Referência Cod3r** :mega:[ https://www.cod3r.com.br/](https://www.cod3r.com.br/)
