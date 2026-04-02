# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
-

```javascript
var kSmallestPairs = function(nums1, nums2, k) {
  const result = [];

  const minSumPairHeap = new MinPriorityQueue({
    compare: (a, b) => a.sum - b.sum
  });

  for (let i = 0; i < nums1.length && i < k; i++) {
    minSumPairHeap.enqueue({
      sum: nums1[i] + nums2[0],
      i,
      j: 0
    });
  }

  while (k > 0 && !minSumPairHeap.isEmpty()) {
    const { i, j } = minSumPairHeap.dequeue();
    result.push([nums1[i], nums2[j]]);
    k--;

    if (j + 1 < nums2.length) {
      minSumPairHeap.enqueue({
        sum: nums1[i] + nums2[j + 1],
        i,
        j: j + 1
      });
    }
  }

  return result;
};

```
