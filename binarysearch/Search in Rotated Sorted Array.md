#Search in Rotated Sorted Array#

##题目##

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.


##代码##

	public class Solution {
	    public int search(int[] nums, int target) {
	        if (nums.length == 0 || nums == null) {
	            return -1;
	        }
	        
	        int start = 0;
	        int end = nums.length - 1;
	        
	        while (start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            if (nums[mid] == target) {
	                end = mid;
	            }
	            else if (nums[mid] < nums[end]) {
	                if (nums[mid] <= target && target <= nums[end]) {  
	                    start = mid;
	                }
	                else {
	                    end = mid;
	                }
	            }
	            // nums[mid] > nums[start]
	            else {
	                if (nums[mid] >= target && target >= nums[start]) {
	                    end = mid;
	                }
	                else {
	                    start = mid;
	                }
	            }
	        }
	        
	        if (nums[start] == target) {
	            return start;
	        }
	        if (nums[end] == target) {
	            return end;
	        }
	        
	        return -1;
	        
	    }
	}

##思路##

在数组发生旋转后会有两种情况产生，以[0,1,2,3,4,5,6]为例：

1. 旋转后形如[3,4,5,6,0,1,2],即较小的数发生了翻转，但前半部分仍然有序

2. 旋转后形如[5,6,0,1,2,3,4],即较大的数发生了翻转，但后半部分仍然有序

为使用二分搜索，那么必须保持使用区间的有序性