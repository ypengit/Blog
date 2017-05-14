---
layout: poster
title: LeetCode代码(逐渐更新)
date: 2017-05-13 21:31:46
tags: 
    编程
    LeetCode
categories: 编程
---

## #1~100

### #1 Two Sum

**Description:**
>Given an array of integers, return indices of the two numbers such that they add up to a specific target.  
>You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example**
>Given nums = [2, 7, 11, 15], target = 9,   
>Because nums[0] + nums[1] = 2 + 7 = 9,     
>return [0, 1]. 
<!--more-->
**Code**

```C++
class Solution {
public:
	vector<int> twoSum(vector<int>& nums, int target) {
		vector<int> res;
		for (int i = 0; i < nums.size()-1; i++){
			for (int j = i + 1; j < nums.size();j++){
                if (nums[i] + nums[j] == target){
					res.resize(2);
					res[0] = i;
					res[1] = j;
					return res;
				}
			}
		}
		return res;
	}
};
```
## #300~400

### #344 Reverse String

**Description**
>Write a function that takes a string as input and returns the string reversed.  

**Example**

>Given s = "hello", return "olleh".

**Code**

```C++

class Solution {
public:
    string reverseString(string s) {
        for(int i = 0;i < s.size() / 2;i++)
        {
            char temp;
            temp = s[i];
            s[i] = s[s.size() - i -1];
            s[s.size() - i -1] = temp;
        }
        return s;
    }
};

```

## #400~500

### #412 Fizz Buzz

**Description:**
>Write a program that outputs the string representation of numbers from 1 to n.  
>But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.  

**Example**

>n = 15,
>
>Return:  
>[  
>    "1",  
>    "2",  
>    "Fizz",  
>    "4",  
>   "Buzz",  
>    "Fizz",  
>    "7",  
>    "8",  
>    "Fizz",  
>    "Buzz",  
>    "11",  
>    "Fizz",  
>    "13",  
>    "14",  
>    "FizzBuzz"  
>]  

**Code**
```C++
class Solution {
public:
	vector<string> fizzBuzz(int n) {
		vector<string> res;
		res.resize(n);
		for (int i = 0; i < n; i++)
		{
			res[i] = to_string(i + 1);
			if (i % 3 == 2)
			{
				res[i] = "Fizz";
			}
			if (i % 5 == 4)
			{
				res[i] = "Buzz";
			}
			if (i % 15 == 14)
			{
				res[i] = "FizzBuzz";
			}
		}
		return res;
		
	}
};
```


### #461 Hamming Distance
**Description:**
>The Hamming distance between two integers is the number of positions at which the corresponding bits are different.    
>Given two integers x and y, calculate the Hamming distance.

**Example**
>Input: x = 1, y = 4    
>Output: 2  
>Explanation:   
>1   (0 0 0 1)  
>4   (0 1 0 0)  
>　　↑　  ↑ 

The above arrows point to positions where the corresponding bits are different.

**Code**

```C++
class Solution 
{
	public:
		int hammingDistance(int x, int y) 
		{
			int sum = 0;
			for (int i = 0; i < 32; i++)
			{
				int flagx = x % 2;
				int flagy = y % 2;
				if (flagx != flagy)
				{
					sum++;
				}
				x /= 2;
				y /= 2;
			}
			return sum;
		}
};
```

### #493 Island Perimeter

**Description:**
>You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.  

**Example**

