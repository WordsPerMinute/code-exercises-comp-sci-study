# Codewars
Having fun here getting a little sharper with Javascript :)
Problems are measured by a kyu level, the smaller the number, the more difficult

---

## Word a10n (abbreviation)
6 kyu
June 13
https://www.codewars.com/kata/5375f921003bf62192000746

```
```

---

## Word a10n (abbreviation)
6 kyu
June 12
https://www.codewars.com/kata/5375f921003bf62192000746

in progress
```
function abbreviate(string) {
  let newString = ""
  if (string.length > 4) {
    let middleCharacters = string.length - 2
    console.log(middleCharacters)
    newString = string.replace(/\B[a-z]*\B/, `${middleCharacters}`)
  }
  
  return newString
}
```

---

## Persistent Bugger
6 kyu
June 11
https://www.codewars.com/kata/55bf01e5a717a0d57e0000ec

```
function persistence(num) {
  let stringedNumber = num.toString();
  let multipliedNumber = 0;
  let multiplyCounter = 0;
  
  while (stringedNumber.length != 1) {
    let separatedNumbers = []
    for (var i = 0; i < stringedNumber.length; i += 1) {
      separatedNumbers.push(parseInt(stringedNumber.charAt(i)))
    }
    multipliedNumber = separatedNumbers.reduce((acc, val) => acc *= val);
    stringedNumber = multipliedNumber.toString();
    multiplyCounter++;
  }
  
  return multiplyCounter
}
```

---

## Disemvowel Trolls
7 kyu
June 11
https://www.codewars.com/kata/52fba66badcd10859f00097e

```
function disemvowel(str) {
  return str.replace(/[aeiou]/gi, '');
}
```

---

## Two Sum
6 kyu
June 10
https://www.codewars.com/kata/52c31f8e6605bcc646000082

```
function twoSum(numbers, target) {
  let firstI = 0;
  let secondI = 0;
  let fired = false;
  numbers.forEach((firstNumber, firstIndex) => {
    numbers.forEach((secondNumber, secondIndex) => {
      if (firstIndex != secondIndex && firstNumber + secondNumber == target && fired != true){
        firstI = firstIndex;
        secondI = secondIndex;
        fired = true;
      }
    })
  })
  return [firstI, secondI];
}
```
---

## Break camelCase
6 kyu
June 9
https://www.codewars.com/kata/5208f99aee097e6552000148

```
function solution(string) {
    let separated = "";
    for (var i = 0; i < string.length; i++) {
      if (string[i] == string[i].toUpperCase()){
        separated += ` ${string[i]}`;
      } else {
        separated += string[i];  
      }
    }
    return separated;
}
```

---

## Count the smiley faces!
6 kyu
June 4
https://www.codewars.com/kata/583203e6eb35d7980400002a

---

## Snakes and Ladders
Starting May 29, back in the city after a mountain hiatus
https://www.codewars.com/kata/587136ba2eefcb92a9000027

---

## Beeramid
Starting May 27, from a vacation cabin in the mountains
https://www.codewars.com/kata/51e04f6b544cf3f6550000c1

> Let's pretend your company just hired your friend from college and paid you a referral bonus. Awesome! To celebrate, you're taking your team out to the terrible dive bar next door and using the referral bonus to buy, and build, the largest three-dimensional beer can pyramid you can. And then probably drink those beers, because let's pretend it's Friday too.
> 
> A beer can pyramid will square the number of cans in each level - 1 can in the top level, 4 in the second, 9 in the next, 16, 25...
> 
> Complete the beeramid function to return the number of complete levels of a beer can pyramid you can make, given the parameters of:
> 
> 1) your referral bonus, and
> 
> 2) the price of a beer can
> 
> For example:
> 
> beeramid(1500, 2); // should === 12
> beeramid(5000, 3); // should === 16

---

## A simple Tic-tac-toe class
My friend who's a decent coder said this had him freeze up during a tech interview.
Starting May 22
https://www.codewars.com/kata/529b9ec8064ec38636000134

---

## The Hashtag Generator
Completed May 21 2020
https://www.codewars.com/kata/52449b062fb80683ec000024/train/javascript

#### Solution 1 (before a final refactor)
```
function generateHashtag (str) {
  let emptyOrLongerThan140Char = false;
  let newString = "";
  str[0] && (str.split(' ').join('').length > 0) ? null : emptyOrLongerThan140Char = true;
  
  if (!emptyOrLongerThan140Char) {
    newString = '#' + str.replace(/  +/g, ' ').split(' ').map(word => word[0].toUpperCase() + word.slice(1, word.length)).join('')
    newString.length > 140 ? emptyOrLongerThan140Char = true : null;
  } else {
    emptyOrLongerThan140Char = true;
  }

  return emptyOrLongerThan140Char ? false : newString
}
```

#### Solution 2 (refactored)
```
function generateHashtag (str) {
  if(!str || str[0] === "") return false;

  let newString = '#' + str.replace(/  +/g, ' ').split(' ').map(word => {
    if (word) {
      return word[0].toUpperCase() + word.slice(1, word.length)
    }
    }).join('')

  return (newString.length > 140 || newString.length == 1) ? false : newString
}
```

---

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

#### Solution 1 (checking for null inputs in the return)
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


#### Solution 2 (checking for null inputs prior to returning)
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

---

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

#### Solution
```
function list(names){
  var namesToJoin = [];
  names.forEach(name => namesToJoin.push(name["name"]));
  var formattedNames = namesToJoin.join(", ").replace(/,([^,]*)$/, ' &' + '$1');
  return formattedNames;
}
```

---

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

#### Solution
```
function myLanguages(results) {
  var sixtyOrHigherTest = Object.entries(results).filter(language => language[1] >= 60)
  return sixtyOrHigherTest.sort((a,b) => b[1] - a[1]).map(language => language[0]);
}
```

---

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

#### Solution
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

---

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

#### Solution
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
