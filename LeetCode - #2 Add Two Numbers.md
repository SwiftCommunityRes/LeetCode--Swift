## 前言

我们社区从本期开始会将顾毅（**Netflix 增长黑客，《iOS 面试之道》作者，ACE 职业健身教练。微博:@故胤道长**）的 Swift 算法题题解整理为文字版以方便大家学习与阅读。

不积跬步，无以至千里；不积小流，无以成江海，Swift社区 伴你前行。

> 难度水平：中等

## 描述

已知两个非负整数（`例如：l1 = 342，l2 = 465`），将数字分别按相反的顺序存储到链表中（`例如：l1 = [2,4,3]，l2 = [5,6,4]`），每个节点都包含一个数字，将两个数字相加并将总和作为链表返回（`例如：[7,0,8]`）。

假设这两个数字不包含任何前导零(`例如：`~~012~~)，除了数字 0 本身。

## 示例

**示例 1**

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7e825f8225274c4888fb02183f163807~tplv-k3u1fbpfcp-zoom-1.image)

```
输入：l1 = [2,4,3]，l2 = [5,6,4]
产出：[7,0,8]
说明：342 + 465 = 807
```

**示例 2**

```
输入：l1 = [0]，l2 = [0]
产出：[0]
```

**示例 3**

```
输入：l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
产出：[8,9,9,9,0,0,0,1]
```

**限制**

* 每个链表中的节点数在 [1, 100] 范围内
* 0 <= 节点值 <= 9
* 保证列表中没有前导零的数字

## 答案

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */
class AddTwoNumbers {
    func addTwoNumbers(l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        guard let l1 = l1 else {return l2}
        guard let l2 = l2 else {return l1}
        
        let outputNode = ListNode((l1.val + l2.val)%10)
        if l1.val + l2.val > 9 {
            outputNode.next = addTwoNumbers(addTwoNumbers(l1.next, l2.next),
                                            ListNode(1))
        } else {
            outputNode.next = addTwoNumbers(l1.next, l2.next)
        }
        return outputNode
    }
}
```

* 主要思想：使用进位并遍历两个链表
* 时间复杂度：O(n)
* 空间复杂度：O(1)

点击前往 [LeetCode](https://leetcode.com/problems/add-two-numbers/) 练习

该算法题解的 github 仓库地址是：[https://github.com/soapyigu/LeetCode-Swift](https://github.com/soapyigu/LeetCode-Swift "LeetCode-Swift")