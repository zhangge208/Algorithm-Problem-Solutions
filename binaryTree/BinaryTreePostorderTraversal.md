#Binary Tree Postorder Traversal#

##Problem##

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

##Code##

	version 1：Non-recursion（recommended）
	a) using two stacks
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
	        Stack<TreeNode> s1 = new Stack<TreeNode>();
	        Stack<TreeNode> s2 = new Stack<TreeNode>();
	        List<Integer> result = new ArrayList<Integer>();
	        if(root == null) {
	            return result;
	        }
	        s1.push(root);
	        while (!s1.empty()){
	            TreeNode node = s1.pop();
	            s2.push(node);
	            if(node.left != null) {
	                s1.push(node.left);
	            }
	            if(node.right != null) {
	                s1.push(node.right);
	            }
	        }
	        
	        while(!s2.isEmpty()) {
	            TreeNode cur = s2.pop();
	            result.add(cur.val);
	        }
	        return result;
	    } 
	}

	b) using one stack
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
	        Stack<TreeNode> s1 = new Stack<TreeNode>();
	        List<Integer> result = new ArrayList<Integer>();
	        if(root == null) {
	            return result;
	        }
	
	        TreeNode cur = root;
	        do {
	            while (cur != null) {
	                if (cur.right != null){
	                    s1.push(cur.right);  
	                }
	                
	                s1.push(cur);
	                cur = cur.left;
	            }
	            cur = s1.pop();
	            if (!s1.isEmpty() && cur.right != null && cur.right == s1.peek()) {
	                TreeNode node = s1.pop();
	                s1.push(cur);
	                cur = node;
	            }
	            else {
	                result.add(cur.val);  
	                cur = null;
	            }
	        } while (!s1.empty());   
	        return result;
	    } 
	}

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

##Solution and Analysis##

三种做法：1.非递归（推荐） 2.递归：遍历 3.递归：分治法

###递归：遍历###

运用遍历的方法

先左再右最后中

###递归：分治法###

运用分治法，这是大多数树问题均可使用的办法

分为左子树和右子树，不断地减小问题的规模

###非递归###

这应该是三种遍历方式中非递归实现最难的一道题目，有用两个栈实现与用一个栈实现两种方式，下面的参考资料讲得实在是太好了，
reference：

[Iterative Postorder Traversal | Set 1 (Using Two Stacks)](http://www.geeksforgeeks.org/iterative-postorder-traversal)

	算法流程：
	1.1 Create two empty stacks s1 and s2, push root into s1
	2.1 Do following while stack s1 is not empty
		a) Pop node from s1, and push this node into s2
		b) If the left child of node is not NULL, push node.left into s1
		c) If the right child of node is not NULL, push node.right into s1
	2.2 Do following while stach s2 is not empty
		Pop node from s2, and add it into result
  
[Iterative Postorder Traversal | Set 2 (Using One Stack)](http://www.geeksforgeeks.org/iterative-postorder-traversal-using-stack)

	算法流程：
	1.1 Create an empty stack
	2.1 Do following while root is not NULL
	    a) Push root's right child and then root to stack.
	    b) Set root as root's left child.
	2.2 Pop an item from stack and set it as root.
	    a) If the popped item has a right child and the right child 
	       is at top of stack, then remove the right child from stack,
	       push the root back and set root as root's right child.
	    b) Else print root's data and set root as NULL.
	2.3 Repeat steps 2.1 and 2.2 while stack is not empty.

