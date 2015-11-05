#Binary Tree Inorder Traversal#

##题目##

Given a binary tree, return the inorder traversal of its nodes' values.

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

运用栈和迭代。值得注意的是，入栈的先后顺序，栈是先入后出的数据结构，为保证是中序遍历，首先需要对左子树进行迭代并将非空节点入栈，直到节点为空，当前节点为空时进行出栈操作，并访问栈顶节点，将当前节点用右子节点代替。
###递归：遍历###

运用遍历的方法

先左再中最后右

###递归：分治法###

运用分治法，这是大多数树问题均可使用的办法

分为左子树和右子树，不断地减小问题的规模

##代码##

	version 1：Non-recursion（recommended）
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
	    public List<Integer> inorderTraversal(TreeNode root) {
	        Stack<TreeNode> stack = new Stack<TreeNode>();
	        List<Integer> result = new ArrayList<Integer>();
	        TreeNode cur = root;
	        while (cur != null || !stack.empty()){
	            while(cur != null){
	                stack.push(cur);
	                cur = cur.left;
	            }
	            cur = stack.pop();
	            result.add(cur.val);
	            cur = cur.right;
	            
	        }
	        return result;
	    }
	}

	version 2：Traversal
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
	    public List<Integer> inorderTraversal(TreeNode root) {
	        List<Integer> inorderTraversal = new ArrayList<Integer>();
	        traversal(root,inorderTraversal);
	        return inorderTraversal;
	    }
	    private void traversal(TreeNode root,List<Integer> result){
	        if (root == null){
	            return;
	        }
	        
	        traversal(root.left,result);
	        result.add(root.val);
	        traversal(root.right,result);
	        
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
	    public List<Integer> inorderTraversal(TreeNode root) {
	        List<Integer> result = new ArrayList<Integer>();
	        if (root == null){
	            return result;
	        }
	        //Divide & Conquer
	        
	        //Divide
	        List<Integer> left = inorderTraversal(root.left);
	        List<Integer> right = inorderTraversal(root.right);
	        //Conquer
	        result.addAll(left);
	        result.add(root.val);
	        result.addAll(right);
	        
	        return result;
	    }
	}

