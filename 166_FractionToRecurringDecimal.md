# 166. Fraction to Recurring Decimal

Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.

For example,

- Given numerator = 1, denominator = 2, return "0.5".
- Given numerator = 2, denominator = 1, return "2".
- Given numerator = 2, denominator = 3, return "0.(6)".

```javascript
/**
 * @param {number} numerator
 * @param {number} denominator
 * @return {string}
 */
var fractionToDecimal = function(numerator, denominator) {
  if (numerator === 0) return '0'

  var result = ''  
  if (numerator < 0 ^ denominator < 0) result += '-'

  numerator = Math.abs(numerator)
  denominator = Math.abs(denominator)

  result += Math.floor(numerator / denominator)

  var remainder = numerator % denominator
  if (remainder === 0) return result

  result += '.'
  var map = {}

  while(remainder) {
    var startIndex = map[remainder]
    if (startIndex !== undefined) {
      result = result.substring(0, startIndex) + '(' + result.substring(map[remainder]) + ')'
      break
    }
    map[remainder] = result.length
    remainder *= 10
    result += Math.floor(remainder / denominator)
    remainder %= denominator
  }
  return result
};
```
