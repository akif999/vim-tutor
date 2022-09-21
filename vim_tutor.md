# はじめての Vim

## 目的・背景

2022 年現在、一般的にテキストエディターは Visual Studio Code が良く用いられるようになってきています。  
それに伴い、古典的なテキストエディターである、Vim や Emacs などを使用するユーザーは少なくなっているように見受けられます。  
しかし、それら古典的なエディターについても開発や新しい機能の追加は実施されており、  
Vim や Emacs をメインのエディターとして使用するユーザーも根強く存在する現状となっています。  

そのような昨今のテキストエディターの情勢を踏まえ、  
このコンテンツでは、 Vim というエディターについて初歩的な知識を独自の視点でまとめています。  

このコンテンツを通じて、実際に Vim を使用するようになる必要はないと考えています。  
Vim がどのような考え方で設計されているかを知るだけでも、ソフトウェア開発者としての学びがあることを意識して、  
この記事は作成されています。

## 概要

本コンテンツでは主に、Vim に特徴的な「モード」という概念を中心に、  
そのモードごとにどのようにテキスト編集を行うかについて説明します。
また、別途 Vim の歴史的な概要や、Visual Studio Code の特徴の比較についても、  
簡単にまとめて掲載しています。

## 目次

1. Vim とは
2. Visual Studio Code の特徴との比較
3. モードについて
4. 各モードごとの基本的な操作
5. Vim で実践できる便利なテクニック
6. 参考文献

## 1. Vim とは

> Vimはオランダ人のプログラマー、ブラム・モールナールによってAmiga向けに開発された。  
> のちにWindowsを含むさまざまな環境に移植され、特にUnix系オペレーティングシステム  
> (OS) ではEmacsと並んで広く使用されているテキストエディタとなっている  
> https://ja.wikipedia.org/wiki/Vim

Vim は現在は Github にてソースコードが管理されており、  
ブラム・モールナール氏と世界中の有志の開発者によって開発が勧められています。  
https://github.com/vim/vim

## 2. Visual Studio code の特徴との比較

Vim と Visual Studio Code を比較したものは以下です。  

### Visual Studio Code

* Electron エンジンを活かしたリッチな GUI 操作/表現
    * Vim では実現ができないソースコードの表示方法も実現できる
        * Vim は基本的に CUI の中で動いている形で動作しているため
* 使用開始からすぐに高い生産性を得られる
    * 学習曲線は Hill Equation のイメージ

<img src="./image/hill_equation_interactive_graph_w.jpg" width="25%"/>  
https://www.physiologyweb.com/calculators/hill_equation_interactive_graph.html

### Vim

* 高度に最適化された CLI ベースの操作/表現
    * 操作が全てコマンドの組み合わせという思想で設計されており、様々な組み合わせで強力な編集が可能
    * 全ての操作にマウス操作が一切必要ない(実質という意味を含む)
* 使用開始からしばらくは生産性を上げにくい
    * 慣れてくると飛躍的に生産性が向上していく
    * 学習曲線は Exponential のイメージ

<img src="./image/image001.png" width="17.5%"/>  
https://content.nroc.org/DevelopmentalMath/U18L1T1_RESOURCE/text.html

## 3. モードについて

Vim は他のエディターにはない、「モード」という概念があります。  
Vim を操作する際は、モードを切り替えながら操作を実施します。  

<img src="./image/vim_mode.avif" width="50%"/>  
https://qiita.com/yamamoto_hiroya/items/31ce5bef451d9e3be225

各モードは、以下のような作業のために用います。

* ノーマルモー ド
    * デフォルトのモード 
    * コマンドをタイプすることにより、編集位置の変更、文字/文字列の削除等を行う
* インサートモード
    * 文字を入力するモード
    * 一般的なテキストエディターの編集操作と同様に文字の追加や BackSpace/Del による削除を行う
* ヴィジュアルモード
    * 選択範囲を指定するモード
    * 選択範囲を指定し、続けて特定のコマンドを実行することにより、文字/文字列のコピー/カット/ペースト等を行う
        * コピー/カット/ペースト以外にも、選択範囲に対して様々なコマンドを実行することができる
* コマンドモード
    * 

https://howpon.com/21851

## 4. 各モードごとの基本的な操作

以下を参照。  
https://qiita.com/hide/items/5bfe5b322872c61a6896

## 5. Vim で実践できる便利なテクニック

### 置換

* `s/hoge/fuga/`
  * `%s/hoge/fuga/` → ファイル全体

### 仮想置換

* `gR`

### グローバルコマンド

* `:g/<regex>/cmd`

### 連番生成

* `g, Ctrl+a`

### バッファへの外部コマンド実行

* %!Cmd

### マクロ

* q + 任意の key で記録開始
* q をタイプして記録終了
* @ + 任意の key でマクロ実行
* @@ で直前のマクロを再実行

### hex dump

* `%!xxd` → hex dump 表示に変換
* `%!xxd -r` → hex dump 表示からバイナリに戻す

### Quickfix

* Makefile を用意する
* `set makeprg=gmake`
* `:make`
* `:copen`

### Language Server

色んな言語の Language Server を入れて保管とかエラーチェックとかするよ。

## 6. 参考文献

* https://ja.wikipedia.org/wiki/Vim
* https://howpon.com/21851
* https://qiita.com/hide/items/5bfe5b322872c61a6896
