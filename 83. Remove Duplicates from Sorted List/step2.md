# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- Setを使った解き方もやってみる
- リストの削除は「要素を消す」というよりも「ポインターをつなぎ替える」だけで実現できる仕組みだと理解した。
- 今見ているノード（current）と、その1つ前のノード（prev）を把握しておけば、重複と判断したときにprev.next = current.nextとして飛ばすことができる。
- Setでは単に「見たことある値かどうか」を判断する役割だけを担わせ、削除そのものはリストの構造を直接つなぎ替えることで表現する、という方針に整理。
- リストは配列と違って「位置によるアクセス」ができないため、prevをどう扱うかがポイントになると感じた。
- 削除処理が正しく機能するのは、この「1つ前のノード」を保持しているから。

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
    const uniqueValues = new Set<number>();
    let currentNode = head;
    let prevNode = null;

    while (currentNode) {
        if (uniqueValues.has(currentNode.val)) {
            if (prevNode) prevNode.next = currentNode.next;
        } else {
            uniqueValues.add(currentNode.val);
            prevNode = currentNode;
        }
        currentNode = currentNode.next;
    }

    return head;
};
```
