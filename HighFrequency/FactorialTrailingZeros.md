#Leetcode@Factorial Trailing Zeroes#

##题目##

Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.

##思路##
考虑n!的质数因子。后缀0总是由质因子2和质因子5相乘得来的。如果可以计算2和5的个数，问题就解决了。考虑到2的个数总是大于等于5的个数。因此只要计录5的个数就可以了。那么如何计算n!的质因子中所有5的个数便成为难点。一个简单的方法是计算(n/5),除此之外，还有一件事情要考虑。诸如25，125之类的数字有不止一个5。处理这个问题也很简单，首先对n除以5，移除所有的单个5，然后除以25，移除额外的5，以此类推，直到 n / 5 == 0。
##代码##

	class Solution {
	public:
    	int trailingZeroes(int n) {
        	int numzero = 0;
        	while (n > 0)
        	{
            	numzero = numzero + n / 5;
            	n = n / 5;
        	}
        	return numzero;
    	
		}
	}; 