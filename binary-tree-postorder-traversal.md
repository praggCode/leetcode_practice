# Binary Tree Postorder Traversal

## Problem

Given the root of a binary tree, return the postorder traversal of its nodes' values.

Example 1

Input: root = [1,null,2,3]  
Output: [3,2,1]

Example 2

Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]  
Output: [4,6,7,5,2,9,8,3,1]

Example 3

Input: root = []  
Output: []

Example 4

Input: root = [1]  
Output: [1]

Constraints

The number of nodes in the tree is in the range [0, 100].  
-100 <= Node.val <= 100

## Solution

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution(object):
    def postorderTraversal(self, root):
        if not root:
            return []

        left = self.postorderTraversal(root.left)
        right = self.postorderTraversal(root.right)

        return left + right + [root.val]