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

O caractere para procurar por todo alfabeto alfanumerico é o /\w/g, que é o equivalente a colocar [a-zA-Z0-9].

Você pode procurar por espaço em branco usando \ s, que é um minúsculo. Esse padrão não corresponde apenas aos espaços em branco, mas também ao return, tab, alimentação de formulário e form feed, and new line characters. Você pode pensar nisso como semelhante à classe de caracteres [\ r \ t \ f \ n \ v].

O atalho para procurar caracteres de dígito é \ d, com um d minúsculo. Isso é igual à classe de caracteres [0-9]

Procure espaços não em branco usando \ S, que é um maiúsculo. Esse padrão não corresponderá a espaços em branco, retorno de carro, tabulação, alimentação de formulário e caracteres de nova linha. Você pode pensar que ele é semelhante à classe de caracteres [^ \ r \ t \ f \ n \ v].

Exemplo de exercicio:
Change the regex timRegex to match the word "Timber" only when it has four letter m's.
```
let timStr = "Timmmmber";
let timRegex = /Tim{4}ber/; // Change this line
let result = timRegex.test(timStr);
```

#### Check for All or None

Às vezes, os padrões que você deseja pesquisar podem ter partes dele que podem ou não existir. No entanto, pode ser importante procurá-los.

Você pode especificar a possível existência de um elemento com um ponto de interrogação,?. Isso verifica zero ou um dos elementos anteriores. Você pode pensar neste símbolo dizendo que o elemento anterior é opcional.

#### Lookaheads

Lookaheads são padrões que instruem o JavaScript a olhar em frente na sua string para verificar os padrões mais adiante. Isso pode ser útil quando você deseja procurar vários padrões na mesma sequência.

Existem dois tipos de lookahead: lookahead positivo e lookahead negativo.

Um lookahead positivo procurará garantir que o elemento no padrão de pesquisa esteja lá, mas na verdade não corresponderá a ele. Um lookahead positivo é usado como (? = ...) onde ... é a parte necessária que não corresponde.

Por outro lado, um lookahead negativo procurará garantir que o elemento no padrão de pesquisa não esteja lá. Um lookahead negativo é usado como (?! ...) onde o ... é o padrão que você não deseja que esteja lá. O restante do padrão será retornado se a parte negativa do lookahead não estiver presente.

Lookaheads são um pouco confusos, mas alguns exemplos ajudarão.

Um uso mais prático de lookaheads é verificar dois ou mais padrões em uma sequência. Aqui está um verificador de senha (ingênuo) simples que procura entre 3 e 6 caracteres e pelo menos um número:
```
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/;
checkPass.test(password); // Returns true
```
#### Replace
Pesquisando é útil. No entanto, você pode tornar a pesquisa ainda mais poderosa quando ela também altera (ou substitui) o texto correspondente.

Você pode pesquisar e substituir texto em uma string usando .replace (). As entradas para .replace () são primeiro o padrão de regex que você deseja procurar. O segundo parâmetro é a string para substituir a correspondência ou uma função para fazer alguma coisa.
```
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
// Returns "The sky is blue."
```

Exercício:
Write a regex fixRegex using three capture groups that will search for each word in the string "one two three". Then update the replaceText variable to replace "one two three" with the string "three two one" and assign the result to the result variable. Make sure you are utilizing capture groups in the replacement string using the dollar sign ($) syntax.
```
let str = "one two three";
let fixRegex = /(\w+)\s(\w+)\s(\w+)/; // Change this line
let replaceText = "$3 $2 $1"; // Change this line
let result = str.replace(fixRegex, replaceText);
```
