---
title: 904 - Fruits into Baskets 
date: 2022-03-08
description: ""
---

# 904 - Fruits into Baskets
You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array `fruits` where `fruits[i]` is the **type** of fruit the `ith` tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

-   You only have **two** baskets, and each basket can only hold a **single type** of fruit. There is no limit on the amount of fruit each basket can hold.
-   Starting from any tree of your choice, you must pick **exactly one fruit** from **every** tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
-   Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array `fruits`, return _the **maximum** number of fruits you can pick_.

**Constraints**
-   `1 <= fruits.length <= 105`
-   `0 <= fruits[i] < fruits.length`

**Examples**
```
**Example 1:**

**Input:** fruits = [1,2,1]
**Output:** 3
**Explanation:** We can pick from all 3 trees.

**Example 2:**

**Input:** fruits = [0,1,2,2]
**Output:** 3
**Explanation:** We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].

**Example 3:**

**Input:** fruits = [1,2,3,2,2]
**Output:** 4
**Explanation:** We can pick from trees [2,3,2,2].
If we had started at the first tree, we would only pick from trees [1,2].
```

**TLDR**

## Solutions
---

### Approach - Brute force
Brute force solution! It's so brutey that it will timeout in leetcode on a big dataset.

We are going to track the count for every number against every other number until the unique number of numbers seen is greater than 2.

**Complexities**
- Time:  O(n^2)
> We are iterating through the loop twice per number.
- Space: O(1)
> While we are expanding our set, our set size will always be less than 3.

**LC Results**
- Runtime: ❌ Runtime exceeded 
> The algorithm could not finish when given an input size of 50+
- Memory: ❌  Runtime exceeded

**Code**
```js
const totalFruit = (nums) => {
  if(nums.length < 2){return 1}

  let maxFruitsSeen = 0

  for(var i = 0; i<nums.length; i++){
    let currentFruitSeen = 1
    let basket = new Set([nums[i]])
    for(var j = i + 1; j < nums.length; j++){
      basket.add(nums[j])
      if(basket.size > 2){
        break;
      }else{
        currentFruitSeen++
        maxFruitsSeen = Math.max(maxFruitsSeen, currentFruitSeen)
      }
    }
  }
  return maxFruitsSeen
}
```

**Tips**
- Understand it, but never submit

---

### Approach
This method uses a hashmap to determine individual fruit type. If the count of keys found in the hashmap is greater than the bucket max size, we want to remove the fruitcount and increment the left pointer. Once the fruit hits 0, we can remove it.

Until then, we track the greatest count and increment the right pointer.

**Complexities**
- Time: O(n) where n is the size of the input array
> Even though we have a nested while loop, this doesn't iterate through the whole loop multiple times. Just a small subset.
- Space: O(1) constant time
> While it might initally look like O(n) space because of the expanding hashmap, we have to look at how big the hashmap will actually get. In this example, the hash map will only expand to the maxbucket size + 1.

**LC Results**
- Runtime: 565 ms, faster than 22.49% of JavaScript online submissions
- Memory: 58.3 MB, less than 21.72% of JavaScript online submissions

**Code**
```js
const totalFruit = (nums) =>{
  let left = 0
  let right = 0
  let maxFruitsCounted = 0
  let maxBucketSize = 2
  let bucketMap = {}

  while(right < nums.length){
    let rightValue = nums[right]

    bucketMap[rightValue] = bucketMap[rightValue] + 1 || 1
    let bucketSize = Object.keys(bucketMap).length

    if(bucketSize<= maxBucketSize){
      maxFruitsCounted = Math.max(((right - left) + 1), maxFruitsCounted)
      right++
    }
    else if(bucketSize> maxBucketSize){
      // Remove values from the left until they're removed from hash
      while(Object.keys(bucketMap).length > maxBucketSize){
        let leftValue = nums[left]

        bucketMap[leftValue]--
        if(bucketMap[leftValue] === 0){delete bucketMap[leftValue]}
        left++
      }
      right++
    }
  }

  return maxFruitsCounted
}
```

**Tips**

---