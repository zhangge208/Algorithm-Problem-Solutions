#Leetcode@Best Time to Buy and Sell Stock II

##题目##

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

##思路##

贪心的想法，既然能交易多次，那就把所有赚钱的时间段赚取的利益相加。首先要构造一个差值数组（前缀和数组？），即price_diff[i] = prices[i] - prices[i-1],然后把全部price_diff > 0的部分相加，即为最大利益

##代码##

	class Solution {
	public:
    	int maxProfit(vector<int> &prices) {
    	    if(prices.size() < 2) 
        	{
            	return 0;
        	}
        	int price_diff = 0;
        	int cur_price = prices[0];
        	int sum = 0;
        	for(int i = 1; i < prices.size(); i++)
        	{
            	price_diff = prices[i]-cur_price;
            	cur_price = prices[i];
            	if(price_diff > 0) sum += price_diff;
        	}
        	return sum;
    	}
	};
