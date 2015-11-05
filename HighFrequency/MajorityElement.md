#Leetcode@Majority Element#

##题目##
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

##思路##
抵消的思想，有一个假设的主元素candidate，计数器count，若为主元素，必须满足严格地大于n/2，那么当元素1（假设的主元素）与元素2不一样时，把这两个数均丢弃，count--,如果是主元素，仍然会剩下一些;当数1与数2相同时，count++;然而，在count == 0时，说明现在的元素并非是主元素，故令 candidate = num[i],重复以上过程。

##代码##
	class Solution {
	public:
    	int majorityElement(vector<int> &num) {
        	int candidate = 0;
        	int count = 0;
        	for(int i = 0;i < num.size(); i++)
        	{
            	if(count == 0)
            	{
                	candidate = num[i];
            	}
            
            	if(candidate == num[i])
            	{
                	count++;
            	}
            
            	else
            	{
                	count--;
            	}
        	}
        	return candidate;
    	}
	};