# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 3つのポインタを使い解く方法
  - 1つ前のnode（tailNode）、現在のnode（headNode）、次のnode（nextNode）を用意する。変数名はpreviousやcurrentを使うのも良さそう。
  - ループを進めるごとに、現在のnodeを1つ前のnodeを参照するようにする。
  - 参照を1つ前にしたら現在のnodeの位置を次のnodeに進める。
  - headNodeの位置がnullになるまで繰り返し、最後にtailNodeを返す
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

function reverseList(head: ListNode | null): ListNode | null {
    let tailNode = null;
    let headNode = head;
    let nextNode = null;

    while (headNode !== null) {
        nextNode = headNode.next;
        headNode.next = tailNode;
        tailNode = headNode;
        headNode = nextNode;
    }

    return tailNode;
};
```
