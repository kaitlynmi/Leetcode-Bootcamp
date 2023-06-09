# LeetCode Bootcamp Day 4  
 with 代码随想录  
  [Table of Contents](./README.md)  
  [prev](./Day3.md) <--> [next](./Day5.md) 


### 前言

The  algorithms we visited today are **1** and **2**.


## [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)  
Editorial: [24. 两两交换链表中的节点](https://programmercarl.com/0024.%E4%B8%A4%E4%B8%A4%E4%BA%A4%E6%8D%A2%E9%93%BE%E8%A1%A8%E4%B8%AD%E7%9A%84%E8%8A%82%E7%82%B9.html#_24-%E4%B8%A4%E4%B8%A4%E4%BA%A4%E6%8D%A2%E9%93%BE%E8%A1%A8%E4%B8%AD%E7%9A%84%E8%8A%82%E7%82%B9)  
Solution : [Iterative](./24.java)/Recursive
> 挺easy的。就是考验在特殊情况的variable互换。


### Approach 1: Iterative 
Visualizing the process is very helpful!
![24_iterative](./24.png)

### Approach 2: Recursive 
TBC

## [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  
Editorial: [19.删除链表的倒数第N个节点](https://programmercarl.com/0019.%E5%88%A0%E9%99%A4%E9%93%BE%E8%A1%A8%E7%9A%84%E5%80%92%E6%95%B0%E7%AC%ACN%E4%B8%AA%E8%8A%82%E7%82%B9.html#_19-%E5%88%A0%E9%99%A4%E9%93%BE%E8%A1%A8%E7%9A%84%E5%80%92%E6%95%B0%E7%AC%ACn%E4%B8%AA%E8%8A%82%E7%82%B9)  
Solution: [Recursive](./19.java)  / Two Pointers

> 第一反应是用recursive call。因为它自然的就会从后往前数。但是在找到node后，在怎么修改和返回这个object的时候卡住了。
> 一开始想把找到的Node 传回主程序做修改，但是会打乱整个递归的格式。最后决定在找到node以后直接对原来的list做修改。
>
> 双指针的解法也很取巧。二刷要用双指针解出来。


### Approach 1: Two Pointers
This is a classic application of the two-pointer technique. To delete the nth node from the end of a linked list, we can use two pointers: fast and slow.

The process involves the following steps:

1. Both fast and slow pointers are set to the head of the linked list.

2. Move the fast pointer n steps ahead in the linked list. 

3. After moving the fast pointer, both fast and slow pointers are moved simultaneously until the fast pointer reaches the end of the linked list. This is done by advancing both pointers one node at a time.

4. At this point, the slow pointer will be pointing to the n-th node from the end of the list.

5. Delete the node pointed to by the slow pointer.

By following this approach, we effectively find the node to be deleted by maintaining a specific distance between the fast and slow pointers. The length between the fast and slow points is equivalent to the n.This eliminates the need to traverse the list multiple times or use additional data structures.

### Approach 2: Recursive
The `removeNthFromEnd` function creates a dummy node. It then calls the nthFromEnd function to find the node that needs to be deleted. 

The `nthFromEnd` helper function recursively traverses the linked list until it reaches the end, keeping track of the position (nth) of each node from the end.

When the nth position matches the target n value, the function updates the next pointer of the current node to skip the node that needs to be deleted.

### Approach 3: Two pass
Not recommended.  
Iterate once to find size L of the list. iterate twice to remove the `(L−n+1)` th node from the beginning in the list.


## [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)  
Editorial: []()  
Solution: [Two Pointers](./LC160_twoPointer.java)/Hashtable  

> 要注意观察input里的规律和规则。这道题就是要找两个list末尾处相等的地方。那length不一的部分就可以无视。  
> 比较两个node可以时候可以直接比较地址，来确定两个reference指向的是不是同一个节点


### Approach 1: Two Pointers
1. Calculate N; the length of list A.
2. Calculate M; the length of list B.
3. Set the start pointer for the longer list.
4. Step the pointers through the list together.  

Time complexity : O(N+M)  
Space complexity : O(1)  

### Approach 2: Simplied Two Pointers
If we say that c is the shared part, a is exclusive part of list A and b is exclusive part of list B, then we can have one pointer that goes over a + c + b and the other that goes over b + c + a.
```java
public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode pA = headA;
        ListNode pB = headB;
        while (pA != pB) {
            pA = pA == null ? headB : pA.next;
            pB = pB == null ? headA : pB.next;
        }
        return pA;
    }
```
Note: In the case lists do not intersect, the pointers for A and B
    will still line up in the 2nd iteration, just that here won't be
    a common node down the list and both will reach their respective ends
    at the same time. So pA will be NULL in that case.

### Approach 3: Hashtable
Time complexity : O(N+M).  
Space complexity : O(M).  
More sufficient solution
TBC

## [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)  
Editorial: [142.环形链表II](https://programmercarl.com/0142.%E7%8E%AF%E5%BD%A2%E9%93%BE%E8%A1%A8II.html)  
Solution: [Solution](./)  

> 


### Approach 1: HashTable
```java
public ListNode detectCycle(ListNode head) {
    Set<ListNode> visited = new HashSet<ListNode>();

    ListNode node = head;
    while (node != null) {
        if (visited.contains(node)) {
            return node;
        }
        visited.add(node);
        node = node.next;
    }

    return null;
}
```
Remembering every node we encoutered, and returns a node when we find a duplicate.

Time and space complexity: O(n)

### Approach 2: 2 pointers (龟兔赛跑)
>很多数学细节， 后面再看视频过一遍写笔记


