## 第四十二题 和为S的两个数字

### 题目描述

>  输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

### 返回值描述:

> 对应每个测试案例，输出两个数，小的先输出。

### 法一：两指针往中间靠拢

**思路：** 既然是递增数组，那么头尾各设置一个指针，如果两者和等于sum，直接返回，如果大于sum，那么表明尾指针可能太大了，往左边走一位。反之，头指针往右边走一位，直到头指针大于尾指针。

**代码：** 

```C#
        public List<int> FindNumbersWithSum(int[] array, int sum)
        {
            List<int> resultList = new List<int>();

            if (array == null || array.Length < 2)
                return resultList;

            int i = 0, j = array.Length - 1; // 设置两个指针，往中间靠拢
            while (i < j)
            {
                if (array[i] + array[j] == sum)
                {
                    resultList.Add(array[i]);
                    resultList.Add(array[j]);
                    return resultList;
                }
                else if (array[i] + array[j] > sum)
                {
                    j--; // 和超过sum了，往小的那边走一位
                }
                else
                {
                    i++;
                }
            }
            return resultList;
        }
```

**运行结果：** 

> 运行时间：25ms   
占用内存：3280k