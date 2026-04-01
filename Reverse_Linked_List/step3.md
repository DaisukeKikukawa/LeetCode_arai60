# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
-

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
