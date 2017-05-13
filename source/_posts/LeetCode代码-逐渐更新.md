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
## #400~500

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

## #500~600

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

