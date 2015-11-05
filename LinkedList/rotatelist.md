#Leetcode@Rotate List#

##题目##
Given a list, rotate the list to the right by k places, where k is non-negative.

For example:
Given `1->2->3->4->5->NULL` and k = `2`,
return `4->5->1->2->3->NULL`.

##思路##
把问题分割，题目要求部分翻转，那么首先要得到开始翻转的位置
这与Remove Nth Node From End of List的思路一致，运用快慢指针，得到要翻转的位置，这部分问题解决。然后就是链表的连接，由于翻转后并不知道头节点是谁，所以需要dummy node来解决这一问题。然后画个图，搞清每一步的连接。链表连接的问题还是要多画图分析。
题目中有个小陷阱，就是翻转位置标识k，并没有说明k有多大，所以需要进行取余操作，那么就先需要知道链表的长度，链表长度的得到是很简单的，遍历一遍，拿一个计数器记录就好。
关于边界的考虑，一定要记得异常处理，首先是链表判空；然后在进行快慢指针的过程时，要保证fast->next不为空；在获取链表长度时也需要让链表head！= NULL。


##代码##
	class Solution {
	public:
    	ListNode *rotateRight(ListNode *head, int k) {
        	if(head == NULL )
        	{
            	return head;
        	}
        
        	int length = getlength(head);
        	k = k % length;
        
        	ListNode *dummy = new ListNode(-1);
        	dummy->next = head;
        	head = dummy;
        
        	ListNode *fast = dummy;
        	ListNode *slow = dummy;
        
        	for(int i = 0; i < k; i++)
        	{
        	    fast = fast->next;
        	}
        
        	while(fast->next != NULL)
        	{
        	    fast = fast->next;
        	    slow = slow->next;
        	}
        
        	fast->next = dummy->next;
        	dummy->next = slow->next;
        	slow->next = NULL;
        	return dummy->next;
    	}
	private:
    	int getlength(ListNode *head)
    	{
        	int length = 0;
        
        	while(head != NULL)
        	{
        	    length++;
            	head = head->next;
        	}
        	return length;
    	}
	};