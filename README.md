# Pythonの最初のステップ

- [Pythonの最初のステップ](#pythonの最初のステップ)
  - [Pythonのインストール](#pythonのインストール)
  - [Visual Studio Code(VSCode)のインストール](#visual-studio-codevscodeのインストール)

## Pythonのインストール

[Python公式サイト](https://www.python.org/)の[ダウンロードページ](https://www.python.org/downloads/)にアクセスして、`Download Python 3.x.x`ボタンをクリックします。

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

## Visual Studio Code(VSCode)のインストール
