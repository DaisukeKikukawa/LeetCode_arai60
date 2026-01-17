# step3:

時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと

-

```javascript
var twoSum = function(nums, target) {
  const numToIndexMap = new Map();

  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];

    if (numToIndexMap.has(complement)) {
      return [numToIndexMap.get(complement), i];
    }

    numToIndexMap.set(nums[i], i);
  }
};
```
