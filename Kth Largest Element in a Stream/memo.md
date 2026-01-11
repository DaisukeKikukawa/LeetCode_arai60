# 進め方
- step1: 5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。
- step2: コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。
- step3: 時間を計りながら書く。10分以内に3回連続でアクセプトされるまで。

## step1
-

## step2
-

## step3

- ヒープの役割
  - k個の最大値だけを保持するデータ構造
  - その中で一番小さい値が「k番目に大きい値」

```javascript
/**
 * @param {number} k
 * @param {number[]} nums
 */
var KthLargest = function(k, nums) {
  this.k = k;
  this.minHeap = new MinPriorityQueue();

  for (const n of nums) {
    this.add(n);
  }
};

/**
 * @param {number} val
 * @return {number}
 */
KthLargest.prototype.add = function(val) {
  this.minHeap.enqueue(val);

  if (this.minHeap.size() > this.k) {
    this.minHeap.dequeue();
  }

  return this.minHeap.front();
};

/**
 * Your KthLargest object will be instantiated and called as such:
 * var obj = new KthLargest(k, nums)
 * var param_1 = obj.add(val)
 */
```
