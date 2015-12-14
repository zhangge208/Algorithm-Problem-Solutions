#Leetcode@Ugly Number#

##题目##

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number

##思路##

按照题意，一个数只含有2、3、5的因子才是Ugly Number，所以，除此之外只要有其他主因子均不符合条件

##代码##

	public class Solution {
	    public boolean isUgly(int num) {
	        if (num <= 0) {
	            return false;
	        }
	        while (num != 1) {
	
	            if (num % 2 == 0) {
	                num = num / 2;
	            }
	            else if (num % 3 == 0) {
	                num = num / 3;
	            }
	            else if (num % 5 == 0) {
	                num = num / 5;
	            }
	            else {
	                return false;
	            }
	        }
	        return true;
	    }
	}



