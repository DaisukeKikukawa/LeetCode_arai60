# step2
コードを読みやすく整える。動くコードになったら終了。このタイミングで他の方のコードも読む。

## 考えたこと
- step1のコードを見直す。
- 他の方のコードを見ているとheadをそのまま処理するのは、一般的ではなさそう
- prevという変数名もわかりづらいので、lastUniqueとする
- 細かいところだが変数に入れて書き直す。その他の部分はそこまでずれたことはしていなそうなのでよかった
- ダミーのノードは、番兵ノード（sentinel node）というらしい
- dummy = new ListNode(0, head)ではなく、stntinel = new ListNode(0, head)でも良さそう

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

function deleteDuplicates(head: ListNode | null): ListNode | null {
    let dummy = new ListNode(0, head);
    let lastUnique = dummy;
    let node = head;

    while (node !== null) {
        if (node.next !== null && node.val === node.next.val) {
            while (node.next !== null && node.val === node.next.val) {
                node = node.next;
            }
            lastUnique.next = node.next;
        } else {
            lastUnique = lastUnique.next!;
        }

        node = node.next;
    }

    return dummy.next;
};
```
