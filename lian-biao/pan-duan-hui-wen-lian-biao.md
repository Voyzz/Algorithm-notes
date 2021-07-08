# 判断回文链表

## 回文链表

### 题目

```text
请判断一个链表是否为回文链表。

示例 1:

输入: 1->2
输出: false
示例 2:

输入: 1->2->2->1
输出: true
```

### 题解

* 首先，寻找回文串是从中间向两端扩展，判断回文串是从两端向中间收缩。对于单链表，无法直接倒序遍历，可以造一条新的反转链表，可以利用链表的后序遍历，也可以用栈结构倒序处理单链表。
* 具体到回文链表的判断问题，由于回文的特殊性，可以不完全反转链表，而是仅仅反转部分链表，将空间复杂度降到 O\(1\)。

#### 递归

```javascript
var isPalindrome = function(head) {
    let preorder = "",
        postorder = "";
    const dfs = (node) => {
        if(node == null) return;
        preorder += node.val;
        dfs(node.next);
        postorder += node.val;
    }
    dfs(head);
    return preorder === postorder;
};
```

#### 双指针

```javascript
//1. 将前半部分链表反转
//2. 判断前后两部分链表是否相等
var isPalindrome = function(head) {
    if(!head) return true;
    let pre = null,temp,fast = head,slow = head;
    while(fast && fast.next){
        fast = fast.next.next;
        // 反转链表
        temp = slow;
        slow = slow.next;
        temp.next = pre;
        pre = temp;
    }
    if(fast) slow = slow.next;
    while(pre && slow){
        if(pre.val !== slow.val) return false;
        pre = pre.next;
        slow = slow.next;
    }
    return true;
};
```

