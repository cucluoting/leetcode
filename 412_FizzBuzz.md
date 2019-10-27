# 412. Fizz Buzz

Write a program that outputs the string representation of numbers from 1 to n.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

**Example:**

```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
  const result = []
  for (let num = 1; num <= n; num++) {
    let divisibleBy3 = num % 3 === 0
    let divisibleBy5 = num % 5 === 0
    let tempStr = ''
    if (divisibleBy3) {
      tempStr += 'Fizz'
    }
    if (divisibleBy5) {
      tempStr += 'Buzz'
    }
    if (tempStr === '') {
      tempStr += `${num}`
    }
    result.push(tempStr)
  }
  return result
};

```
