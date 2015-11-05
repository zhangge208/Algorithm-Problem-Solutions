#First Bad Version#

##题目##

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool isBadVersion(version)` which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

##代码##

	/* The isBadVersion API is defined in the parent class VersionControl.
	      boolean isBadVersion(int version); */
	
	public class Solution extends VersionControl {
	    public int firstBadVersion(int n) {
	        if (n == 0) {
	            return -1;
	        }
	        
	        int start = 1;
	        int end = n;
	        while (start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            if (isBadVersion(mid) == false) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        
	        if (isBadVersion(start) == true) {
	            return start;
	        }
	        
	        if (isBadVersion(end) == true) {
	            return end;
	        }
	        
	        return -1;
	    }
	}

##思路##

很基础的二分搜索，先要判断mid处的版本是否是bad version，如果不是，那么前半部分均可以不要，start = mid。套用二分法模板就好
