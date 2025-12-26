# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 問題の整理
  - 数が追加されていく中で「常にk番目に大きい数」を答え続ける
  - 数値が順次追加されていく中で、常に「k番目に大きい数」を返し続ける問題である。
  - 重要なのは、新しい数が追加されるたびに、どうすれば高速にk番目を求められるかという点。
- どうやって毎回k番目を素早く求めるか？
  - 毎回全部ソートする
    - addのたびにO(n log n)→これだと遅すぎる
- 上位k個だけ覚えておけばよい
  - k番目に大きい数を求めるために、すべての値を保持する必要はない。
  - 「大きい方から上位k個」だけを保持しておけば十分である。
  - たとえばk = 3の場合：
    - 大きい方から3つの値だけを持っておく
    - その中で一番小さい値が「3番目に大きい数」になる
  - k =3なら、大きい方から3つだけ持っておく→その中で一番小さいやつ = 3番目に大きい
- データ構造
  - 上位k個を効率よく管理するために、最小ヒープ（Min Heap）を使う。
  - このとき、ヒープの先頭（最小値）がk番目に大きい数になる。
- 標準でHeapはないものの、LeetCode環境ではdatastructures-js/priority-queueが提供されているようなのでこれを使えそう。
  - そのため、MinPriorityQueueを使って最小ヒープを実装できる。
  - 参考： https://support.leetcode.com/hc/en-us/articles/360011833974-What-are-the-environments-for-the-programming-languages#:~:text=NET%209%20runtime-,JavaScript,-node.js%2022.14.0
-
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
