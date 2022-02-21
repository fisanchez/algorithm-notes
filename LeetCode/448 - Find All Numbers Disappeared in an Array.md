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