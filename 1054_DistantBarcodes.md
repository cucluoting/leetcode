# 1054. Distant Barcodes

In a warehouse, there is a row of barcodes, where the i-th barcode is `barcodes[i]`.

Rearrange the barcodes so that no two adjacent barcodes are equal.  You may return any answer, and it is guaranteed an answer exists.

**Example 1:**
```
Input: [1,1,1,2,2,2]
Output: [2,1,2,1,2,1]
```

**Example 2:**
```
Input: [1,1,1,1,2,2,3,3]
Output: [1,3,1,3,2,1,2,1]
``` 

**Note:**

1. 1 <= barcodes.length <= 10000
2. 1 <= barcodes[i] <= 10000
 
```javascript
/**
 * @param {number[]} barcodes
 * @return {number[]}
 */
var rearrangeBarcodes = function(barcodes) {
  const map = new Map()
  const len = barcodes.length
  for (let i = 0; i < len; i++) {
    const barcode = barcodes[i]
    if (!map.has(barcode)) {
      map.set(barcode, 0)
    }
    map.set(barcode, map.get(barcode) + 1)
  }
  const entries = [...map]
  entries.sort((a, b) => b[1] - a[1])
  
  const result = []
  let index = 0
  for (let i = 0; i < entries.length; i++) {
    const [barcode, count] = entries[i]
    for (let j = 0; j < count; j++) {
      result[index] = barcode
      index += 2
      if (index >= len) {
        index = 1
      }
    }
  }
  return result
};
```
