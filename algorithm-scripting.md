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

#### Repeat a String

"Repeat a given string str (first argument) for num times (second argument). Return an empty string if num is not a positive number."

```
function repeatStringNumTimes(str, num) {
  if (num < 1) {
    return "";
  } else if (num === 1) {
    return str;
  } else {
    return str + repeatStringNumTimes(str, num - 1);
  }
}
```

#### Finders Keepers 

"Create a function that looks through an array (first argument) and returns the first element in the array that passes a truth test (second argument). If no element passes the test, return undefined."
```
function findElement(arr, func) {
  let num = 0;
  for (var i = 0; i < arr.length; i++) {
    num = arr[i];
    if (func(num)) {
      return num;
    }
  }

  return undefined;
}
```

#### Mutations

"Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

For example, ["hello", "Hello"], should return true because all of the letters in the second string are present in the first, ignoring case.

The arguments ["hello", "hey"] should return false because the string "hello" does not contain a "y".

Lastly, ["Alien", "line"], should return true because all of the letters in "line" are present in "Alien"."

```

```


