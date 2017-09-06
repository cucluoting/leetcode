# 79. Word Search

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

For example,  
Given **board** =

```
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
```

**word** = `"ABCCED"`, -> returns `true`,  
**word** = `"SEE"`, -> returns `true`,  
**word** = `"ABCB"`, -> returns `false`.  

```javascript
/**
 * @param {character[][]} board
 * @param {string} word
 * @return {boolean}
 */
var exist = function(board, word) {
  if (word.length === 0) return true
  if (board.length === 0 || board[0].length === 0) return false

  var visited = []
  board.map(function(row, rowIndex) {
    visited[rowIndex] = []
    var visitedRow = visited[rowIndex]
    row.map(function(cell, index) {
      visitedRow[index] = false
    })
  })
  
  for (var i = 0; i < board.length; i++) {
    for (var j = 0; j < board[0].length; j++) {
      if (helper(board, word, visited, 0, i, j)) {
        return true
      }
    }
  }
  return false
};

var helper = function(board, word, visited, index, i, j) {
  if (index === word.length) return true
  if (
    i < 0 
    || j < 0 
    || i > board.length - 1 
    || j > board[0].length - 1 
    || visited[i][j] 
    || word[index] !== board[i][j]
  ) {
    return false
  }

  visited[i][j] = true
  var result = helper(board, word, visited, index + 1, i + 1, j)
    || helper(board, word, visited, index + 1, i, j + 1)
    || helper(board, word, visited, index + 1, i - 1, j)
    || helper(board, word, visited, index + 1, i, j - 1)
  visited[i][j] = false
  return result
};
```
