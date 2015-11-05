#Leetcode@Remove Linked List Elements#

##题目##

Remove all elements from a linked list of integers that have value val.

**Example**

**_Given:_** 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6

**_Return:_** 1 --> 2 --> 3 --> 4 --> 5

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