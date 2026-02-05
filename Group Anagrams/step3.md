# step3:

時間を計りながら書く。10 分以内に 3 回連続でアクセプトされるまで

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
