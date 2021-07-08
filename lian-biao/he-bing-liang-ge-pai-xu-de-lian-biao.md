# 合并两个排序的链表

## 剑指 Offer 25. 合并两个排序的链表

### 题目

```text
输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

示例1：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
限制：

0 <= 链表长度 <= 1000

注意：本题与主站 21 题相同：https://leetcode-cn.com/problems/merge-two-sorted-lists/

相关标签
分治算法
```

### 题解

#### 遍历

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    let preHead = new ListNode(-1);
    let _pre = preHead;

    while(l1 != null && l2 != null){
        if(l1.val < l2.val){
            _pre.next = l1;
            l1 = l1.next;
        }else{
            _pre.next = l2;
            l2 = l2.next;
        }
        _pre = _pre.next;
    }
    _pre.next = l1 == null ? l2 : l1;
    return preHead.next
};
```

#### 分治算法

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if(l1 == null){
        return l2
    }
    if(l2 == null){
        return l1
    }
    if(l1.val > l2.val){
        l2.next = mergeTwoLists(l2.next,l1);
        return l2
    }else{
        l1.next = mergeTwoLists(l1.next,l2);
        return l1
    }
};
```

