# 剑指 Offer 06. 从尾到头打印链表

## 题目

```JavaScript
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

示例 1：

输入：head = [1,3,2]
输出：[2,3,1]
 

限制：

0 <= 链表长度 <= 10000

相关标签
链表
```

## 题解

### 栈

```JavaScript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {number[]}
 */
var reversePrint = function(head) {
    const res = [];
    let _point = head;

    while(_point !== null){
        res.push(_point.val)
        _point = _point.next;
    }

    return res.reverse();
};
```
