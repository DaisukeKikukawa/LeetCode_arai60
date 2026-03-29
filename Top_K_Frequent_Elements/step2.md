# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと

- 配列の中から「出現回数が多い順にk個の数字」を取り出す問題
- まず各数字の出現回数を数える必要があるため、Mapを使って頻度をカウントする
- すべての要素をソートするとO(n log n) かかるため、より効率的な方法を考えたい
- 「上位k個だけ分かればよい」ので、常にk個だけを保持するデータ構造が使えそう
- 出現回数が小さい要素をすぐに捨てられるよう、出現回数を基準にしたmin-heapを使う
- heapの中には「今まで見た中で頻度が高い数字だけ」を最大k個入れておく
- heapのサイズがkを超えたら、最も出現回数が少ない数字を取り除く
- これをすべての数字に対して行うことで、最終的にheapには頻度上位k個だけが残る
- heapに残った要素を取り出せば、それが答えになる
- この方法はheap操作がlog kで済むため、全体の計算量を抑えられる

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    // ① 出現回数をカウント
    const count = new Map();
    for (const num of nums) {
      count.set(num, (count.get(num) ?? 0) + 1);
    }

    // ② 出現回数が小さい順の min-heap
    const heap = new MinPriorityQueue({
      compare: (a, b) => count.get(a) - count.get(b)
    });

    // ③ heap に入れて、サイズを k に保つ
    for (const num of count.keys()) {
      heap.enqueue(num);

      if (heap.size() > k) {
        heap.dequeue(); // 一番頻度が低いものを削除
      }
    }

    // ④ heap に残った k 個を取り出す
    const result = [];
    while (!heap.isEmpty()) {
      result.push(heap.dequeue());
    }

    return result;
};

```
