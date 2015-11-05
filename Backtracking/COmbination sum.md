#Combination Sum#

##题目##

Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The **same** repeated number may be chosen from C unlimited number of times.

Note:

- All numbers (including target) will be positive integers.
- Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
- The solution set must not contain duplicate combinations.

For example, given candidate set `2,3,6,7` and target `7`, 
A solution set is: 

`[7]`
 
`[2, 2, 3]` 

##代码##

	public class Solution {
	    public List<List<Integer>> combinationSum(int[] candidates, int target) {
	        if (candidates.length == 0 || candidates == null) {
	            return null;
	        } 
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        List<Integer> list = new ArrayList<Integer>();
	        Arrays.sort(candidates);
	        helper(result, list,candidates, target, 0);
	        return result;
	    }
	    
	    private void helper(List<List<Integer>> result,List<Integer> list, int[] candidates, int target, int pos ) {
	        if (target == 0) {
	            result.add(new ArrayList<Integer>(list));
	            return;
	        }
	        else if (target < 0) {
	            return;
	        }
	        
	        for(int i = pos; i < candidates.length; i++) {
	            list.add(candidates[i]);
	            helper(result, list, candidates, target - candidates[i],i);
	            list.remove(list.size() - 1);
	        }
	    }
	}

##思路##

套用subsets模板，

1. 一定要有

	else if (target < 0) {
	            return;
	        }
不然会栈溢出

2. helper(result, list, candidates, target - candidates[i],**i**);
  这里为什么是i而不是i + 1，因为题目中说C中的元素可以重复取无限次，那么如果写为i + 1的话，这个元素将不能再次被取到

3. Arrays.sort(candidates);先要排序
        