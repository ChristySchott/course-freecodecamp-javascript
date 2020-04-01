# Object Oriented Programming 

Neste módulos tratamos dos principios básicos da **Programação Orientada a Objetos** no JavaScript. E como o a própria freeCodeCamp anuncia:

"Como o próprio nome indica, a programação orientada a objetos organiza o código em definições de objetos. Às vezes, são chamadas de classes e agrupam dados com comportamento relacionado. Os dados são os atributos de um objeto e o comportamento (ou funções) são métodos.

A estrutura do objeto a torna flexível dentro de um programa. Os objetos podem transferir informações chamando e passando dados para os métodos de outro objeto. Além disso, novas classes podem receber ou herdar todos os recursos de uma classe base ou pai. Isso ajuda a reduzir o código repetido."

Eu já havia tido contato com a POO durante dois anos do meu curso Técnico em Informática, e claro, já havia exercitado a abordagem em diferentes contextos, então foi relativamente fácil absover o conteúdo desse bloco.



------

Os primeiros exercícios vão tratar, naturalmente, das questões mais básicas, como criação e manipulação de objeto.

#### Creat a Method on an Object

```
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + duck.name + ".";}
};
duck.sayName();
```

O resultado retornado será "The name of this duck is Aflac."

Embora essa seja uma maneira válida de acessar a propriedade do objeto, existe uma armadilha aqui. Se o nome da variável for alterado, qualquer código referente ao nome original também precisará ser atualizado. Em uma definição curta de objeto, não é um problema, mas se um objeto tem muitas referências a suas propriedades, há uma chance maior de erro.

Uma maneira de evitar esse erro é utilizando a keyword *this*:
```
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + this.name + ".";}
};
```

#### Define a Constructor Function

- Os construtores são definidos com um nome em maiúscula para distingui-los de outras funções que não são construtoras.
- Os construtores usam a keyword this para definir as propriedades do objeto que eles criarão. Dentro do construtor, isso se refere ao novo objeto que ele criará.
- Os construtores definem propriedades e comportamentos em vez de retornar um valor como outras funções.

```
function Passaro() {
  this.nome = "Albert";
  this.cor = "blue";
  this.numPernas = 2;
}
```
Podemos agora, extender esse construtor para ele receber argumentos. No exemplo abaixo vou adicionar uma nova cor ao construtor Bird:
```
let joaoBarro = new Passaro();
joaoBarro.nome = "Carlos";
joaoBarro.cor = "white";
```

Criei a variável joaoBarro, mas o nome fica de acordo com a necessidade do programa.
Agora vem uma questão imporatante:

Suponha que você queira registar milhares de aves. Levaria muito tempo para criar todos os pássaros e depois alterar as propriedades para valores diferentes para cada um. Para criar mais facilmente objetos Passaro diferentes, você pode projetar seu construtor Passaro para aceitar parâmetros:

```
function Passaro(nome, cor) {
  this.nome = nome;
  this.cor = cor;
  this.numPernas = 2;
}

// repare que o numero de pernas é fixo.
```

Agora se eu preciso criar um novo Passaro eu faço: 
> let gaivota = new "Passaro"("Marcio","azul");

#### Verify an Object's Constructor with instanceof

Sempre que uma função construtora cria um novo objeto, esse objeto é considerado uma instância de seu construtor. O JavaScript fornece uma maneira conveniente de verificar isso com o operador instanceof. instanceof permite comparar um objeto com um construtor, retornando verdadeiro ou falso com base em se esse objeto foi ou não criado com o construtor.
Segue dois exemplos, um verdade e um falso, respectivamente:

```
let Bird = function(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}

let crow = new Bird("Alexis", "black");

crow instanceof Bird; // => true
```

Falso:
```
let canary = {
  name: "Mildred",
  color: "Yellow",
  numLegs: 2
};

canary instanceof Bird; // => false
```

#### Understand Own Properties

No exemplo a seguir, Bird tem duas propriedades, o name e o número de pernas:
```
function Bird(name) {
  this.name  = name;
  this.numLegs = 2;
}

let duck = new Bird("Donald");
let canary = new Bird("Tweety");
```

Elas são chama de *own* Properties, porque são definidas diretamente na instacia do objeto. Isso significa que cada duck e canary tem sua própria cópia separada dessas propriedades.

