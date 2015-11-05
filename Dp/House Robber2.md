#Leetcode@House Robber II 

##题目##

Note: This is an extension of House Robber.

After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

##思路##

题目变化导致的特殊判断条件为是否抢劫第一件房屋。如果是，则不能抢最后一件房屋。否则，可以抢最后一间房屋。

以此为依据，将环形DP问题转化为两次序列DP问题

异常处理，考虑边界情况，nums为空或长度为1的情况

##代码##

	public class Solution {
	    public int rob(int[] nums) {
	        if (nums == null || nums.length == 0){
	            return 0;
	        }
	        if (nums.length == 1){
	            return nums[0];
	        }
	        int prev = 0;
	        int cur = 0;
	        for (int i = 1; i < nums.length; i++){
	            int temp = cur;
	            cur = Math.max(cur, prev + nums[i]);
	            prev = temp;
	        }
	        int missing_first = cur;
	        
	        prev = 0;
	        cur = 0;
	        for (int i = 0; i < nums.length - 1; i++){
	            int temp = cur;
	            cur = Math.max(cur, prev + nums[i]);
	            prev = temp;
	        }
	        int missing_last = cur;
	        
	        return Math.max(missing_first,missing_last);
	    }
	}