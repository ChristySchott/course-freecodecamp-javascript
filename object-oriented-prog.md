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
