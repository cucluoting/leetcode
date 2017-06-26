# 36. Valid Sudoku

Determine if a Sudoku is valid, according to: [Sudoku Puzzles - The Rules](http://sudoku.com.au/TheRules.aspx).

The Sudoku board could be partially filled, where empty cells are filled with the character `'.'`.

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.


```javascript
/**
 * @param {character[][]} board
 * @return {boolean}
 */
var isValidSudoku = function(board) {
  var column = []
  var subBoard = []

  for (var i = 0; i < board.length; i++) {
    var currentRow = board[i]
    for (var j = 0; j < currentRow.length; j++) {
      var currentNum = currentRow[j]
      var flag = false
      if (currentNum === '.') continue
      for (var index = 0; index < j; index++) {
        if(currentRow[index] === currentNum) flag = true
      }
      if (flag) return false
      
      if (!column[j]) {
        column[j] = []
      } else {
        column[j].forEach(function (item) {
          if (item === currentNum) flag = true
        })
        if (flag) return false
      }
      column[j].push(currentNum)

      var k = (Math.ceil((j + 1) / 3) - 1) * 3 + (Math.ceil((i + 1) / 3) - 1)
      if (!subBoard[k]) {
        subBoard[k] = []
      } else {
        subBoard[k].forEach(function (item) {
          if (item === currentNum) flag = true
        })
        if (flag) return false
      }
      subBoard[k].push(currentNum)
    }
  }
  return true
};
```
