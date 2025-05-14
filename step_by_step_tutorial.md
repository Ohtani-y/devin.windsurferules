# Windsurfとdevin.windsurferulesのステップバイステップチュートリアル

このチュートリアルは、Windsurfを初めて使用するユーザー向けに設計されています。インストール、設定から、@grapeotの[`devin.windsurferules`](https://github.com/grapeot/devin.cursorrules)リポジトリを使用してWindsurfをツール呼び出し機能を備えた自己進化型AIエージェントに変換する方法まで、最初から説明します。このドキュメントは初心者向けに設計されていますが、経験豊富なWindsurfユーザーにも役立つ情報が含まれています。すでに知っているセクションはスキップしてください。

## インストールと初期設定

Windsurfのダウンロードとインストールは、他のアプリと同様です。公式ウェブサイト[https://www.windsurf.sh/](https://www.windsurf.sh/)からダウンロードリンクを見つけることができます。Windsurfを初めて起動すると、ログインを求められます。初めてのユーザーは、公式ウェブサイトで登録ボタンをクリックしてアカウントを作成する必要があります。

Windsurfを最大限に活用するには、月額$15のWindsurf Proプランのサブスクリプションが必要です。ただし、Windsurfは新規ユーザーに無料トライアル期間を提供しています。試してみた後、サブスクリプションするかどうかを決めることができます。

![Windsurf Proプラン](images/image2.png)

## 基本インターフェース

Windsurfはコードエディタで、通常は作業するフォルダを開きます。例えば、コンピュータに`~/Downloads/tmp`のような新しいフォルダを作成し、Windsurfの「フォルダを開く」オプションを使用してこの場所を開くことができます。

インターフェースは主に3つの部分で構成されています：
- 左サイドバー：現在のフォルダの内容を表示します（新しく作成した場合は空）
- 中央エリア：コード編集スペース（ただし、主にWindsurfのエージェント型AI機能を使用します）
- 右サイドバー：Windsurfとコミュニケーションし、指示を出し、応答を受け取るチャットエリア。このエリアが表示されない場合は、Command+Iを押して表示します。

![基本インターフェース](images/image10.png)

Windsurfのエージェント型AI機能を主に使用するため、チャットサイドバーを広くすることをお勧めします。

VS Codeと同様に、Windsurfの多くの機能はコマンドパレットを通じてアクセスします。F1を押すとコマンドパレットが表示されます。例えば、チャットパネルの表示方法を思い出せない場合は、コマンドパレットで「チャット」と入力するだけです。オプションが表示され、適切なものをクリックしてチャットを再度表示できます。コマンドには右側にキーボードショートカットも表示されるので、将来的に素早くアクセスするために覚えておくと便利です。

![コマンドパレット](images/image4.png)

![コマンドオプション](images/image9.png)

## 重要な初期設定

Windsurfは現在、デフォルトでエージェントモードを使用した統合AIエクスペリエンスを提供しています。これにより、チャット、コンポーザー、エージェントなどの異なるモード間を切り替える必要がなくなり、ニーズに適応する1つのスマートインターフェースだけを使用できます。

チャットパネルの左下隅で、使用したいAIモデルを指定できます。現在、WindsurfはClaude、GPT-4o、o3-miniなど、いくつかのAIモデルをサポートしています。一般的には、さまざまなシナリオで最も優れたパフォーマンスを発揮するClaudeを使用することをお勧めしますが、他のモデルも自由に試してみてください。

設定は次のようになります（左下にClaudeが表示されていることに注意）：

![設定](images/image8.png)

## YOLOモード設定

最初の例を始める前に、もう1つ設定変更を行う必要があります。Windsurfインターフェースの右上隅には歯車アイコンがあります。これをクリックするとWindsurfの設定に移動します。設定画面の左側には、一般、モデル、機能、ベータの4つのタブがあります。3番目のタブ（機能）をクリックし、「YOLOモードを有効にする」までスクロールします。

![YOLOモード設定](images/image5.png)

ここでは、好みに応じて設定できます：
- AIが実行する前にすべてのコマンドを確認して手動で確認したい場合は、チェックを外したままにします
- AIがシステムに害を与えないと信頼し、コマンドを自動的に実行させたい場合は、このオプションをチェックできます

この下にあるYOLOプロンプトでは、AIがコマンドを自動的に実行するタイミングをさらにカスタマイズできます。例えば、「ファイル削除を含むコマンド（rm、rmdir、rsync --delete、find -deleteなど）の場合は確認を求める」などと書くことができます。

## 最初の例：株価の可視化

Windsurfを適切に設定したので、最初の例を試してWindsurfのAIエージェント機能を実際に見てみましょう。コンポーザーパネルで、「2024年のGoogleとAmazonの株価をプロットして1つの図に表示する」のような簡単なリクエストを入力できます。

この時点で、Windsurfはエージェントモードを使用してタスクを分析し、要件を理解し、このタスクを完了するためにPythonを使用することを決定します。

![最初の例のリクエスト](images/image1.png)

Windsurfがコードの作成、環境のセットアップ、スクリプトの実行をすべて自動的に処理した後、現在のフォルダに画像ファイルが生成されます。左サイドバーでこの画像ファイルをクリックすると、リクエストした株価曲線が表示されます。

![株価プロット](images/image3.png)

この簡単な例は、WindsurfのAIエージェントが自然言語リクエストを理解し、適切なコードを作成し、依存関係を処理し、コードを実行して望ましい出力を生成する方法を示しています。これらすべてを手動でコードを書くことなく行います。

## devin.windsurferulesのセットアップ

ここまでは、Windsurfの組み込み機能を使用してきました。このAIエージェントはすでに強力ですが、自己進化できない、学習した経験/教訓を記憶できない、一般的な外部ツールを呼び出せないなど、いくつかの重要な制限があります。これらの機能をWindsurfに追加するために、@grapeotのリポジトリを使用できます：[https://github.com/grapeot/devin.cursorrules](https://github.com/grapeot/devin.cursorrules)

このリポジトリを設定して使用する手順は次のとおりです：

1. まだPythonをインストールしていない場合は、[https://www.python.org/downloads/](https://www.python.org/downloads/)にアクセスするか、好みのパッケージマネージャーを使用してPythonをインストールおよび設定します。

2. Cookiecutter依存関係をインストールして、Windsurfプロジェクトを簡単に初期化します。システムのコマンドライン（またはWindsurfのコマンドウィンドウ）で次のコマンドを実行します：
```bash
pip3 install cookiecutter
```

3. このWindsurfプロジェクトを配置したい場所に移動し、次のコマンドを実行します：
```bash
cookiecutter gh:grapeot/devin.cursorrules --checkout template
```

「command not found: cookiecutter」エラーが発生した場合は、代わりに次のコマンドを試してください：
```bash
python3 -m cookiecutter gh:grapeot/devin.cursorrules --checkout template
```

設定ウィザードが起動します。出力例は次のとおりです：

```
➜  Downloads python3 -m cookiecutter gh:grapeot/devin.cursorrules --checkout template                
/Users/grapeot/Library/Python/3.9/lib/python/site-packages/urllib3/__init__.py:35: NotOpenSSLWarning: urllib3 v2 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled with 'LibreSSL 2.8.3'. See: https://github.com/urllib3/urllib3/issues/3020
  warnings.warn(
You've downloaded /Users/grapeot/.cookiecutters/devin.cursorrules before. Is it okay to delete and re-download it? [y/n] (y):
  [1/3] project_name (my-project): my-windsurf-project
  [2/3] Select project_type
        1 - cursor
        2 - windsurf
        Choose from [1/2] (1): 2
  [3/3] Select llm_provider [Optional. Press Enter to use None]
        1 - None
        2 - OpenAI
        3 - Anthropic
        4 - DeepSeek
        5 - Google
        6 - Azure OpenAI
        Choose from [1/2/3/4/5/6] (1):
Creating virtual environment...
Installing dependencies...
```

設定には3つのステップがあります：

1. 新しいプロジェクトの名前を入力します。入力した名前に関係なく、現在のディレクトリに新しいサブフォルダが作成され、そこで設定が実行されます。

2. プロジェクトタイプを選択します。現在、CursorとWindsurfエディタをサポートしています。Windsurfを使用しているので、「2」を選択します。

3. LLMプロバイダーを選択します。これは完全にオプションの設定です。最初に始める場合は、Enterキーを押して「None」を選択するだけです。一部の高度な機能にのみ必要です。最初は「None」で始め、より慣れてきて一部の高度な機能を使用する必要がある場合に後で変更することができます。

スクリプトは自動的にフォルダを作成し、Python環境を設定します。

次に、コマンドラインで`windsurf my-windsurf-project`を使用して、新しく作成したプロジェクトを開くことができます。これで準備完了です。

## 拡張ツールの使用

この拡張Windsurfプロジェクトの使用は、通常のWindsurfプロジェクトの使用と似ていますが、タスクをより適切に完了するための追加ツールにアクセスできるようになりました。例えば、プロンプトで「OpenAIに関する最近のニュースを検索する」と言うことができます。

![拡張ツールの例](images/image6.png)

この新しく設定されたワークスペースでは、Windsurfがいくつかの追加機能を獲得したことに気付くでしょう。例えば、最初に計画のために`.windsurfrules`ファイルを編集し、次にシステム検索ツールを呼び出し、最後により多くのWebページを閲覧して最新情報を取得します。

これで、拡張Windsurfプロジェクトを使用して他のタスクを完了する準備ができました！

![ツール使用例](images/image7.png)
