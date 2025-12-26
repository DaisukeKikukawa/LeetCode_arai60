# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
- mapを使わずにオブジェクトを使って解いた方がコードがシンプルになったので、この解き方で解く

```typescript
function isValid(s: string): boolean {
    let stack = [];
    const pair = {
        ')': '(',
        '}': '{',
        ']': '['
    }

    for (const bracket of s) {
        if (bracket === '(' || bracket === '{' || bracket === '[') {
            stack.push(bracket);
        } else {
            let top = stack.pop();
            if (top !== pair[bracket]) {
                return false;
            }
        }
    }

    if (stack.length === 0) {
        return true;
    } else {
        return false;
    }
};
```
