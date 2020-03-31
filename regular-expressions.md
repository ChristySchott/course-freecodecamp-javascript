#### Regular Expressions
são usadas em linguagens de programação para corresponder a partes de strings. Você cria padrões para ajudá-lo a fazer essa correspondência.
Se você deseja encontrar a palavra "the" na string "The dog chased the cat", você pode usar a seguinte expressão regular: / the /. Observe que aspas não são necessárias na expressão regular.
Uma maneira de testar uma regex é usando o método .test (). O método .test () pega o regex, aplica-o a uma string (colocada entre parênteses) e retorna true ou false se o seu padrão encontrar algo ou não.
```
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
// Returns true
```
Você pode procurar por vários patterns usando a alternation ou o operador OR: | .

Este operador corresponde aos padrões antes ou depois dele. Por exemplo, se você deseja corresponder "yes" ou "no", a regex desejada é / yes | no /.

```
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/; 
let result = petRegex.test(petString);
```

#### Ignore Case While Matching

A regex, sem um ignore case, irá diferenciar as letras minúsculas das maiúsculas, pode causar um problema na nossa busca.

Você pode combinar os dois casos usando o que é chamado de flag. Existem outras flag, mas aqui eu apresentarei  a flag que ignora maiúsculas e minúsculas - a flag i. Você pode usá-la anexando-a à regex. Um exemplo do uso dessa flag é / ignorecase / i. Essa regex pode corresponder às cadeias "ignorecase", "igNoreCase" e "IgnoreCase".

#### Extract Matches

Por enquanto estamos só verificando se o valor existe ou não, mas também podemos extrair essse valor, usando *.match()*. Veja no exemplo:
```
"Hello, World!".match(/Hello/);
// Returns ["Hello"]
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
// Returns ["expressions"]
```

#### Find More Than the First Match

No caso de houver uma palavra repetida e eu quiser retornar todas as vezes que ela aparece, devo usar a flag ***g***:
```
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
// Returns ["Repeat", "Repeat", "Repeat"]
```
#### Match Anything with Wildcard Period

Obs: o caractere que estarei me referindo aqui é o  .   (ponto), caso não fique claro
às vezes você não conhece ou não precisa conhecer os caracteres exatos em seus padrões. Pensar em todas as palavras que correspondem, digamos, a um erro de ortografia levaria muito tempo. Felizmente, você pode economizar tempo usando o caractere: *.*

O caractere  *.* irá corresponder a qualquer caractere. Você pode usar o caractere como qualquer outro caractere na regex. Por exemplo, se você deseja combinar "hug", "huh", 
"hut" e "hum", você pode usar o regex /hu./ para corresponder às quatro palavras.
```
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr); // Returns true
huRegex.test(hugStr); // Returns true
```

#### Match Single Character with Multiple Possibilities

Você pode procurar um padrão literal com alguma flexibilidade nas classes de caracteres. As classes de caracteres permitem definir um grupo de caracteres que você deseja corresponder colocando-os dentro de colchetes ([e]).

Por exemplo, você deseja combinar "bag "bige "bug", mas não "bug Você pode criar o regex / b [aiu] g / para fazer isso. O [aiu] é a classe de caracteres que corresponderá apenas aos caracteres "a", "i" ou "u".
Um dos usos para essa sintaxe é procurar por vogais :)

####  Match Numbers and Letters of the Alphabet

Se você quiser pegar todas letras de b até g, por exemplo, basta usar um hífen no meio delas:
> /[b-g]/gi;
O mesmo pode ser feito com números, por exemplo, quero pegar todas as letras de a até h e números de 0 a 6:
> /[a-h0-6]/gi;

#### Match Single Characters Not Specified
> Até agora, você criou um conjunto de caracteres que deseja corresponder, mas também pode criar um conjunto de caracteres que não deseja corresponder. Esses tipos de conjuntos de caracteres são chamados de conjuntos de caracteres negados.
Para criar um conjunto de caracteres negados, coloque um caractere de interpolação (^) após o colchete de abertura e antes dos caracteres que não deseja corresponder.
Por exemplo, / [^ aeiou] / gi corresponde a todos os caracteres que não são uma vogal. Observe que caracteres como.,!, [, @, / E espaço em branco são correspondidos - o conjunto de caracteres da vogal negada exclui apenas os caracteres da vogal.
------

Às vezes, você precisa corresponder a um caractere (ou grupo de caracteres) que apareça uma ou mais vezes seguidas. Isso significa que ocorre pelo menos uma vez e pode ser repetido.

Você pode usar o caractere + para verificar se é esse o caso. Lembre-se, o caractere padrão deve estar presente consecutivamente. Ou seja, o caracter precisa repetir um após o outro.

Por exemplo, / a + / g encontraria uma correspondência em "abc" e retornaria ["a"]. Por causa do +, ele também encontraria uma única correspondência em "aabc" e retornaria ["aa"].

Se, em vez disso, estivesse verificando a string "abab", encontraria duas correspondências e retornaria ["a", "a"] porque os caracteres a não estão em uma linha - existe um b entre eles. Por fim, como não há "a" na string "bcd", ele não encontrará uma correspondência.
