#3Sum Closest#

##Problem##

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

		For example, given array S = {-1 2 1 -4}, and target = 1.
	
		The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

##Code##
	public class Solution {
	    public int threeSumClosest(int[] nums, int target) {
	        Arrays.sort(nums);
	        int start = 0;
	        int end = nums.length - 1;
	        int min = Integer.MAX_VALUE /2;
	        for (int i = 0; i < nums.length - 2; i++) {
	            start = i + 1;
	            end = nums.length - 1;
	            while (start < end) {
	                int sum = nums[i] + nums[start] + nums[end];
	                if (sum == target) {
					    return sum;
				    } else if (sum < target) {
					    start++;
				    } else {
						end--;
					}
					min = Math.abs(sum - target) < Math.abs(min - target) ? sum : min; 
	            }
	        }
	        return min;
	    }
	}

##Solution && Analysis##
The main code is same as the template of two point.
There are some points we should notice:

- The sum of three integers should be defined in while loop,because nums[start] and nums[end] are changed along with variable start, end.Do not place variable sum in for loop. 
  
- To find three integers in S such that the sum is closest to target, and how to select the variable min？  
 
We have this test case as below:

		Input:
		[0,1,2] 0
		Output:
		0
		Expected:
		3
if we define : 
	
	int min = 0;
	
and Math.abs(min - 0) = 0,but Math.abs(sum - 0) = 3,it will return 0.Wrong answer!

and how about assign Integer.MAX_VALUE to variable min?
Look another test case:
   
		Input:
		[-3,-2,-5,3,-4] -1
		Output:
		2147483647
		Expected:
		-2

it will overflow for opeartion (min-target)

To sum up，we can select Interger.MAX_VALUE or 1000 for variable min.