#Roman to Integer#

##Problem##
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

##Code##

	public class Solution {
	    public int romanToInt(String s) {
	        if (s == null || s.length() == 0) {
	            return 0;
	        }
	        Map<Character, Integer> map = new HashMap<Character, Integer>();
	        map.put('I',1);
	        map.put('V',5);
	        map.put('X',10);
	        map.put('L',50);
	        map.put('C',100);
	        map.put('D',500);
	        map.put('M',1000);
	        int result = map.get(s.charAt(s.length() - 1)) ;
	        for (int i = s.length() - 1; i >= 1 ; i--) {
	            if (map.get(s.charAt(i - 1)) >= map.get(s.charAt(i))) {
	                result += map.get(s.charAt(i - 1));
	            }
	            else {
	                result -= map.get(s.charAt(i - 1));
	            }
	            
	        }
	        return result;
	    }
	}

##Solution and Analysis##

It`s boring so long as you know the rule that how to convert roman numeral to an integer.

The base:

I = 1

V = 5

X = 10

L = 50

C = 100

D = 500

M = 1000

So we need create a map to store key-value<Character, Integer>.

Rule:

- If a lower value symbol is before a higher value one, it is subtracted. Otherwise it is added 

- Order: Right to left