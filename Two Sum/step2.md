# step2

コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと

- 2重ループを作るのではなく、HashMapを使う解放で考える
- 配列を先頭から順に走査し、「今の値」と足してtargetになる補数（complement）を求める
- すでに見た値をHashMapに保存しておき、その中に補数が存在するかを確認する
- HashMapにはキーに数値、値にそのインデックスを保存することで、補数が見つかった場合に対応するインデックスを即座に取得できる
- 先にmap.has(complement) で存在確認を行い、見つかった時点で[補数のインデックス, 現在のインデックス]を返す
- 補数がまだ存在しない場合のみ、現在の値とインデックスをHashMapに保存する
- こうすることで、同じ要素を2回使うことを防ぎつつ、1回のループで問題を解くことができる

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
