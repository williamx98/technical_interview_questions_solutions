# Palindrome Linked List  

[Question Link](https://leetcode.com/problems/palindrome-linked-list/)  

Given a singly linked list, determine if it is a palindrome.

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """

        fast = head
        middle = head
        reverse = None

        # find the middle node and reverse node before middle
        while fast and fast.next:
            fast = fast.next.next
            current = middle
            middle = middle.next
            current.next = reverse
            reverse = current

        if fast:  # mean list has odd count nodes, need change to next.
            middle = middle.next

        # check the reverse equal the middle
        while reverse:
            if reverse.val != middle.val:
                return False
            reverse = reverse.next
            middle = middle.next

        return True
```