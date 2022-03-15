---
title: 713 - Subarray Product Less than K 
date: 2022-03-08
description: ""
---

# 713 - Subarray product less than k
Given an array of integers `nums` and an integer `k`, return _the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than_ `k`.

**Constraints**
-   `1 <= nums.length <= 3 * 104`
-   `1 <= nums[i] <= 1000`
-   `0 <= k <= 106`

**Examples**
```
Input: nums = [10,5,2,6], k = 100
Output: 8
Explanation: The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
```

**TLDR**
Use two pointers left and right starting at 0. If product * right value => update count and update product else divide left value

## Solutions
### Approach - Brute Force
We want to test whether each subarray product are less than k, but looking at the example, this includes single values.

We want to test whether the current product value times the neighbor value is less than k. If it is, then we want to multiple the next neighbor and check if it's less than k. When it's greater than k, we can break out of the subloop and start again.

Because we are traversing the entire array for each value as a worst case scenario, the time complexity is `O(n^2)`

**Complexities**
- Time: O(n^2), where n is the input size
	> We are iterating through the entire array for each value at our worst case
- Space: O(1), after initializing our variables we don't require additional memory
	> O(1), after initializing our variables we don't require additional memory

**LC Results**
- Runtime: 1048 ms, faster than 23.99% of JavaScript online submissions
- Memory: 47.7 MB, less than 39.68% of JavaScript online submissions

**Code**
```js
const numSubarrayProductLessThanK = (nums, k) =>{
	let product;
  let count = 0

  // check each if each value < k
  for(num of nums){
    if(num < k){count++}
  }

  for(let i = 0; i < nums.length; i++){
    product = nums[i]
    for(let j = (i + 1) ; j < nums.length; j++){
      product *= nums[j]
      if(product < k){count++}
      else{break;}
    }
  }


  return count
}
```

**Tips**
- Draw this problem out and try to solve this using brute force first before moving to optimal solution
---

### Approach - Optimal Solution
Using a two pointer approach we will initialize our left and right pointers to index 0 and keep track of both our counter and product.

Both pointers will iterate through the entire array. When the existing product * the value at right index, we update the counter and product. Remember, if the product of two numbers is less than k, that also means the compoents are also less than k. To adjust for this, we take the difference of the right and left value and add 1.

When the existing product times the current value at right index is greater than k, we want to remove the left value from the product total. We can do this by dividing the product by the left value.

**Complexities**
- Time: O(n) where n is the size of the array
	> We are only iterating through the array once
- Space: O(1) no additional memory is needed

**LC Results**
- Runtime: 76 ms, faster than 97.71% of JavaScript online submissions
- Memory: 47.9 MB, less than 28.92% of JavaScript online submissions

**Code**
```js
const numSubarrayProductLessThanK = (nums, k) =>{
  let left = 0
  let right = 0
  let product = 1
  let count = 0

  while(left < nums.length && right < nums.length){
    if((product * nums[right]) < k){
      // update product & count
      product = product * nums[right]
      count += ((right - left) + 1)
      right++
    }else{
      // Remove value from our product
      product = product / nums[left]
      left++
    }
  }
  return count
}
```

**Tips**

---
