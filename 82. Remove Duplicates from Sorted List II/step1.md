# step1
5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。

## 考えたこと
- 解き方はいくつかあるみたいだが、dummyを使った方法でやってみる
- 重複があるかないかを1つずつ調べていく
- 現在のカーソルより前で、重複がないノードを記録しておく
- 重複があった際には、重複が終わるまでカーソルを進め、前のノードを重複ブロックの次に繋ぎ替える（prev.next = head.next;）
- 今までlet node = headのように置き換えていたが、そのままheadを操作しても問題ないか
- あくまで何をしているのかをわかるように変数に入れているだけ

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
    let prev = dummy;

    while (head !== null) {
        // 重複開始
        if (head.next !== null && head.val === head.next.val) {
            // 重複部分を最後まで進める
            while (head.next !== null && head.val === head.next.val) {
                head = head.next;
            }
            // prevのnext を、重複ブロックの次に繋ぎ替える
            prev.next = head.next;
        } else {
            // 重複がない → prev を進める
            prev = prev.next!;
        }

        head = head.next;
    }

    return dummy.next;
};
```
