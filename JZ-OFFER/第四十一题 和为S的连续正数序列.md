## 第四十一题 和为S的连续正数序列

### 题目描述

> 小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!

### 返回值描述:

> 输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

### 法一：移动检索

**思路：** 一开始从1，2那里分别设置一个low, high指针，high往后移动，然后计算low到high的和与目标值sum是否一致，如果一致则将low到high的数添加进集合再添加进结果集，再将low往后移动，继续向前检索。如果当前的范围内的和比sum小，那么往右扩大范围，如果比sum大，那么low往前移动，缩小范围。直到low超过high，那么后面的每一个数都比sum大了，就没有计算的必要了。

**代码：** 

```C#
        public List<List<int>> FindContinuousSequence(int sum)
        {
            List<List<int>> resultList = new List<List<int>>();
            int low = 1, high = 2; // 设置两个指针，从1，2开始
            while (high > low)
            {
                // 由于是连续的正整数，这也就是增量为1的递增数列，使用求和公式 Sum = (a1 + an) * n / 2
                int curSum = (high + low) * (high - low + 1) / 2; // 对当前区间数进行求和
                if (curSum == sum) // 符合条件，将low到high的数都添加到集合里，再添加入结果集
                {
                    List<int> list = new List<int>();
                    for (int i = low; i <= high; i++)
                    {
                        list.Add(i);
                    }
                    resultList.Add(list);
                    low++; // 左指针往前移动
                }
                else if (curSum < sum) // 右指针需要往前移动
                {
                    high++;
                }
                else // 当前计数已经超过目标数了，向前移动
                {
                    low++;
                }
            }
            return resultList;
        }
```

**运行结果：** 

> 运行时间：24ms   
占用内存：3372k