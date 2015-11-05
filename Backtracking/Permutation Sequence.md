#Permutation Sequence#

##题目##

The set `[1,2,3,…,n]` contains a total of n! unique permutations.

By listing and labeling all of the permutations in order,
We get the following sequence (ie, for n = 3):

1. `"123"`
2. `"132"`
3. `"213"`
4. `"231"`
5. `"312"`
6. `"321"`

Given n and k, return the kth permutation sequence.

**Note:** Given n will be between 1 and 9 inclusive.

##代码##

public class Solution {
    public String getPermutation(int n, int k) {
        List<Integer> nums = new ArrayList<Integer>();
        if (n == 0){
            return "";
        }
        for(int i = 0; i <= n; i++){
            nums.add(i);
        }
        String res = "";
        
        int factorial;
        int index;

        for (int i = n;i > 0;i--){
            factorial = nFatorial(i - 1);
            index = (int) Math.ceil(k / (double) factorial);

            k = k % factorial;
           
            res += nums.get(index);
            nums.remove(index);
            if (k == 0){
                k = factorial;
            }
        }
        return res;
    
    }
     public int nFatorial(int n ) {
        if(n == 0){
            return 1;
        }
        return n * nFatorial(n - 1);
    }

}