# Pythonの最初のステップ for Windows

- [Pythonの最初のステップ for Windows](#pythonの最初のステップ-for-windows)
  - [Pythonのインストール](#pythonのインストール)
  - [Visual Studio Code(VSCode)のインストール](#visual-studio-codevscodeのインストール)
  - [Python拡張機能のインストール](#python拡張機能のインストール)

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

「内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチファイルとして認識されません。」などのエラーメッセージが表示された場合は、Pythonインタープリタへのパスが環境変数に設定されていない可能性があります。この場合、次をコマンドプロンプトで実行した後、再度`python --version`を実行してください。

```dos
set PATH=%PATH%;C:\Users\d12272\AppData\Local\Programs\Python\Python312\Scripts\
# 上記はPython3.12の場合です、異なるバージョンをインストールした場合は`Python<version>`の部分を適宜変更してください。
```

![Pythonバージョン確認](./images/python-version.png)

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
- スタートメニューフォルダーの指定: デフォルト
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
