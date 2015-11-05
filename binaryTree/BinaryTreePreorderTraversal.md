#Binary Tree Preorder Traversal#

##题目##

Given a binary tree, return the preorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},

	　　1
	 　　\
	  　　2
     　　/
    　　3
return [1,2,3].

Note: Recursive solution is trivial, could you do it iteratively?

##思路##

三种做法：1.非递归（推荐） 2.递归：遍历 3.递归：分治法

###非递归###

运用栈和迭代。值得注意的是，左右节点入栈的先后顺序，栈是先入后出的数据结构，为保证是前序遍历，所以右节点先入栈，然后左节点。

###递归：遍历###

运用遍历的方法

先根再左最后右

###递归：分治法###

运用分治法，这是大多数树问题均可使用的办法

分为左子树和右子树，不断地减小问题的规模

**值得注意：**
(1)容器中addAll方法的使用，把一个容器中的所有元素加入到另一个容器的后面。
 
　　　　　　(2)记得对于边界条件的处理、异常处理。

##代码##
	version 1：Non-recurison
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
	    public List<Integer> preorderTraversal(TreeNode root) {
	        Stack<TreeNode> stack = new Stack<TreeNode>();
	        List<Integer> preorder = new ArrayList<Integer>();
	        
	        if (root == null){
	            return preorder;
	        }
	        
	        stack.push(root);
	        
	        while (!stack.empty()){
	            TreeNode node = stack.pop();
	            preorder.add(node.val);
	            
	            if (node.right != null){
	                stack.push(node.right);
	            }
	            if (node.left != null){
	                stack.push(node.left);
	            }
	        }
	        return preorder;
	    }
	}
		
	
	version 2：Traverse
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
	    public List<Integer> preorderTraversal(TreeNode root) {
	        ArrayList<Integer> preorder = new ArrayList<Integer>();
	        traverse(root,preorder);
	        return preorder;
	    }
	    private void traverse(TreeNode root, ArrayList<Integer>preorder){
	        if (root == null){
	            return ;
	        }
	        
	        preorder.add(root.val);
	        traverse(root.left,preorder);
	        traverse(root.right, preorder);
	        
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
	    public List<Integer> preorderTraversal(TreeNode root) {
	        ArrayList<Integer> result = new ArrayList<Integer>();
	        if (root == null){
				return result;
			}
			//Divide & Conquer
	        
	        //Divide
	        ArrayList<Integer> left = preorderTraversal(root.left);
	        ArrayList<Integer> right = preorderTraversal(root.right);
	        
	        //Conquer
	        result.add(root.val);
	        result.addAll(left);
	        result.addAll(right);
	        return result;
	    }
	}
