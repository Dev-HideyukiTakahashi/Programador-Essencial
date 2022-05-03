# 📋Dicas com tipos de variáveis:

---

### :gem:Operadores matemáticos

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

