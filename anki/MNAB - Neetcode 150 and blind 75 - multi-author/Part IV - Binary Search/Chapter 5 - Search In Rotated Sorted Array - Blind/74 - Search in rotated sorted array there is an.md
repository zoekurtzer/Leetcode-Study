========== Question ==========  

### Search In Rotated Sorted Array

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` after the possible rotation and an integer `target`, return the index of `target` if it is in `nums`, or `-1` if it is not in `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**Example 2:**

```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

**Constraints:**

-   `1 <= nums.length <= 5000`

-   `-10^4 <= nums[i] <= 10^4`

-   `All values of nums are unique.`

-   `nums is an ascending array that is possibly rotated.`

-   `-10^4 <= target <= 10^4`

---

To summarize, the below code will solve this problem using an augmented binary search solution. What is the time and space complexity?

```python
def search(self, nums: List[int], target: int) -> int:
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] >= nums[0] and target < nums[0]:
            # We're in left sorted array
            # But target is in right sorted array
            left = mid + 1
        elif nums[mid] < nums[0] and target >= nums[0]:
            # We're in right sorted array
            # But target is in left sorted array
            right = mid - 1
        # Otherwise: Normal binary search
        elif target > nums[mid]:
            left = mid + 1
        elif target < nums[mid]:
            right = mid - 1
        else:
            return mid
        return -1
```

A) Time complexity: O(n), Space complexity: O(1)

B) Time complexity: O(log n), Space complexity: O(1)

C) Time complexity: O(n log n), Space complexity: O(n)

D) Time complexity: O(n^2), Space complexity: O(n)  

========== Answer ==========  

**Answer**: B

The binary search approach has a time complexity of O(log n) because in each step, you reduce the problem size by half. The space complexity is O(1) because you are not using any additional space that scales with the input size. You only need a constant amount of space to store the variables left, right, and mid.

========== Id ==========  
74

---

DECK INFO

TARGET DECK: Data Structures and Algorithms::Leetcode::MNAB - Neetcode 150 and blind 75 - multi-author::Part IV - Binary Search::Chapter 5 - Search In Rotated Sorted Array - Blind

FILE TAGS: #DSA::#Leetcode::#MNAB-Neetcode-150-and-blind-75-multi-author::#Part-IV-Binary-Search::#Chapter-5-Search-In-Rotated-Sorted-Array-Blind::#74-Search-in-rotated-sorted-array-there-is-an

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```
QUESTION STATUS: Safe to store