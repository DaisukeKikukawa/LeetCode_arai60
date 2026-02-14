# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

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
