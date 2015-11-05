#Palindrome Partitioning#

##Problem##

Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

For example, given s = `"aab"`,

Return

	[
    	["aa","b"],
    	["a","a","b"]
  	]

##Code##

	public class Solution {
	    public List<List<String>> partition(String s) {
	        List<List<String>> result = new ArrayList<List<String>>();
	        List<String> list = new ArrayList<String>();
	        helper(result, list, s, 0);
	        return result;
	    }
	    
	    private void helper(List<List<String>> result, List<String> list, String str, int pos) {
	        if (pos == str.length()) {
	            result.add(new ArrayList<String>(list));
	            return;
	        }
	        
	        for (int i = pos; i < str.length(); i++) {
	            String sub = str.substring(pos, i + 1);
	            if (isPartition(sub)) {
	                list.add(sub);
	                helper(result, list, str, i + 1);
	                list.remove(list.size() - 1);
	            }
	        }
	    }
	    
	    private boolean isPartition(String str) {
	        int left = 0, right = str.length() - 1;
	        while (left < right) {
	            if (str.charAt(left) != str.charAt(right)) 
	                return false;
	            left++;
	            right--;
	        }
	        return true;
	    }
	}

##Solution and Analysis##



