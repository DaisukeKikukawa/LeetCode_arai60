//step1
解法が思いつかなかったため荒井さんのyoutube上の解説動画を見て自分で書き直す
一度すべて消してやり直す

```typescript
function hasCycle(head: ListNode | null): boolean {
    if(head == null) {
        return false;
    }
    
    let fast = head;
    let slow = head;

    while(fast != null) {
        if(fast.next != null) {
            fast = fast.next.next;
        } else {
            return false;
        }
        slow = slow.next;

        if(fast == slow) {
            return true;
        }
    }
    return false;
};
```

//step2
step1のコードだと`return false`が2回あるため、これを共通化できそうだなと思い修正。

```typescript
function hasCycle(head: ListNode | null): boolean {
    if(head == null) {
        return false;
    }

    let fast = head;
    let slow = head;

    while(fast != null && fast.next != null) {
        fast = fast.next.next;
        slow = slow.next;

        if(fast == slow) {
            return true;
        }
    }
    return false;
};
```

//step3
step2のコードを3連続で10分以内に1回もエラーを出さずに書ける状態になるまで繰り返す
```typescript
function hasCycle(head: ListNode | null): boolean {
    if(head == null) {
        return false;
    }
    let fast = head;
    let slow = head;

    while (fast != null && fast.next != null) {
        fast = fast.next.next;
        slow = slow.next;

        if (fast == slow) {
            return true;
        }
    }

    return false;
};
```

## step4
いただいたレビューと他の方のコードをみて解き方を考え直す。
Floyd's tortoise and hareはソフトウェアエンジニアの常識には含まれておらず、この解放を使うことは求められていない。ノードをSetに入れて判定する解法が期待されるので、Setを使った解法で解き直す。
- 先頭のnodeの取得は今まで通り
- まずSetオブジェクトを作成する
  - これはSetではなく、Arrayでも良いのか？計算量が多くなってしまうからSetの方が適している？問題に正解するだけならArrayでも解くことはできた。
- nodeをwhile文で回していく
  - もしnodeがnullの場合は循環がないのでfalseを返すようにする。この部分は今までと同じやり方でよさそう
  - もしSetオブジェクトの中に対象のnodeが存在しているなら、これは循環があることになるのでtrueを返す。この部分も今までと同じやり方でよさそう。
  - Setオブジェクトへの追加、nodeの更新を行えばnodeを1つ1つ確認できる。
  - Set.add(node) した後、node = node.nextすることで線形にすべてたどれる

```typescript
function hasCycle(head: ListNode | null): boolean {
    if (head == null) {
        return false;
    }

    let node = head;
    let visited = new Set<ListNode>();

    while (node != null) {
        if (visited.has(node)) {
            return true;
        }
        
        visited.add(node);
        node = node.next
    }

    return false;
};
```
