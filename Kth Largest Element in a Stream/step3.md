# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

```typescript
class KthLargest {
  private k: number;
  private minHeap: MinPriorityQueue<number>;

  constructor(k: number, nums: number[]) {
    this.k = k;
    this.minHeap = new MinPriorityQueue<number>();

    for (const n of nums) {
      this.add(n);
    }
  }

  add(val: number): number {
    this.minHeap.enqueue(val);

    if (this.minHeap.size() > this.k) {
      this.minHeap.dequeue();
    }

    return this.minHeap.front();
  }
}
```
