# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- 動作が正しいことを確認したうえで、処理の意図がわかる構成になっているかを意識した
- addメソッドにロジックを集約し、constructorでは初期配列をaddに流すだけにした
  - 初期値の追加と、後続の追加処理を同じルールで扱えるようにするため
- 変数名は「何をしているか」がわかることを優先した
  - minHeapは「上位k個を管理する最小ヒープ」であることがわかる名前としてそのまま使用
- ヒープの操作は
  - `enqueue`：値を追加
  - `dequeue`：不要な（小さすぎる）値を削除
  - `front`：現在のk番目に大きい値を取得
という役割が明確になるよう、処理の順序を固定した

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
