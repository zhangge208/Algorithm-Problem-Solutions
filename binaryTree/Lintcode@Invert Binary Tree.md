#Leetcode@Invert Binary Tree#

##题目##
Invert a binary tree.

	     4
	   /   \
	  2     7
	 / \   / \
	1   3 6   9

to
    
	     4
	   /   \
	  7     2
	 / \   / \
	9   6 3   1

##思路##

非递归的还没想出来，不会做，那就来递归的吧先，递归很简单，交换左右节点就跟交换a,b两个数一样，需要一个中间变量，先把左子树的指针赋给中间变量，然后交换。

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
	    public TreeNode invertTree(TreeNode root) {
	        if (root == null){
	            return root;
	        }
	        
	        TreeNode temp = root.left;
	        root.left = root.right;
	        root.right = temp;
	        invertTree(root.left);
	        invertTree(root.right);
	        return root;
	    }
	}
		
