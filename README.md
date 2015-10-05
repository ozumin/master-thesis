# Template for Bachelor / Master's Thesis

__Distributed under terms of the BSD license__

## 利用法
### プリアンブルの変更
* 33, 34行目にある以下の部位を利用者の目的に合わせて変更する

```
\def\name{\color{red}{学籍番号 名前}}
\def\ttl{\color{red}{タイトル}}
```

* 37行目にある以下の部位を利用者の所属に合わせて変更する

```
\author{早稲田大学 先進理工学研究科\\電気・情報生命専攻\\情報学習システム研究室\\\\\name}
```

* テーブル及び画像のindexが必要な場合は、66, 67行目のコメントアウトを削除する

```
% \listoftables
% \listoffigures
```

### 画像の挿入
1. `graphics`ディレクトリに画像を入れる
1. xbbファイルの自動生成設定を行っていない場合は
   `graphics`下で`extractbb *.png`コマンドなどを利用し、`.xbb`ファイルを作成する
    - `texmf.cnf`を適切に設定している場合は`.xbb`ファイルは自動的に作成できる
    - `texmf.cnf`の場所は`~ $ kpsewhich -var-value TEXMFLOCAL`で調べられる。
    - `texmf.cnf`には以下を記述する
      ```
      shell_escape_commands = \
      bibtex,bibtex8,bibtexu,pbibtex,upbibtex,biber,\
      kpsewhich,\
      makeindex,mendex,texindy,\
      mpost,pmpost,upmpost,\
      repstopdf,epspdf,extractbb,\
      ```
1. 本文に`\includegraphics{filename.png}`で画像を挿入する

### 本文の作成
1. 本テンプレートでは分割ファイル式を採用している。
1. `main.tex`には書き込まず、`intro.tex`や`theory.tex`などに本文を書き込む
1. 69行目以下の`\include{ファイル名}`でファイルを読み込み、コンパイルする
1. 各ファイルは個別にコンパイルする必要はない
1. 各ファイルにプリアンブルを書き込む必要はない
1. 本テンプレートは document class として`jreport`を採用しているので、以下のセクション構成が利用できる
    - chapter
    - section
    - subsection
    - subsubsection

### コマンドショートカット
* 以下のコマンドショートカットを作成してある。
* リファレンス
    - \Alref: アルゴリズムのリファレンスに利用する
    - \Equref: 数式のリファレンスに利用する
    - \Figref: 図のリファレンスに利用する
* 数式
    - \mb: \mathbfの省略形
    - \mr: \mathrmの省略形
    - \argmin: TeXではargminのコマンドが存在しないため、これを作成した
    - \argmax: TeXではargmaxのコマンドが存在しないため、これを作成した

* 以下がコマンドショートカットのコード

```
\newcommand{\Alref}[1]{Algorithm~\ref{#1}}
\newcommand{\Equref}[1]{式~(\ref{#1})}
\newcommand{\Figref}[1]{図~\ref{#1}}
\newcommand{\mb}{\mathbf}
\newcommand{\mr}{\mathrm}
\DeclareMathOperator*{\argmin}{arg\,min}
\DeclareMathOperator*{\argmax}{arg\,max}
```

