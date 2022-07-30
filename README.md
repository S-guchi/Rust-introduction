# Rust-introduction

↓これ読んだ
https://speakerdeck.com/rmizuta3/pythonyuzaniyorurustru-men?slide=10

## list型

rustは基本変数は不変
あとで変更する可能性がある場合はmutをつける

```rs
let mut list_sample: [i32:5] = [1,2,3,4,5];
```

要素の追加や削除が必要な場合はベクタ型(vec)を使用する。
```rs
let mut list_sample: vec[i32:5] = [1,2,3,4,5];
```

## dict

宣言のところややこし！

```rs
let mut hash_map: HashMap<&str,&str> = std::collections::HashMap::new();
hash_map.insert(k: 'KEY', v: 'VALUE');
println("{}",hash_map["KEY"])
```

## if,for,while
```rs
for i:i32 in 0..10{
    println("{}",i);
}
```

```rs
let mut cnt: i32 = 0
loop {
    if cnt == 10{
        break
    }
    cnt += 1
}
```

## コンパイルについて

```
cargo run 
```
コンパイルは早く、デバッグ情報が有効化される。
最適化は行われない。開発中ならこっちで良さげ

```
cargo run -release
```
コンパイルは遅く、デバッグ情報は無効化される。
最適化が行われる。本番用。

## Rustはガベージコレクションしない
Rustはガベージコレクション機能を持っていない。
所有権、借用という仕組みでメモリ管理を行なっている。

- 所有権
  - 変数の値を他の変数に代入したり、関数の引数に渡したりすると所有権が移る
  - 所有権が移ると、元の変数に入っていた値は自動的に使えなくなる
- 借用
  - 所有権だけでは値を渡すのが大変なので借用という機能がある
  - 変数の手前に&をつけて渡すことで借用という形になる。
  - これは値を渡すのではなく参照を渡すということになる。

## 型について
- 型は厳密で例えばi32とi64の足し算でもエラーとなる
- 配列にアクセスできる型はusizeのみ、なので要素指定してアクセスするときはasとか使ってusizeに変換したりする
- 文字の型には3種類あって、String,&str,char型がある
- 結合したいときはString&strとする必要がある。
- String同士や、&str同士だと結合できない
