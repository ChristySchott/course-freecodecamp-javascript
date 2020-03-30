## ES6

#### Let e Const
Um dos maiores problemas de se declarar variavéis com o prefixo *var* é o fato dela pode ser sobreescrita. Uma nova keyword foi introduzida no ES6, a **let**. Usando a let não é possível declarar um novo valor para a variável. Veja o exemplo:
```
let camper = 'James';
let camper = 'David'; // throws an error
```
Além disso, ao declarar uma variável local com a keyword let, não é possível usá-la globalmente. Logo, se eu tiver mais de um *for* no meu código, em diferentes funções, posso declarar um *let i =0*, dentro de cada um, sem medo dela ser sobreescrita.

No ES6 também é possível declarar uma variável usando a keyword ***const*** . Ela tem a mesma característica da keyword let, mas ela serve apenas para leitura. 

> "They are a constant value, which means that once a variable is assigned with const, it cannot be reassigned."

OBS: É uma convenção nomear as variáveis const com CAPSLOCK.

A maioria dos desenvolvedores hoje em dia prefere declarar todas as variáveis como const, modificando para let apenas aquelas cujo valor será modificado.

Entretanto, é importante entender que os objetos (arrays e functions) atribuidos a variáveis const podem ser modificados. Segue exemplo:

```
const s = [5, 6, 7];
s = [1, 2, 3]; // throws error, trying to assign a const
s[2] = 45; // works just as it would with an array declared with var or let
console.log(s); // returns [5, 6, 45]
```

#### Prevent Object Mutation

Como vimos, só a leyword const não previne que o objeto sofra mutação, para isso podemos utilizar a função Object.freeze:

```
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad"; // will be ignored. Mutation not allowed
obj.newProp = "Test"; // will be ignored. Mutation not allowed
console.log(obj); 
// { name: "FreeCodeCamp", review:"Awesome"}
```
