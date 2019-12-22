# 475. Heaters

Winter is coming! Your first job during the contest is to design a standard heater with fixed warm radius to warm all the houses.

Now, you are given positions of houses and heaters on a horizontal line, find out minimum radius of heaters so that all houses could be covered by those heaters.

So, your input will be the positions of houses and heaters seperately, and your expected output will be the minimum radius standard of heaters.

**Note:**

1. Numbers of houses and heaters you are given are non-negative and will not exceed 25000.
2. Positions of houses and heaters you are given are non-negative and will not exceed 10^9.
3. As long as a house is in the heaters' warm radius range, it can be warmed.
4. All the heaters follow your radius standard and the warm radius will the same.
 

**Example 1:**
```
Input: [1,2,3],[2]
Output: 1
Explanation: The only heater was placed in the position 2, and if we use the radius 1 standard, then all the houses can be warmed.
```

**Example 2:**
```
Input: [1,2,3,4],[1,4]
Output: 1
Explanation: The two heater was placed in the position 1 and 4. We need to use radius 1 standard, then all the houses can be warmed.
```

解法1: 

```javascript
/**
 * @param {number[]} houses
 * @param {number[]} heaters
 * @return {number}
 */
var findRadius = function(houses, heaters) {
  let result = Number.MIN_VALUE
  houses.sort((a, b) => a - b)
  heaters.sort((a, b) => a - b)
  let j = 0
  for (let i = 0; i < houses.length; i++) {
    while (
      j < heaters.length - 1 &&
      Math.abs(heaters[j + 1] - houses[i]) <= Math.abs(heaters[j] - houses[i])
    ) {
      j++
    }
    result = Math.max(result, Math.abs(heaters[j] - houses[i]))
  }
  return result
};
```

解法2:(二分法)

```javascript
/**
 * @param {number[]} houses
 * @param {number[]} heaters
 * @return {number}
 */
var findRadius = function(houses, heaters) {
  let result = Number.MIN_VALUE
  houses.sort((a, b) => a - b)
  heaters.sort((a, b) => a - b)
  for (let i = 0; i < houses.length; i++) {
    const radius = findOne(houses[i], heaters)
    result = Math.max(radius, result)
  }
  return result
};

var findOne = function(house, heaters) {
  let start = 0
  let end = heaters.length - 1
  let left = Number.MAX_VALUE
  let right = Number.MAX_VALUE
  while (start <= end) {
    const mid = Math.ceil((end + start) / 2)
    const heater = heaters[mid]
    if (house === heater) {
      return 0
    } else if (heater < house) {
      start = mid + 1
      left = house - heater
    } else {
      end = mid - 1
      right = heater - house
    }
  }
  return Math.min(left, right)
};
```
