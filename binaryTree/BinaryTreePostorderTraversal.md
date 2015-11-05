#Binary Tree Postorder Traversal#

##题目##

Given a binary tree, return the postorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},
	
	   1
	    \
	     2
	    /
	   3

return [1,3,2].

Note: Recursive solution is trivial, could you do it iteratively?

##思路##

三种做法：1.非递归（推荐） 2.递归：遍历 3.递归：分治法

###非递归###

运用栈和迭代。值得注意的是，入栈的先后顺序，栈是先入后出的数据结构，为保证是中序遍历，所以右节点先入栈，然后左节点。

###递归：遍历###

运用遍历的方法

先左再右最后中

###递归：分治法###

运用分治法，这是大多数树问题均可使用的办法

分为左子树和右子树，不断地减小问题的规模

##代码##

	version 1：Non-recursion（recommended）
	
	version 2：Traversal
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
	    public List<Integer> postorderTraversal(TreeNode root) {
	        List<Integer> postorder = new ArrayList<Integer>();
	        traversal(root,postorder);
	        return postorder;
	    }
	    private void traversal(TreeNode root, List<Integer> postorder){
	        if (root == null){
	            return ;
	        }
	    traversal(root.left,postorder);
	    traversal(root.right,postorder);
	    postorder.add(root.val);
	    }
	}
	version 3：Divide & Conquer
	/**
	 * Definition for binary tree
	 * public class TreeNode {
	 *     int val;
	 *     TreeNode left;
	 *     TreeNode right;
	 *     TreeNode(int x) { val = x; }
	 * }
	 */
	public class Solution {
	    public List<Integer> postorderTraversal(TreeNode root) {
	        List<Integer> result = new ArrayList<Integer>();
	        if (root == null){
	            return result;
	        }
	        //Divide & Conquer
	        
	        //Divide
	        List<Integer> left = postorderTraversal(root.left);
	        List<Integer> right = postorderTraversal(root.right);
	        //Conquer
	        result.addAll(left);
	        result.addAll(right);
	       	result.add(root.val);

	        return result;
	    }
	}

