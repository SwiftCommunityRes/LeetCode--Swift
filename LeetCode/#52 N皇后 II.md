![](https://upload-images.jianshu.io/upload_images/2829694-8d80389416deefc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 前言

我们社区陆续会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:@故胤道长**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

LeetCode 算法到目前我们已经更新了 51 期，我们会保持更新时间和进度（**周一、周三、周五早上 9:00 发布**），每期的内容不多，我们希望大家可以在上班路上阅读，长久积累会有很大提升。

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。**如果大家有建议和意见欢迎在文末留言，我们会尽力满足大家的需求。**

> 难度水平：困难

## 1. 描述

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n × n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回 **n 皇后问题** 不同的解决方案的数量。

## 2. 示例

**示例 1**

```
输入：n = 4
输出：2
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

**示例 2**

```
输入：n = 1
输出：1
```

**约束条件：**

- `1 <= n <= 9`

## 3. 答案

```swift
class NQueensII {
    func totalNQueens(_ n: Int) -> Int {
        guard n > 0 else {
            return 0
        }
        var count = 0
        var usedCols = Array(repeating: 0, count: n)
        
        dfs(&usedCols, &count, n, 0)
        
        return count
    }
    
    private func dfs(_ usedCols: inout [Int], _ count: inout Int, _ n: Int, _ row: Int) {
        if row == n {
            count += 1
            return
        }
        
        for col in 0..<n {
            if isValid(usedCols, row, col) {
                usedCols[row] = col
                dfs(&usedCols, &count, n, row + 1)
            }
        }
    }
    
    private func isValid(_ usedCols: [Int], _ row: Int, _ col: Int) -> Bool {
        var c = -1
    
        for i in 0..<row {
            c = usedCols[I] 
            
            // check col
            if c == col {
                return false
            }
            
            if abs(c - col) == abs(i - row) {
                return false
            }
        }
        
        return true
    }
}
```

* 主要思想：经典的深度优先搜索，逐行填写，每次检查列和诊断，只需要关心使用哪个列。
* 时间复杂度： O(n^n)
* 空间复杂度： O(n)

该算法题解的仓库：[LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")

点击前往 [LeetCode](https://leetcode.com/problems/n-queens-ii/ "LeetCode") 练习

## 关于我们

我们是由 Swift 爱好者共同维护，我们会分享以 Swift 实战、SwiftUI、Swift 基础为核心的技术内容，也整理收集优秀的学习资料。

后续还会翻译大量资料到我们公众号，有感兴趣的朋友，可以加入我们。
