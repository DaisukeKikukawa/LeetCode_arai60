# 進め方
- step1: 5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。
- step2: コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。
- step3: 時間を計りながら書く。10分以内に3回連続でアクセプトされるまで。

## step1
``` javascript
//counts.set(num, (counts.get(num) || 0) + 1);
//以下の意味
if (counts.has(num)) {
  counts.set(num, counts.get(num) + 1);
} else {
  counts.set(num, 1);
}
```
https://qiita.com/Cheap-Engineer/items/428143c9872a7910908c
```javascript
function compare(a, b) {
  if (counts.get(a) > counts.get(b)) {
    return -1; // a を前
  }
  if (counts.get(a) < counts.get(b)) {
    return 1;  // b を前
  }
  return 0;
}
//これを短く書いたのが
(a, b) => counts.get(b) - counts.get(a)
```

## step2
-

## step3
-
