# 反转链表部分链表

## 反转链表 II

### 题目

```text
反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

说明:
1 ≤ m ≤ n ≤ 链表长度。

示例:

输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL
```

### 题解

#### 递归

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} left
 * @param {number} right
 * @return {ListNode}
 */
var reverseBetween = function(head, left, right) {
    if(!head) return null;
    // 当left=1的时候就转换为了翻转前n个结点
    if(left === 1)  return reverseN(head,right);
    // left前的结点不变，直至left变为1
    head.next = reverseBetween(head.next,left-1,right-1);
    return head;
};

let successor = null;
const reverseN = function(head,n){
    if(!head) return null;
    if(n == 1){
        // 记录后置结点
        successor = head.next;
        return head;
    }
    // 下一节点的翻转前n-1个结点后的头结点
    const _last = reverseN(head.next,n-1);
    // 重新链接head结点
    head.next.next = head;
    head.next = successor;
    return _last;
}
```

