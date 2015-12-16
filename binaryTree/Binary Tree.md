#Binary Tree#

**Note:**讲义的思路为参加[九章算法](http://www.jiuzhang.com)培训学习，部分代码、模板均有所参考

特别感谢前辈：[http://www.shuatiblog.com/](http://www.shuatiblog.com/)

##Outline##

1.Binary Tree DFS Traversal
  
　-preorder/inorder/postorder

　-Divide & Conquer

　-DFS Template
 
2.Binary Tree BFS Traversal
 
　-BFS Template

3.Binary Search Tree


##Binary Tree DFS Traversal##

###三种基本遍历方法###

	    A
       / \
      B   C
     / \  
    D   E

前序(Preorder)：A BDE C

中序(Inorder)：DBE A C

后序(Postorder)：DEB C A

###递归 or 非递归？###

递归的办法会很简单，一般来说不推荐，然而，Done is better than Perfect！

###Divide & Conquer Algorithm###

**Merge Sort**

**Quick Sort**

**适用于大多数的Binary Tree Problem**

分治法对于二叉树问题，进行如下的操作：

1.**Divide**：对于左右子树分别去同时处理，将原问题划分成为更小的子问题

2.**Conquer**：将子问题的解合并，返回问题的解

###Binary Tree DFS Template###

	Template 1:Traverse

	public class Solution {
		public void traverse(TreeNode root) {
			if (root == null) {
				return ;
			}
		//do something with root
		traverse(root.left);
		//do something with root
		traverse(root.right);
		//do something with root
		}
	}
	
	Template 2:Divide & Conquer
	
	public class Solution {
		public ResultType traversal(TreeNode root) {
			// null or leaf
			if (root = null) {
				//do something and return;
			}

			//Divide
			ResultType left = traversal(root.left);
			ResultType right = traversal(root.right);

			//Conquer
			ResultType result = Merge from left and right;
			return result;
		}
	}

###Problem List###

**Traversal**

[Binary Tree Preorder Traversal](http:)

[Binary Tree Inorder Traversal](http:)

[Binary Tree Postorder Traversal](http:)

**Divide & Conquer**

[Maximum Depth of Binary Tree](http:)

[Minimum Depth of Binary Tree](http:)

[Balanced Binary Tree](http:)

[Binary Tree Maximum Path Sum](http:) – **the most important question** 








