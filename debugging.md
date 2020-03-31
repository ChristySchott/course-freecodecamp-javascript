#### Introduce to Debbugging Challenges 

Esse capítulo foi muito interessante. Além de definir o conceito de debugging e explicar formas de testar possíveis erros, foram requeridos exercicios onde o aluno deve fazer a correção de códigos com erros.

Debugging é uma ferramenta valiosa e (infelizmente) necessária para os programadores. Ele segue a fase de teste para verificar se o seu código funciona como pretendido e descobrir que não.É o processo de encontrar exatamente o que não está funcionando e corrigi-lo. Depois de gastar
tempo criando um brilhante bloco de código, é difícil perceber que pode haver erros. Esses problemas geralmente vêm em três formas:

1. Erros de sintaxe que impedem a execução de um programa
2. Erros de tempo de execução quando o código falha ao executar ou tem comportamento inesperado
3. Erros semânticos (ou lógicos) quando o código não faz o que deve.

####  Use the JavaScript Console to Check the Value of a Variable

O método console.log (), que "imprime" a saída do que está entre parênteses no console, provavelmente será a ferramenta de depuração mais útil. 
Colocá-lo em pontos estratégicos do seu código pode mostrar os valores intermediários das variáveis.

#### Use typeof to Check the Type of a Variable

Você pode usar typeof para verificar a estrutura de dados ou o tipo de uma variável. Isso é útil no debugging ao trabalhar com vários tipos de dados. Se você acha que está adicionando dois números, mas um é realmente uma sequência, os resultados podem ser inesperados. Erros de tipo podem ocorrer em cálculos ou chamadas de função. Tenha cuidado, especialmente quando estiver acessando e trabalhando com dados externos na forma de um objeto JSON (JavaScript Object Notation).
Exemplos: 
```
console.log(typeof ""); // outputs "string"
console.log(typeof 0); // outputs "number"
console.log(typeof []); // outputs "object"
console.log(typeof {}); // outputs "object"
```

O módulo contém apenas 12 exercícios então foi o mais rápido do curso, porém cumpriu o seu propósito.

