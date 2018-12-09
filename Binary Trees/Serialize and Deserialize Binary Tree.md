# Serialize and Deserialize Binary Tree

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/995)  

Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.  

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

##### Constraints:

### Explanation:
TLDR: Use preorder to serialize and deserialize the tree.

The serializing of a subtree stops once it reaches a leaf node.

### Notes:


## Solution With Comments:
```Python
class Codec:
	# pretty straight forward. Use preorder to construct and encoded string
    def serialize(self, root):
        def recurse(node):
            if node:
                encode.append(str(node.val))
                recurse(node.left)
                recurse(node.right)
            else:
                encode.append('N')
        encode = []
        
        recurse(root)
        return ' '.join(encode)

    # since we know what order to expexct, perform the exact same preorder traversal but make a tree now
    def deserialize(self, data):
        def doit(index):
            val = data[index[0]]
            index[0] += 1
            if val == '#':
                return None
            node = TreeNode(int(val))
            node.left = doit(index)
            node.right = doit(index)
            return node
        
        data = data.split(" ")
        return doit([0])
```

## Solution Without Comments:
```Python

```