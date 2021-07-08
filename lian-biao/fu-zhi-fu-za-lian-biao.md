# 复制复杂链表

[复杂链表的复制](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

请实现一个函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。

```javascript
function Clone(pHead)
{
    // write code here
    if(pHead === null) return pHead;
    let p1 = pHead;
    while(p1 !== null){
        let node = new RandomListNode(p1.label);
        node.next = p1.next;
        p1.next = node;
        p1 = node.next;
    }
    p1 = pHead;
    while(p1 !== null){
        let node = p1.next;
        if(p1.random) node.random = p1.random.next;
        p1 = node.next;
    }
    p1 = pHead;
    let p2 = pHead.next;
    while(p1.next !== null){
        let node = p1.next;
        p1.next = node.next;
        p1 = node;
    }
    return p2;
}
```

