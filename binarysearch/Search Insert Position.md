#Search Insert Position#

##题目##

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.
[1,3,5,6], 5 → 2

[1,3,5,6], 2 → 1

[1,3,5,6], 7 → 4

[1,3,5,6], 0 → 0

##代码##
	version 1：first postion >= target
	public class Solution {
	    public int searchInsert(int[] nums, int target) {
	        if (nums == null || nums.length == 0) {
	            return -1;
	        }
	        int start = 0;
	        int end = nums.length - 1;
	        while (start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            if (target < nums[mid]) {
	                end = mid;
	            }
	            else if (target > nums[mid]) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        
	        if (nums[start] >= target) {
	            return start;
	        }
	        else if (nums[end] >= target) {
	            return end;
	        }
	        //nums[end] < target
	        else {
	            return end + 1;
	        }
	        
	        
	    }
	}

	version 2：last postion < target
	public class Solution {
		public int searchInsert(int[] nums, int target) {
			if (nums == null || nums.length == 0) {
				return -1;
			}
			
			int start = 0;
			int end = nums.length - 1;
			while (start + 1 < end) {
				int mid = start + (end -start) / 2;
				if (target > nums[mid]) {
					start = mid;
				}
				else {
					end = mid;
				}
			}
			if (target < nums[0]) {
            	return 0;
        	}
			if (nums[start] == target) {
				return start;
			}
			if (nums[end] == target) {
				return end;
			}	
			if (nums[end] < target){
				return end + 1;
			}
			return start + 1;
		}
	 } 



##思路##

如果target在数组中，那么可直接运用二分搜索的模板，但需要处理的一个问题是，如果target不在数组中，那么应该把它放在哪里合适呢？
直接地，有两种思路：

1.找到first postion >= target的地方，把target放在这个位置

2.找到last postion < target的地方，把target放在这个位置

值得注意的是，对一些边界的问题需要进行考虑

1.使用第一种思路时，要注意处理nums[end] < target的情况

2.使用第二种思路时，要注意处理target < nums[0]的情况

