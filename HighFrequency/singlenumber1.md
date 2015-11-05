#Leetcode@Single Number#

##题目##
Given an array of integers, every element appears twice except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

##思路##

异或运算特点（不进位加法）:

- a ^ b = c ,a ^ c = b -> b ^ c = a
- a ^ a = 0 （信息抵消）
- a ^ 0 = a
- (a ^ b) ^ c = a ^ (b ^ c)

根据 a ^ a = 0,我们可以知道两个相同的数进行异或会相抵消，所以把数组中的所有数异或一遍即可得到答案
##代码##

	class Solution {
	public:
    	int singleNumber(int A[], int n) {
        	int num = 0;
        	for(int i = 0; i < n; i++)
        	{
            	num = num ^ A[i];
        	}
        	return num;
    	}
	};
