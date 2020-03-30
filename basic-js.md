

## Basic JavaScript

A partir do nome do módulo é possível raciocinar que se trata de uma introdução a linguagem. Como ja tenho uma boa base de outros cursos de JS, aproveitei pouca coisa, mas foi ótimo para lembrar dos conteúdos, pois o conteúdo é bem completo e enxuto.
O modulo possui 110 exercícios com uma breve explicação do conteúdo ao lado, um ponto forte do curso. Pôr em prática o conhecimento é essencial para fixar o resultado. Colocarei apenas alguns códigos que eu fiz e me ajudaram a lembrar de determinados assuntos.


Neste exemplo eu acessei a propriedade de um objeto com uma variável:
```
var testObj = {
  12: "Namath",
  16: "Montana",
  19: "Unitas"
};


var playerNumber = 16;       
var player = testObj[playerNumber];   // Change this line
```

Neste outro eu atribuí um novo valor a uma propriedade de um objeto:
```
var myDog = {
  "name": "Coder",
  "legs": 4,
  "tails": 1,
  "friends": ["freeCodeCamp Campers"]
};


myDog.name = "HappyCoder";
```

Removendo uma propriedade de um objeto:
```
var myDog = {
  "name": "Happy Coder",
  "legs": 4,
  "tails": 1,
  "friends": ["freeCodeCamp Campers"],
  "bark": "woof"
};

delete myDog.tails;
```

Testando se objeto possui uma determinada propriedade:

```
var myObj = {
  top: "hat",
  bottom: "pants"
};
myObj.hasOwnProperty("top");   //true
myObj.hasOwnProperty("middle"); //false

OU:

function checkObj(obj, checkProp) {
  if(obj.hasOwnProperty(checkProp)) {
    return obj[checkProp];
  } else {
    return "Not Found";
  }
}
```

Acessando Objetos Aninhados:

Irei pegar a propriedade *glove box*:

```
var myStorage = {
  "car": {
    "inside": {
      "glove box": "maps",
      "passenger seat": "crumbs"
     },
    "outside": {
      "trunk": "jack"
    }
  }
};

var gloveBoxContents = myStorage.car.inside['glove box'];
```
**Como o gloce box possui um espaço entre as palavras, eu coloco entre []**

Acessando valores de um array com um loop:

```
var myArr = [ 2, 3, 4, 5, 6];

var total = 0;
for(var i = 0; i < myArr.length; i ++){
 total += myArr[i];
}

```

Profile lookUp:

Pesquisarei dentro do array contacts se possui o nome e a propriedade informa na função.
```
function lookUpProfile(name, prop){

for(var i =0; i<contacts.length; i++){  // percorro todo array
if (contacts[i].firstName === name){   // confro se há o nome informado em alguma posição
    if (contacts[i].hasOwnProperty(prop)){ // caso haja, eu procuro se aquela posição tem uma propriedade
    return contacts[i][prop]; // se ela tiver eu retorno essa propriedade
    }
 else {
    return "No such property"; // caso não tenha eu retorno que não tem
   }
  }
 }
    return "No such contact"; // caso não não haja o nome ele retorna isso
 }


```

Gerando um valor aleatório entre 0 e 9:

Devo fazer o seguinte:
- Usar Math.random() para um valor decimal aleatório;
- Multiplicar o Math.random() por 10;
- Usar o Math.floor para arrendodar o valor para para baixo.

Como estou usando Math.floor(), que arredonda para baixo, não poderei obter o 10, logo minhas possibilidades ficam entre 0 a 9.

O código ficará assim
> Math.floor(Math.random() * 10);


Gerando um valor aleatório entre numeros especificados:

Para fazer isso temos que definir um máximo e um mínimo, usando a seguinte sintaxe:

> Math.floor(Math.random() * (max - min + 1)) + min


A função parseInt() converte uma string para um inteiro, como no exemplo:

> var a = parseInt("007");

Iremos obter um valor inteiro de 007. Caso o primeiro valor não posso ser convertido para inteiro a função irá retornar NaN.

Também posso converter o número e retornar ele como binário, usando a sintaxe:

> var a = parseInt("11",2);


Operadores ternários multiplos condicionais.

Uma técnica que possibilita tornar o código muito mais enxuto e légivel, veja no exemplo:

O seguinte código

```
function findGreaterOrEqual(a, b) {
  if (a === b) {
    return "a and b are equal";
  }
  else if (a > b) {
    return "a is greater";
  }
  else {
    return "b is greater";
  }
}
```

Pode ser expresso assim
```
function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" : (a > b) ? "a is greater" : "b is greater";
}
```
