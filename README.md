# WindowsDriverHowto  (README-ja.md)

Windows ドライバー開発環境のインストールと使い方

[English version](README-en.md)

## はじめに

[**Windows 10 ドライバー開発入門セミナー**](https://connpass.com/event/208039/) で **勝手にハンズオン** に参加される方向けの、**事前準備用** Windowsドライバー開発環境の構築手順を示します。

これらのインストールは全部行うと1時間程度かかるため、オンラインセミナー 中にハンズオンを試したい方は設定を完了しておいて下さい。
<br/>

### 事前準備に必要なもの

- Windows PC (x64版を推奨、空きDISKスペース50GB以上を推奨)
- Visual Studio 2019（最新版にアップデート済、Preview版は非推奨）
- ブラウザでインターネットにアクセスできる環境

続いて開発環境のインストール手順を紹介します。

Windows ドライバー開発環境をインストールする前提として、経験上次の注意があります。
ドライバー開発にそれほど興味が無い方は、WDK をインストールしないことをお勧めします。

#### 注意：Windows ドライバー開発環境構築は少し手ごわい

Windwows ドライバー開発は Visual Studio 2019 に WDK (Windows Driver Kit) と呼ぶプラグインを追加インストールして開発環境を構築します。

しかし Visual Studio には多くのAdd In Plug In ソフトウェアとインストールオプションや設定があり、
時としてこれらが WDK と干渉し、WDK や Visual Studio の機能が正常動作しなくなる場合があります。

そのため業務などで Visual Studioを頻繫に使用する方は、複数のVisual Studio環境を用意しておき、
WDKの正常動作が確認出来るまでは、WDKのインストールは1台だけ等、限定的にしておくことをお勧めします。

なお幸いに次の現在の最新版では、大きな不具合はありません。

- Visual Studio Version: 16.9.2
- WDK Version: 10.0.19041.1

それでは Windows ドライバー開発環境を構築する方法を紹介します。
インストールは次の順で行います。

- Visual Studio 2019 のインストールと設定
- WDKのダウンロードとインストール
<br/>

## Visual Studio 2019 のインストールと設定

Visual Studio 2019 のインストールと設定を示します。
すでにインストール済の方は、再インストールの必要はありません。
設定内容を確認・変更して下さい。
<br/>

### Visual Studio 2019 Community Edition のインストール

https://visualstudio.microsoft.com/ja/downloads/

から、Visual Studio 2019 Community エディションをダウンロードしてインストールします。

他のエディションを使用しても問題ありませんが、ここでは Community エディションで説明します。
インストール済の方は、Visual Studio Installerでインストール設定を確認してください。
<br/>

### Visual Studio の設定

ドライバー開発用Visual Studio 2019 のインストール設定は、次の3点に気をつけてください。

- .NET デスクトップ開発、C++によるデスクトップ開発とユニバーサルプラットフォーム開発の **ワークロード** インストール
- 最新版(10.0.19041.1) SDKのインストール
- MSVC v142 - VS2019 C++ x64/x86 Spectre 軽減ライブラリ（最新）の **個別コンポーネント** のインストール

#### インストール ワークロード の選択

Visual Studio のインストール時に次のワークロードを選択します。
追加で他のワークロード選択してインストールしても問題ありません。
インストール済の方は Visual Studio Installer の変更機能を使用して、確認・変更して下さい。

![ワークロード選択](VS-Insta111.png)
<br/>**ワークロード選択**<br/>

#### Windows SDK 最新版 (10.0.19041.1) インストール

Windows SDK 最新版 (10.0.19041.1) のインストールを確認して下さい。
インストール済の方は Visual Studio Installの変更機能を使用して、個別のコンポーネント機能で確認・変更して下さい。

![Windows SDK 最新版](VS-Insta311.png)
<br/>**Windows SDK 最新版**<br/>

#### Spectre 軽減ライブラリ（最新）インストール

![Spectre 軽減ライブラリ（最新）](VS-Insta411.png)
<br/>**Spectre 軽減ライブラリ（最新）**<br/>

個別のコンポーネントのインストールタブを選択して、
**MSVC v142 - VS2019 C++ x64/x86 Spectre 軽減ライブラリ（最新）**
のインストールを確認して下さい。

このライブラリをインストールしてない場合、Visual Studio のビルドで次のエラーが発生します。

![エラー：Spectre 軽減ライブラリ が必要です](VS-Insta211.png)
<br/>**Spectre 軽減ライブラリが無いエラー事例**<br/>
<br/>

## WDK のインストール

WDK (Windows Driver Kit)をダウンロードしてインストールする手順を示します。
<br/>

### 最新版 WDK のダウンロード

Visual Studio 2019 のインストールと設定が完了した後は、最新版のWDKをダウンロードしてインストールします。

![Hardware Windows](HardwareWindows.png)

ブラウザの検索窓に **Hardware Windows** と入力して、次の Windows ハードウェア デベロッパー センターのページを表示します。

https://developer.microsoft.com/ja-jp/windows/hardware/

![Windows ハードウェア デベロッパー センター](WDK2.png)
<br/>**Windows ハードウェア デベロッパー センター**<br/>

Windows Driver Kit (WDK) の **今すぐダウンロード** をクリックしてダウンロード用ページを表示します。このページの内容と URL は時々更新されます。

![今すぐダウンロード](WDK4.png)
<br/>**今すぐダウンロード**<br/>

表示されたページの中程にある、

	手順 2:Windows 10 バージョン 2004 用の更新された WDK をインストールする

	WDK for Windows 10 バージョン 2004 のダウンロード

の次のリンクをクリックして **wdksetup.exe** を入手して実行、インストールを開始します。

![WDK のダウンロード](WDK5.png)
<br/>**WDK のダウンロード**<br/>

なおすぐ下にある **EWDK with Visual Studio Build Tools** は、Visual Studio無しでWindowqs ドライバーをビルドするツールです。
通常使用しないため、ダウンロード不要です。
<br/>

### WDK のインストール

wdksetup.exe を実行してインストールする手順を示します。
起動画面では通常、**Install the Windows Driver Kit - Windows 10.0.19041.1 to this computer**
を選択して **Next** で進みます。

下の選択肢の **Download the Windows Driver Kit - Windows 10.0.19041.1 for installation on a separate computer**
は、オフライン インストール用の全 WDK バイナリーのダウンロードを行います。

![Specify Location: ダウンロードオプション選択](WDK-Insta1.png)
<br/>**Specify Location: ダウンロードオプション選択**<br/>

wdksetup.exe によるインストールが一旦完了すると、次の確認ダイアログが開きます。
**Install Windows Driver Kit Visual Studio extension** にチェックをいれたまま、**Close** します。

![Visual Studio extensionのインストール](WDK-Insta2.png)
<br/>**Visual Studio extensionのインストール**<br/>

続いて Visual Studio extensionのインストール先の選択ダイアログが表示されます。
複数のインストール対象の Visual Studio がインストールされている環境では、インストール先を選択してチェック後、**Install** をクリックします。

![WDK をインストールする](WDK-Insta3.png)
<br/>**VSIXのインストール先確認**<br/>

しばらくすると次の完了ダイアログが出ます。

![WDK をインストールする](WDK-Insta4.png)
<br/>拡張機能インストールの完了<br/>

以上で、Windows ドライバー開発環境のインストールが終了です。
