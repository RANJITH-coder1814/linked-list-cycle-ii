# LeetCode 142 - Linked List Cycle II

## Problem Statement
Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

## Approach
This solution uses Floyd's Cycle Detection Algorithm (Tortoise and Hare).

### Steps
1. Use two pointers (`slow` and `fast`) to detect a cycle.
2. If they meet, a cycle exists.
3. Move one pointer to the head.
4. Move both pointers one step at a time.
5. The node where they meet is the starting node of the cycle.

## Algorithm
- Initialize `slow` and `fast` at `head`.
- Move:
  - `slow` by 1 step.
  - `fast` by 2 steps.
- If they meet:
  - Set `entry = head`.
  - Move both `entry` and `slow` one step at a time.
  - Return the meeting node.
- If no cycle is found, return `nullptr`.

## Complexity Analysis
- Time Complexity: **O(n)**
- Space Complexity: **O(1)**

## C++ Code

```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *slow = head;
        ListNode *fast = head;

        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;

            if (slow == fast) {
                ListNode *entry = head;

                while (entry != slow) {
                    entry = entry->next;
                    slow = slow->next;
                }

                return entry;
            }
        }

        return nullptr;
    }
};
