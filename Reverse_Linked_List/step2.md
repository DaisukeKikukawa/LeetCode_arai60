# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- 他の方のコードを読んでいるとstackを使う方法の方が一般的なようなので、stackを使って解き直す。
- stackに積む前にnextを必ず切る→ stack:[ListNode { val: 1, next: null },ListNode { val: 2, next: null }]のような状態を作っていくイメージ
- stackに積み上がったらpopしながら再度接続

```typescript
let node = head;
const stack = [];

// stackに積む前にnext を必ず切る
while (node !== null) {
    let nextNode = node.next; // 次を退避
    node.next = null; // ここで接続を切る
    stack.push(node);
    node = nextNode;
}

// stackからpopしながら再接続
let dummy = new ListNode(0);
let tail = dummy;

while (stack.length > 0) {
    tail.next = stack.pop();
    tail = tail.next;
}

return dummy.next;
```
