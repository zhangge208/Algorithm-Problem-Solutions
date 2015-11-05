#Find Minimum in Rotated Sorted Array#

##题目##

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

Find the minimum element.

You may assume no duplicate exists in the array.

##代码##

	public class Solution {
	    public int findMin(int[] nums) {
	        if (nums == null || nums.length == 0) {
	            return -1;
	        }
	        
	        int start = 0;
	        int end = nums.length - 1;
	        
	        while (start + 1 < end) {
	            int mid =start + (end - start) / 2;
	            if (nums[mid] > nums[end]) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        return nums[start] < nums[end] ? nums[start] : nums[end];
	    }
	}

##思路##

与Search in Rotated Sorted Array很类似，但我们是需要寻找最小元素，那么最小元素的位置该如何确定？

只需判断nums[mid]和nums[end]的大小，如果nums[mid] > nums[end]，表明前半部分有序，那么最小元素一定在后半部分，反之nums[mid] < nums[end]表明后半部分有序，最小元素在前半部分，依据这个核心思路，利用二分搜索模板即可。