# LeetCode Problem - Removing duplicates from a sorted array 

> Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.
> Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

> Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.

> Return k.

> Example 1:

- Input: nums = [1,1,2]
- Output: 2, nums = [1,2,_]
- Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
- It does not matter what you leave beyond the returned k (hence they are underscores).

> Example 2:
- Input: nums = [0,0,1,1,1,2,2,3,3,4]
- Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
- Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
- It does not matter what you leave beyond the returned k (hence they are underscores).
 
> Constraints:

- 1 <= nums.length <= 3 * 104
- -100 <= nums[i] <= 100
- nums is sorted in non-decreasing order.

```JS 
var removeDuplicates = function(nums) {
  // Handle edge case
    if (nums.length === 0) return 0; 

 // Initialize the unique elements counter
    let k = 1;
    
    // Loop through the array starting from the second element
    for (let i = 1; i < nums.length; i++) {
        // If the current element is different from the previous one
        if (nums[i] !== nums[i - 1]) {
           // Move the current element to the next available position
            nums[k] = nums[i];
            // Increment the unique elements counter
            k++; 
        }
    }
    
    return k; // Return the number of unique elements
};
```

> Challenges 
- I struggled with understanding what exactly the problem was asking. It was either return the new array with the proper numbers not dupicted or the length of the array. 
- I tried initializing a new empty array then using a forEach with the condition .includes to check if my new unique array contained duplicates. If a duplicate does not exist then the num would be pushed into the new unique array, then I returned the uniqueArray.length - this did not work
- In the end a counter is used to keep track of the number of elements in the array which is then returned in the end. The for loops goes through the array starting a the second element and checks each element with the element next to it to see if there are duplicates. If the current element is different from the first one, we then move that element to the next avaliable position. Then the count is incremented every time a new element is added to the array. 

