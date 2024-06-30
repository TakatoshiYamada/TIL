# Chapter1

## 1.01.出力とコメント

キーポイント
- #include <bits/stdc++.h>とusing namespace std;は毎回最初に書く
- C++のプログラムはmain関数から始まる
- cout << "文字列" << endl;で文字列を出力できる
- //や/* */でコメントを書ける
    - //	同じ行の//を書いた場所より後
    - /* */	/*と*/の間

main関数の外の部分についての詳細は第4章で説明しますが、このページの末尾の「細かい話」で簡単に説明しています。気になる人は読んでみてください。
読むのが面倒な人は「プログラムの最初にとりあえず書く必要があるもの」くらいの認識で良いです。

### cout
しーあうと
文字列出力
endlは開業

### セミコロン

行の一番最後には;（セミコロン）が必要です。
C++では、大抵の行の一番最後にはセミコロンが必要になります。どの行にセミコロンが必要でどの行に不要なのかは新しい文法を学んだ際に適宜見ていって下さい。
セミコロンが必要なところで書き忘れるとエラーになるので、注意しましょう。

### 複数の出力

```c
#include <bits/stdc++.h>
using namespace std;

int main() {
  cout << "a";
  cout << "b" << endl;
  cout << "c" << "d" << endl;
}
```

### include <bits/stdc++.h>

C++の機能を「全て」読み込むための命令

Q. C++標準で無い機能を利用すべきではないのでは？

A. インクルードパスを設定して自分で作成したstdc++.hファイルを使えばGCC以外でも利用できるので、少し便利なライブラリがある環境で作業しているような状況だと考えてください。それでも受け入れられない場合は、APG4bで扱っているのはC++ではなく「GCCのC++」だと認識してもらえれば結構です。

### using namespace std;
- using namespace std;はプログラムを短く書くための機能です。
- #includeで読み込んだC++の機能を利用するためには、通常はstd::coutやstd::endlのようにstd::をはじめに付ける必要があります。
- using namespace std;を利用すると、このstd::を省略して書くことができます。
- なお、using namespace std;も業務におけるプログラミングでは推奨されないことがありますが、競技プログラミングやAPG4bで利用する場合は全く問題ありません。

## 1.02 プログラムの書き方とエラー

キーポイント
- スペース・改行・インデントを使ってプログラムを見やすくする
- プログラムは「書く→実行→正しく動作することを確認」で初めて完成と言える
- コンパイルエラーは文法のエラーで、プログラムは実行されない
- 実行時エラーは内容のエラーで、プログラムは強制終了される
- 論理エラーは内容のエラーで、プログラムは正しく動いているように見えてしまう
- エラーは「実行して動作を確認する」「Webで検索する」等して修正する
- エラーの大まかな発生箇所は./Main.cpp:行:文字目: errorからわかる
- エラーメッセージが複数表示された場合は最初のエラーから直す

c++は基本的にスペースと改行は同じ意味
どちらも省略できる
インデントも
AtCoderは2

大量のエラーメッセージが表示された場合、とりあえず一番最初のエラーメッセージだけを見ると良いです。

## D - 1.03.四則演算と優先順位

- 7 / 3が2になっていることに注意して下さい。C++では、整数同士で割り算した場合、結果は小数点以下を切り捨てした値になります。
- （ 7÷3=2.33...→2, −7÷3=−2.33...→−2）
- 小数点以下を切り捨てないで計算してほしい場合、7.0 / 3.0のように.0をつけます。同様に7.0 / 3.5のような計算も行えます。

7÷3=2 あまり 1
4÷5=0 あまり 4
となるため、このプログラムの出力は1と4になります。

C++の算術演算子の優先順位は、一般的な数学の優先順位と同じです。%は*や/と同じ優先順位になります。

注意点
除算の順序
割り算/のある整数同士の計算では、切り捨てが行われるタイミングの違いで結果が異なることがあります。

例えば
3÷2×4を計算する場合、書き方によって2つの計算結果が考えられます。

3 / 2 * 4 → 1 * 4 → 4
3 * 4 / 2 → 12 / 2 → 6
多くの場合、割り算はできるだけ後の方で行うようにしたほうが正しい結果になります。

