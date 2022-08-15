# 📋Dicas com tipos de variáveis:

---

### :gem:String

---

#### Algumas dicas

```javascript
const curso = "javascript";

//Seleciona o caractere na posição 2 da String
console.log(curso.charAt(2));
//Seleciona os caracteres a partir da posição 3 da String, incluindo a posição 3
console.log(curso.substring(3));
//Seleciona do indice 0 até o índice 3, sem incluir o 3 índice('a')
console.log(curso.substring(0, 3));
//Podemos utilizar uma String literal sem necessariamente ter uma variável para utilizar seus métodos
console.log("Curso".concat(" " + curso));
```

```
v
ascript
jav
Curso javascript
```

---

### :gem:Operadores matemáticos

---

#### Função para limitar número float

```javascript
var precoTotal = 20 / 2.55;

console.log(precoTotal);
//Passamos como parâmetro o número de casas para formatar
console.log(precoTotal.toFixed(2));
```

- Outline:
  `7.843137254901961`
  `7.84`

---

#### Uma concatenação de String com Number retorna uma String

```javascript
var idade = 50,
  nome = "Maria";
var total = nome + idade;
console.log(typeof total);
```

- Outline:
  `string`

---

#### Conversão de String para Number

- Basta adicionar o sinal de adição(+) na frente da String(que contenha apenas números).

```javascript
var idade = +"50";
console.log(typeof idade);
console.log(idade);
```

- Outline:

```
number
50
```

```javascript
var idade = +"50a";
console.log(typeof idade);
console.log(idade);
```

- Outline:

```
number
NaN (Not a Number)
```

- Obs: existe a função **isNaN()** para verificar se uma variável é um number ou não, retornando false se for um number.

```javascript
var divisao = "Divide 10" / 2;
console.log(isNaN(divisao));
```

- Outline:

`true`

---

### Arredondado números:

- **toFixed()**

```javascript
var x = 1.4;
var y = 1.6;

console.log("Valor de 'x' arredondado: " + x.toFixed());
console.log("Valor de 'y' arredondado: " + y.toFixed());
```

- Outline:

```
Valor de 'x' arredondado: 1
Valor de 'y' arredondado: 2
```

```javascript
function fixarValor(a) {
  console.log(`R$ ${a.toFixed(2).replace(".", ",")}`);
}

fixarValor(0.30000000000000004);
```

- Outline:

```
R$ 0,30
```

---

### :gem:Boolean

---

### Valores que retornam false:

```

if(false)
if(0) // ou -0
if(NaN)
if(null)
if(undefined)
if('') // ou "" ou ``

```

---

**Referência Origamid** :mega:[ https://www.origamid.com/](https://www.origamid.com/)
**Referência Cod3r** :mega:[ https://www.cod3r.com.br/](https://www.cod3r.com.br/)
