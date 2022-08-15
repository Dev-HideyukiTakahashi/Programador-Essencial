```javascript
const obj = {
  a: 1,
  b: 2,
  c: 3,
  // JSON não retorna função
  soma() {
    return a + b + c;
  },
};

//Transformando um obj em JSON
console.log(JSON.stringify(obj));

//Transformando um JSON em obj
//a chave precisa estar em aspas duplas obrigatoriamente, o valor apenas se for texto
console.log(JSON.parse('{"a":1, "b":2, "c":3}'));
console.log(JSON.parse('{"a":"texto", "b":true, "c":{}, "d":[]}'));

//Array em formato JSON
const carrinho = [
  '{"nome": "Borracha","preco":3.45}',
  '{"nome": "Caderno","preco":13.90}',
  '{"nome": "Kit de Lapis","preco":41.22}',
  '{"nome": "Caneta","preco":7.50}',
];

//método para converter um array Json em obj com map
const paraObj = (json) => JSON.parse(json);

const resultado = carrinho.map(paraObj);
console.log(resultado);
/* Out (retorna um Array de objetos) : [
{ nome: 'Borracha', preco: 3.45 }, 
{ nome: 'Caderno', preco: 13.9 }, 
{ nome: 'Kit de Lapis', preco: 41.22 }, 
{ nome: 'Caneta', preco: 7.5 }
// ***** Nota-se que não há aspas no campo chave, confirmando que não é mais um JSON
] */
```

**Site útil** :mega:[ JSON Validator](https://jsonlint.com/)
