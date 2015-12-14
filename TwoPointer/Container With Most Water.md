#Container With Most Water#

##Problem##

Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container.

##Code##

	public class Solution {
	    public int maxArea(int[] height) {
	        if (height == null || height.length < 2) {
	            return 0;
	        }
	        int left = 0;
	        int right = height.length - 1;
	        int area = 0;
	        while (left <= right) {
	            area = Math.max(area, computeArea(left, right, height));
	            if (height[left] <= height[right]) {
	                left++;
	            }
	            else {
	                right--;
	            }
	        }
	        return area;
	    }
	    public int computeArea(int left, int right, int[] height) {
	        int h = Math.min(height[left], height[right]);
	        return (right - left) * h;
	    }
	}

##Solution && Analysis##
Two Pointer类型问题

这道题目的意思是尽可能多地盛放水，那么左端点left、右端点right的高度height[left]和height[right]越高越好，如果确定了左端点L和右端点R，那么最大可能的高度就是min(height[left],height[right])。所以为了area尽可能的大，要求搜索左右端点最大可能高度。