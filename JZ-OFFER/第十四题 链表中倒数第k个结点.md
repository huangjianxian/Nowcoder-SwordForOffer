## 第十四题 链表中倒数第k个结点

### 题目描述

> 输入一个链表，输出该链表中倒数第k个结点。

**思路：** 定义两个指针 p, q，让p先前进k个单位，然后两个指针一起往后走，直到p走到最后的位置，则q所指的结点为倒数第K个结点。

### 法一：制造刻度尺

**代码：** 

```C#
        public ListNode FindKthToTail(ListNode head, int k)
        {
            ListNode p, q;
            p = q = head; // 两只指针都指向头结点
            int i = 0;
            while (p != null)
            {
                if (i >= k)
                    q = q.next; // q也往后移动，此时两个指针一起往后走
                p = p.next; // 先让p前进k个单位
                i++;
            }
            return i < k ? null : q;
        }
```
**运行结果：** 

> 运行时间：25ms   
占用内存：3524k

### 法二：栈

**思路：** 先将链表所有结点入栈，然后出栈k个结点即可。

**代码：** 

```C#
        public ListNode FindKthToTail(ListNode head, int k)
        {
            Stack<ListNode> stack = new Stack<ListNode>();
            ListNode p = head;
            while (p != null)
            {
                stack.Push(p);
                p = p.next;
            }
            if (k > stack.Count)
                return null;
            ListNode node = null;
            for (int i = 0; i < k; i++)
            {
                node = stack.Pop();
            }
            return node;
        }
```

**运行结果：** 

> 运行时间：28ms   
占用内存：3516k
