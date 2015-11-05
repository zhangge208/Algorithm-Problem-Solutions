Title:Subsets II
Date:2015-10-13
Category:Algorithm Backtracking
Tags:Algorithm Backtracking
Author:zhangge208

---

#Subsets II# 

##Problem##

Given a collection of integers that might contain duplicates, nums, return all possible subsets.

Note:
- Elements in a subset must be in non-descending order.

- The solution set must not contain duplicate subsets.

For example,

If **nums** = `[1,2,2]`, a solution is:

	[
	  [2],
	  [1],
	  [1,2,2],
	  [2,2],
	  [1,2],
	  []
	]
##Code##
	
	public class Solution {
	    public List<List<Integer>> subsetsWithDup(int[] nums) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        
	        if (nums == null || nums.length == 0) {
	            return result;
	        }
	        
	        Arrays.sort(nums);
	        List<Integer> list = new ArrayList<Integer>();
	        helper(result, list, nums, 0);
	        return result;
	    }
	    private void helper(List<List<Integer>> result, List<Integer> list, int[] nums, int pos) {
	        result.add(new ArrayList<Integer>(list));
	        for (int i = pos; i < nums.length; i++) {
	            if ( i != pos && nums[i] == nums[i - 1]) {
	                continue;
	            }
	            list.add(nums[i]);
	            helper(result, list, nums, i + 1);
	            list.remove(list.size() - 1);
	        }
	
	    }
	}

##Solution and Analysis##

The main part of code is same as the subset template，


For example，input = {1，2(1)，2(2)，2(3)}

Initialize the subset: {}

Added element “1”: {}, **{1}** 

Added element “2”: {}, {1}, **{2(1)}**

{1, 2(1)}, {1, 2(2)} are duplicate subset, {1,2(1),2(2)}, {1,2(2),2(3)} are iterant, too. 

We arrive ar a conclusion:we are only concerned with getting how many '2' rather than get which '2'  


