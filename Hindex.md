#H-Index#

##题目##

Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the [definition of h-index on Wikipedia](https://en.wikipedia.org/wiki/H-index): "A scientist has index h if h of his/her N papers have **at least** h citations each, and the other N − h papers have **no more than** h citations each."

For example, given `citations = [3, 0, 6, 1, 5]`, which means the researcher has `5` papers in total and each of them had received `3, 0, 6, 1, 5` citations respectively. Since the researcher has 3 papers with **at least** `3` citations each and the remaining two with **no more than** `3` citations each, his h-index is `3`.

`Note`: If there are several possible values for h, the maximum one is taken as the h-index.

##代码##

	public class Solution {
	    public int hIndex(int[] citations) {
	        int len = citations.length;
	        int[] count = new int[len + 1];
	        
	        for (int c:citations) {
	            if (c > len) {
	                count[len]++;
	            }
	            else {
	                count[c]++;
	            }
	        }
	        
	        int total = 0;
	        for (int i = len; i >= 0; i--) {
	            total += count[i];
	            if (total >= i) {
	                return i;
	            } 
	        }
	        return 0;
	    }
	}

##思路##

