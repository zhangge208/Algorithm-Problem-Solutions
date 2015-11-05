#Search a 2D Matrix #

##题目##

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.
For example,

Consider the following matrix:
	
	[
	  [1,   3,  5,  7],
	  [10, 11, 16, 20],
	  [23, 30, 34, 50]
	]

Given **target** = `3`, return `true`.

##代码##

	public class Solution {
	    public boolean searchMatrix(int[][] matrix, int target) {
	        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
	            return false;
	        }
	        int row = matrix.length;
	        int col = matrix[0].length;
	        int start = 0;
	        int end = row * col - 1;
	        while (start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            int x = mid / col ;
	            int y = mid % col ;
	            if (matrix[x][y] == target) {
	                end = mid;
	            }
	            else if (matrix[x][y] < target) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        if (matrix[start / col][start % col] == target) {
	            return true;
	        }
	        if (matrix[end / col][end % col] == target) {
	            return true;
	        }
	        
	        return false;
	    }
	}

##思路##

参考Python中用列表表示多维数组的想法，可以将整个二维数组展成一维的数组，这样直接使用二分搜索就可以了。一个小trick，如何用mid表示二维数组的下标呢？行下标为mid / col,列下标为mid % col