ゼロ除算
0で割ると実行時エラーが発生します。

```c
#include <bits/stdc++.h>
using namespace std;

int main() {
  cout << 3 / 0 << endl;
}
```
end status:  136

3 % 0のように0で剰余演算%をした場合も同様に実行時エラーになります。

コードテスト上で表示される終了コードは136になります。
コードテスト以外の環境で実行した場合、Floating point exceptionと表示されることもあります。

なお、0 / 3や0 % 3のように、割られる数が0の場合は問題なく計算できることに注意してください。どちらも結果は0になります。

```c
#include <bits/stdc++.h>
using namespace std;

int main() {
  // 1/2×100×(100+1)
  cout << 100 * (100+1) * 1/2 << endl;
}
```
↑これを間違えたので暗記すること

## E - 1.04.変数と型

キーポイント
変数は「メモ」
=は代入
「データの種類」のことを型という

変数の宣言時に,を間に入れることで複数の変数を同時に宣言することもできます。

利用できない変数名
以下の条件に該当する名前は変数名にできません。

- 数字で始まる名前
- _以外の記号が使われている名前
- キーワード（C++が使っている一部の単語）

int	整数
double	小数（実数）
string	文字列

## G - 1.06.if文・比較演算子・論理演算子

キーポイント
if文を使うと「ある条件が正しい時だけ処理をする」というプログラムが書ける
else句を使うと「条件式が正しくなかった時」の処理を書ける
Copy
if (条件式1) {
  処理1
}
else if (条件式2) {
  処理2
}
else {
  処理3
}
比較演算子
演算子	意味
x == y	xとyは等しい
x != y	xとyは等しくない
x > y	xはyより大きい
x < y	xはyより小さい
x >= y	xはy以上
x <= y	xはy以下
論理演算子
演算子	意味	真になる時
!(条件式)	条件式の結果の反転	条件式が偽
条件式1 && 条件式2	条件式1が真 かつ 条件式2が真	条件式1と条件式2のどちらも真
条件式1 || 条件式2	条件式1が真 または 条件式2が真	条件式1と条件式2の少なくとも片方が真

## H - 1.07.条件式の結果とbool型

キーポイント
条件式の結果は真のとき1に、偽のとき0になる
1をtrueで、0をfalseで表す
bool型はtrueとfalseだけが入る型
int型の表現	bool型の表現
真	1	true
偽	0	false

#include <bits/stdc++.h>
using namespace std;

int main() {
  // 変数a,b,cにtrueまたはfalseを代入してAtCoderと出力されるようにする。
  bool a = true  // true または false
  bool b = true  // true または false
  bool c = false // true または false

  // ここから先は変更しないこと

  if (a) {
    cout << "At";
  }
  else {
    cout << "Yo";
  }

  if (!a && b) {
    cout << "Bo";
  }
  else if (!b || c) {
    cout << "Co";
  }

  if (a && b && c) {
    cout << "foo!";
  }
  else if (true && false) {
    cout << "yeah!";
  }
  else if (!a || c) {
    cout << "der";
  }

  cout << endl;
}

I - 1.08.変数のスコープ

キーポイント
{ }で囲われた部分のところをブロックという
変数が使える範囲のことをスコープという
変数のスコープは「変数が宣言されてからそのブロックが終わるまで」
スコープが重なっている場合は最も内側のブロックで宣言された変数が選ばれる

#include <bits/stdc++.h>
using namespace std;

int main() {
  int p;
  int price;
  string text;

  cin >> p;

  // パターン1
  if (p == 1) {
    int price;
    cin >> price;
  }

  // パターン2
  if (p == 2) {
    cin >> text >> price;

    int N;
    cin >> N;
  }

  cout << text << "!" << endl;
  cout << price * N << endl;
}

## J - 1.09.複合代入演算子

キーポイント
x = x + yはx += yのように短く書ける
x += 1はx++と書ける（インクリメント）
x -= 1はx--と書ける（デクリメント）

## K - 1.10.while文

キーポイント
while文を使うと繰り返し処理ができる
条件式が真のとき処理を繰り返す

