#Find Peak Element#

##题目##

A peak element is an element that is greater than its neighbors.

Given an input array where `num[i] ≠ num[i+1]`, find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that `num[-1] = num[n] = -∞`.

For example, in array `[1, 2, 3, 1]`, 3 is a peak element and your function should return the index number 2.

##代码##

	public class Solution {
	    public int findPeakElement(int[] num) {
	         int start = 0, end = num.length - 1;  
	         while(start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            if(num[mid] > num[mid - 1] && num[mid] > num[mid + 1]) {
	                end = mid;
	            } 
	            else if(num[mid] < num[mid + 1]) {
	                start = mid;
	            } 
	            else {
	                end = mid;
	            }
	        }
	        if(num[start] < num[end]) {
	            return end;
	        } 
	        else { 
	            return start;
	        }
	    }
	}
		

##思路##

寻找局部的最大值，二分搜索

需要对二分搜索的模板进行一下改动
	
- 如果num[i-1] < num[i] > num[i+1], 那么num[i]是峰值元素

- 如果num[i-1] < num[i] < num[i+1], 那么num[i+1...n-1]一定包含一个峰值元素

- 如果num[i-1] > num[i] > num[i+1], 那么num[0...i-1]一定包含一个峰值元素

- 如果num[i-1] > num[i] < num[i+1], 那么任意一边都可能有峰值元素
