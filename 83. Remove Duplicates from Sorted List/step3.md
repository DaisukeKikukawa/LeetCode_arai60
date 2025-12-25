# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと

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
  let node = head;

    while (node != null && node.next != null) {
        if (node.val === node.next.val) {
            node.next = node.next.next;
        } else {
            node = node.next
        }
    }
    return head;
};
```
