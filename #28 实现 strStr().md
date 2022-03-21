![](https://upload-images.jianshu.io/upload_images/2829694-8d80389416deefc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 前言

我们社区陆续会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:@故胤道长**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

LeetCode 算法到目前我们已经更新了 27 期，我们会保持更新时间和进度（**周一、周三、周五早上 9:00 发布**），每期的内容不多，我们希望大家可以在上班路上阅读，长久积累会有很大提升。

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。**如果大家有建议和意见欢迎在文末留言，我们会尽力满足大家的需求。**

> 难度水平：简单

## 1. 描述

实现 `strStr()` 函数。

给你两个字符串 `haystack` 和 `needle`，请你在 `haystack` 字符串中找出 `needle` 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  `-1` 。

**说明：**

当 `needle` 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 `needle` 是空字符串时我们应当返回 0 。这与 C 语言的 `strstr()` 以及 Java 的 `indexOf()` 定义相符。

## 2. 示例

**示例 1**

```
输入：haystack = "hello", needle = "ll"
输出：2
```

**示例 2**

```
输入：haystack = "aaaaa", needle = "bba"
输出：-1
```

**示例 3**

```
输入：haystack = "", needle = ""
输出：0
```

**约束条件：**

- `0 <= haystack.length, needle.length <= 5 * 10^4`
- `haystack` 和 `needle` 仅由小写英文字符组成
  
## 3. 答案

```swift
class StrStr {
    func strStr(_ haystack: String, _ needle: String) -> Int {
        let hChars = Array(haystack.characters), nChars = Array(needle.characters)
        let hLen = hChars.count, nLen = nChars.count
    
        guard hLen >= nLen else {
            return -1
        }
        guard nLen != 0 else {
            return 0
        }
        
        for i in 0...hLen - nLen {
            if hChars[i] == nChars[0] {
                for j in 0..<nLen {
                    if hChars[i + j] != nChars[j] {
                        break
                    }
                    if j + 1 == nLen {
                        return i
                    }
                }
            } 
        }
        
        return -1
    }
}
```

* 主要思想：保留一个索引，向前移动时将该索引处的元素与 val 进行比较
* 时间复杂度： O(nm)
* 空间复杂度： O(n)

该算法题解的仓库：[LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")

点击前往 [LeetCode](https://leetcode.com/problems/implement-strstr/ "LeetCode") 练习

## 关于我们

我们是由 Swift 爱好者共同维护，我们会分享以 Swift 实战、SwiftUI、Swift 基础为核心的技术内容，也整理收集优秀的学习资料。

后续还会翻译大量资料到我们公众号，有感兴趣的朋友，可以加入我们。
