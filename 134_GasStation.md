# 134. Gas Station

There are N gas stations along a circular route, where the amount of gas at station i is `gas[i]`.

You have a car with an unlimited gas tank and it costs `cost[i]` of gas to travel from station i to its next station (i+1). You begin the journey with an empty tank at one of the gas stations.

Return the starting gas station's index if you can travel around the circuit once, otherwise return -1.

**Note:**  
The solution is guaranteed to be unique.

```javascript
/**
 * @param {number[]} gas
 * @param {number[]} cost
 * @return {number}
 */
var canCompleteCircuit = function(gas, cost) {
  var sum = 0
  var tempSum = 0
  var index = 0
  for (var i = 0; i < gas.length; i++) {
    tempSum += gas[i] - cost[i]
    sum += gas[i] - cost[i]
    if (tempSum < 0) {
      index = i + 1
      tempSum = 0
    }
  }
  return sum < 0 ? -1 : index
};
```