O código a seguir adiciona todas as propriedades próprias do duck ao array ownProps:
```
let ownProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  }
}

console.log(ownProps); // prints [ "name", "numLegs" ]
```

#### Use Prototype Properties para reduzir o código duplicado

Como numLegs provavelmente terá o mesmo valor para todas as instâncias de Bird, você basicamente possui uma variável duplicada numLegs dentro de cada instância de Bird.

Isso pode não ser um problema quando há apenas duas instâncias, mas imagine se houver milhões de instâncias. Isso seria um monte de variáveis duplicadas.

Uma maneira melhor é usar prototype de Bird. As propriedades no protótipo são compartilhadas entre TODAS as instâncias do Bird. Veja como adicionar numLegs ao prototype Bird:

> Bird.prototype.numLegs = 2;

Agora todas instãncias de Bird tem a propriedade numLegs.

#### Iterate Over All Properties

Adicionado as own properties do duck às propriedades ownProps e prototypes ao array prototypeProps:
```
function Bird(name) {
  this.name = name;  //own property
}

Bird.prototype.numLegs = 2; // prototype property

let duck = new Bird("Donald");


let ownProps = [];
let prototypeProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  } else {
    prototypeProps.push(property);
  }
}

```

#### Understand the Constructor Property

Existe uma propriedade *constructor* localizada na instância dos objetos duck e beagle que criamos antes:
```
let duck = new Bird();
let beagle = new Dog();

console.log(duck.constructor === Bird);  //prints true
console.log(beagle.constructor === Dog);  //prints true
```
Observe que a propriedade construtor é uma referência à função construtora que criou a instância. A vantagem da propriedade construtora é que é possível verificar essa propriedade para descobrir que tipo de objeto é. Aqui está um exemplo de como isso pode ser usado:

```
function joinBirdFraternity(candidate) {
  if (candidate.constructor === Bird) {
    return true;
  } else {
    return false;
  }
}
```

Como a propriedade do construtor pode ser substituída geralmente é melhor usar o método instanceof para verificar o tipo de um objeto.

Com o protoype eu posso adicionar funçõesno objeto:
```
Bird.prototype = {

  constructor: Bird,
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```
#### Use Inheritance So You Don't Repeat Yourself

Observe no exemplo abaixo que o método de descrição é compartilhado por Bird e Dog:
```
Bird.prototype = {
  constructor: Bird,
  describe: function() {
    console.log("My name is " + this.name);
  }
};

Dog.prototype = {
  constructor: Dog,
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

O método de descrição é repetido em dois lugares. O código pode ser editado criando um supertype (ou pai) chamado Animal:

```
function Animal() { };

Animal.prototype = {
  constructor: Animal, 
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

Como Animal inclui o método de descrição, você pode removê-lo de Bird and Dog:
```
Bird.prototype = {
  constructor: Bird
};

Dog.prototype = {
  constructor: Dog
};
```

#### Inherit Behaviors from a Supertype

Para reutilizar os métodos de Animal dentro de Bird e Dog sem defini-los novamente, usa-se uma técnica chamada herança. Criando instância para eles:
> let duck = Object.creat(Animal.prototype);
> let dog = Object.create(Animal.protoype);

#### Understand the Immediately Invoked Function Expression (IIFE)

Um padrão comum no JavaScript é executar uma função assim que for declarada:
```
(function () {
  console.log("Chirp, chirp!");
})(); // this is an anonymous function expression that executes right away
// Outputs "Chirp, chirp!" immediately
```

Observe que a função não tem nome e não é armazenada em uma variável. Os dois parênteses () no final da expressão da função fazem com que ela seja executada ou invocada imediatamente. Esse padrão é conhecido como uma *expressão de função chamada imediatamente* ou IIFE.


#### Use an IIFE to Create a Module

Uma expressão de função chamada imediatamente (IIFE) é frequentemente usada para agrupar funcionalidades relacionadas em um único objeto ou módulo. 
```
function glideMixin(obj) {
  obj.glide = function() {
    console.log("Gliding on the water");
  };
}
function flyMixin(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  };
}
```

Nós podemos agrupar esse mixins em um módulo:
```
let motionModule = (function () {
  return {
    glideMixin: function(obj) {
      obj.glide = function() {
        console.log("Gliding on the water");
      };
    },
    flyMixin: function(obj) {
      obj.fly = function() {
        console.log("Flying, wooosh!");
      };
    }
  }
})(); // The two parentheses cause the function to be immediately invoked
```
