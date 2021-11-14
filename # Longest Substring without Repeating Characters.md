## 前言

我们社区从本期开始会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:[@故胤道长](https://m.weibo.cn/u/1827884772 "@故胤道长")**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

该算法题解的 github 仓库地址是：[https://github.com/soapyigu/LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。

## 1. 描述

给定一个字符串 `s`, 找出最长未重复的子字符串的长度.


## 2. 示例

**示例 1**

```
输入： s = "abcabcbb"
输出： 3
解释： 最长为重复的子字符串答案是 "abc", 长度为 3.
```

**示例 2**

```
输入： s = "bbbbb"
输出： 1
解释： 最长为重复的子字符串答案是 "b", 长度为 1.
```

**示例 3**

```
输入： s = "pwwkew"
输出： 3
解释： 最长为重复的子字符串答案是 "wke", 长度为 3.
注意答案必须是自字符串,“pwke” 是一个子列,而不是一个自字符串.
```

**示例 4**

```
输入： s = ""
输出： 0
```
## 3. 答案

```swift
class LongestSubstringWithoutRepeatingCharacters {
    func lengthOfLongestSubstring(_ s: String) -> Int {
        var maxLen = 0, startIdx = 0, charToPos = [Character: Int]()
        let sChars = Array(s)
        
        for (i, char) in sChars.enumerated() {
            if let pos = charToPos[char] {
                startIdx = max(startIdx, pos)
            }
            
            // update to next valid position
            charToPos[char] = i + 1
            maxLen = max(maxLen, i - startIdx + 1)
        }
        
        return maxLen
    }
}

```

* 主要思想：使用字典存储非重复子字符串的下一个可能有效字符的位置,然后迭代字符串更新 maxLen、dictionary 和遇到重复时的 startIdx .
* 时间复杂度： O(n)
* 空间复杂度： O(n)

点击前往 [LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/) 练习