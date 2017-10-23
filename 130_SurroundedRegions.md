# 130. Surrounded Regions

Given a 2D board containing `'X'` and `'O'` (the letter O), capture all regions surrounded by `'X'`.

A region is captured by flipping all `'O'`s into `'X'`s in that surrounded region.

For example,

```
X X X X
X O O X
X X O X
X O X X
```

After running your function, the board should be:

```
X X X X
X X X X
X X X X
X O X X
```

**解题思路：** 从边缘出发，找出与边缘的 `'O'` 相连的 `'O'` ，将其置为 `'#'` ，那么最后就可以把矩阵里剩下的 `'O'` 置为 `'X'` ，再将 `'#'` 改回 `'O'` 。

```javascript
/**
 * @param {character[][]} board
 * @return {void} Do not return anything, modify board in-place instead.
 */
var solve = function(board) {
  if (!board || board.length <= 1 || board[0].length <= 1) return
  for (var i = 0; i < board[0].length; i++) {
    helper(board, 0, i)
    helper(board, board.length - 1, i)
  }
  for (var i = 0; i < board.length; i++) {
    helper(board, i, 0)
    helper(board, i, board[0].length - 1)
  }
  for (var row = 0; row < board.length; row++) {
    for (var col = 0; col < board[0].length; col++) {
      if (board[row][col] === 'O') board[row][col] = 'X'
      else if (board[row][col] === '#') board[row][col] = 'O'
    }
  }
};

var helper = function(board, i, j) {
  if (board[i][j] !== 'O') return
  board[i][j] = '#'
  if (i > 0) helper(board, i - 1, j)
  if (i < board.length - 1) helper(board, i + 1, j)
  if (j > 0) helper(board, i, j - 1)
  if (j < board[0].length - 1) helper(board, i, j + 1)
};
```
