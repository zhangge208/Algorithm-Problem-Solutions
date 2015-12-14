#Two Sum II#

##Problem##

Given an array of integers, find how many pairs in the array such that their sum is bigger than a specific target number. Please return the number of pairs.

##Code##

	public class Solution {
	    /**
	     * @param nums: an array of integer
	     * @param target: an integer
	     * @return: an integer
	     */
	    public int twoSum2(int[] nums, int target) {
	        // Write your code here
	        if (nums == null || nums.length == 0) {
	            return 0;
	        }
	        Arrays.sort(nums);
	        int res = 0;
	        int start = 0;
	        int end = nums.length - 1;
	        while (start < end) {
	            int sum = nums[start] + nums[end];
	            if (sum <= target) {
	                start++;
	            } else {
	                res += end - start;
	                end--;
	            }
	        }
	        return res;
	    }
	}