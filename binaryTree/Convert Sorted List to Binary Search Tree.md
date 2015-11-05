#Convert Sorted List to Binary Search Tree#

##题目##

Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

##思路##

与[Convert Sorted Array to Binary Search Tree](http://www.zhangge208.com/pages/2015/06/29/leetcodeconvert-sorted-array-to-binary-search-tree.html)的思路很像，首先是得找到根节点，但考虑到是链表，没法直接到中间的元素，只能依次移动指针，联想到中序遍历与BST的关系，我们依据inorder来构造BST，前半部分为左子树，然后根节点，后半部分为右子树。

##代码##

	/**
	 * Definition for singly-linked list.
	 * public class ListNode {
	 *     int val;
	 *     ListNode next;
	 *     ListNode(int x) { val = x; }
	 * }
	 */
	/**
	 * Definition for a binary tree node.
	 * public class TreeNode {
	 *     int val;
	 *     TreeNode left;
	 *     TreeNode right;
	 *     TreeNode(int x) { val = x; }
	 * }
	 */
	public class Solution {
	    private ListNode current;
	    
	    public TreeNode sortedListToBST(ListNode head) {
	        int size = getLength(head);
	        current = head;
	        return sortedListToBSTHelper(size);
	        
	    }
	    
	    private int getLength(ListNode head){
	        int length = 0;
	        while(head != null ){
	            length++;
	            head = head.next;
	        }
	        return length;
	    }
	    
	    public TreeNode sortedListToBSTHelper(int size){
	        if (size <= 0){
	            return null;
	        }
	        
	        TreeNode left = sortedListToBSTHelper(size/2);
	        TreeNode root = new TreeNode(current.val);
	        current = current.next;
	        TreeNode right = sortedListToBSTHelper(size - 1 -size/2);
	        root.left = left;
	        root.right =right;
	        
	        return root;
	    }    
	}