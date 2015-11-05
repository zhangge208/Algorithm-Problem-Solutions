#Leetcode@Validate Binary Search Tree#

##题目##

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys less - than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

##思路##
1.递归：设置上下限([http://blog.csdn.net/fightforyourdream/article/details/14444883](http://blog.csdn.net/fightforyourdream/article/details/14444883))，在递归左右子树时为它们设置最大值、最小值，如果节点值超过限定，肯定不是，然后下一次递归时将上下限继续传递下去

2.递归：分治法递归求解

3.非递归：栈实现，对树进行中序遍历，然后看是否从左到右有序

##代码##

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
	    public boolean isValidBST(TreeNode root) {
	       return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
	    }
	    
	    private boolean isValidBST(TreeNode root, long min, long max){
	        if (root == null){
	            return true;
	        }
	        
	        if (root.val <= min || root.val >= max){
	            return false;
	        }
	        
	        return isValidBST(root.left,min,root.val) && isValidBST(root.right,root.val,max);
	    }
	}
