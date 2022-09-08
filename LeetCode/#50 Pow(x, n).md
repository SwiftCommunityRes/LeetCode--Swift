![](https://upload-images.jianshu.io/upload_images/2829694-8d80389416deefc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 前言

我们社区陆续会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:@故胤道长**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

LeetCode 算法到目前我们已经更新了 49 期，我们会保持更新时间和进度（**周一、周三、周五早上 9:00 发布**），每期的内容不多，我们希望大家可以在上班路上阅读，长久积累会有很大提升。

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。**如果大家有建议和意见欢迎在文末留言，我们会尽力满足大家的需求。**

> 难度水平：中等

## 1. 描述

实现 `pow(x, n)` ，即计算 `x` 的 `n` 次幂函数（即，`x^n` ）。

## 2. 示例

**示例 1**

```
输入：x = 2.00000, n = 10
输出：1024.00000
```

**示例 2**

```
输入：x = 2.10000, n = 3
输出：9.26100
```

**示例 3**

```
输入：x = 2.00000, n = -2
输出：0.25000
解释：2-2 = 1/22 = 1/4 = 0.25
```

**约束条件：**

- `-100.0 < x < 100.0`
- `-2^31 <= n <= 2^31-1`
- `-10^4 <= x^n <= 10^4`

## 3. 答案

```swift
class Pow {
    func myPow(x: Double, _ n: Int) -> Double {
        var x = x, n = n
    
        if n < 0 {
            x = 1.0 / x
            n = -n
        }

        var res = 1.0

        while n > 0 {
            if n % 2 != 0 {
                res *= x
            }
            x *= x
            n /= 2
        }

        return res
    }
}
```

* 主要思想：经典递归，先处理正负情况。
* 时间复杂度： O(logn)
* 空间复杂度： O(n)

该算法题解的仓库：[LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")

点击前往 [LeetCode](https://leetcode.com/problems/powx-n/ "LeetCode") 练习

## 关于我们

我们是由 Swift 爱好者共同维护，我们会分享以 Swift 实战、SwiftUI、Swift 基础为核心的技术内容，也整理收集优秀的学习资料。

后续还会翻译大量资料到我们公众号，有感兴趣的朋友，可以加入我们。
