#Permutations#

##题目##

Given a collection of numbers, return all possible permutations.

For example,
`[1,2,3]` have the following permutations:
`[1,2,3]`, `[1,3,2]`, `[2,1,3]`, `[2,3,1]`, `[3,1,2]`, and `[3,2,1]`.

##代码##

	public class Solution {
	    public List<List<Integer>> permute(int[] nums) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        if (nums == null && nums.length == 0){
	            return result;
	        }
	        
	        List<Integer> list = new ArrayList<Integer>();
	        permuteHelper(result, list, nums);
	        return result;
	    }
	    private void permuteHelper(List<List<Integer>> result, List<Integer> list, int[] nums){
	        if (list.size() == nums.length) {
	            result.add(new ArrayList<Integer>(list));
	        }
	        
	        for(int i = 0; i < nums.length; i++) {
	            if (list.contains(nums[i])) {
	                continue;
	            }
	            list.add(nums[i]);
	            permuteHelper(result, list, nums);
	            list.remove(list.size() - 1);
	        }
	    }
	}

##思路##

