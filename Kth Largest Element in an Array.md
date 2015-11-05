Title:Leetcode@Kth Largest Element in an Array
Date:2015-5-28
Category:Algorithm
Tags:Algorithm Leetcode Heap
Author:zhangge208


---
#Leetcode@Kth Largest Element in an Array#

##题目##

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

For example,
Given [3,2,1,5,6,4] and k = 2, return 5.

Note: 
You may assume k is always valid, 1 ≤ k ≤ array's length.

##思路##

使用优先队列来解决。由于题目是求第k大的数，反过来也就是求第n-k+1小的数，那么只需要生成一个队长为k的优先队列，把n个数中k个最大的数放入队列中即可，此时返回队头即可。所以，对于nums中前k个数，我们全部放入优先队列中；对于剩下的n-k个元素，我们挨个将其与现有队头比较，如果比现有队头大，那么更新队头，原队头出队，元素入队。

##代码##
	public class Solution {
	    public int findKthLargest(int[] nums, int k) {
	        PriorityQueue<Integer> queue = new PriorityQueue<Integer>(k);
	        for (int i = 0; i < nums.length; i++){
	            if (queue.size() < k){
	                queue.add(nums[i]);
	            }
	            else{
	                if (nums[i] > queue.peek()){
	                    queue.remove();
	                    queue.add(nums[i]);
	                }
	            }
	        }
	        return queue.remove();
	    }
	}