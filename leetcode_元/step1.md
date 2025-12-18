# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- let pair = {')': '(',']': '[','}': '{',}のようにオブジェクトでペアを事前に定義しておき、出てきたものを突き合わせれば組み合わせの判定ができる
  - let map = new Map<string, string>([[')', '('],[']', '['],['}', '{'],]);のようにmapを使っても良い
```typescript
function isValid(s: string): boolean {
    let stack = [];
    const pair = {
      ')': '(',
      ']': '[',
      '}': '{',
    };

    for (let bracket of s) {
        // 開き括弧なら積む
        if (bracket === '(' || bracket === '[' || bracket === '{') {
        stack.push(bracket);
        } else {
          // 閉じ括弧の場合
          let top = stack.pop();
          if (top !== pair[bracket]) {
              return false;
          }
        }
    }

    // 最後にスタックが空ならOK
    if (stack.length === 0) {
      return true;
    } else {
      return false;
    }
};

```
