# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- 問題の解き方はstep1と変えずに各変数名の見直しと処理の流れを修正する
    - dummyではなくrootという名前に変える
    - currentだとわかりづらいのでcurrentNodeにする
    - 使用する変数は最初にすべて初期化を行なってしまっても良さそう

```typescript
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function detectCycle(head: ListNode | null): ListNode | null {
    let root = new ListNode(0);
    let currentNode = root;
    let carry = 0;
    let sum = 0;
    let digit = 0;
    let val1 = 0;
    let val2 = 0;

    while (l1 !== null || l2 !== null || carry !== 0) {

        if (l1 !== null) {
            val1 = l1.val;
        }

        if (l2 !== null) {
            val2 = l2.val;
        }

        sum = val1 + val2 + carry;
        carry = Math.floor(sum / 10);

        digit = sum % 10;
        currentNode.next = new ListNode(digit);
        currentNode = currentNode.next;

        if (l1 !== null) {
            l1 = l1.next;
        }

        if (l2 !== null) {
            l2 = l2.next;
        }
    }
    return root.next;
};
```
