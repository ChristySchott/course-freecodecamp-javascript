

## Basic JavaScript

A partir do nome do módulo é possível raciocinar que se trata de uma introdução a linguagem. Como ja tenho uma boa base de outros cursos de JS, aproveitei pouca coisa, mas foi ótimo para lembrar dos conteúdos, pois o conteúdo é bem completo e enxuto.
O modulo possui 100 explicações com um editor de texto ao lado para a realização de exercícios, um ponto forte do curso. Pôr em prática o conhecimento é essencial para fixar o resultado. Colocarei apenas alguns códigos que eu fiz e me ajudaram a lembrar de determinados assuntos.


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
