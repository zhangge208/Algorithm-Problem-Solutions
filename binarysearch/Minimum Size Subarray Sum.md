#Minimum Size Subarray Sum#

##题目##

Given an array of **n** positive integers and a positive integer **s**, find the minimal length of a subarray of which the sum ≥ **s**. If there isn't one, return 0 instead.

For example, given the array `[2,3,1,2,4,3]` and `s = 7`,
the subarray `[4,3]` has the minimal length under the problem  constraint.

click to show more practice.

**More practice:**

If you have figured out the O(n) solution, try coding another solution of which the time complexity is O(nlogn).

**Credits:**

Special thanks to @Freezen for adding this problem and creating all test cases.


##代码##

	public class Solution {
	    public int minSubArrayLen(int s, int[] nums) {
	        if (nums.length == 0 || nums == null) {
	            return 0;
	        }
	        int[] sum = new int[nums.length];
	        sum[0] = nums[0];
	        for (int i = 1; i < nums.length; i++) {
	            sum[i] = sum[i - 1] + nums[i];
	        }
	        int ans = Integer.MAX_VALUE;
	        int start, end, mid;
	        for (int i = 0; i < sum.length; i++) {
	            start = i;
	            end = sum.length - 1;
	            while (start + 1 < end) {
	                mid = start + (end - start) / 2;
	                if (sum[mid] - sum[i] + nums[i] == s){
	                    end = mid;
	                    break;
	                }
	                else if (sum[mid] - sum[i] + nums[i] < s) {
	                    start = mid;
	                }
	                else {
	                    end = mid;
	                }
	            }
	            if (sum[start] - sum[i] + nums[i] >= s){
	                ans = Math.min(ans, start - i + 1);
	            }
	            if (sum[end] - sum[i] + nums[i] >= s){
	                ans = Math.min(ans, end - i + 1);
	            }
	            
	        }
	        return (ans == Integer.MAX_VALUE ? 0 : ans);
	    }
	}

##思路##

###O(n) solution###


###O(nlogn) solution###

O(nlogn)的解法很不易想到，tag上提示为二分搜索，binary search的复杂度为O(logn)，那么在外层应该有一个for循环。