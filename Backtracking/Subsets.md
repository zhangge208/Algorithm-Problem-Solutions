#Subsets#

##题目##

Given a set of distinct integers, nums, return all possible subsets.

**Note:**
- Elements in a subset must be in non-descending order.
- The solution set must not contain duplicate subsets.

For example,

If **nums** = `[1,2,3]`, a solution is:

	[
	  [3],
	  [1],
	  [2],
	  [1,2,3],
	  [1,3],
	  [2,3],
	  [1,2],
	  []
	]

##代码##

	public class Solution {
	    public List<List<Integer>> subsets(int[] nums) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        if (nums == null || nums.length == 0){
	            return result;
	        }
	        List<Integer> list = new ArrayList<Integer>();
	        Arrays.sort(nums);
	        subsetHelp(result, list, nums, 0);
	        return result;
	    }
	    
	    private void subsetHelp(List<List<Integer>> result, List<Integer>list, int[] nums, int pos){
	        result.add(new ArrayList<Integer>(list));
	        
	        for (int i = pos; i < nums.length; i++){
	            list.add(nums[i]);
	            subsetHelp(result, list, nums, i + 1);
	            list.remove(list.size() - 1);
	            
	        } 
	    }
	}

##思路##

reference: [http://algorithm.yuanbin.me](http://algorithm.yuanbin.me)

backtracking可用图示与函数运行的堆栈来理解，以[1, 2, 3]为例，下图为list及result的变化过程，箭头向下表示list.add及result.add操作，箭头向上表示list.remove操作


![](http://7xltae.com1.z0.glb.clouddn.com/subset.jpg)	




	





















































