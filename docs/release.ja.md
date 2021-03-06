# リリースノート

## Teamstudio Usage Auditor 5.0.1

Teamstudio Usage Auditor 5.0.1 には製品の正確性と信頼性を向上する不具合修正と機能拡張を含んでいます。もっとも顕著な変更には以下が含まれます:
### Web 利用状況
Usage Auditor 5.0.1 には特定のサーバー設定で Web ブラウザからのアクティビティがレポートできない問題を修正しています。このリリースには拡張 URL のパターンマッチングが含まれ、サーバーのデータディレクトリーの場所に関わらず Web アクティビティをレポートできるようになりました。

### トレンディング
Usage Auditor 5.0.1 はインポートされた利用状況のデータが月をまたいで行われる際に自動的にレポートを生成するトレンディングのレポートの正確性を改善しています。前のバージョンではその月の特定の日に起動され、インポートされるトレンディングに依存していましたが、これでは月々生成されるレポートが行われないという潜在的な問題がありました。このリリースでは、トレンディングの2ヶ月目に内容が正確でなくなってしまうトレンドデータの計算に関する問題を修正しています。
### 再インポートの機能
Usage Auditor 5.0.1 では、各サーバーで「Save Supporting Data」が有効になっているときに、保存したデータから利用状況のアクティビティのレポートを再生成します。

再インポートに機能は、Usage Auditor 内のすべての統計情報をクリアし、次にCSVフォーマットで保存した基のアクティビティデータを基に統計情報を再作成します。

再インポートでは、5.0.1 で修正した Web 利用状況で以前スキャンしたデータから正しいものに適用し直す場合にも用いることができます。その他、ユーザーの名前を共通名から完全名に変えたいといった、以前の内容を変更したい、特定のユーザーのアクティビティを遡って無視したいと行った場合に使用できます。

Supporting Data ビュー (表示 > 移動先から) には再インポートできる CSV ファイルを含む文書が表示されます。「Save Supporting Data」が有効であった場合の期間ごとのデータのみ再インポートが利用できます。しかしながら、再インポートはサーバー上の log.nsf のデータ保持期間 10 日という制限には一切影響をあたえるものではありません。

!!! note
    利用状況の統計情報はあらゆる理由から再インポート中に変更が加えられる可能性があります。理由の中には、「Track DB Usage」も含まれデータのすべてに適用され、レポーティングの動作への変更、以下にリストした不具合修正に対しても適用されます。

再インポートする前に、Usage Auditor データベースのバックアップを取ることを強く推奨します。

この機能は、アクション > Admin > Re-import form saved CSV data エージェントから利用できます。

## 不具合修正と機能拡張
[TMS-458] - 特定のサーバー設定をもつ Web 利用状況の検知が 5.0.0 で失敗する問題を修正  
[TMS-421] - ライセンスキー入力ダイアログにライセンス番号とシリアルキーの入力フォーマットの例を表示するように修正  
[TMS-462] - トレンディングデータアクティビティインポート中インラインで生成するように変更  
[TMS-461] - トレンドの最初の2ヶ月目以降データが正確でない問題を修正  
[TMS-463] - 保存した「サポートファイル」から利用状況の統計情報を再インポートする機能を追加  
[TMS-465] - 再インポート中、ユーザー利用状況が一秒の100回目にデータが重複する問題を修正  
[TMS-464] - 5.0.0 がデータベースパスのマッチングに大文字小文字の区別をしていたため、正しくない記録しない問題を修正  
[TMS-581] - ユーザー参照でユーザー文書を作成する際に失敗し「アイテムまたは合致しない」というエラーをログに書き込む問題を修正

## Teamstudio Usage Auditor 5.0
このメジャーリリースに数多くの機能拡張が追加されています:

* パフォーマンスの改善とユーザーアクティビティ収集とレポートの信頼性向上
* 現在時刻に対応したかたちで、スキャンを必要なときに実行できるようにしました
* ユーザー統計と追跡を拡張し、ユーザーの利用状況の総合計を表示するようになりました。加えてサーバーを選択してユーザー追跡を有効化／無効化できるようにしました
* 利用状況の統計を見やすくするためユーザーインターフェースを改善しました

### システム要件 
Usage Auditor は IBM が正式サポートする Windows 上で動作する Notes の 32 bit 版をサポートしています。Usage Auditor は現在、64 bit の Domino のインストール上での動作をサポートしていません。クライアントワークステーション上で Usage Auditor をご使用いただくことを推奨します。

### 前提条件
Teamstudio Usage Auditor は IBM Domino サーバーのアクティビティ・ロギングによって収集したデータをもとに集積、レポーティングを行っています。詳細は [Usage Auditor のインストール](installing.md) をご参照ください。

### 以前のバージョンからアップグレードするには
現在お使いのバージョンからアップグレードされる場合には Usage Auditor のオンラインマニュアル [Usage Auditor のインストール](installing.md) をご参照ください。
