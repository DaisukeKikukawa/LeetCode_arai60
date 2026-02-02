# step3:
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
- step2のやり方で3連続合格になるまで解く

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
