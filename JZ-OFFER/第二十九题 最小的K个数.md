## 第二十九题 最小的K个数

### 题目描述

> 输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4。

**思路：** 做k遍冒泡排序，每次将遍历的最后一个结点加入集合中。

**代码：** 

```C#
        /// <summary>
        /// 冒泡排序
        /// </summary>
        /// <param name="input"></param>
        /// <param name="k"></param>
        /// <returns></returns>
        public List<int> GetLeastNumbers_Solution(int[] input, int k)
        {
            List<int> resultList = new List<int>();
            if (k > input.Length)
                return resultList;

            for (int i = 0; i < k; i++)
            {
                for (int j = 0; j < input.Length - i - 1; j++)
                {
                    if (input[j] < input[j + 1])
                    {
                        // 交换
                        int temp = input[j];
                        input[j] = input[j + 1];
                        input[j + 1] = temp;
                    }
                }
                resultList.Add(input[input.Length - i - 1]);
            }
            return resultList;
        }
```

**运行结果：** 

> 运行时间：25ms   
占用内存：3388k