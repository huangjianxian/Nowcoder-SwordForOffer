## 第二十题 包含min函数的栈

### 题目描述

> 定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

### 法一：辅助栈

**思路：** 数据栈每次都要入栈；最小栈也需要每次都入栈，不然出栈的时候可能出现数据栈中A元素已经出栈，但是最小栈中还有A这个元素；最小栈在入栈时，先取得当前栈顶元素Min（也就是当前最小元素），用Min和当前要入栈的Node比较，将小的那一个入栈到最小栈。出栈的时候两个都出。

**代码：** 

```C#
        Stack<int> dataStack = new Stack<int>(); // 数据栈
        Stack<int> minStack = new Stack<int>(); // 最小栈
        
        public void push(int node)
        {
            dataStack.Push(node); // 每次进栈，数据栈都要进栈
            if (minStack.Count == 0)
                minStack.Push(node); // 如果最小栈为空，直接入栈
            else
            {
                int minValue = minStack.Peek(); // 返回当前最小栈的最小值
                if (node <= minValue) // 如果当前要入栈的元素值比最小栈的栈顶值还要小，入栈
                {
                    minStack.Push(node);
                }
                else
                {
                    minStack.Push(minValue);
                }
            }
        }
        
        // 如果出栈的时候不对最小栈处理，可能这个元素已经从数据栈出出去了，但是最小栈还有它
        public void pop()
        {
            dataStack.Pop();
            minStack.Pop();
        }
        
        public int top()
        {
            return dataStack.Peek();
        }
        
        public int min()
        {
            return minStack.Peek();
        }
```

**运行结果：** 

> 运行时间：32ms   
占用内存：3736k