>[[0,1,0,0],  
> [1,1,1,0],  
> [0,1,0,0],  
> [1,1,0,0]]  
>  
>Answer: 16  
>Explanation: The perimeter is the 16 yellow stripes in the   image below:  
[image link](https://leetcode.com/static/images/problemset/island.png)


**Code**
```C++

class Solution {
public:
	int islandPerimeter(vector<vector<int>>& grid) {
		int neiboor = 0, count = 0;
		for (int i = 0; i < grid.size(); i++){
			for (int j = 0; j < grid[0].size(); j++)
			{
				if (grid[i][j] == 1)
				{
					count++;
					if (i != 0 && grid[i - 1][j]) neiboor++;
					if (j != 0 && grid[i][j - 1]) neiboor++;
				}
			}
		}
		return count * 4 - neiboor * 2;
	}
};

```


### #496 Next Greater Element I

**Description:**
>You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.  
>The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.  

**Example1**

>Input: nums1 = [4,1,2], nums2 = [1,3,4,2].  
>Output: [-1,3,-1]  
>Explanation:  
>    For number 4 in the first array, you cannot find the >next greater number for it in the second array, so >output   -1.  
>    For number 1 in the first array, the next greater >number for it in the second array is 3.  
>    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.  

**Example2**

>Input: nums1 = [2,4], nums2 = [1,2,3,4].  
>Output: [3,-1]  
>Explanation:  
>    For number 2 in the first array, the next greater   number for it in the second array is 3.  
>    For number 4 in the first array, there is no next   greater number for it in the second array, so output -1.  


**Note**

>All elements in nums1 and nums2 are unique.  
>The length of both nums1 and nums2 would not exceed 1000.  


**Code**
```C++

class Solution {
public:

	int findval(vector<int> nums,int val){
		vector<int>::iterator it = find(nums.begin(), nums.end(), val);
		int t = (it - nums.begin());
		return t;
	}
	vector<int> nextGreaterElement(vector<int>& findNums, vector<int>& nums) {
		vector<int> res;
		int flag = 0;
		for (int i = 0; i < findNums.size(); i++)
		{
			int pos = -1;
			
			for (int j = 1 +  findval(nums,findNums[i]); j < nums.size(); j++)
			{
				if (nums[j] > findNums[i])
				{
					pos = j;
					break;
				}
			}
			if (pos != -1)
			{
				pos = nums[pos];
			}
			res.push_back(pos);
		}
		return res;
	}
};

```

## #500~600

### #500 Keyboard Row
**Description:**
>Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.

**Example**
>Input: ["Hello", "Alaska", "Dad", "Peace"]  
>Output: ["Alaska", "Dad"]  

**Node**
>You may use one character in the keyboard more than once.
>You may assume the input string will only contain letters of alphabet.

**Code**
```C++
class Solution {
public:
	bool test(string s)
	{
		transform(s.begin(), s.end(), s.begin(), ::tolower);
		unordered_set<string> line1 = { "q", "w", "e", "r", "t", "y", "u", "i", "o", "p" };
		unordered_set<string> line2 = { "a", "s", "d", "f", "g", "h", "j", "k", "l" };
		unordered_set<string> line3 = { "z", "x", "c", "v", "b", "n", "m" };
		
		unordered_set<string>::iterator it;
		
		string s2 = s.substr(0, 1);

		it = line1.find(s2);

		int type = -1;

		if (it != line1.end())
		{
			type = 1;
		}		
		it = line2.find(s2);
		if (it != line2.end())
		{
			type = 2;
		}		
		
		it = line3.find(s2);
		if (it != line3.end())
		{
			type = 3;
		}

		unordered_set<string> targetSet;

		switch (type)
		{
		case 1:targetSet = line1; break;
		case 2:targetSet = line2; break;
		case 3:targetSet = line3; break;
		default:
			break;
		}

		for (int i = 0; i < s.size();i++)
		{
			string s1 = s.substr(i,1);
			unordered_set<string>::iterator it;
			it = targetSet.find(s1);
			if (it == targetSet.end())
			{
				return false;
			}

		}
		return true;

	}
	vector<string> findWords(vector<string>& words) {
		vector<string> str;
		for (int i = 0; i < words.size(); i++){
			if (!test(words[i]))
			{
				continue;
			}
			str.push_back(words[i]);
		}
		return str;
	}
};
```

### #557 Reverse Words in a String III
**Description:**
>Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

**Example 1**:  
>Input: "Let's take LeetCode contest"  
>Output: "s'teL ekat edoCteeL tsetnoc"  

**Note:**
>In the string, each word is separated by single space and there will not be any extra space in the string.

**Code**

```C++
class Solution {
public:
	string reverse(string s){
		string res = "";
		for (int i = s.size() - 1; i >= 0;i--){
			res += s[i];
		}
		return res;
	}

	string reverseWords(string s) {
		vector<string> str;
		while (true){
			int ix = s.find(" ");
			if (s.find(" ") == -1){
				str.push_back(s);
				break;
			}
			string strtmp = s.substr(0,ix);
			str.push_back(strtmp);
			s = s.substr(ix+1,s.size()-1);
		}
		string res="";
		for (int i = 0; i < str.size(); i++){
			if (i != str.size() - 1){
				res += reverse(str[i]) + " ";
			}
			else{
				res += reverse(str[i]);
			}
		}
		return res;
	}
};
```

### #561 Array Partition I
**Description:**
>Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

**Example**
>Input: [1,4,3,2]   
>Output: 4  
>Explanation: n is 2, and the maximum sum of pairs is 4.

**Code**

```C++
class Solution {
public:
	int arrayPairSum(vector<int>& nums) {
		sort(nums.begin(), nums.end());
		int n = nums.size();
		int sum = 0;
		for (int i = 0; i < n; i += 2){
			sum += nums[i];
		}
		return sum;
	}
};
```

### #566 Reshape the Matrix
**Description:**
>In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.  
>You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.  
>The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.  
>If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

**Example1**

>**Input:** 
>nums =   
>[[1,2],  
> [3,4]]  
>r = 1, c = 4  
>**Output:**   
>[[1,2,3,4]]  
>**Explanation:**  
>The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.

**Example2**

>**Input:**   
>nums =   
>[[1,2],  
> [3,4]]  
>r = 2, c = 4  
>**Output:**  
>[[1,2],
> [3,4]]  
>**Explanation:**   
>There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.

**Code**

```C++
class Solution {
public:
	vector<vector<int>> matrixReshape(vector<vector<int>>& nums, int r, int c) {
		int realr = nums.size();
		int realc = nums[0].size();
		if (realr * realc != r * c){
			return nums;
		}
		else{
			vector<vector<int>> res;
			res.resize(r);
			for (int i = 0; i < r; i++){
				res[i].resize(c);
			}
			for (int i = 0; i < realr; i++){
				for (int j = 0; j < realc; j++){
					int temp = i * realc + j;
					int tempi = temp / c;
					int tempj = temp % c;
					res[tempi][tempj] = nums[i][j];
				}
			}
			return res;
		}
	}
};
```


### #575 Distribute Candies
**Description:**
>Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain.

**Example1**

>**Input:** candies = [1,1,2,2,3,3]  
>**Output:** 3  
>**Explanation:**  
>There are three different kinds of candies (1, 2 and 3), and two candies for each kind.  
>Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too.   
>The sister has three different kinds of candies. 

**Example2**

>**Input:** candies = [1,1,2,3]  
>**Output:** 2  
>**Explanation:**   
>For example, the sister has candies [2,3] and the brother has candies [1,1].   
>The sister has two different kinds of candies, the brother has only one kind of candies. 

**Code**

```C++
class Solution {
public:
	int distributeCandies(vector<int>& candies) {
		sort(candies.begin(),candies.end());
		int n = candies.size();
		int sum = 0;
		for (int i = 1; i < n; i++){
			if (candies[i] != candies[i - 1]){
				sum++;
			}
		}
        if(sum == 0) return 1;
        if(sum >= candies.size()/2){
            return candies.size()/2;
        }
        return sum+1;
	}
};
```
