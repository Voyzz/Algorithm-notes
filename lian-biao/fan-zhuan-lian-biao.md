# 反转链表

## 剑指 Offer 24. 反转链表

### 题目

```text
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。



示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL


限制：

0 <= 节点个数 <= 5000



注意：本题与主站 206 题相同：https://leetcode-cn.com/problems/reverse-linked-list/

相关标签
链表
```

### 题解

#### 迭代

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
    let pre = head,
        curr = null;

    while (pre != null){
        const tmp = pre.next;
        pre.next = curr;
        curr = pre;
        pre = tmp;
    }

    return curr;
};
```

#### 递归

```typescript
function reverseList(head: ListNode | null): ListNode | null {
    if(!head || !head.next) return head;
    const last:ListNode = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return last;
};
```

