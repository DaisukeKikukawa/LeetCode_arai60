# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 141. Linked List Cycleで使った考え方（Setを作成し、そのなかに各nodeを入れていく）と同じやり方でいける？
  - 前の問題ではtrue,falseを返していたが今回はノードそのものを返せばよさそう
  - サイクルがない場合はnullを返す
  - かなりあっさりと解けてしまったが本当にこれでよい？

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
