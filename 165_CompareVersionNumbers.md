# 165. Compare Version Numbers

Compare two version numbers version1 and version2.  
If version1 > version2 return 1, if version1 < version2 return -1, otherwise return 0.

You may assume that the version strings are non-empty and contain only digits and the . character.  
The . character does not represent a decimal point and is used to separate number sequences.  
For instance, 2.5 is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

Here is an example of version numbers ordering:

```
0.1 < 1.1 < 1.2 < 13.37
```

```javascript
/**
 * @param {string} version1
 * @param {string} version2
 * @return {number}
 */
var compareVersion = function(version1, version2) {
  var index = 0
  var versionArr1 = version1.split('.')
  var versionArr2 = version2.split('.')

  while (versionArr1.length > index || versionArr2.length > index) {
    var num1 = Number(versionArr1[index])
    var num2 = Number(versionArr2[index])

    if (Number.isNaN(num1) && num2 > 0) return -1
    if (Number.isNaN(num2) && num1 > 0) return 1
    if (num1 > num2) return 1
    if (num1 < num2) return -1
      
    ++index
  }
  return 0
};
```
