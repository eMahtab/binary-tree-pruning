# Binary Tree Pruning
## https://leetcode.com/problems/binary-tree-pruning

We are given the head node root of a binary tree, where additionally every node's value is either a 0 or a 1.

Return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

(Recall that the subtree of a node X is X, plus every node that is a descendant of X.)


**Note:**

1. The binary tree will have at most 100 nodes.
2. The value of each node will only be 0 or 1.

![Binary Tree Pruning](binary-tree-pruning.PNG?raw=true "Binary Tree Pruning")


# Implementation :

```java
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
    public TreeNode pruneTree(TreeNode root) {
        if(root == null)
            return null;
        return prune(root);
    }
    
    public TreeNode prune(TreeNode node){
        if(node == null)
            return node;
        node.left = prune(node.left);
        node.right = prune(node.right);
        return (node.left == null && node.right == null && node.val == 0) ?
                null : node;
    }
}

```

# Key Points :
Note that in the recursive prune method we are first calling the prune on left subtree and right subtree, if we move the check `(node.val == 0 && node.left == null && node.right == null)` before calling prune on left subtree and right subtree, it will lead to wrong result.

# References :
https://www.youtube.com/watch?v=77LJc56bwnE
