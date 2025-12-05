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
