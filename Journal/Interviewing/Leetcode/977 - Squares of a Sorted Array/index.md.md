---
title: 977 - Squares of a Sorted Array 
date: 2022-03-08
description: "Level: Easy, Category: Array"
---

Given an integer array `nums` sorted in **non-decreasing** order, return _an array of **the squares of each number** sorted in non-decreasing order_.

**Constraints**
-   `1 <= nums.length <= 104`
-   `-104 <= nums[i] <= 104`
-   `nums` is sorted in **non-decreasing** order.

**Examples**

## Solutions
---

### Approach
We could map each number then sort the resulting array

**Complexities**
- Time: O(n log n) where n is the length of the input array
- Space: O(n) where n is the length of the input array

**LC Results**
- Runtime: 165 ms
- Memory: 49 MB

**Code**
```js
const sortedSquares = (nums) =>{
  let sum = []
  for(num of nums){
    sum.push((num ** 2))
  }

  sum.sort((a,b) => {return a - b})
  return sum
}
```

**Tips**

---

### Approach
Using a two pointer approach, we can start at the end of both sides, compare them and add the largest of the two. This will create the result array backwords, we will have to reverse the array at the end.

**Complexities**
- Time: O(n)
- Space: O(n)

**LC Results**
- Runtime: 99ms
- Memory: 48.5 MB

**Code**
```js
const sortedSquares = (nums) =>{
  let results = []
  let leftPointer = 0
  let rightPointer = nums.length - 1

  while(leftPointer <= rightPointer){
    if((nums[leftPointer] ** 2) > (nums[rightPointer] ** 2)){
      results.push(nums[leftPointer] ** 2)
      leftPointer++
    }else{
      results.push(nums[rightPointer] ** 2)
      rightPointer--
    }
  }

  return results.reverse()
}
```

**Tips**

---