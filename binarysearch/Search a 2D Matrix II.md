#Search a 2D Matrix II#

##题目##

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
For example,

Consider the following matrix:

	[
	  [1,   4,  7, 11, 15],
	  [2,   5,  8, 12, 19],
	  [3,   6,  9, 16, 22],
	  [10, 13, 14, 17, 24],
	  [18, 21, 23, 26, 30]
	]
Given **target** = 5, return `true`.

Given **target** = 20, return `false`.

##代码##

	public class Solution {
	    public boolean searchMatrix(int[][] matrix, int target) {
	        if (matrix == null || matrix.length == 0) {
	            return false;
	        }
	        
	        if (matrix[0] == null || matrix[0].length == 0) {
	            return false;
	        }
	        
	        int rowBegin = 0;
	        int rowEnd = matrix.length - 1;
	        int colBegin = 0;
	        int colEnd = matrix[0].length - 1;
	        
	        
	        while(colEnd >= colBegin && rowBegin <= rowEnd) {
	            int temp = matrix[rowBegin][colEnd];
	            if(target == temp) {
	                return true;
	            }
	            else if (target < temp) {
	                colEnd--;
	            }
	            else if (target > temp) {
	                rowBegin++;
	            }
	        
	        }
	        
	        return false;
	    }
	}

##思路##

这道题目的难度主要在于并不是全部有序的，仅存在行有序与列有序，这时需要观察数组的特殊元素，例如四个角上的元素，并且选择的特殊元素能使用上有序的属性。那么左上角和右下角的元素就不合适了，左上角的元素是数组中最小的，右下角元素是数组中最大的。而右上角元素在这一行中是最大的，但在列中却是这一列最小的。左下角也一样，在列排序中是最大的，在行排序中是最小的。代码中选择的是右上角元素，在target小于该元素时，移动列下标，在更小的一列寻找target，而在target大于该元素时，那么移动行下标，在更大的一行寻找target