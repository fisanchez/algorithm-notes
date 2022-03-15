---
title: 448 - Find All Numbers Disappeaered in an Array 
date: 2022-03-08
description: ""
---

# 448 - Find All Numbers Disappeared in an Array
Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return _an array of all the integers in the range_ `[1, n]` _that do not appear in_ `nums`.

**Constraints**
-   `n == nums.length`
-   `1 <= n <= 105`
-   `1 <= nums[i] <= n`

**Examples**
```
**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].


**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Input:** nums = [3,3], target = 6
**Output:** [0,1]
```

## Solutions

### Approach: Brute Force
Brute force approach would be to compare each value with each other to check against target value.

**Complexities**
- Time: O(n^2) where n is size of array input
- Space: O(1) no additional space is created

**LC Results**
- Runtime: 100 ms
- Memory: 42.2 MB

**Code**
```js
const twoSum = (nums, target) => {
  for(var i = 0; i < nums.length; i++){
    for(var j = i + 1; j < nums.length; j++){
      if(nums[i] + nums[j] == target){
        return [i, j]
      }
    }
  }
}
```

**Tips**

---

### Approach:  HashMap
We know what number we are looking for for every number, it is just the difference of the current value minus the target value. Instead of iterating through the entire array we can use HashMap to get O(1) lookup time. We are trading time for space.

For every item we check if the complement number is in the hash map, if it's not then we will add the value to the map and continue. Important note - if we add the value to the map before we check, we might have false positives with multiples. Every number in the nums array is unique.

**Complexities**
- Time: O(n) where n is the size of nums array
- Space: O(n) where n is the size of nums array

**LC Results**
- Runtime: 64 ms
- Memory: 43.8 MB

**Code**
```js
const twoSum = (nums, target) => {
  let map = new Map()
  for(var i = 0; i < nums.length; i++){
    let diff = target - nums[i]
    if(map.has(diff)){
      return [map.get(diff),i]
    }
    map.set(nums[i], i)
  }
}
```

**Tips**

---