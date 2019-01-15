## Min Stack

> Design a stack that supports push, pop, top, and retrieving the minimum element in constant time. 
>
> (My Note: All of the operations should be in constant time.)

### Solution

这个问题的关键要从 stack 的操作出发，并不是说要找到任何一个stack的最小值。用一个例子来 walkthrough 也许会带来启发。



```java
class MinStack {

    private Stack<Integer> stack;
    private Stack<Integer> mins;
    
    /** initialize your data structure here. */
    public MinStack() {
        stack = new Stack<>();
        mins = new Stack<>();
    }
    
    public void push(int x) {
        if (stack.size() == 0 || mins.peek() >= x) {
            mins.push(x);
        }
        stack.push(x);
    }
    
    public void pop() {
        if (stack.size() == 0) {
            throw new RuntimeException();
        }
        if (stack.peek().equals(mins.peek())) { // == is wrong!
            mins.pop();
        }
        stack.pop();
    }
    
    public int top() {
        if (stack.size() == 0) {
            throw new RuntimeException();
        }
        return stack.peek();
    }
    
    public int getMin() {
        if (stack.size() == 0) {
            throw new RuntimeException();
        }
        return mins.peek();
    }
}
```

另外，两个stack可以合并，只要在每次min变化的时候把之前的也存下来就好。