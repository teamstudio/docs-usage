# Usage Auditor のインストール

Teamstudio Usage Auditor は 利用状況の集積データをスキャンし、レポートを生成する Lotus Notes アプリケーション (TSUsage.ntf) と、サーバーで生成されるアクティビティロギングの生データを収集するプログラムとで構成されています。

Usage Auditor はワークステーション上で動作するように設計されています。利用状況のスキャンとレポートは非常にリソースを消費するプロセスを含んでいるため、実ユーザーが使用していないワークステーションにインストールしたノーツクライアントからスキャンを実行することで Usage Auditor がサーバーのパフォーマンスに与える影響を抑えられます。

## システム要件  
Usage Auditor は Windows 上で動作する IBM がサポートする 32 ビット構成のノーツクライントをサポートしています。

Usage Auditor は現在 64 ビットの Domino のインストレーション上ではサポートしていません。従って、Usage Auditor はクライアントワークステーション上で動作させることを推奨します。
 
## 前提となる要件
Teamstudio Usage Auditor は IBM Domino サーバーのアクティビティロギングタスクで収集されたデータを元に、集積とレポートを行います。

Usage Auditor の使用には、対象となるサーバーすべてにアクティビティロギングを有効化する必要があります。

アクティビティロギングはドミノディレクトリーのサーバー設定文書で有効にできます。Usage Auditor は次のアクティビティ・ストリームを追跡します:

* Domino.Notes.Database
* Domino.Notes.Session
* Domino.AGENT
* Domino.HTTP
<figure markdown="1">
  ![Activity Logging](img/installing.png)
</figure>

Domino 上のアクティビティロギングの設定におけるデフォルトは、アクティビティの情報がサーバー上の Log.nsf データベースに書き込まれ、最新の 2 週間分だけアクティビティ情報が保存されるようになっています。Usage Auditor はアクティビティの収集において不足がないように定期的に動作するようになっています。つまり、アクティビティを Usage Auditor を使って記録すれば、レポーティングを開始した直後から「すべてのアクティビティ」のサマリー情報を保持できるようになります。

上記のようにすでにアクティビティロギングの設定がオンになっていれば、Usage Auditor を直ちに起動し、設定を行うだけで Log.nsf 内のアクティビティをレポート可能になります。
 
## Usage Auditor アプリケーションのインストール
Usage Auditor のメインのアプリケーションは TSUsage.ntf というテンプレートを基にしたノーツアプリケーション(NSF)です。

このアプリケーションはクライアントからスキャンを実行するように作られています。スキャンやアクティビティのレポーティングには、複数サーバーへのアクセスすることや、プロセスの一部としてファイルシステム上のファイルを扱うため、リソースをかなり消費するものになる可能性があります。

このアプリケーションをサーバーに複製することで、生成されたレポート結果を他のユーザーにも公開することができます。

Usage Auditor ノーツアプリケーションのインストールには、TSUsage.ntf テンプレートを基に新規のデータベース(NSF)をワークステーション上のノーツデータディレクトリーに作成します。このアプリケーションにはスキャン対象となるサーバー上の Log.nsf にすくなくとも読者権限でアクセスできる ID で署名してください。サーバーが複数ドメインにまたがる場合は、この ID とワークステーションは、その対象となるすべてのサーバーに相互認証が正しくされていることが必要となります。
 
## ユーティリティ・プログラムのインストール
Usage Auditor は logscan.exe というユーティリティ・プログラムを使って、Domino サーバーからアクティビティの生データを収集します。

スキャンが実行されてこのユーティリティプログラムがノーツプログラムディレクトリーにない場合でも、Usage Auditor は自動的にユーティリティ・プログラムをインストールするようになっています。ただし、現在のユーザーがインストールに必要な OS 上の権限が必要になります。

ノーツプログラムディレクトリーにこのプログラムを保存する管理者権限が必要など自動でプログラムをインストールできなかった場合には、このユーティリティ・プログラムはデータベースの「ヘルプ」>「アプリケーションについて」に添付してあります。マニュアルでノーツ実行ディレクトリーに保存してください。

保存後、Notes 上の Usage Auditor を起動するユーザーがこのプログラムを実行するのに必要な読み取り、実行の権限が必要になります。
 
## Usage Auditor の以前のバージョンからのアップグレード
Usage Auditor をアップグレードするには、Usage Auditor のテンプレートに署名をし、ターゲットとなる Usage Auditor のデータベースの設計を更新します。

!!! Note
    Usage Auditor 5.0.0 からソフトウェアライセンスキーの入力が必要になります。新しいライセンスキーの入手には技術サポート [teamstudio.com](http://jp.teamstudio.com/support) で問い合わせするか [techsupport_japan@teamstudio.com](mailto:techsupport_japan@teamstudio.com) にメールでお問い合わせください。
    
以前のバージョンからアップグレードするとき、logscan.exe は自動的にアップグレードされません。「ヘルプ」 > 「アプリケーションについて」から logscan.exe を保存し、Notes 実行ディレクトリーにマニュアルで配置してアップグレードしてください。あるいは、Notes 実行ディレクトリーに既にある logscan.exe を削除し、最初のスキャンの際に Usage Auditor が自動で再インストールさせるようにしてください。

Usage Auditor バージョン 5.0.0 からユーザーのアクティビティは個々のユーザー文書で追跡できるようになっています。データベースレベルでのユーザー利用状況を収集はこれらの文書で無効化できます。以前のバージョンで「Show non-users for server...」ボタンで特定のユーザーを追跡しない設定は自動的にアップグレードされません。

Usage Auditor の以前のバージョンからアップグレードに関する詳細やサポートは技術サポート [teamstudio.com](http://jp.teamstudio.com/support) で問い合わせするか [techsupport_japan@teamstudio.com](mailto:techsupport_japan@teamstudio.com) にメールでお問い合わせください。