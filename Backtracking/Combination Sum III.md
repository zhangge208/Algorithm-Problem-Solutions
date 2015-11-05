#Combination Sum III#

##Problem##
Find all possible combinations of **k** numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

Ensure that numbers within the set are sorted in ascending order.
##Code##

	public class Solution {
	    public List<List<Integer>> combinationSum3(int k, int n) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        List<Integer> list = new ArrayList<Integer>();
	        int[] nums = new int[9];
	        for (int i = 1; i <= 9; i++) {
	            nums[i - 1] = i;
	        }
	        helper(result, list, nums, k, n, 0);
	        return result;
	    }
	    private void helper(List<List<Integer>> result, List<Integer> list, int[] nums, int size, int target, int pos) {
	        if (list.size() == size && target == 0) {
	            result.add(new ArrayList<Integer>(list));
	            return;
	        }
	        else if (target < 0) {
	            return;
	        }
	        for (int i = pos; i < nums.length; i++) {
	            list.add(nums[i]);
	            helper(result, list, nums, size, target - nums[i], i + 1);
	            list.remove(list.size() - 1);
	        }
	    }
	}

##