while (条件式) {
  処理
}

N回処理する」というプログラムを書く場合、「カウンタ変数を0からはじめ、カウンタ変数が
Nより小さいときにループ」という形式で書く

int i = 0; // カウンタ変数
while (i < N) {
  処理
  i++;
}

## AP4 - 付録4.ループの裏技repマクロ

キーポイント
repマクロを使うと「指定した回数だけ処理を繰り返す」ことができる
repマクロを使うには宣言が必要
Copy
#define rep(i, n) for (int i = 0; i < (int)(n); i++)
指定した回数だけ処理を繰り返す
Copy
rep (i, 回数) {
  処理
}
カウンタ変数iを使えば「何回目の繰り返しか」という情報が利用できる
カウンタ変数は
0から始まり「
回数−1」で終わる
カウンタ変数名は変更できる
breakを使うとループを途中で抜けられる
continueを使うと後の処理を飛ばして次のループへ行けるo

## repマクロ

repマクロは「指定した回数だけ処理を繰り返す」という機能です。
次のプログラムは「"Hello"と出力して改行した後、"AtCoder"と出力する処理」を3回繰り返します。

Copy
#include <bits/stdc++.h>
using namespace std;
#define rep(i, n) for (int i = 0; i < (int)(n); i++)
 
int main() {
  rep(i, 3) {
    cout << "Hello" << endl;
    cout << "AtCoder" << endl;
  }
}

breakとcontinue
repマクロのループを制御する命令として、breakとcontinueがあります。

break
breakはループを途中で抜けるための命令です。

continue
continueは後の処理をとばして次のループへ行くための命令です。

注意点
repマクロを使用するときの注意
repマクロは簡潔でわかりやすい構文ですが、多人数が参加する開発等では利用できない場合もあります。
実はrepマクロはC++の標準の構文ではなく、マクロという機能を使って自分で定義した構文です。

多人数開発でマクロにより様々な構文が定義されるとプログラムが過度に複雑になるなどの理由から、マクロによる構文の定義は禁止されていることがよくあります。 repマクロを使用するときはコーディングルールを確認するようにしましょう。

ただし、競技プログラミングやAPG4bでrepマクロを使う分には何も問題は無いので、気にせず使ってください。個人開発でも基本的には使って良いです。
なお、この付録を除くAPG4bの説明文ではrepマクロは使わずにwhile文やfor文を使いますが、練習問題を解く時はrepマクロを利用しても構いません。

・細かい話

repマクロの派生
もう少し自由度を上げて、「カウンタ変数が
Sから
N−1の間処理を繰り返す」というrepマクロを利用することもあります。

カウンタ変数のスコープ
repマクロのカウンタ変数はrepマクロ{ }中でしか使えません。
次の例では、repマクロのカウンタ変数であるiがスコープの範囲外で使われているため、コンパイルエラーが発生しています。

{ }の省略
if文と同様に、repマクロの処理が一文のみの場合も{ }を省略できます。

repマクロのネスト
if文と同様に、repマクロもネストさせることができます。そのような書き方は多重ループと呼ばれます。
詳しくは2.02.多重ループで説明します。

forループとの関係
repマクロはfor文の機能を制限する代わりにシンプルに書けるようにしたものです。
以下のrepマクロとfor文はほとんど同じ意味になります。

途中でループ回数やカウンタ変数を書き換えた場合
repマクロの処理の中でループ回数やカウンタ変数を書き換えると、ループの処理に影響が出ます。
次の例ではその両方をループの中で書き換えています。

## K - 1.10.while文

キーポイント
while文を使うと繰り返し処理ができる
条件式が真のとき処理を繰り返す
Copy
while (条件式) {
  処理
}
「
N回処理する」というプログラムを書く場合、「カウンタ変数を0からはじめ、カウンタ変数が
Nより小さいときにループ」という形式で書く
Copy
int i = 0; // カウンタ変数
while (i < N) {
  処理
  i++;
}

「
N回処理する」というプログラムを書く場合、次のように「iを0からはじめ、iが
Nより小さいときにループする」という形式で書くのが一般的です。

