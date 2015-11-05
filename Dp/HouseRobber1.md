#Leetcode@House Robber I

##题目##
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

##思路##

属于序列动态规划(Sequence Dp)

state：f[i]表示到第i个位置时可获得的最大利益

function：f[i] = max(f[i-1], f[i-2]+nums[i])

initialize: f[0] = nums[0], f[1] = max(f[0],nums[1])

answer:f[n-1]

异常处理，考虑边界情况，nums为空或长度为1的情况

##代码##

	public class Solution {
	    public int rob(int[] nums) {
	        if (nums == null || nums.length == 0){
	            return 0;
	        }
	        int[] f = new int[nums.length];
	        for (int i = 0; i < nums.length; i++){
	            if (i == 0){
	                f[0] = nums[0];
	            }
	            else if (i == 1){
	                f[1] = Math.max(f[0],nums[1]);
	            }
	            else{
	                f[i] = Math.max(f[i - 1],f[i - 2]+nums[i]);
	            }
	        }
	        return f[nums.length - 1];
	    }
	}