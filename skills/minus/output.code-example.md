# 例: コード

作業ディレクトリが /work で、todo リポジトリが /work/todo にあり、PR のブランチを手元に取り込んでいない場合:

````markdown
todo の PR の head（a1b2c3d）の lib/ と bin/ を、後続のタスク（フィルタ表示の追加）と突き合わせて読みました。テストは動かしていません。

## Findings

### 1. Medium: 読み込みの状態を、組み合わせが自由なフィールドで持っている

**Before**

```ocaml
(* 後続のタスクで、フィルタ表示の画面を足すとき *)
type state = { loading : bool; error : string option; items : todo list option }
if s.loading then spinner ()
else match s.error, s.items with Some e, _ -> ... | None, Some xs -> ... | None, None -> ...
```

**After**

```ocaml
(* 後続のタスクで、フィルタ表示の画面を足すとき *)
type state = Loading | Failed of string | Loaded of todo list
match s with Loading -> spinner () | Failed e -> ... | Loaded xs -> ...
```

- **箇所**：
  - state: todo/lib/state.ml:3（PR）
  - render: todo/bin/view.ml:18（PR）
- **うれしさ**：画面を足す人は、状態の数だけ分岐を書けば済む。分岐の順番や、loading と error が同時にある状態を考えなくてよい
- **範囲**：この PR では state の型だけを変え、ほかの画面は後続でよい
````
