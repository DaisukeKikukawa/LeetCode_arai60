# 進め方
- step1: 5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。
- step2: コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。
- step3: 時間を計りながら書く。10分以内に3回連続でアクセプトされるまで。

## step1
- 問題の整理：アナグラム（anagram）をグループ分けする問題。文字の並びを入れ替えることで別の文字列になるものをグループ分けする問題

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
  const map = new Map();

  for (const str of strs) {
    const key = str.split('').sort().join('');

    if (!map.has(key)) {
      map.set(key, []);
    }

    map.get(key).push(str);
  }

  return Array.from(map.values());
};
```

## step2
-

## step3
-
