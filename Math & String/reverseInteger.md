#Leetcode@Reverse Integer#

##题目##

Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321

click to show spoilers.

Have you thought about this?
Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!

If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.

Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?

For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

##思路##

主要是要考虑负数和溢出的问题，另外，像题目中提示说的一样，如果是像10，100这样的数字，翻转后应该如何表示。

对于负数来说，只需要判断输入整数是否小于0，拿一个flag标记，并将输入整数变为正数，翻转后再变回来。

关于溢出，这里有个小坑，之前定义result时定义为int类型，输入整数为1534236469的测试用例出现了问题，才明白result = result * 10 + x % 10就可能已经溢出了，这时候再判断result是否
溢出就没有意义了，所以应该将result定义为long类型，然后判断翻转后的result是否溢出就好，最后返回时强制转换为int类型就好

##代码##

	public class Solution {
	    public int reverse(int x) {
	        int flag = 0;
	        long result = 0;
	        if (x < 0) {
	            flag = 1;
	            x = -x;
	        }
	        
	        while (x > 0) {
	            result = result * 10 + x % 10;
	            x = x / 10;
	        }
	        
	        if (result > Integer.MAX_VALUE || result < Integer.MIN_VALUE) {
	            return 0;
	        }
	        
	        if (flag == 1) {
	            result = -result;
	        }
	        
	        return (int)result;
	    }
	}



