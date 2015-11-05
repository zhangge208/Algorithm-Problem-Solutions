#Leetcode@Gas Station#

##题目##

There are N gas stations along a circular route, where the amount of gas at station i is gas[i].

You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from station i to its next station (i+1). You begin the journey with an empty tank at one of the gas stations.

Return the starting gas station's index if you can travel around the circuit once, otherwise return -1.

**Note:**
The solution is guaranteed to be unique.

##思路##

基础的链表操作题目。首先考虑到头节点可能会被修改，所以要使用dummynode，然后根据判断条件进行remove即可，现指针节点为p，p的后继节点的值若与给定的val相等，则令p指向p后继的后继即可移除p现在的后继。注意边界条件的处理。

##代码##
	/**
	 * Definition for singly-linked list.
	 * public class ListNode {
	 *     int val;
	 *     ListNode next;
	 *     ListNode(int x) { val = x; }
	 * }
	 */
	public class Solution {
	    public ListNode removeElements(ListNode head, int val) {
	        if (head == null ){
	            return null;
	        }
	        ListNode dummy = new ListNode(-1);
	        dummy.next = head;
	        head = dummy;
	        while(head != null && head.next != null){
	            if (head.next.val == val){
	                head.next = head.next.next;
	            }
	            else{
	                head = head.next;
	            }
	        }
	        return dummy.next;
	    }
	}