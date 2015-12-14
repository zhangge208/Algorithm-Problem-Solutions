#Minimum Path Sum#

##Problem##

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

##Code##

	public class Solution {
	    public int minPathSum(int[][] grid) {
	        if (grid == null || grid.length == 0) {
	            return 0;
	        }
	        int m = grid.length;
	        int n = grid[0].length;
	        int[][] f = new int[m][n];
	        f[0][0] = grid[0][0]; 
	        for (int i = 0; i < m - 1; i++) {
	            f[i + 1][0] = f[i][0] + grid[i + 1][0]; 
	        }
	        for (int i = 0; i < n - 1; i++) {
	            f[0][i + 1] = f[0][i] + grid[0][i + 1];
	        }
	        for (int i = 1; i < m; i++) {
	            for (int j = 1; j < n; j++) {
	                f[i][j] = Math.min(f[i - 1][j], f[i][j - 1]) + grid[i][j];
	            }
	        }
	        
	        return f[m - 1][n - 1];
	    }
	}

##Solution and Analysis##

state：f[i][j]表示到达点（i，j）时的最小和

function：f[i][j] = Math.min(f[i - 1][j], f[i][j - 1]) + grid[i][j];

initial：f[0][0] = grid[0][0];

answer：f[m - 1][n - 1]

Note：

- 边界的处理，在i = 0和j = 0时只有一种移动状态，即i = 0时，一直向右，j = 0时只能一直向下，所以边界的f[][]数组需要单独处理
