#Convert Sorted Array to Binary Search Tree#

##题目##

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

##思路##

按照题目要求，第一想法是得到树的根节点，如果没有构建平衡二叉搜索树的要求，那很容易，联想BST和binary search的关系，选择排序数组中间元素作为根节点，元素左边的全部元素作为左子树，右边全部元素作为右子树，然后用同样的方法寻找根节点，递归。

需要注意对边界的处理，必须满足BST的定义。

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
	    public TreeNode sortedArrayToBST(int[] nums) {
	        if (nums == null){
	            return null;
	        }
	        
	        return buildTree(nums, 0, nums.length - 1);
	    }
	    private TreeNode buildTree(int[] nums, int start, int end){
	        if (start > end) {
	            return null;
	        }
	        
	        TreeNode node = new TreeNode(nums[(end + start) / 2 ]);
	        node.left = buildTree(nums,start, (end + start) / 2 - 1);
	        node.right = buildTree(nums,(end + start) / 2 + 1, end);
	        
	        return node;
	    }    
	        
	}
