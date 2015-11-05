#Permutations II#

##Problem##
Given a collection of numbers that might contain duplicates, return all possible unique permutations.

For example,

`[1,1,2]` have the following unique permutations:

`[1,1,2]`,`[1,2,1]`, and `[2,1,1]`.

##Code##

	public class Solution {
	    public List<List<Integer>> permuteUnique(int[] nums) {
	        List<List<Integer>> result = new ArrayList<List<Integer>>();
	        
	        if (nums == null || nums.length == 0){
	            return result;
	        }
	            
	        List<Integer> list = new ArrayList<Integer>();
	        int[] visited = new int[nums.length];
	        Arrays.sort(nums);
	        permuteHelper(result, list,visited, nums);
	        return result; 
	    }
	    public void permuteHelper( List<List<Integer>> result, List<Integer> list,int[] visited, int[] nums){
	        
	        if (list.size() == nums.length){
	            result.add(new ArrayList(list));
	            return;
	        }
	        for (int i = 0; i < nums.length; i++){
	            if (visited[i] == 1 ||(i != 0 && nums[i] == nums[i - 1] && visited[i - 1] == 0)){
	                continue;
	            }
	            visited[i] = 1;
	            list.add(nums[i]);
	            permuteHelper(result, list,visited, nums);
	            list.remove(list.size() - 1);
	            visited[i] = 0;
	        }
	    }
	}

##Solution and Analysis##
