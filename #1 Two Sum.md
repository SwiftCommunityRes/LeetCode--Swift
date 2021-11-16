## 前言

我们社区从本期开始会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:[@故胤道长](https://m.weibo.cn/u/1827884772 "@故胤道长")**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。

> 难度水平：简单

## 1. 描述

已知一个整数数组 `nums` 和一个整数 `target`，取数组中任意两个值相加的和等 整数 `target`，返回这两个值在数组中的索引。

**假设：**

1. 只有一个有效答案
2. 同一个值不能重复取两次
3. 可以按任意顺序返回答案

## 2. 示例

**示例 1**

```
输入：nums = [2,7,11,15]，target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9，所以返回 [0, 1]
```

**示例 2**

```
输入：nums = [3,2,4]，target = 6
输出：[1,2]
```

**示例 3**

```
输入：nums = [3,3]，target = 6
输出： [0,1]
```

## 3. 答案

```swift
class TwoSum {
    func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
        var dict = [Int: Int]()
  
        for (i, num) in nums.enumerated() {
            if let lastIndex = dict[target - num] {
                return [lastIndex, i]
            }
    
            dict[num] = i
        }
  
        fatalError("No valid outputs")
    }
}
```

* 主要思想：遍历数组并在字典中存储目标 - nums[i]
* 时间复杂度：O(n)
* 空间复杂度：O(n)

点击前往 [LeetCode](https://leetcode.com/problems/two-sum/) 练习

该算法题解的 github 仓库地址是：[https://github.com/soapyigu/LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")