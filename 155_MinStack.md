# 155. Min Stack

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- push(x) -- Push element x onto stack.  
- pop() -- Removes the element on top of the stack.  
- top() -- Get the top element.  
- getMin() -- Retrieve the minimum element in the stack.  

**Example:**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

```javascript
/**
 * initialize your data structure here.
 */
var MinStack = function() {
  this.stack = []
  this.minStack = []
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
  this.stack.push(x)

  var len = this.minStack.length
  var minItem = len > 0 ? Math.min(this.minStack[len - 1], x) : x
  this.minStack.push(minItem)
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
  this.stack.pop()
  this.minStack.pop()
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
  var len = this.stack.length
  return len > 0 ? this.stack[len - 1] : 0
};

/**
 * @return {number}
 */
MinStack.prototype.getMin = function() {
  var len = this.minStack.length
  return len > 0 ? this.minStack[len - 1] : 0
};

/** 
 * Your MinStack object will be instantiated and called as such:
 * var obj = Object.create(MinStack).createNew()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.getMin()
 */
```
