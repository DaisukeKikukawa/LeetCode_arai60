# step1

5 分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず 5 分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと

- 2つの配列の両方に入っている値を探せばよさそう
- 同じ値は1回しか入れちゃダメらしい
- どっちかをSetにして、もう一方をループすればいい？
- 結果もSetにすれば重複しなくて済みそう

```javascript
var intersection = function(nums1, nums2) {
  const set1 = new Set(nums1);
  const result = [];

  for (let n of nums2) {
    if (set1.has(n)) {
      result.push(n);
    }
  }

  return result;
};

```
