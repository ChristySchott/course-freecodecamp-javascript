## ES6 É TUDO DE BOM!!!

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

#### Usando Arrow Functions

No JavaScript, as vezes não precisamos nomear nossas funções, pois não iremos reutilizá-las. Para isso utilizamos a seguinte sintaxe:

```
const myFunc = function() {
  const myVar = "value";
  return myVar;
}
```

Com o advento do ES6, podemos utilizar a seguinte sintaxe:

```
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```

E como só retornaremos um valor, podemos diminuir ainda mais:

> const myFunc = () => "value";

Caso eu precise passar parâmetros para  a função, basta colocar entre os parenteses:

> const myFunc = (num1,num1) => console.log(num1,num2);

Caso haja apenas um parâmetro, deixo sem os parenteses:

> const myFunc = num1 => console.log(num1);

Utilizarei muito menos linhas de código no meu programa!


####  Set Default Parameters for Your Functions

Outra inovação do ES6 que facilita muito a vida do programador. Esse valor Default se refere a quando um argumento de um parâmetro não é especificado, então tenho que usar um valor ja definido. Veja o exemplo:
```
const greeting = (name = "Anonymous") => "Hello " + name;

console.log(greeting("John")); // Hello John
console.log(greeting()); // Hello Anonymous
```
Na ultima linha eu não passei um argumento para o parâmetro, então o JS usou o vaor que eu havia definido para a variável nome.

#### Use the Rest Parameter with Function Parameters

Para podermos criar funções mais flexíveis, o ES6 introduziu o *rest parameter*. Com ele, posso criar uma função com um nome variável de argumentos. Esse argumentos são armazenados num array e podem ser utilizados posteriiormente.

Veja o exemplo:
```
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2)); // You have passed 3 arguments.
console.log(howMany("string", null, [1, 2, 3], { })); // You have passed 4 arguments.
```

#### Use Destructuring Assignment to Extract Values from Objects

É uma sintaxe usada para atribuir ordenadamente valores obtidos diretamente de um objeto.

Confira o código do ES5:
```
const user = { name: 'John Doe', age: 34 };

const name = user.name; // name = 'John Doe'
const age = user.age; // age = 34
```

Veja o mesmo código, agora no ES6:

```
const user = { name: 'John Doe', age: 34 };

const { name, age } = user;
```

####  Use Destructuring Assignment to Assign Variables from Objects

A reestruturação permite atribuir um novo nome de variável ao extrair valores. Você pode fazer isso colocando o novo nome após dois pontos ao atribuir o valor.

Vamos usar o mesmo objeto do código acima (const user = { name: 'John Doe', age: 34 };).

Veja como você pode dar novos nomes de variáveis na atribuição:
```
const { name: userName, age: userAge } = user;
// userName = 'John Doe', userAge = 34
```
Você pode lê-lo como "obtenha o valor de user.name e atribua-o a uma nova variável chamada userName" e assim por diante.


#### Use Destructuring Assignment to Assign Variables from Arrays


O ES6 torna as matrizes de desestruturação tão fáceis quanto os objetos de desestruturação.

```
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b); // 1, 2
```

A variável a recebe o primeiro valor da matriz e b o segundo valor da matriz. Também podemos acessar o valor em qualquer índice de uma matriz com desestruturação usando vírgulas para alcançar o índice desejado:

```
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c); // 1, 2, 5
```

#### Use Destructuring Assignment with the Rest Parameter to Reassign Array Elements
```
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b); // 1, 2
console.log(arr); // [3, 4, 5, 7]
```
As variáveis a e b recebem o primeiro e o segundo valores da matriz. Depois disso, devido à presença do parâmetro rest, arr obtém o restante dos valores na forma de uma matriz.

#### Use Destructuring Assignment to Pass an Object as a Function's Parameters

Veja o código abaixo:
```
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;
  // do something with these variables
} 
```
Isso efetivamente desestrutura o objeto enviado para a função. Isso também pode ser feito no local:
```
const profileUpdate = ({ name, age, nationality, location }) => {
  /* do something with these fields */
}
```

Isso acaba diminuindo o número de linhas, fator essencial para um código limpo.

#### Create Strings using Template Literals

 Esse é um tipo especial de string que facilita a criação de strings complexos.

Os templates model permitem criar sequências de várias linhas e usar recursos de interpolação de sequências para criar sequências.

Veja o código abaixo:
```
const person = {
  name: "Zodiac Hasbro",
  age: 56
};

// Template literal com multi-linha e interpolação de string
const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting); // prints
// Hello, my name is Zodiac Hasbro!
// I am 56 years old.
```

Muitas coisas aconteceram lá. Primeiramente, o exemplo usa reticulares **(`)**, não aspas ('ou"), para quebrar a cadeia.

A sintaxe ${variavel} usada acima é um placeholder. Basicamente, você não precisará mais usar a concatenação com o operador +. Para adicionar variáveis às strings, basta soltar a variável em uma string de modelo e envolvê-la com $ { e }.

Você pode incluir outras expressões em sua string literal, por exemplo $ {a + b}.
