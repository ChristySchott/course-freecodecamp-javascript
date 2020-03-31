#### Basic Data Structure Challenges

O assunto abordado aqui não é novidade para quem chegou nessa parte do curos, pois já utilizamos as estruturas apresentadas nos exercícios dos módulos anteriores. Aqui porém, vamos mais fundo na explicação de assuntos como declaração e manipulação de arrays.

#### Remove Items from an Array with pop() and shift()

Tanto push () quanto unshift () têm métodos correspondentes que são opostos quase funcionais: pop () e shift (). Como você já deve ter adivinhado, em vez de adicionar, pop () remove um elemento do final de uma matriz, enquanto shift () remove um elemento desde o início. A principal diferença entre pop () e shift () e seus primos push () e unshift () é que nenhum dos métodos aceita parâmetros e cada um permite apenas que uma matriz seja modificada por um único elemento de cada vez.

#### Remove Items Using splice()

 Splice () nos permite remover qualquer número de elementos consecutivos de qualquer lugar em uma matriz.

splice () pode levar até 3 parâmetros, mas, por enquanto, focaremos apenas os dois primeiros. Os dois primeiros parâmetros de splice () são números inteiros que representam índices ou posições da matriz que splice () está sendo chamado.  splice () representa o índice na matriz da qual começar a remover elementos, enquanto o segundo parâmetro indica o número de elementos a serem excluídos. Por exemplo:
```
let array = ['today', 'was', 'not', 'so', 'great'];

array.splice(2, 2);
// remove 2 elements beginning with the 3rd element
// array now equals ['today', 'was', 'great']
```

Também posso usar o splice() para devolver o conteúdo que recortei:
```
let array = ['I', 'am', 'feeling', 'really', 'happy'];

let newArray = array.splice(3, 2);
// newArray equals ['really', 'happy']

```

#### Add Items Using splice()

Você pode usar o terceiro parâmetro, composto por um ou mais elementos, para adicionar à matriz. Isso pode ser incrivelmente útil para trocar rapidamente um elemento, ou um conjunto de elementos, por outro.
```
const numbers = [10, 11, 12, 12, 15];
const startIndex = 3;
const amountToDelete = 1;

numbers.splice(startIndex, amountToDelete, 13, 14);
// the second entry of 12 is removed, and we add 13 and 14 at the same index
console.log(numbers);
// returns [ 10, 11, 12, 13, 14, 15 ]
```
#### Combine Arrays with the Spread Operator

Outra grande vantagem do operador spread, é a capacidade de combinar matrizes ou inserir todos os elementos de uma matriz em outra, em qualquer índice. Com sintaxes mais tradicionais, podemos concatenar matrizes, mas isso só nos permite combinar matrizes no final de uma e no início de outra. A sintaxe de propagação torna a seguinte operação extremamente simples:
```
thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];

let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
// thatArray now equals ['basil', 'cilantro', 'sage', 'rosemary', 'parsley', 'thyme', 'coriander']
```

#### Check For The Presence of an Element With indexOf()

Como os arrays podem ser alteradas ou mutadas a qualquer momento, não há garantia sobre onde um determinado dado estará em uma determinada matriz ou se esse elemento ainda existe. Felizmente, o JavaScript nos fornece outro método interno, indexOf (), que permite verificar rápida e facilmente a presença de um elemento em uma matriz. indexOf () usa um elemento como parâmetro e, quando chamado, retorna a posição ou índice desse elemento ou -1 se o elemento não existir na matriz.

Por exemplo:
```
let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

fruits.indexOf('dates'); // returns -1
fruits.indexOf('oranges'); // returns 2
fruits.indexOf('pears'); // returns 1, the first index at which the element exists
```

Exercício que respondi:

indexOf() can be incredibly useful for quickly checking for the presence of an element on an array. We have defined a function, quickCheck, that takes an array and an element as arguments. Modify the function using indexOf() so that it returns true if the passed element exists on the array, and false if it does not.
```
function quickCheck(arr, elem) {
  if(arr.indexOf(elem) >= 0){ //note que se o index for negativo, não existe
    return true;
  } else {
    return false;
  }
}

console.log(quickCheck(['squash', 'onions', 'shallots'], 'mushrooms'));

```
