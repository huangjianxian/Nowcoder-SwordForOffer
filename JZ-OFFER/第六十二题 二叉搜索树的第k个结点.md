## 第六十二题 二叉搜索树的第k个结点

### 题目描述

> 给定一棵二叉搜索树，请找出其中的第k小的结点。

### 法一：递归

**思路：** 二叉搜索树的中序遍历即为从小到大来排列的序列。

**代码：** 

```C#
        int count = 0; // 计数器
        public TreeNode KthNode(TreeNode pRoot, int k)
        {
            // 利用中序遍历
            if (pRoot != null)
            {
                TreeNode node = KthNode(pRoot.left, k);
                if (node != null)
                    return node;
                count++;
                if (count == k)
                    return pRoot;
                node = KthNode(pRoot.right, k);
                if (node != null)
                    return node;
            }
            return null;
        }
```

**运行结果：** 

> 运行时间：25ms   
占用内存：3352k