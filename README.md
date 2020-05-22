# Codewars
Having fun here getting a little sharper with Javascript :)

## The Hashtag Generator
https://www.codewars.com/kata/52449b062fb80683ec000024/train/javascript

### Working solution (9pm... not quite there but want to get there before I go to sleep!)
```
function generateHashtag (str) {
  let emptyOrLongerThan140Char = false;
  let newString = "";
  str[0] ? null : emptyOrLongerThan140Char = true;
  console.log('t/f:', emptyOrLongerThan140Char);
  
  if (!emptyOrLongerThan140Char && (str.split(' ').join('').length > 0)) {
    console.log('initial string:', str);
    console.log('initial string length:', str.length);
    newString = '#' + str.split(' ').map(word => word[0].toUpperCase() + word.slice(1, word.length)).join('')
    console.log('new string:', newString);
  } else {
    emptyOrLongerThan140Char = true;
  }
  
  newString.length > 140 ? emptyOrLongerThan140Char = true : null;

  return emptyOrLongerThan140Char ? false : newString
}
```


## Are they the "same"?
Completed May 2020
https://www.codewars.com/kata/550498447451fbbd7600041c

> Given two arrays a and b write a function comp(a, b) (compSame(a, b) in Clojure) that checks whether the two arrays have the "same" elements, with the same multiplicities. "Same" means, here, that the elements in b are the elements in a squared, regardless of the order.
> Examples
> Valid arrays
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11]  
> b = [121, 14641, 20736, 361, 25921, 361, 20736, 361]
> 
> comp(a, b) returns true because in b 121 is the square of 11, 14641 is the square of 121, 20736 the square of 144, 361 the square of 19, 25921 the square of 161, and so on. It gets obvious if we write b's elements in terms of squares:
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] 
> b = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19]
> 
> Invalid arrays
> 
> If we change the first number to something else, comp may not return true anymore:
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11]  
> b = [132, 14641, 20736, 361, 25921, 361, 20736, 361]
> 
> comp(a,b) returns false because in b 132 is not the square of any number of a.
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11]  
> b = [121, 14641, 20736, 36100, 25921, 361, 20736, 361]
> 
> comp(a,b) returns false because in b 36100 is not the square of any number of a.
> Remarks
> 
>     a or b might be [] (all languages except R, Shell).
>     a or b might be nil or null or None or nothing (except in Haskell, Elixir, C++, Rust, R, Shell, PureScript).
> 
> If a or b are nil (or null or None), the problem doesn't make sense so return false.
> Note for C
> 
> The two arrays have the same size (> 0) given as parameter in function comp.
> 

### Solution 1 (checking for null inputs in the return)
```
function comp(array1, array2){
  const checkForFalses = () => {
    var onlyTrues = true;
    array1.forEach(number => {
      if (!array2.includes(number ** 2)) {
        onlyTrues = false;
      } else {
        array2.splice([array2.findIndex(num => num === (number ** 2))], 1);
      }
    })
    return onlyTrues;
  }
  return array1 && array2 ? checkForFalses() : false;
}
```


### Solution 2 (checking for null inputs prior to returning)
```
function comp(array1, array2){
  var onlyTrues = true;
  if (!array1 || !array2) {
    return false;
  }
  array1.forEach(number => {
    if (!array2.includes(number ** 2)) {
      onlyTrues = false;
    } else {
      var currentNumberSquaredIndex = array2.findIndex(num => num === (number ** 2));
      array2.splice([currentNumberSquaredIndex], 1);
    }
  })
  return onlyTrues;
}
```


## Format a string of names like 'Bart, Lisa & Maggie'.
Completed May 2020
https://www.codewars.com/kata/53368a47e38700bd8300030d

> Given: an array containing hashes of names
> 
> Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.
> 
> Example:
> 
> list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
> // returns 'Bart, Lisa & Maggie'
> 
> list([ {name: 'Bart'}, {name: 'Lisa'} ])
> // returns 'Bart & Lisa'
> 
> list([ {name: 'Bart'} ])
> // returns 'Bart'
> 
> list([])
> // returns ''
> 
> Note: all the hashes are pre-validated and will only contain A-Z, a-z, '-' and '.'.

### Solution
```
function list(names){
  var namesToJoin = [];
  names.forEach(name => namesToJoin.push(name["name"]));
  var formattedNames = namesToJoin.join(", ").replace(/,([^,]*)$/, ' &' + '$1');
  return formattedNames;
}
```

## My Languages
Completed April 2020
https://www.codewars.com/kata/5b16490986b6d336c900007d

> Your task
> 
> You are given a dictionary/hash/object containing some languages and your test results in the given languages. Return the list of languages where your test score is at least 60, in descending order of the results.
> 
> Note: the scores will always be unique (so no duplicate values)
> Examples
> 
> {"Java": 10, "Ruby": 80, "Python": 65}    -->  ["Ruby", "Python"]
> {"Hindi": 60, "Dutch" : 93, "Greek": 71}  -->  ["Dutch", "Greek", "Hindi"]
> {"C++": 50, "ASM": 10, "Haskell": 20}     -->  []

### Solution
```
function myLanguages(results) {
  var sixtyOrHigherTest = Object.entries(results).filter(language => language[1] >= 60)
  return sixtyOrHigherTest.sort((a,b) => b[1] - a[1]).map(language => language[0]);
}
```

## Happy Birthday, Darling!
Completed April 2020
https://www.codewars.com/kata/5e96332d18ac870032eb735f

> As you may know, once some people pass their teens, they jokingly only celebrate their 20th or 21st birthday, forever. With some maths skills, that's totally possible - you only need to select the correct number base!
> 
> For example, if they turn 32, that's exactly 20 - in base 16... Already 39? That's just 21, in base 19!
> 
> Your task is to translate the given age to the much desired 20 (or 21) years, and indicate the number base, in the format specified below.
> 
> Note: input will be always > 21
> Examples:
> 
> 32  -->  "32? That's just 20, in base 16!"
> 39  -->  "39? That's just 21, in base 19!"
> 
> Hint: if you may don't know (enough) about numeral systems and radix, just observe the pattern!

### Solution
```
function womensAge(n) {
  base = 1;
  
  while (n / base > 2) {
    base++;
    //make n / base doesn't go under 2
    if (n / base < 2){
    base--;
    break;
    }
  }
  
  if (n % base === 0 || n % base === 1){
  return `${n}? That's just 2${n % base}, in base ${base}!`
  }
}
```

## Sum of Digits / Digital Root
Completed March 2020
https://www.codewars.com/kata/541c8630095125aba6000c00

> In this kata, you must create a digital root function.
> 
> A digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.
> 
> Here's how it works:
> 
> digital_root(16)
> => 1 + 6
> => 7
> 
> digital_root(942)
> => 9 + 4 + 2
> => 15 ...
> => 1 + 5
> => 6
> 
> digital_root(132189)
> => 1 + 3 + 2 + 1 + 8 + 9
> => 24 ...
> => 2 + 4
> => 6
> 
> digital_root(493193)
> => 4 + 9 + 3 + 1 + 9 + 3
> => 29 ...
> => 2 + 9
> => 11 ...
> => 1 + 1
> => 2

### Solution
```
function digital_root(n) {
  let currentNumbers = n
  let sum = 0
  console.log("num before loop", currentNumbers)

  while (currentNumbers >= 10) {
        sum = 0
        currentNumbers.toString().split('').forEach(num => {
          sum += parseInt(num)
        })
        currentNumbers = sum
  }
  console.log("num after loop", currentNumbers)
  return currentNumbers
}
```
