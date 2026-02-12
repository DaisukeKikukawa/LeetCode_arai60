# step3: 
時間を計りながら書く。10分以内に3回連続でアクセプトされるまで

## 考えたこと
- Setを使った開放で解く

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
  let visited = new Set<ListNode>();

  while (node != null) {
    if (visited.has(node)) {
        return node;
    }
    visited.add(node);
    node = node.next;
  }  
  return null;
};
```
