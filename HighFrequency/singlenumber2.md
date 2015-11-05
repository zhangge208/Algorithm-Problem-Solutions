#Leetcode@Single Number II#

##题目##
Given an array of integers, every element appears three times except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

##思路##
构造一个3进制的异或运算（XOR3），使得三个相同的数进行不进位加法（XOR3）后结果为0，与single number1的思路一样。