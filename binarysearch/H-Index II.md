#H-Index II#

##题目##

**Follow up** for [H-Index](https://leetcode.com/problems/h-index/): What if the `citations` array is sorted in ascending order? Could you optimize your algorithm?

**Hint:**

Expected runtime complexity is in O(log n) and the input is sorted.

##代码##

    public class Solution {
	    public int hIndex(int[] citations) {
	        if (citations == null || citations.length == 0) {
	            return 0;
	        }
	        
	        int start = 0;
	        int end = citations.length - 1;
	        while (start + 1 < end) {
	            int mid = start + (end - start) / 2;
	            if (citations[mid] == citations.length - mid) {
	                return citations.length - mid;
	            }
	            else if (citations[mid] < citations.length - mid) {
	                start = mid;
	            }
	            else {
	                end = mid;
	            }
	        }
	        
	        if (citations[start] >= citations.length - start) {
	            return citations.length - start;
	        }
	        if (citations[end] >= citations.length - end) {
	            return citations.length - end;
	        }
	        return 0;
	    }
	}

##思路##

O(log n)的复杂度，排序的数组输入，那么一定是二分搜索无疑了，但在模板上应该做什么样的改动呢？

关键就在于h因子的定义：被引用次数等于或超过h的文章至少有h篇

如果定义数组长度为n的话，最后h篇文章被引用次数应该等于或超过h，那么也就是说第n - h篇文章被引用次数应该等于或超过h，即：

citations[n - h] >= h 

如果令mid = n - h，这样就可以使用二分搜索：

- 如果citations[mid] == citations.length - mid，那么citations.length - mid即为h因子

- 如果citations[mid] < citations.length - mid，那么说明选择的mid太小，第n - h篇文章并不能满足等于或超过h，需要后移

- 如果citations[mid] > citations.length - mid，那么说明选择的mid太大，第n - h篇之前的文章就能满足等于或超过h，需要前移

边界条件：判断start、end两个特殊点哪个满足条件