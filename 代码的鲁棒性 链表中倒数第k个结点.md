# 代码的鲁棒性 链表中倒数第k个结点

* 输入一个链表，输出该链表中倒数第k个结点。

* 双指针，pNode正常遍历链表，ansNode为滞后pNode距离k的结点，当pNode指向尾部null时，ansNode是该链表中倒数第k个结点。


```
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        if (k <= 0) {
            return null;
        }
        ListNode pNode = head;
        ListNode ansNode = null;
        int cnt = 0;
        while (pNode != null) {
            cnt++;
            pNode = pNode.next;
            if (cnt == k) {
                ansNode = head;
            }
            if (cnt > k) {
                ansNode = ansNode.next;
            }
        }
        return ansNode;
    }
}
```