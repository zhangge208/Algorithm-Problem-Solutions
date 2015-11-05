#Leetcode@Best Time to Buy and Sell Stock 

##题目##

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

##思路##

动态规划的想法，属于sequence DP

- state：f[i]代表前i天的最大收益
- function：f[i] = max(f[i-1],f[i-1]+prices[i]-prices[i-1])
- intialize:f[0] = 0
- answer:f[n] 

##代码##
