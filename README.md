
# CMSC398L_Presentation

## Problem Statement
Given an `n x n` array of integers `matrix`, return _the **minimum sum** of any **falling path** through_ `matrix`.

A **falling path** starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position `(row, col)` will be `(row + 1, col - 1)`, `(row + 1, col)`, or `(row + 1, col + 1)`.

**Example 1:**
![enter image description here](https://assets.leetcode.com/uploads/2021/11/03/failing1-grid.jpg)   
**Input:** matrix = [[2,1,3],[6,5,4],[7,8,9]]
**Output:** 13
**Explanation:** There are two falling paths with a minimum sum as shown.

**Example 2:**
![enter image description here](https://assets.leetcode.com/uploads/2021/11/03/failing2-grid.jpg)
**Input:** matrix = [[-19,57],[-40,-5]]
**Output:** -59
**Explanation:** The falling path with a minimum sum is shown.

**Constraints:**

-   `n == matrix.length == matrix[i].length`
-   `1 <= n <= 100`
-   `-100 <= matrix[i][j] <= 100`

Source: https://leetcode.com/problems/minimum-falling-path-sum/description/?envType=study-plan-v2&envId=dynamic-programming

## Solution
The intuition for this problem is to apply dynamic programming. 

    class Solution:
	    def minFallingPathSum(self, matrix: List[List[int]]) -> int:
		    for i in range(1, len(matrix)):
			    for j in range(len(matrix[0])):
				    if j == 0:
					    matrix[i][j] += min(matrix[i-1][j], matrix[i-1][j+1])
				    elif j == len(matrix[0])-1:
						matrix[i][j] += min(matrix[i-1][j-1], matrix[i-1][j])
					else:
						matrix[i][j] += min(matrix[i-1][j-1], matrix[i-1][j], matrix[i-1][j+1])
			return  min(matrix[-1])
