#Leetcode@Find Peak Element#

##题目##

A peak element is an element that is greater than its neighbors.

Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that num[-1] = num[n] = -∞.

For example, in array [1, 2, 3, 1], 3 is a peak element and your function should return the index number 2.

##思路##

寻找局部的最大值，二分搜索

我们需要对二分搜索的模板进行一下小小的改动

- 如果num[mid] > num[mid + 1]并且num[mid] > num[mid - 1],
  那么返回mid，这是没问题的
- 如果num[mid] < num[mid + 1],那么说明若有解，则这个局部最大值在mid的右侧，


二分搜索的边界问题，我现在一直对这个不清楚

##代码##

	class Solution {
	public:
    	int findPeakElement(const vector<int> &num) {
        	int low = 0, high = num.size() - 1;
        	while (low < high - 1) {
            	int mid = low + (high - low ) / 2;
            	if (num[mid] > num[mid - 1] && num[mid] > num[mid + 1])
				{ 
					return mid;
				}
            	else if (num[mid] < num[mid + 1])
				{
                    low = mid + 1;
				}
                else
				{ 
                    high = mid - 1;
				}    
			}
        	return num[low] > num[high] ? low : high;
    	}
	};