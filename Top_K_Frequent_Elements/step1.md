# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- まず各数字の出現回数を把握する必要があるため、Mapを使って頻度をカウントする
- 「出現回数が多い順にk個取り出す」なので、
- 数値そのものではなく出現回数を基準に並び替える必要がある
- Mapのkey（数字）を配列に変換し、
- counts.get(b) - counts.get(a) のように出現回数で降順ソートすることで、出現回数が多い順に数字を並べられる
- ソート後の配列の先頭からk個を取り出せば答えになるため、配列の長さをkに切り詰めて返している
- この方法は実装がシンプルで直感的に理解しやすい一方、ユニークな要素数をnとするとソートにO(n log n) の計算量がかかる。
- kが小さい場合でも全体をソートしているため、「上位k個だけ分かれば良い」という条件を考えると、もう少し効率の良い方法がありそう、と感じた。

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const counts = new Map();
    nums.forEach(num => {
      counts.set(num, (counts.get(num) || 0) + 1);
    });

    const results = Array.from(counts.keys()).sort((a, b) => {
      return counts.get(b) - counts.get(a);
    });

    results.length = k;
    return results;
};

```
