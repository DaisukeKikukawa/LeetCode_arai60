# step1

5 分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず 5 分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと

- 整数の配列numsと、整数targetが与えられる。numsの中から2つの異なる要素を選んで、その合計がtargetになるような組を見つける問題。値そのものではなく、配列のインデックス（位置）を返すようにする。
- 素直な解き方としては二重ループにし、1組ずつ確認していく
- 配列のサイズが小さければ良いが、大きくなると計算量が増えてしまう

```javascript
var twoSum = function(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
};

```
