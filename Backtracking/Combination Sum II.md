#Combination Sum II#

##Problem##

Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

Each number in C may only be used once in the combination.

**Note:**

- All numbers (including target) will be positive integers.
- Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
- The solution set must not contain duplicate combinations.

For example, given candidate set `10,1,2,7,6,1,5` and target `8`, 
A solution set is: 
`[1, 7]`
 
`[1, 2, 5]`
 
`[2, 6]`
 
`[1, 1, 6]`

##Code##

	public class Solution {
	    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        List<Integer> list = new ArrayList<Integer>();
	        Arrays.sort(candidates);
	        helper(result, list,candidates, target, 0);
	        return result;
	    }
	    private void helper(List<List<Integer>> result, List<Integer> list, int[] candidates, int target, int pos) {
	        if (target == 0) {
	            result.add(new ArrayList<Integer>(list));
	            return;
	        }
	        else if (target < 0) {
	            return;
	        }
	        
	        for (int i = pos; i < candidates.length; i++) {
	            if (i > pos && candidates[i] == candidates[i - 1]) {
	                continue;
	            }
	            list.add(candidates[i]);
	            helper(result, list, candidates, target - candidates[i], i + 1);
	            list.remove(list.size() - 1);
	        }
	    }
	}

##Solution and Analysis##

reference: [http://www.shuatiblog.com/blog/2014/05/13/Combination-Sum-II/](http://www.shuatiblog.com/blog/2014/05/13/Combination-Sum-II/)

**the main part of is same as “Combination Sum”**,there is only some code that needs to be modified.

Considering Each number in C may only be used once in the combination. When going into the next recursive call, instead of:

	helper(result, list, candidates, target - candidates[i], i);

Change it to:

	helper(result, list, candidates, target - candidates[i], i + 1);

In addition,we take over this test case:

	[1,1] 1

in order to ensure that the solution set must not contain duplicate combinations, instead of getting next element right away, we get the element with different value.

add some code as below:

 	if (i > pos && candidates[i] == candidates[i - 1]) {
	                continue;
	}
 