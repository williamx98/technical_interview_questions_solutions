# Kth Smallest Element in a BST

[Question Link](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)  

Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.  

##### Constraints:

### Explanation:
TLDR: Traverse in-order and keep track of what number element you are on via a one-element array which simulates an integer passed by reference.

### Notes:


## Solution (Python):
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: int
        """
        def recurse(node,k):
            if not node:
                return None
            
            left = recurse(node.left,k)
            if left is not None:
                return left
            
            k[0] -= 1
            if k[0] == 0:
                return node.val
            
            return recurse(node.right,k)
            
            
        return recurse(root, [k]) 
```

## Solution (Java):
```Java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        int[] res = new int[2];
        res[0] = k;
        find(root, res);
        return res[1];
    }
    
    private boolean find(TreeNode root, int[] res){
        if (root == null) 
            return false;
        
        if (find(root.left, res))
            return true;
        
        res[0]--;
        if(res[0] == 0) {
            res[1] = root.val;
            return true;
        }
        
        return find(root.right, res);
    }
}
```