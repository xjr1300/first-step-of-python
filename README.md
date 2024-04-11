# Pythonの最初のステップ for Windows

- [Pythonの最初のステップ for Windows](#pythonの最初のステップ-for-windows)
  - [Pythonの簡単な説明](#pythonの簡単な説明)
    - [Pythonの特徴](#pythonの特徴)
    - [Pythonの欠点](#pythonの欠点)
  - [Pythonのインストール](#pythonのインストール)
  - [Visual Studio Code(VSCode)のインストール](#visual-studio-codevscodeのインストール)
  - [Python拡張機能のインストール](#python拡張機能のインストール)
  - [VSCodeのエディタ設定](#vscodeのエディタ設定)
  - [インタープリタの使用](#インタープリタの使用)
  - [チュートリアル用のプロジェクトの作成](#チュートリアル用のプロジェクトの作成)
  - [仮想環境の作成](#仮想環境の作成)
  - [VSCodeで仮想環境を選択](#vscodeで仮想環境を選択)
  - [言語機能の説明](#言語機能の説明)
    - [コメント](#コメント)
    - [データ型](#データ型)
      - [string型（文字列）](#string型文字列)
      - [int型（整数）](#int型整数)
      - [float型（32bit浮動小数点数）](#float型32bit浮動小数点数)
      - [Decimal型（固定小数点数）](#decimal型固定小数点数)
      - [bool型（真偽値）](#bool型真偽値)
      - [list型（リスト）](#list型リスト)
      - [tuple型（タプル）](#tuple型タプル)
      - [dict型（辞書）](#dict型辞書)
      - [set型（集合）](#set型集合)
      - [None](#none)
    - [変数](#変数)
    - [関数](#関数)
    - [スコープ](#スコープ)

## Pythonの簡単な説明

### Pythonの特徴

- オープンソース
- コードの記述がシンプルなインタプリタ言語
- Python公式から提供される標準ライブラリが豊富
- Pythonのエコシステムを形成するコミュニティのライブラリの開発が活発
- 機械学習向けの言語として注目
- 動作環境(Pythonランタイム)があれば、Webシステムなど、どのようなプログラムでも記述可能
- 人気のあるプログラミング言語の1つで、人気は`JavaScript`に次いで２位(2024年)

### Pythonの欠点

- プログラムの実行速度が遅い
- 型安全でない
- 実行する前にプログラムに誤りがあることに気付きにくい
- 明示的に型を示さないため、過去に実装したコードの可読性が低い
- プログラムの可搬性が低い
- OS上で動作するランタイム上で実行されるため、OSなど低水準（機械に近い）な処理は記述不可能

```python
# pythonで実装したフィボナッチ数列の例
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

# pythonはタイプヒントにより、次のように関数を定義できるが、実行時には無視される。
# def fibonacci(n: int) -> int:
#     pass
#
# `mypy`などの静的型チェッカーを使うことで、実行前に型の不整合を検出できる。
# ただし、正しくタイプヒントで表現することが難しい場合がある。
# 次の場合、型をタイプヒントでどのように表現する???
# d = { "a": 42, "b": "foo", "c": 3.47, "d": [1, ["a", "b", 3], "bar"]}
```

```rust
/// rustで実装したフィボナッチ数列の例
fn fibonacci(n: u32) -> u32 {
    match n {
        0 => 0,
        1 => 1,
        _ => fibonacci(n - 1) + fibonacci(n - 2),
    }
}
```

Pythonは処理が遅いにも関わらず、機械学習や画像処理に利用される理由は、コストの高い処理を`C`言語で記述されたプログラム（ライブラリ）に移譲して、結果を受け取っているからです。

## Pythonのインストール

[Python公式サイト](https://www.python.org/)の[ダウンロードページ](https://www.python.org/downloads/)にWebブラウザでアクセスして、`Download Python 3.x.x`ボタンをクリックします。

![Pythonダウンロードページ](./images/python-download-page.png)

ダウンロードボタンをクリックしたブラウザが動作している環境に適した最新のPythonのインストーラーの保存を求められるため、自分のPCにインストーラーを保存します。

Pythonインストーラーのダウンロードが完了したら、ダウンロードしたインストーラーをダブルクリックして実行します。

Install Python 3.x.xの画面では、`Add python.exe to PATH`にチェックを入れて、`Install Now`ボタンをクリックします。

![Pythonインストール画面](./images/python-install.png)

`Setup was successful`と表示されればPythonのインストールは完了です。同じ画面の`Close`ボタンをクリックしてインストーラーを終了します。

Pythonが正常にダウンロードされているか確認するために、タスクバーの検索ボックス(Windowsアイコンの右の虫眼鏡)をクリックして、`ここに入力して検索`に`cmd`と入力してコマンドプロンプトを起動します。

コマンドプロンプトが起動したら、`python --version`と入力してEnterキーを押します。
インストールしたPythonのバージョンが表示されればPythonのインストールは成功です。

![Pythonバージョン確認](./images/python-version.png)

「内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチファイルとして認識されません。」などのエラーメッセージが表示された場合は、Pythonインタープリタへのパスが環境変数に設定されていない可能性があります。この場合、次をコマンドプロンプトで実行した後、再度`python --version`を実行してください。

> 次はPython3.12の場合です、異なるバージョンをインストールした場合は`Python<version>`の部分を適宜変更してください。

- PowerShellの場合

```ps
 $ENV:Path+=";C:\Users\d12272\AppData\Local\Programs\Python\Python312\Scripts\"
```

- MS-DOSの場合

```dos
set PATH=%PATH%;C:\Users\d12272\AppData\Local\Programs\Python\Python312\Scripts\
```

## Visual Studio Code(VSCode)のインストール

[VSCode公式サイト](https://azure.microsoft.com/ja-jp/products/visual-studio-code)にWebブラウザでアクセスして、`Visual Studio Codeをダウンロードする`ボタンをクリックします。

![VSCodeダウンロードページ](./images/vscode-download-page.png)

表示された`Download Visual Studio Code`ページにある`Windows`ボタンをクリックします。
`Windows`ボタンをクリックすると最新のVSCodeのインストーラーの保存を求められるため、自分のPCにインストーラーを保存します。

![VSCodeインストーラー保存](./images/download-vscode-for-win.png)

VSCodeのインストーラーのダウンロードが終了したら、VSCodeのインストーラーをダブルクリックして実行します。

インストーラーを実行した時、「このインストーラーは管理者としてVSCodeを実行することを意図していない・・・」などの警告が表示されるかもしれませんが、無視して`OK`ボタンをクリックしてください。

VSCodeのインストーラーには、次を入力してください。

- 使用許諾契約書の同意: 同意する
- インストール先の指定: デフォルト
- スタートメニューディレクトリーの指定: デフォルト
- 追加タスクの選択
  - アイコンを追加する:
    - デスクトップ上にアイコンを作成する: 任意
  - その他:
    - エクスプローラーのファイルコンテキストメニューに[Codeで開く]アクションを追加する: チェック推奨
    - エクスプローラーのディレクトリコンテキストメニューに[Codeで開く]アクションを追加する: チェック推奨
    - サポートされているファイルの種類のエディターとして、Codeを登録する: チェック推奨
  - PATHへの追加(再起動後に使用可能): **チェック**
- インストール準備完了
  - `インストール`ボタンをクリック

VSCodeのインストール完了画面が表示されたら`完了`ボタンをクリックして、VSCodeのインストーラーを終了します。

VSCodeが起動したらVSCodeのインストールは成功です。

タスクバーの検索ボックスに`code`と入力してVSCodeを起動できることを確認してください。
またインストーラーの画面で`エクスプローラーの〇〇コンテキストメニューに・・・`をチェックした場合は、エクスプローラーでファイルまたはディレクトリをマウスで右クリックして表示されるコンテキストメニューに`Codeで開く`メニューがあること、そのメニューをクリックしたときVSCodeが起動することを確認してください。

![エクスプローラからVSCodeを起動](./images/run-vscode-from-explorer.png)

## Python拡張機能のインストール

VSCodeの画面の左にある`Extensions`をクリックして次の拡張機能をインストールします。

- `Python`: Microsoft社
- `Japanese Language Pack for Visual Studio Code`: Microsoft社
- `indent-rainbow`: oderwat社

上記拡張機能は、`Extensions`の上部にある`Search Extensions in Marketplace`に`python`や`japanese`を入力することで検索できます。
それぞれの拡張機能が見つかったら、その拡張機能の右下にある小さな`Install`をクリックすることで拡張機能をインストールできます。

Python拡張機能をインストールすると`Pylance`と`Python Debugger`も同時にインストールされます。
これらの拡張機能が、Pythonコードを自動補間や整形したり、デバッグを支援するなど、開発者の実装体験(エクスペリエンス)を向上します。
<<<<<<< HEAD

Pythonコードは、条件判断した結果によって実行するコードの範囲や、繰り返し処理するコードの範囲をインデント(字下げ)で表現します。
`indent-rainbow`拡張機能は、Pythonコードのインデントを視覚的にわかりやすく表示するための拡張機能です。
また、上記で説明したコードの範囲をインデントで表現することを、Pythonではブロックと呼びます。

![indent-rainbowの効果](./images/effect-of-indent-rainbow.png)

## VSCodeのエディタ設定

Pythonでコードを記述する場合、次のようなコーディングスタイルがあり[PEP8](https://peps.python.org/pep-0008/)として公開されています。

- 文字エンコーディングはUTF-8
- インデントはスペース4つ

また、改行コードの標準は、Windowsでは`CRLF`、LinuxやMacでは`LF`です。
PEP8に定められてはいませんが、`LF`が望ましいのではないかと考えています。

> 共同開発する場合は、コーディングスタイルを統一することが重要です。

上記コーディングスタイルを苦痛なく実現するために、VSCodeの設定を次の通り変更します。

1. VSCodeで`Ctrl+Shift+P`を押して、コマンドパレットを表示します。
2. コマンドパレットに`open user settings`と入力していくと、コマンドの候補がリストされるため`Preferences: Open User Settings`をマウスで選択します。
3. テキスト入力欄に`editor: tab size`と入力して、表示された`Editor: Tab Size`の値を`4`に変更します。
4. 同様に`editor: insert spaces`と入力して、表示された`Editor: Insert Spaces`をチェックします。
5. 次に`files: eol`と入力して、表示された`Files: Eol`に`\n`を入力します。
6. 最後に`files: encoding`と入力して、表示された`Files: Encoding`に`UTF-8`を入力します。

`eol`は`end of line(s)`の略です。

VSCodeの設定は即座に反映されるため、`OK`ボタンをクリックするなどのアクションは必要ありません。

- `Preferences: Open User Settings`

![ユーザー設定](./images/open-user-settings.png)

- `Editor: Tab Size`

![タブサイズ](./images/tab-size.png)

- `Editor: Insert Spaces`

![スペース挿入](./images/insert-spaces.png)

- `Files: Eol`

![改行コード](./images/eol.png)

- `Files: Encoding`

![文字エンコーディング](./images/character-encoding.png)

## インタープリタの使用

インタープリタを使用するためには、ターミナルを起動する必要があります(もしかしたら、すでに起動しているかもしれません)。
VSCodeの[Terminal]メニューから[New Terminal]を選択すると、VSCodeの下部にターミナルが表示されます(Ctrl+Shift+@)。

- PowerShellの場合

![PowerShell](./images/power-shell.png)

- コマンドプロンプト(MS-DOS)の場合

![DOS](./images/dos.png)

ターミナルに`python`と入力して`Enter`キーを押します。
Pythonのインタープリタが起動し、`>>>`(プロンプト)が表示されれば、Pythonのインタープリタを使用できます。

- PowerShellの場合

```ps
PS C:\Users\xxx> python
Python 3.12.3 (tags/v3.12.3:f6650f9, Apr  9 2024, 14:05:25) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

- MS-DOSの場合

```dos
C:\Users\xxx> python
Python 3.12.3 (tags/v3.12.3:f6650f9, Apr  9 2024, 14:05:25) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

インタープリタに次を1行ずつ入力して、`Enter`キーを押して、どのように機能するか確認してください。

```python
print("Hello, Python!")
1 + 2
3 * 6
12 / 4
type(12 / 4)
12 // 4
type(12 // 4)
13 / 4
13 // 4
13 % 4
4**2
10 + 10.5
"hello, " + "world!"
type(43)
type("43")
a = 43
print(f"a = {a}")
import math
pi = math.pi
pi
math.sin(pi)
math.sin(math.pi)
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

fibonacci(10)
exit()
```

`def fibonacci(n):`と入力して`Enter`キーを押すと、次の行が`...`に変わります。
関数のブロックを表現する必要があるため、`Tab`キーを押した後`if n == 0:`と入力して`Enter`キーを押します。
それぞれの`return`文を入力する前に`Taq`キーを2回押す必要があります。
`fibonacci`関数の最後の`return`文の後は、`Enter`キーを2回押すと`...`が消えて、次の行が`>>>`に変わります。

> `...`が表示されている場合、ブロック内のコードを入力する必要があることを示しています。

インタープリタに`exit()`と入力して`Enter`キーを押すと、Pythonのインタープリタが終了します(`Ctrl+d`でも終了できます)。

## チュートリアル用のプロジェクトの作成

1. エクスプローラーを開き、例えば`C:\Users\<user-identifier>\Documents`ディレクトリ(フォルダ、`PC > ドキュメント`と表示されています)に`py_tutorial`ディレクトリを作成します。
2. 作成した`py_tutorial`ディレクトリを右クリックして、表示されたコンテキストメニューから`Codeで開く`を選択して、`py_tutorial`をカレントディレクトリとしてVSCodeが起動します。

`Do you trust the authors of the files in this folder?`と表示された場合、**全面的に信用**するため、`Truest the authors of all file in the parent folder 'Documents'`をチェックして、`Yes, I trust the authors`ボタンをクリックしてください。

以降`py_tutorial`ディレクトリを**プロジェクトディレクトリ**と呼びます。
また、ファイルやディレクトリのパスは、カレントディレクトリからの相対パスで表現します。

```text
py_tutorial
├─cart
│  └─templates
├─coupons
│  └─migrations
└─locale
    └─es
        └─LC_MESSAGES
        └─payment
```

`cart`のパスは、`cart`または`.\cart`と表現します。
`LC_MESSAGES`のパスは、`locale\es\LC_MESSAGES`または`.\locale\es\LC_MESSAGES`と表現します。
最初の`.`は現在のディレクトリを示しており、つまり`py_tutorial`ディレクトリです。
ただし、`cart`ディレクトリを`py_tutorial\cart`と表現できません。これは存在しない`py_tutorial\py_tutorial\cart`を示します。

## 仮想環境の作成

PythonはOSにインストールされています。
今後のプロジェクトでは、多種多彩なプログラムを実装することになります。
しかし、将来を含むそれぞれのプロジェクトは、現在インストールされているPythonのバージョンで動作しないでしょう。

また、それぞれのプロジェクトでは、色々なパッケージを導入して、プログラムの機能や開発速度を向上させます。
ここで、パッケージ間のバージョン依存により、新しい機能が追加された最新バージョンのパッケージを利用する必要があったとします。
しかし、あるプロジェクトが想定しているパッケージのバージョンと最新バージョンに互換性がない場合、最新バージョンを導入をあきらめなければならないかもしれません。

> セマンティックバージョニングを採用している場合の、メジャーバージョンの増加(1.0.0 -> 2.0.0)は、後方互換性を維持していません。

このため、Pythonのプログラムを実装する場合、そのプロジェクトのPythonバージョンやパッケージのバージョンが、OSにインストールされたPythonに影響を与えないように、別の環境を用意してプロジェクト用に環境を固定することが基本です。
この別の環境のことを**Python仮想環境**または単に**仮想環境**と呼んでいます。

プロジェクト用の仮想環境を作成して、作成した仮想環境を次の通り有効にします。
1行目は、プロジェクトディレクトリ（カレントディレクトリ）に`.venv`ディレクトリを作成して、そのディレクトリに仮想環境を作成するコマンドです。
2行目は、作成した仮想環境を有効にするコマンドです。

- PowerShellの場合

```ps
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

- MS-DOSの場合

```dos
python -m venv .venv
.venv\Scripts\activate.bat
```

## VSCodeで仮想環境を選択

Python拡張機能がプロジェクト用の仮想環境を認識できるように、次の通りVSCodeを設定します。

1. `Ctrl+Shit+P`を押してコマンドパレットを表示します。
2. 表示さえたコマンドパレットで`python: select interpreter`と入力して、表示されたリストから`Python: Select Interpreter`を選択します。
3. 表示された仮想環境（OSにインストールされたPythonを含む）がリストされるため、表示された候補のパスを確認して`Python x.x.x ('.venv': venv) .\venv\Scripts\python.exe - Recommended`を選択します。

![仮想環境の選択](./images/select-venv.png)

「Pythonの仮想環境の有効化に成功しけど、ターミナルのプロンプトのインジケーターに"(.venv)"と表示されてないかもしれないよ」的なメッセージが表示されるかもしれません。
その場合、単にそのメッセージを閉じるか、`Don't show again`をクリックしてください。
`Don't show again`ボタンの下に`Python 3.12.3 ('.venv': venv)`と表示されていれば、仮想環境が有効になっています。

![ターミナルからの通知](./images/venv-terminal-message.png)

## 言語機能の説明

### コメント

VSCodeのエクスプローラーにある`New File`ボタンをクリックして、新しく作成するファイルの名前を`comments.py`と入力します。
次に示すように`comments.py`ファイルが配置されていない場合、プロジェクトディレクトリ直下に`comments.py`ファイルが作成されていない可能性があります。

![comments.pyファイル作成](./images/add-new-file.png)

`comments.py`ファイルに次を入力して、ファイルを保存してください。

```python
# これはコメントです。

print("Hello, Python!")  # `#`から右はコメントです。

"""
ダブルクォート3つで上下を挟んだ場合、ダブルクォートを含めてすべてコメントです。
このコメントの記述は、複数行のコメントを記述できます。
"""

'''
シングルクォート3つで上下を挟んだ場合、効果はダブルクォート3つと同じです。
'''
```

ターミナルで次を実行すると、ターミナル（標準出力）に`Hello, Python!`が表示されます。
他の部分はプログラムの実行に影響せず、インタープリタがコメントとして判断されていることがわかります。

![comments.pyの実行](./images/run-comments.png)

### データ型

Pythonには、次のようなデータ型があります。

- `str`: 文字列
- `int`: 整数
- `float`: 浮動小数点数
- `Decimal`: 固定小数点数
- `bool`: 真偽値
- `list`: リスト
- `tuple`: タプル
- `dict`: 辞書
- `set`: 集合
- `None`

#### string型（文字列）

文字列を扱う型です。
表現したい文字列をダブルクォートまたはシングルクォートで挟んで表現します。
文字列を操作する便利な機能（メソッド）が多く提供されています。

```python
>>> "Hello, Python!"
'Hello, Python!'
>>> 'Hello, Python!'
'Hello, Python!'
>>> "Hello, " + "Python!"
'Hello, Python!'
>>>
>>> "foo, bar, baz, qux, quux".split(",")
['foo', ' bar', ' baz', ' qux', ' quux']
```

#### int型（整数）

整数を表現する型で、他のプログラミング言語と異なり、扱える値の範囲は正負とも無限大です。

#### float型（32bit浮動小数点数）

小数を含む数値を扱う型です。
有理数の中で正確に表現できない値（割り切れない分数の値）があるため注意が必要ですが、座標値などを扱うときに便利です。

```python
>>> 0.1 + 0.1 + 0.1
0.30000000000000004
```

この理由で、float型でお金を扱わないようにしてください。
お金を扱う場合は、次に説明するDecimal型を使用してください。

#### Decimal型（固定小数点数）

十進数を正確に表現できる型です。
人々が学校で習った算術と同じように動作する算術を提供します。

```python
>>> from decimal import Decimal
>>> Decimal("0.1") + Decimal("0.1") + Decimal("0.1")
Decimal('0.3')
```

`Decimal("0.1")`などと値を文字列で与えていることに注意してください。
`Decimal(0.1)`とすると、浮動小数点数の誤差が発生するため、正確な計算ができません。

```python
Decimal(0.1)
Decimal('0.1000000000000000055511151231257827021181583404541015625')
```

#### bool型（真偽値）

`True`または`False`を表現する型です。

```python
>>> True
True
>>> False
False
```

#### list型（リスト）

複数の要素を順序付けて格納する型です。
Pythonの配列(`array.array`)や他の言語の配列と異なり、異なるデータ型の要素を格納できます。

要素を追加、削除、取得するための便利な機能（メソッド）が多く提供されています。
末尾への要素の追加は定数時間(`O(1)`)ですが、中間への要素の追加は線形時間(`O(n)`)です。
先頭の要素の追加を定数時間にしたい場合は、`collections.deque`を使用します。

```python
[1, 2, 3, 4, 5]
>>> ["foo", "bar", "baz", "qux", "quux"]
['foo', 'bar', 'baz', 'qux', 'quux']
>>> [1, "foo", 3.14, True, [1, 2, 3]]
[1, 'foo', 3.14, True, [1, 2, 3]]
```

list型の要素を追加、削除、取得するためのメソッドは次の通りです。

```python
>>> l = [1, 2, 3, 4, 5]
>>>
>>> l[0]
1
>>> l[1]
2
>>> l[-1]
5
>>> l[2:4]
[3, 4]
>>>
>>> l.append(6)
>>> l
[1, 2, 3, 4, 5, 6]
>>> l.insert(0, 0)
>>> l
[0, 1, 2, 3, 4, 5, 6]
>>> l.pop()
6
>>> l
[0, 1, 2, 3, 4, 5]
>>> l.pop(0)
0
>>> l
[1, 2, 3, 4, 5]
>>> l.remove(3)
>>> l
[1, 2, 4, 5]
```

リストの値を順に取得する場合は、次のように`for`文などを使用します。

```python
>>> values = list(range(5))
>>> for value in values:
...     print(value)
...
0
1
2
3
4
>>>
>>> values[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

list型には異なる型を格納できますが、その場合、格納する要素には何らかの区分があることがあります。
その場合、list型ではなくdict型を使用します。

#### tuple型（タプル）

複数の要素を順序付けて格納する型です。
list型と同様に異なる型を格納できますが、要素を変更できません。

> list型で異なる型を格納することはあまり推奨できませんが、tuple型は不変であるため、どの位置に何が格納されているかは決まっています。
> よって、異なる型を格納するためにtuple型を利用することは推奨できます。

```python
>>> values1 = (0, 1, 2, 3, 4)
>>> values1
(0, 1, 2, 3, 4)
>>> values2 = tuple(range(5))
>>> values2
(0, 1, 2, 3, 4)
>>>
>>> for value in values1:
...     print(value)
...
0
1
2
3
4
>>>
>>> values[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: tuple index out of range
```

#### dict型（辞書）

キーと値のペアを格納するデータ型です。
キーには、通常string型が使用されますが、ハッシュ化が可能なデータ型であればキーに利用できます。
値にはどのようなデータ型も格納できます。
dictにキーと値を追加するとき、すでに同じキーが存在する場合、値が新しい値で上書きされます。

> ハッシュ化可能なデータ型は、`__hash__`メソッドが実装されています。
> int型、tuple型は`__hash__`メソッドが実装されているため、キーに利用できます。

```python
>>> d = {"a": 1, "b": 3.14, "c": "hello"}
>>> d
{'a': 1, 'b': 3.14, 'c': 'hello'}
>>> d["b"]
3.14
>>> d["e"] = "foo"
>>> d
{'a': 1, 'b': 3.14, 'c': 'hello', 'e': 'foo'}
>>> del d["e"]
>>> d
{'a': 1, 'b': 3.14, 'c': 'hello'}
>>> d["c"] = "python"
>>> d
{'a': 1, 'b': 3.14, 'c': 'python'}
>>>
>>> d["e"]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'e'
>>>
>>> for key, value in d.items():
...     print(key, value)
...
a 1
b 3.14
c hello
```

#### set型（集合）

重複した値を格納できないデータ型で、和集合、差集合、積集合などの集合演算ができます。
listなどのコレクションから重複した値を取り除く場合に便利です。

```python
>>> s1 = set()
>>> s1.add(0)
>>> s1.add(1)
>>> s1.add(2)
>>> s1
{0, 1, 2}
>>> s2 = {0, 1, 2}
>>> s2
{0, 1, 2}
>>> s2.add(2)
>>> s2
{0, 1, 2}
>>>
>>> l = [0, 0, 3, 6, 7, 8, 9, 7, 5, 5]
>>> s3 = set(l)
>>> s3
{0, 3, 5, 6, 7, 8, 9}
```

#### None

値または参照するデータがないことを示すデータ型です。

### 変数

Pythonにおける変数とは、データをメモリに格納するときに、そのデータの位置（メモリアドレス）を示すラベルのようなものです。

<https://pythontutor.com/render.html#mode=edit>

![変数の可視化](./images/variable-visualization.png)

./movies/allocation-visualization.mov

Pythonの関数は変数に代入でき、変数に代入できたり、関数の引数や戻り値に関数を指定できる**高階関数**です。

### 関数

関数は、ある処理を実行するための一連の手順をまとめて、名前をつけたものです。
Pythonは、標準で膨大な数の便利な関数を提供しています。
また、プログラムが複雑になってくると、大きな処理の流れを記述する部分と、細かな処理をする部分を分けることで、プログラムの見通しが良くなります。

プロジェクトディレクトリに、`functions1.py`ファイルを作成して、次のコードを入力してください。

```python
def main():
    foo()
    bar()
    baz()


def foo():
    print("foo")


def bar():
    print("bar")


def baz():
    print("baz")


if __name__ == "__main__":
    main()
```

そして、ターミナルに次を入力して、`functions.py`ファイルを実行してください。

```ps
python functions.py
```

関数には値を受け取り、値を返すことができます。
関数に渡す値を**引数**、関数から返ってくる値を**戻り値**と呼びます。

> 呼び出し側で関数に渡した引数を**実引数**、関数で受け取った引数を**仮引数**と区別する場合があります。

プロジェクトディレクトリに、`functions2.py`ファイルを作成して、次のコードを入力してください。

```python
def add(x, y):
    return x + y


def sub(x, y):
    return x - y


def mul(x, y):
    return x * y

if __name__ == "__main__":
    x = add(2, 3)
    print(f"x = {x}")
    y = sub(2, 3)
    print(f"y = {y}")
    print(f"z = {mul(2, 3)}")
```

関数の引数に渡された値は、その関数で行われた処理の影響を受ける引数の型と受けない引数の型があります。
関数の引数は、値をコピーして関数に渡されます。
しかし、データ型によって値そのものがコピーされるか、値が格納されている場所（メモリアドレス）がコピーされるかが異なります。

値そのものがコピーされることを**値渡し**、値が格納されている場所がコピーされることを**参照渡し**と呼びます。

int型、float型、str型は**値渡し**です。

プロジェクトディレクトリに、`functions3.py`ファイルを作成して、次のコードを入力／実行して出力される値が**変更されていない**ことを確認してください。

```python
def call_by_int_value(n: int):
    n += 10


def call_by_float_value(f: float):
    f += 10


def call_by_str_value(s: str):
    s = s + "asdf"


if __name__ == "__main__":
    n = 1
    call_by_int_value(1)
    print(f"n = {n}")

    f = 3.14
    call_by_float_value(f)
    print(f"f = {f}")

    s = "1234"
    call_by_str_value(s)
    print(f"s = '{s}'")
```

![値渡し](./images/call-by-value.png)

list型、dict型、set型は**参照渡し**です。

プロジェクトディレクトリに、`functions4.py`ファイルを作成して、次のコードを入力／実行して出力される値が**変更されている**ことを確認してください。

```python
def call_by_reference(l: list):
    l.append("added")


if __name__ == "__main__":
    l = ["foo", "bar", "baz"]
    call_by_reference(l)
    print(l)

```

![参照渡し](./images/call-by-reference.png)

### スコープ

スコープとは、変数や関数が扱える有効な範囲を示します。
関数内で宣言された変数はローカル変数で、ローカルが示す通りその関数内でのみ有効です。
ローカル変数は、その変数が宣言されたスコープから外れると、Pythonの**ガベージコレクタ**によって回収されて破棄されます。
この**ガベージコレクション**によって、メモリ領域が枯渇することを防いでいます。

Pythonでスコープは**ブロック**によって決定されます。

```python
def foo():
    a = 10
    print("foo: ", a)

    def bar():
        b = 11
        print("bar: ", b)

    bar()


if __name__ == "__main__":
    foo()

    def baz():
        c = 12
        print("bar: ", c)

    baz()
```

上記コードで宣言された変数や関数がどのようなスコープで有効か動画で確認します。
変数や関数がスコープから外れると、削除されることを確認してください。

./movies/variable-scopes.mov

プロジェクトディレクトリに`scopes1.py`ファイルを作成して、次のコードを入力／実行してください。
`print`関数をコメントアウトしていおり、プログラムはエラーなしで実行されます。

しかし、それぞれの`print`関数をコメントアウトを解除して実行すると、エラー（例外）が発生します。
実際に片方ずつ`print`関数のコメントを解除及び実行して、エラー（例外）が発生することを確認してください。

```python
def foo():
    x = 1
    print("I have x in foo: ", x)


if __name__ == "__main__":
    # 変数`x`は`foo`関数のスコープで宣言されているため参照できない
    # print(x)  # `print`文の`#`を削除すると、実行時にエラー（例外）が発生

    # `foo`関数はモジュール（ファイル）レベルで宣言されているためスコープ内
    foo()

    if True:
        y = 2

    # 知らんかった
    # 右に記述したことは誤り: 変数`y`は`if`文のスコープで宣言されているため参照できない
    print(y)

    if True:
        # 変数`z`はさらにネストした`if`文のスコープで宣言されているため参照できない
        # print(z)
        if True:
            z = 10
```

モジュール（ファイル）レベルで宣言された変数は、プログラム全体をスコープとするグローバルスコープを持ちます。
関数内でグローバール変数を利用するためには、変数名の衝突を避けるため、その変数を`global`キーワードで宣言する必要があります。

プロジェクトディレクトリに`scopes2.py`ファイルを作成して、次のコードを入力／実行してください。

```python
import sys

x = 100


def foo():
    # 関数内でグローバル変数の参照を試行
    # しかし、変数がローカルスコープで束縛されていない（宣言されていない）ことを
    # 示す`UnboundLocalError`例外が発生するため、例外処理してプログラムが
    # クラッシュすることを避ける
    try:
        print("x in foo func:", x)
    except UnboundLocalError as e:
        print(f"UnboundLocalError: {e}", file=sys.stderr)

    # 関数内でグローバル変数と同じ名前の変数を宣言
    # この変数`x`は`foo`関数のローカル変数であり、`foo`関数の終了とともに破棄
    # される。
    # また、グローバル変数`x`は、見えなくなる
    x = 300
    print("x is a local variable in foo func:", x)


def bar():
    # `x`はグローバル変数であることを宣言
    global x

    # 関数内でグローバル変数`x`を参照
    print("x in bar func:", x)

    # 関数内でグローバル変数`x`の値を変更
    x = 400
    print("x was changed in bar func:", x)


if __name__ == "__main__":
    # 関数の外でグローバル変数`x`を参照
    print("x:", x)

    # 関数の外でグローバル変数`x`の値を変更
    x = 200
    print("x after changing:", x)

    print("\n--- go to foo func ---")
    foo()
    print("--- return from foo func ---\n")

    print("x:", x)

    print("\n--- go to bar func ---")
    bar()
    print("--- return from bar func ---\n")

    print("x:", x)

    # グローバル変数`x`が400出ない場合、プログラムがクラッシュ
    assert x == 400
```

グローバル変数の使用はプログラムが複雑になると、プログラムの見通しが悪くなるため、避けることが推奨されます。
実際にグローバル変数を使用する場面は少ないです。
変数を宣言したら、関数の引数として渡すことを推奨します。
