#  Basic Algorithm Scripting

#### Reverse a String

```
function reverseString(str) {
  return str
    .split("")
    .reverse()
    .join("");
}
```

#### Factorialize a Number

Um modo de fazer a fatoração é o seguinte:

```
function factorialize(num) {
  for (var product = 1; num > 0; num--) { // vai tirando um enquanto o numero for maior que zero.
    product *= num;
  }
  return product;
}

factorialize(5);

```

Achando o tamanho da maior palavra em uma sentença:
```
function findLongestWordLength(str) {
  var words = str.split(' ');
  var maxLength = 0;

  for (var i = 0; i < words.length; i++) {
    if (words[i].length > maxLength) {
      maxLength = words[i].length;
    }
  }

  return maxLength;
}
```

#### Largest Numbers in Arrays
```
function largestOfFour(arr) {
  var results = [];
  for (var n = 0; n < arr.length; n++) {
    var largestNumber = arr[n][0];
    for (var j = 1; j < arr[n].length; j++) {
      if (arr[n][j] > largestNumber) {
        largestNumber = arr[n][j];
      }
    }

    results[n] = largestNumber;
  }

  return results;
}
```
