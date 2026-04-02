# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 問題の整理
  - 各ペア (u, v) について、u + v（ペアの和）を計算する
  - その中から和が小さい順にk個のペアを返す
  - →「和が小さいペアをk個」返す
- 思いついた解法
  - nums1とnums2の全組み合わせを作る
  - 各ペアの和を計算
  - 和が小さい順に並べる
  - 先頭からk個返す

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
