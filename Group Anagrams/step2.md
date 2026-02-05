# step2

コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと

-

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
