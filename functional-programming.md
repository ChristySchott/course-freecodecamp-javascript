# Functional Programming

A programação funcional segue alguns princípios fundamentais:

- As funções são independentes do estado do programa ou das variáveis globais. Elas dependem apenas dos argumentos passados para fazer um cálculo
- As funções tentam limitar quaisquer alterações no estado do programa e evitar alterações nos objetos globais que contêm dados.
- Funções têm efeitos colaterais mínimos no programa.

A programação funcional é sobre:

1) Funções isoladas - não há dependência do estado do programa, que inclui variáveis globais sujeitas a alterações

2) Funções puras - a mesma entrada sempre dá a mesma saída

3) Funções com efeitos colaterais limitados - quaisquer alterações ou mutações no estado do programa fora da função são cuidadosamente controladas

Um dos princípios da Programação Funcional, é diminuir o número de variáveis globais para evitar a mutação num array.
Perceba como mudamos:
```
var fixedValue = 4;

function incrementer () {
  return fixedValue += 1;
}
```
Estamos perto de um código com Programação Funcional, mas não chegamos la ainda. Por quê? Bom, não alteramos o valor da variável global, porém, sem ela fixada no escopo global não conseguíriamos utilizar a função incrementer.

Outro princípio da programação funcional é sempre declarar explicitamente suas dependências. Isso significa que se uma função depende da presença de uma variável ou objeto, passe essa variável ou objeto diretamente para a função como argumento.

Vamos atualizar a função incrementer para declarar claramente suas dependências.Ela um argumento e, em seguida, aumentar o valor em um.

```
var fixedValue = 4;

function incrementer (arg) {
  arg = fixedValue;
  return arg += 1;

}
```

Até agora, vimos dois princípios distintos para a programação funcional:

1. Não altere uma variável ou objeto - crie novas variáveis ​​e objetos e retorne-os, se necessário, a partir de uma função.
2. Declarar argumentos da função - qualquer cálculo dentro de uma função depende apenas dos argumentos, e não de qualquer objeto ou variável global.

####  Use the map Method to Extract Data from an Array

Map é um dos recursos mais incríveis da Programação Funcional. O método é invocado a partir de um array e recebe como parâmetro uma função de callback, que é invocada para cada item e retorna o valor do item equivalente no array resultante.
Aqui é importante destacar que o método map() não modifica o array original, ele retorna um novo array com os itens resultantes do mapeamento.

Sintaxe:

> arrayOriginal.map(callback)

callback é uma função que será executada para cada elemento no vetor original e retornará uma representação dele com base em alguma lógica, que será o item equivalente no vetor resultante. Sua estrutura é a seguinte:

> function(valorAtual, indice, array)

- O parâmetro valorAtual é obrigatório e representa o próprio item da iteração atual. Ou seja, à medida que a função map itera sobre o array, esse parâmetro receberá cada item.
- O parâmetro indice é opcional e representa o índice do item da iteração atual.
- O parâmetro array também é opcional e representa o próprio array ao qual os itens pertencem.

 usar o recurso de arrow functions, do ECMAScript 6, para definir a função de callback com uma sintaxe mais simples:
 ```
var quadrados = [25, 16, 9, 4, 1];
  
var raizes = quadrados.map(numero => Math.sqrt(numero));
  
document.write(raizes); 
```

Essa parte inicial do método Map() eu peguei do site da [DevMedia](https://www.devmedia.com.br/javascript-map-mapeando-elementos-de-um-array/40648), recomendo darem uma olhada.

Outro exemplo: 
```
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const names = users.map(user => user.name);
console.log(names); // [ 'John', 'Amy', 'camperCat' ]
```

#### Use the filter Method to Extract Data from an Array

O método  filter() vai percorrer cada elemento de um array e colocar, em um novo array, os elementos que retornam TRUE, de acordo com a função especificada no nosso filtro.

Para ficar mais claro, vamos usar um exemplo. Imagine o seguinte array:
```
const people = [
    { name: 'Carlos', age: 28 },
    { name: 'Henrique', age: 22 },
    { name: 'João', age: 27 },
    { name: 'Paulo', age: 30}
]
````
Agora, vamos usar a função  filter() para percorrer o array e retornar, em um novo array, todo mundo que tenha mais de 22 anos.

Para isso vamos definir uma nova variável, chamada  newArray e como valor inicial da mesma, vamos passar o retorno da nossa função  filter(). Ou seja, nosso novo array, vai ser composto de todo mundo, no array antigo, com mais de 22 anos.

> const newArray = people.filter(person => person.age > 22);

---------

O método filter() cria um novo array com todos os elementos que passaram no teste implementado pela função fornecida.
```
function isBigEnough(value) {
  return value >= 10;
}

var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtrado é [12, 130, 44]
```


