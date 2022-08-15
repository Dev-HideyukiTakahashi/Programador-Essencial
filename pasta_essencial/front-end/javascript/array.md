# 📋Dicas com Arrays :

---

### :gem:Arrays

- Algumas funções:

```javascript
const palavras = ["Mesa", "Cadeira", "Sofa", "Cama"];

console.log(palavras);
// Out: [ 'Mesa', 'Cadeira', 'Sofa', 'Cama' ]

palavras.push("Cortina"); // método para adicionar um elemento na última posição Array
console.log(palavras);
// Out: [ 'Mesa', 'Cadeira', 'Sofa', 'Cama', 'Cortina' ]

palavras.unshift("Unshift"); // método para adicionar um elemento na primeira posição Array
console.log(palavras);
// Out: [ 'Unshift', 'Mesa', 'Cadeira', 'Sofa', 'Cama', 'Cortina' ]

palavras.pop(); // método para remover o último elemento e a posição do Array
console.log(palavras);
// Out: [ 'Unshift', 'Mesa', 'Cadeira', 'Sofa', 'Cama' ]

palavras.shift(); // método para remover o primeiro elemento e a posição do Array
console.log(palavras);
// Out: [ 'Mesa', 'Cadeira', 'Sofa', 'Cama' ]

const palavras2 = palavras.slice(2); // método que "corta" um array para outro a partir do parâmetro, no exemplo a partir do índice 2 em diante
console.log(palavras2);
// Out: [ 'Sofa', 'Cama' ]
```

---

### :gem:ForEach

```javascript
const aprovados = ["Ana", "Maria", "João"];

// os parâmetros não são obrigatórios
aprovados.forEach(function (nome, indice) {
  console.log(`${indice}.${nome} foi aprovado`);
});

/*  OUT
0.Ana foi aprovado
1.Maria foi aprovado
2.João foi aprovado
*/

// Com arrow function
aprovados.forEach((nome) => console.log(`${nome} foi aprovado`));

/*  OUT
Ana foi aprovado
Maria foi aprovado
João foi aprovado
*/
```

---

### :gem:Map

```javascript
const nums = [1, 2, 3, 4, 5];

// Map : é como um 'foreach'cria um novo array com algum propósito//condição
// map pode receber 3 parâmetros
// (valor, indice, array)

/* let resultado = nums.map(function(elemento) {
    return elemento + 1;
});*/

let resultado = nums.map((elemento) => elemento + 10);

//Novo array somando +10 em cada elemento de nums
console.log(resultado);
// Out: [ 11, 12, 13, 14, 15 ]

const vezesDez = (e) => e * 10;
const paraReal = (e) => `R$ ${parseFloat(e).toFixed(2)} `;

//Encadeando map
console.log(nums.map(vezesDez).map(paraReal));
// Out :[ 'R$ 10.00 ', 'R$ 20.00 ', 'R$ 30.00 ', 'R$ 40.00 ', 'R$ 50.00 ' ]

//Array em formato JSON
const carrinho = [
  '{"nome": "Borracha","preco":3.45}',
  '{"nome": "Caderno","preco":13.90}',
  '{"nome": "Kit de Lapis","preco":41.22}',
  '{"nome": "Caneta","preco":7.50}',
];

//método para converter um array Json em obj com map
const paraObj = (json) => JSON.parse(json);
//método para mapear apenas o preço
const apeansPreco = (produto) => produto.preco;

const result = carrinho.map(paraObj).map(apeansPreco);
console.log(resultado);
// Out : [ 3.45, 13.9, 41.22, 7.5 ]
```

---

### :gem:Filter

```javascript
const produtos = [
  { nome: "Notebook", preco: 2499, fragil: true },
  { nome: "Ipad", preco: 4199, fragil: true },
  { nome: "Copo de vidro", preco: 12.49, fragil: true },
  { nome: "Copo de plastico", preco: 18.99, fragil: false },
];

// filtrando apenas produtos frágeis
console.log(produtos.filter((p) => p.fragil == false));
// Out: [ { nome: 'Copo de plastico', preco: 18.99, fragil: false } ]

const precoMenorCem = (p) => p.preco <= 100;
//criando outro array apenas com produtos com preço menor que 100
const produtosBaratos = produtos.filter(precoMenorCem);
console.log(produtosBaratos);
/* Out:
  { nome: 'Copo de vidro', preco: 12.49, fragil: true },
  { nome: 'Copo de plastico', preco: 18.99, fragil: false }
*/

//Aninhando com map
const vezesDez = (e) => e * 10;
const apenasPar = (e) => e % 2 == 0;
const nums = [1, 2, 3, 4, 5, 6];
console.log(nums.filter(apenasPar).map(vezesDez));
// Out : [ 20, 40, 60 ]
```

---

### :gem:Concat

```javascript
const nums1 = [1, 2, 3];
const nums2 = [6, 7, 8];

//método para concatenar 2 arrays
//o array original não é comprometido
const todos = nums1.concat(nums2);
console.log(todos);
// Out: [ 1, 2, 3, 6, 7, 8 ]

// pode-se passar ainda quantos parâmetros necessitar após o primeiro argumento
const todos2 = nums1.concat(nums2, 9, 10);
console.log(todos2);
// Out: [ 1, 2, 3, 6, 7, 8, 9, 10 ]
```

---

**Referência Origamid** :mega:[ https://www.origamid.com/](https://www.origamid.com/)
**Referência Cod3r** :mega:[ https://www.cod3r.com.br/](https://www.cod3r.com.br/)
