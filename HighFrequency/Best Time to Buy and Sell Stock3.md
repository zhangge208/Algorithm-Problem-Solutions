#Leetcode@Best Time to Buy and Sell Stock III#

##题目##

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete at most two transactions.

Note:
You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

##思路##

动态规划+前后遍历

基本的想法是分成两个时间段，对于某一天j，计算之前的max profit和之后的max profit。

即寻找一个点j，将原来的prices[0..n-1]分割成[0..j]和[j..n-1]两个子区间，分别求两段最大的收益，l_profit和r_profit，profit = l_profit + r_profit。然后用O(n)的时间在[0...n-1]上选择使得profit最大的j，返回最大的profit。

对于点j，求price[0..j]的最大profit时，很多工作是重复的，在求price[0..j-1]的最大profit中已经做过了。Best Time to Buy and Sell Stock I的dp解法可以在O(1)的时间从price[0..j-1]推出price[0..j]的最大profit。
难点在于如何从price[j..n-1]推出price[j+1..n-1]，反过来思考，我们可以用O(1)的时间由price[j+1..n-1]推出price[j..n-1]。
所以进行前后遍历，即可得到结果。前后遍历的题目还有一些。

整体思路：

- 数组l[i]记录了price[0..i]的最大profit，
- 数组r[i]记录了price[i..n]的最大profit。
- 已知l[i]，求l[i+1]是简单的，同样已知r[i]，求r[i-1]也很容易。
- 用O(n)的时间找出最大的l[i]+r[i]，即为题目所求。

##代码##

	class Solution {
	public:
    	int maxProfit(vector<int> &prices) {
        	if(prices.size() < 2)
        	{
            	return 0;
        	}
        	vector<int> left(prices.size());
        	vector<int> right(prices.size());
        	// DP from left to right;
        	left[0] = 0;
        	int min_price = prices[0];
        	for (int i = 1; i < prices.size(); i++) 
        	{
            	min_price = min(prices[i], min_price);
            	left[i] = max(left[i - 1], prices[i] - min_price);            
        	}
        
        	//DP from right to left;
        	right[0] = 0;
        	int max_price = prices[prices.size() - 1];
        	for (int i = prices.size() - 2; i >= 0; i--)
        	{
            	max_price = max(prices[i],max_price);
            	right[i] = max(right[i+1], max_price - prices[i]);
        	}
        
        	int profit = 0;
        	for (int i = 0; i < prices.size(); i++)
        	{
            	profit = max(left[i] +right[i], profit);
        	}
        
        	return profit;
    	}
	};