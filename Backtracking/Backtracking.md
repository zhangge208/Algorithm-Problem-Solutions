#Backtracking#

##concept && idea

###concept###

回溯法是一种选优搜索法，按选优条件向前搜索，以达到目标。但当探索到某一步时，发现原先选择并不优或达不到目标，就退回一步重新选择，这种走不通就退回再走的技术为回溯法，而满足回溯条件的某个状态的点称为“回溯点”。

###idea###

在包含问题的所有解的解空间树中，按照深度优先搜索的策略，从根结点出发深度探索解空间树。当探索到某一结点时，要先判断该结点是否包含问题的解，如果包含，就从该结点出发继续探索下去，如果该结点不包含问题的解，则逐层向其祖先结点回溯。（其实回溯法就是对隐式图的深度优先搜索算法）。

若用回溯法求问题的所有解时，要回溯到根，且根结点的所有可行的子树都要已被搜索遍才结束。

而若使用回溯法求任一个解时，只要搜索到问题的一个解就可以结束。

##step && Template##

###step###

- 针对所给问题，确定问题的解空间：首先应明确定义问题的解空间，问题的解空间应至少包含问题的一个（最优）解。
- 确定结点的扩展搜索规则
- 以深度优先方式搜索解空间，并在搜索过程中用剪枝函数避免无效搜索。

###Template###

以[Subsets](https://leetcode.com/problems/subsets/)为例，给出Backtracking Template

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
	
**Note：**很多题目的解法均是在这个模板的基础上，但剪枝的条件会有所不同

##Problem List##

[Subsets]()

[Subsets II]()

[Permutations]()

[Permutations II]()

[Combinations]()

[Combination Sum]()

[Combination Sum II]()

[Combination Sum III]()

[Palindrome Partitioning]()

[Palindrome Partitioning II]()

[Restore IP Addresses]()



Letter Combinations of a Phone Number