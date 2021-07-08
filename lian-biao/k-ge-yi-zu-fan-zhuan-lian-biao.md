# K 个一组翻转链表



## K 个一组翻转链表

### 题目

```text
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。
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
 * @param {number} k
 * @return {ListNode}
 */
var reverseKGroup = function(head, k) {
    if(head == null) return null;
    let a = head,
        b = head;
    // base case: 节点数小于k时直接返回原链表
    for(let i=0;i<k;i++){
        if(b == null) return head;
        b = b.next;
    }
    // 重新拼接新链表
    const _last = reverseFrag(a,b);
    a.next = reverseKGroup(b,k);
    return _last;
};

// 反转两节点间的链表（左闭右开）
const reverseFrag = function(_start,_end){
    let _pre = null,
        _curr = _start;

    while(_curr != _end){
        const _tmp = _curr.next;
        _curr.next = _pre;
        _pre = _curr;
        _curr = _tmp;
    }

    return _pre;
}
```

