#Search for a Range#

##题目##

Given a sorted array of integers, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return `[-1, -1]`.

For example,
Given `[5, 7, 7, 8, 8, 10]` and target value 8,
return `[3, 4]`.

	
##代码##

	public class Solution {
	    public int[] searchRange(int[] nums, int target) {
	        int[] result = new int[2];
	        if (nums == null || nums.length == 0) {
	            return result;
	        }
	        //search for left bound
	        int start = 0;
	        int end = nums.length - 1;
	        int mid = 0;
	        while (start + 1 < end) {
	            mid = start + (end - start) / 2;
	            if (target == nums[mid]) {
	                end = mid;        
	            }
	            else if (target > nums[mid]) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        if (nums[start] == target) {
	            result[0] = start;
	        }
	        else if (nums[end] == target) {
	            result[0] = end;
	        }
	        else {
	            result[0] = result[1] = -1;
	            return result;
	        }
	        
	        start = 0;
	        end = nums.length - 1;
	        while (start + 1 < end) {
	            mid = start + (end - start) / 2;
	            if (target == nums[mid]) {
	                start = mid;        
	            }
	            else if (target > nums[mid]) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	            
	        }
	        if (nums[end] == target) {
	            result[1] = end;
	        }
	        else if (nums[start] == target){
	            result[1] = start;
	        }
	        else {
	            result[0] = result[1] = -1;
	            return result;
	        }
	        return result;
	        
	    }
	}

##思路##

这道题目是练习寻找二分搜索的边界。运用二分搜索模板可以找到左边界，那么该如何寻找右边界呢，只需要将模板稍稍修改即可，寻找左边界时，
如果target == nums[mid]，那么令end = mid；寻找右边界时，
如果target == nums[mid]，那么令start = mid。想想其中原因，若二分法的end越小，则越靠近左边，而start越大则越靠近右边。故寻找到了左右边界。  