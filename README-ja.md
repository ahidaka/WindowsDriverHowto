# WindowsDriverHowto  (README-ja.md)

Windows ドライバー開発環境のインストールと使い方

[English version](README.md)

## Windows ドライバー開発環境のインストール

### 必要なもの

- Windows PC (X64版を推奨、空きDISKスペース50GB以上を推奨)
- Visual Studio 2019（最新版にアップデート済, Preview版不可）
- ブラウザでインターネットにアクセスできる環境

以下、開発環境のインストール手順を紹介します。

Windows ドライバー開発環境をインストールする大前提として次の注意があります。

#### Windows ドライバー開発環境構築上の注意

Windwows ドライバー開発は Visual Studio 2019 に WDK (Windows Driver Kit) 
と呼ぶプラグインを追加インストールして開発環境を構築しいます。
Visual Studio には多くのAdd In Plug In ソフトウェアとインストールオプションや設定があり、
時としてこれらがWDKと干渉し、WDKやVisual Studio の機能が正常動作しなくなる場合があります。

そのため、Visual Studioを頻繫に使用する人は複数のVisual Studio環境を用意しておき、
WDKの正常動作が確認出来るまでは、全ての環境にWDKをインストールしないことをお勧めします。

### Visual Studio 2019 Community Edition のインストール

https://visualstudio.microsoft.com/ja/downloads/
から、Visual Studio 2019 Community エディションをダウンロードしてインストールします。

使用するのは、他のエディションでも問題ありませんが、ここではCommunity エディションで
説明します。

### 最新版のWindows SDK のインストール


### 最新版のWindows WDK のインストール

