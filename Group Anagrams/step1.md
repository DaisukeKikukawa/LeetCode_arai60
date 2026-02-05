# step1

5 分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず 5 分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- アナグラムかどうかは、文字をソートすると同じになるかで判断できそう
- ソート後の文字列を共通のキーとして使えば、アナグラム同士をまとめられる
- キーと値をセットで管理できるMapを使い、
  - キー：ソート後の文字列
  - 値：そのキーに対応する元の文字列の配列という形でグループ化する
- 配列strsを先頭から順に見ていって
  - 各文字列をソートしてキーを作成
  - そのキーがMapに存在しなければ、新しく空の配列を用意
  - 対応する配列に元の文字列を追加という処理を繰り返す
  - 最後に、Mapに格納されている値（グループ化された配列）だけを取り出す

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
  const sortedWordToOriginalWords = new Map();

  for (const originalWord of strs) {
    const sortedWord = originalWord.split('').sort().join('');

    if (!sortedWordToOriginalWords.has(sortedWord)) {
      sortedWordToOriginalWords.set(sortedWord, []);
    }

    sortedWordToOriginalWords.get(sortedWord).push(originalWord);
  }

  return Array.from(sortedWordToOriginalWords.values());
};
```
