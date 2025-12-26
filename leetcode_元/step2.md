# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- mapを使って解いてみる

```typescript
function isValid(s: string): boolean {
    let stack = [];
    const pair = new Map<string, string>([
        [')', '('],
        [']', '['],
        ['}', '{'],
    ]);

    for (const bracket of s) {
        if (pair.has(bracket)) {
            let top = stack.pop();
            if (top !== pair.get(bracket)) {
                return false;
            }
        } else {
            stack.push(bracket);
        }
    }

    if (stack.length === 0) {
        return true;
    } else {
        return false;
    }
};
```
