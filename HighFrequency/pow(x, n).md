#Leetcode@Pow(x, n)#

##题目##

Implement pow(x, n).

##思路##

分治法

x^n = x^(n/2) * x^(n/2); x^(n/2) = x^(n/4) * x^(n/4)

不过有些细节需要注意：

- n = 0时 return 1
- n < 0时 return 1 / power(x,-n)
- n > 0时，令value = power(x,n/2),需要对n的奇偶性进行讨论。  
  n = 2k + 1时，返回 value * value * x；  
  n = 2k时，返回value * value 

##代码##

	
	class Solution {
	public:
    	double pow(double x, int n) {
        	if(n < 0)
        	{
            	return 1.0 / power(x, -n);
        	}
        	else
        	{
            	return power(x,n);
        	}
    	}
	private:
    	//divide & conquer
    	double power(double x, int n)
    	{
        	if (n == 0)
        	{
            	return 1;
        	}
        	else
        	{
            	double value = power(x, n / 2);
            	if (n % 2 == 0)
            	{
                	return value * value;
            	}
            	else
            	{
                	return value * value * x;
            	}
        	}
    	}
	};
    

