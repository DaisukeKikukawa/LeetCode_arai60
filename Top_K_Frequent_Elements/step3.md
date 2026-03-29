# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
- step2のheapを使った解き方で3回アクセプトされるまで解く

```typescript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const count = new Map();
    for (const num of nums) {
      count.set(num, (count.get(num) ?? 0) + 1);
    }

    const heap = new MinPriorityQueue({
      compare: (a, b) => count.get(a) - count.get(b)
    });

    for (const num of count.keys()) {
      heap.enqueue(num);

      if (heap.size() > k) {
        heap.dequeue();
      }
    }

    const result = [];
    while (!heap.isEmpty()) {
      result.push(heap.dequeue());
    }

    return result;
};

```
