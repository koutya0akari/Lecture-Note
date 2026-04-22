# LuaLaTeX Documents

数学関連の講義ノートを管理しているリポジトリです。各 `.tex` ファイルは基本的に独立した文書として構成されており、対応する `.pdf` を生成できます。

## 内容

- `2026s_*.tex`
  2026年度の春学期に私が受講している講義の講義ノート。

## 使用環境

- LuaLaTeX 

## 注意点

ここで公開されている `*.tex` はすべて私が作成した以下のスタイルファイルで作られているので、公開されている `*.tex` をそのまま local でコンパイルしてもエラーがでるので注意してください。 

- `jpreport.sty`
- `jpreport-beamer-template.sty`

## `\jpreportsetup` の使い方

`jpreport.sty` では、前文で

```tex
\usepackage{jpreport}
\jpreportsetup{...}
```

の形で設定を変更できます。複数の設定はカンマ区切りでまとめて指定します。

```tex
\jpreportsetup{theoremwithin=none,theoremformat=T\jpreporttheoremnumber}
```

この設定は `thm`, `lem`, `prop`, `cor`, `dfn`, `ex`, `rem`, `exe`, `prob` の各環境に共通の番号付けに反映されます。

### 主な設定項目

- `theoremwithin=<counter|none>`
  定理系環境の番号をどのカウンタに従属させるかを指定します。既定値は `section` です。
- `theoremformat=<format>`
  表示される番号の書式を直接指定します。定理自身の通し番号は `\jpreporttheoremnumber` で参照できます。

### 例

#### 節ごとの番号付け（既定値）

```tex
\jpreportsetup{theoremwithin=section}
```

`1.1`, `1.2`, `2.1` のような番号になります。

#### 文書全体で通し番号にする

```tex
\jpreportsetup{theoremwithin=none}
```

`1`, `2`, `3` のような番号になります。

#### 小節ごとの番号付けにする

```tex
\jpreportsetup{theoremwithin=subsection}
```

`1.1.1`, `1.1.2` のような番号になります。

#### 表示だけを独自形式にする

```tex
\jpreportsetup{theoremwithin=none,theoremformat=T\jpreporttheoremnumber}
```

`T1`, `T2`, `T3` のような番号になります。

```tex
\jpreportsetup{theoremwithin=section,theoremformat=\thesection-\jpreporttheoremnumber}
```

`1-1`, `1-2`, `2-1` のような番号になります。

### 補足

- `\jpreportsetup` は `\usepackage{jpreport}` の後、`\begin{document}` の前で使います。
- `theoremwithin` には `section`, `subsection` など既存の LaTeX カウンタ名を指定できます。
- `theoremformat` を使うと、同じ共有カウンタを使う定理・命題・問題などの表示形式がまとめて変わります。
