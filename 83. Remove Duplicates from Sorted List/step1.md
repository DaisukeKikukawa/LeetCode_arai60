# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- まだリストの扱い方に慣れていないかもしれない
- 配列なら「新しい配列を作って、そこに非重複の値を詰め直す」という発想をしがちだが、linked listではその必要はない。
- linked listではheadが「リストの先頭ノード」を指すポインターで、これがリスト全体の入り口になっている。
- 重複を削除するときは、ノード同士のnextポインターをつなぎ替えるだけで構造を変えられるので、わざわざ別のリストを用意する必要がない。
- また、この操作では先頭ノードの位置は変わらないため、最終的に返すべきなのはcurrentではなくhead（＝最初のノード）であると理解した。

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
  let current = head;

    while (current && current.next) {
        if (current.val === current.next.val) {
            current.next = current.next.next;
        } else {
            current = current.next;
        }
    }

    return head;
};
```
