#Word Search#

##Problem##

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

For example,
Given **board** = 

	[
	  ['A','B','C','E'],
	  ['S','F','C','S'],
	  ['A','D','E','E']
	]

word = `"ABCCED"`, -> returns `true`,

word = `"SEE"`, -> returns `true`,

word = `"ABCB"`, -> returns `false`.

##Code##

	public class Solution {
	    public boolean exist(char[][] board, String word) {
	        if (board.length == 0 || board == null){
	            return false;
	        }
	        if (word == null){
	            return true;
	        }
	        
	        for (int i = 0; i < board.length;i++){
	            for (int j = 0; j < board[0].length; j++){
	                if (board[i][j] == word.charAt(0)){
	                    boolean res = find(board,word,i,j,0);
	                    if (res){
	                        return true;
	                    }
	                }
	            }
	        }
	        return false;
	    }
	    
	    
	    
	    private boolean find(char[][] board, String word, int i, int j, int start){
	        
	        if(start == word.length()){
	            return true;
	        }
	        if (i < 0 || i>= board.length || j < 0 || j >= board[0].length || board[i][j] != word.charAt(start)){
	            return false;
		    }
	        
	        board[i][j] = '#';
	        boolean rst = find(board, word, i-1, j, start+1) || find(board, word, i, j-1, start+1) || find(board, word, i+1, j, start+1) || find(board, word,i, j+1, start+1);
	        board[i][j] = word.charAt(start);
	        return rst;
	    }
	
	}

##Solution and Analysis##

This is a very classical DFS question. Writing this solution fast and precise is very importnt.

The solution is recursive DFS search.We should notice backtracking problem, remember using '#' to mark the point we have visited:
	
	board[i][j] = '#';

and before returning false，we must remark it back: 

	board[i][j] = word.charAt(start);