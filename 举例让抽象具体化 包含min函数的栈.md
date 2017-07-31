# 举例让抽象具体化 包含min函数的栈

* 定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。

* 新建一个辅助栈min，只保存比当前min栈顶元素小(<=)的元素，则min栈顶的元素就是data栈中元素的最小值。数据栈data出栈元素与min栈顶元素是同一元素的话，则min栈也出栈即可。

```
import java.util.Stack;

public class Solution {
    private Stack<Integer> data = new Stack<>();
    private Stack<Integer> min = new Stack<>();
    public void push(int node) {
        data.push(node);
        if (min.empty() || min.peek() >= node) {
            min.push(node);
        }
    }
    
    public void pop() {
        if (data.pop() == min.peek()) {
            min.pop();
        }
    }
    
    public int top() {
        return data.peek();
    }
    
    public int min() {
        return min.peek();
    }
}
```