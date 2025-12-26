# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 削除や挿入じゃなく「つなぎ替え」
Linked Listの操作は、値を消す → nextを飛ばす、追加する → nextに繋ぐを意識する。慣れている配列の感覚で考えないのが大事そう。
- 返却用の仮のノードを1つ作っておく。
  - let dummy = new ListNode(0);
  - 最終的に返すのはdummy.next
- 「結果リストの末尾」を指すポインターの意味でcurrentを定義
  - let current = dummy;
  - 新しいノードを作るたびに、ここからnextに繋いでいく
- 繰り上がりは専用の変数に入れておき、次のループに持ち越すことで処理できる
  - 今回はcarryという変数にする
- ループを続ける条件はl1, l2のどちらかが残っているor最後にcarryが残っている限りループを続けるとすれば良さそう
   - while (l1 !== null || l2 !== null || carry !== 0) {処理}


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

function addTwoNumbers(l1: ListNode | null, l2: ListNode | null): ListNode | null {
    let dummy = new ListNode(0);
    let current = dummy;
    let carry = 0;
    let sum = 0;

    while (l1 !== null || l2 !== null || carry !== 0) {

        let val1 = 0;
        if (l1 !== null) {
            val1 = l1.val;
        }

        let val2 = 0;
        if (l2 !== null) {
            val2 = l2.val;
        }

        sum = val1 + val2 + carry;
        carry = Math.floor(sum / 10);

        let digit = sum % 10;
        current.next = new ListNode(digit);
        current = current.next;

        if (l1 !== null) {
            l1 = l1.next;
        }

        if (l2 !== null) {
            l2 = l2.next;
        }
    }
    return dummy.next;
};
```
