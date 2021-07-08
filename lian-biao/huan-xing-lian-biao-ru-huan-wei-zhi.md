# 环形链表入环位置

## LeetCode 142. 环形链表 II

[LeetCode 142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)

### 题目

```text
给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意，pos 仅仅是用于标识环的情况，并不会作为参数传递到函数中。

说明：不允许修改给定的链表。

进阶：

你是否可以使用 O(1) 空间解决此题？


示例 1：

输入：head = [3,2,0,-4], pos = 1
输出：返回索引为 1 的链表节点
解释：链表中有一个环，其尾部连接到第二个节点
示例 2：

输入：head = [1,2], pos = 0
输出：返回索引为 0 的链表节点
解释：链表中有一个环，其尾部连接到第一个节点。

示例 3：

输入：head = [1], pos = -1
输出：返回 null
解释：链表中没有环。
```

### 题解

#### 快慢指针

```javascript
var detectCycle = function(head) {
    let _slow = head,
        _fast = head,
        _pre = head,
        _meet;

    // 确定是否有环，确定快慢指针相遇点
    while(_fast){
        if(_fast.next == null) return null;
        _fast = _fast.next.next;
        _slow = _slow.next;
        if(_fast == _slow){
            _meet = _fast;
            break;
        }
    }

    // 确定环入口
    if(_fast){
        while(true){
            if(_pre == _meet) return _pre;
            _pre = _pre.next;
            _meet = _meet.next;
        }
    }else{
        return null;
    }

};
```

