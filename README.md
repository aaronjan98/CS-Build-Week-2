# CS Build Week 2: Technical Interview Prep

Details about the week, [check out the page in
TrainingKit](https://learn.lambdaschool.com/cs/sprint/reco0t22NdXmr8VyL).

### Monday June 22 2020

My Solution to [LeetCode problem 217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/):

```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # checks for num of unique items in list
        check_dupl = len(set(nums))
        
        # if the set matches the original list
        if check_dupl == len(nums):
            # return false
            return False
        
        # if there are duplicates, return true
        return True
```

My first pass solution to [LeetCode problem 2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/):

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        q1 = []
        q2 = []
        
        # traverse through l1 to store the node values in a list
        while l1.next != None:
            q1.insert(0, l1.val)
            
            try:
                l1.val = l1.next.val
                l1.next = l1.next.next.val
            except AttributeError:
                q1.insert(0, l1.next)
                break
            
        # traverse through the second ll and concatenate it to a variable
        while l2.next != None:
            q2.insert(0, l2.val)
            
            try:
                l2.val = l2.next.val
                l2.next = l2.next.next.val
            except AttributeError:
                q2.insert(0, l2.next)
                break
        
        # turn the list values into integers
        num1 = ''
        num2 = ''
        
        for item_l1 in q1:
            num1 += str(item_l1)
        for item_l2 in q2:
            num2 += str(item_l2)
            
        # addition of the two reversed ll
        sum = int(num1) + int(num2)
        
        # return the sum in a reversed ll
        item_sum = -1
        # create reverse sum instance of ListNode
        sum_ll = ListNode()
        int_ll = sum_ll
        
        # iterating through each indv. digit of sum
        while abs(item_sum) <= len(str(sum)):
            # extracting an ind integer from sum
            node = int(str(sum)[item_sum])
            # create node instance and update val and next attributes
            int_ll.val = node
            int_ll.next = ListNode()
            
            try:
                int_ll.next.val = int(str(sum)[item_sum-1])
            except IndexError:
                int_ll.next = None
                
            # increment to the next value to add as a node to sum_ll
            if abs(item_sum) == 1:
                int_ll = sum_ll.next
            elif abs(item_sum) == 2:
                int_ll = sum_ll.next.next
            item_sum -= 1
        
        print(sum_ll)
        return sum_ll
```

