# 复制带随机指针的链表

[复制带随机指针的链表](https://leetcode-cn.com/problems/copy-list-with-random-pointer/)

给定一个链表，每个节点包含一个额外增加的随机指针，该指针可以指向链表中的任何节点或空节点

```javascript
var copyRandomList = function(pHead) {
    if(pHead === null) return pHead;
    let p1 = pHead;
    while(p1 !== null){
        let node = new Node(p1.val);
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
};

```

