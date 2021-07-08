# 删除倒数第n个节点

```javascript
var removeNthFromEnd = function(head, n) {
    if(!head) return null;
    let fast = head,slow = head,pre = head,p1 = head,len = 0;
    while(p1){
        len++;
        p1 = p1.next;
    }
    //注意头节点删除的情况
    if(len === n) return head.next;
    while(n--){
        fast = fast.next;
    }
    while(fast){
        fast = fast.next;
        pre = slow;
        slow = slow.next;
    }
    pre.next = slow.next;
    return head;
};
```

