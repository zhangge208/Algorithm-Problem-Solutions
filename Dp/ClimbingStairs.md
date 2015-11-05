#Leetcode@Climbing Stairs#

##题目##

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

##思路##

动态规划的思路，属于sequence DP

- state: f[i]表示前i个位置，跳到第i个位置共有多少种方案
- function: f[i] = f[i-1] + f[i-2] （跳一步和跳两步）
- intialize: f[0] = 1, f[1] = 1
- answer: f[n]

小陷阱：动态分配数组的时候要记得数组的大小应为0-n+1

本题背后的故事实际上是斐波那契数列

##代码##

	class Solution {
	public:
    	int climbStairs(int n) {
        	vector<int> res(n+1);
        	res[0] = 1;
        	res[1] = 1;
        	for(int i = 2; i <= n; i++)
        	{
            	res[i] = res[i-1] + res[i-2];
        	}
        	return res[n];
    	}
	};


节省空间的写法：

	int climbStairs2(int n)  
    {  
        vector<int> res(3);  
        res[0] = 1;  
        res[1] = 1;  
        for (int i = 2; i <= n; i++)  
        {  
            res[i%3] = res[(i-1)%3] + res[(i-2)%3];  
        }  
        return res[n%3];  
    }  