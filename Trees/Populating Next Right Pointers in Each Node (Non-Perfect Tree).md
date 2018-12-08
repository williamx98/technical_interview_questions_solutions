# Populating Next Right Pointers in Each Node (Non-Perfect Tree)

[Question Link](https://leetcode.com/explore/learn/card/data-structure-tree/133/conclusion/1016/)  


Given a binary tree
```Python
struct TreeLinkNode {
  TreeLinkNode *left;
  TreeLinkNode *right;
  TreeLinkNode *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.
Initially, all next pointers are set to NULL.

Contraints:
You may only use constant extra space.
Recursive approach is fine, implicit stack space does not count as extra space for this problem.

### Explaination:
TLDR: Making a linkedlist via the children nodes of the current level's linkedlist.

This solution is a top-down, level-order approach.  

It works by assembling a linkedlist consisting of the nodes from the level below the current level via traversing the current level's linkedlist.  

It assumes that current level has been correctly "connected" which will always be `True` for the root level. The `root`'s next value is set to and will always be `NULL` meaning that the second level can be assembled under that assumption.


### Notes:
You don't have to set each level's right-most-node's `next` manually. When the tree was made, all of the nodes had their `next` pointers set to `NULL` so once you connect the second right-most node of the level, there is no need to set the right-most node since it's already pointing to the correct value (`NUll`)


## Solution With Comments:
```Python
# Definition for binary tree with next pointer.
# class TreeLinkNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
#         self.next = None

class Solution:
    # @param root, a tree link node
    # @return nothing
    def connect(self, root):
        if not root:
            return

        # each level will esstentially turn into a linkedlist.
        # connected level = all of the level's nodes next pointers are properly set

        currLvlPointer = root                   # Traveling pointer for the current level
        dummyNxtLvlHolder = TreeLinkNode(0)     # Non-traveling pointer to hold the front of the next level as its next
        nxtLvlPointer = dummyNxtLvlHolder       # Traveling pointer to build the connection of the next level's nodes.
        
        # continue to iterate through the current level
        # the next
        while currLvlPointer:
        	# if the next level begins at the current level's pointer, the dummyNxtLvlHolder will hold this node at the dummyNxtLvlHolder's next
        	# assemble as much of the next level's "linkedlist" via the current node. 
        	# i.e if there are two nodes at the current level's node, connect them both in the next level's "linkedlist"
            if currLvlPointer.left:
                nxtLvlPointer.next = currLvlPointer.left
                nxtLvlPointer = nxtLvlPointer.next
        
            if currLvlPointer.right:
                nxtLvlPointer.next = currLvlPointer.right
                nxtLvlPointer = nxtLvlPointer.next
            
            # move to next avaible pointer to continue building the next level's "linkedlist"
            currLvlPointer = currLvlPointer.next
            
            # when there are no more pointers left on the current level, it can be concluded that the next level's nodes have ALL been connected
            # This implies it is time to move down to the next level, and assemble the next level's, next level's "linkedlist" 
            if currLvlPointer is None:
                currLvlPointer = dummyNxtLvlHolder.next
                dummyNxtLvlHolder = TreeLinkNode(0)
                nxtLvlPointer = dummyNxtLvlHolder
```

## Solution With Comments:
```Python
class Solution:
    def connect(self, root):
        if not root:
            return

        currLvlPointer = root
        dummyNxtLvlHolder = TreeLinkNode(0)
        nxtLvlPointer = dummyNxtLvlHolder
        
        while currLvlPointer:
            if currLvlPointer.left:
                nxtLvlPointer.next = currLvlPointer.left
                nxtLvlPointer = nxtLvlPointer.next
        
            if currLvlPointer.right:
                nxtLvlPointer.next = currLvlPointer.right
                nxtLvlPointer = nxtLvlPointer.next
            
            currLvlPointer = currLvlPointer.next
            
            if currLvlPointer is None:
                currLvlPointer = dummyNxtLvlHolder.next
                dummyNxtLvlHolder = TreeLinkNode(0)
                nxtLvlPointer = dummyNxtLvlHolder
```