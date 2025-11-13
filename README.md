# typescript-type-stripping1

(2025-11)

- [Node.jsでネイティブにTypeScriptを実行できる「Type Stripping」機能が安定版に到達。Node.js v25.2.0 - Publickey](https://www.publickey1.jp/blog/25/nodejstypescripttype_strippingnodejs_v2520.html)
- [Node\.js v25\.2\.0 \(Current\)](https://nodejs.org/en/blog/release/v25.2.0#2025-11-11-version-2520-current-aduh95)

ということで、
Type Stripping で動かないものを確認してみるためのワークスペース。

## 実行(暫定)

```sh
# 準備
pnpm i

# テスト実行 - Type stripping するだけで実行できる
node src/hello.ts

# enum テスト
ts-node src/ex1_enum.ts
tsx src/ex1_enum.ts
bun src/ex1_enum.ts  # bunがあれば
tsc && node dist/ex1_enum.js # トランスパイルして実行
node --experimental-transform-types src/ex1_enum.ts

## 以下おなじノリで追加
```

### 実行例

```console
$ tsx src/ex1_enum.ts
Rose is 0

$ node --experimental-transform-types src/ex1_enum.ts 
Rose is 0
(node:13934) ExperimentalWarning: Transform Types is an experimental feature and might change at any time
(Use `node --trace-warnings ...` to show where the warning was created)

$ node -v
v22.21.1
```

## 公式ドキュメントの情報

「Modules: TypeScript」セクション(Node.js v 25.2.0 版)に、タイプストリッピング(type-stripping)機能の説明があります。

URL: [https://nodejs.org/api/typescript.html#type-stripping](https://nodejs.org/api/typescript.html#type-stripping) ([Node.js][1])

この中に「TypeScript features」→「Since Node.js is only removing inline types, any TypeScript features that involve replacing TypeScript syntax with new JavaScript syntax will error, unless the flag `--experimental-transform-types` is passed.」という記載があります。 ([Node.js][1])

### サポートされていない(あるいは制限されている)構文

以上の内容により、以下のような TS 構文/機能はそのままでは動作しない、または別途フラグが必要です。

- `enum` 宣言。([Node.js][1])
- `namespace`/古い `module`(値を含むランタイムコードを持つ形)宣言。([Node.js][1])
- パラメータ・プロパティ(constructor 引数と同時にプロパティを宣言する構文)。([Node.js][1])
- デコレーター(Decorators)/TC39 提案段階の構文。([Node.js][1])
- `tsconfig.json` の設定(例えば `paths` やトランスパイル設定)をそのまま反映するわけではない。([Node.js][1])
- import で型だけを使いたいときに `type` キーワードを付けないと実行時エラーになる場合あり。([Node.js][1])
- `.tsx` ファイル(JSX を含む TSX)はサポート外、との記載あり。([Node.js][1])

[1]: https://nodejs.org/api/typescript.html "Modules: TypeScript | Node.js v25.1.0 Documentation"
