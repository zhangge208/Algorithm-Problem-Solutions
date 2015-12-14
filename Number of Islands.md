#Number of Islands#

##Problem##

Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**
	
	11110
	11010
	11000
	00000

Answer: 1

**Example 2:**
	
	11000
	11000
	00100
	00011

Answer: 3

##Code##

	public class Solution {
	    public int numIslands(char[][] grid) {
	        if (grid == null || grid.length == 0 || grid[0].length == 0 || grid[0] == null) {
	            return 0;
	        }
	        int count = 0;
	        
	        for (int i = 0; i < grid.length; i++) {
	            for (int j = 0;j <grid[0].length; j++) {
	                 if (grid[i][j] == '1') {
	                     helper(grid,i,j);
	                     count++;
	                 }
	            }
	        }
	        return count;
	    }
	    
	    private void helper(char[][] grid, int i, int j) {
	        if (i < 0 || j < 0 || i > grid.length - 1|| j > grid[0].length - 1 || grid[i][j] != '1'){
	            return;
	        }
	        grid[i][j] = '0';
	        helper(grid, i + 1, j);
	        helper(grid, i - 1, j);
	        helper(grid, i, j + 1);
	        helper(grid, i, j - 1);
	    }
	}

##Solution and Analysis##
BFS典型题目

坑： 先要保证数组本身不为null， 长度不为0，不能写成下面这样：

	if (grid == null || grid[0] == null || grid.length == 0 || grid[0].length == 0) {
            return 0;
    }

则会报错：Runtime Error 

	Runtime Error Message:
	Line 3: java.lang.ArrayIndexOutOfBoundsException: 0
	Last executed input:

follow up I：如果不是全一，而是有数字代表面积，求各岛屿的面积
follow up II：lintcode Number of Islands II