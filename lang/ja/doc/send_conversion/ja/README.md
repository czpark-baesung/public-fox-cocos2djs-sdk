## sendConversionの詳細

sendConversionメソッドを利用することで、インストール計測を行うことができます。Cookie計測を利用する場合には、外部ブラウザが起動されます。この際、外部ブラウザの遷移先をsendConversionの引数にURL文字列を指定することができます。

プロジェクトのソースコードを編集し、アプリケーションの起動時に呼び出される画面のAppDelegate:applicationDidFinishLaunching:メソッド等、アプリケーションの起動時に必ず呼ばれる箇所に対して、次の通り実装を行ってください。

> 【ご注意】
sendConversionは、特に理由がない限りはアプリケーションの起動時に呼び出されるAppDelegate:applicationDidFinishLaunching内に実装してください。それ以外の箇所に実装された場合にはインストール数が正確に計測できない場合があります。
アプリケーションの起動時に呼び出されるAppDelegate:applicationDidFinishLaunching内に実装していない状態でインストール成果型の広告を実施する際には、必ず広告代理店もしくは媒体社の担当にその旨を伝えてください。正確に計測が行えない状態でインストール成果型の広告を実施された際には、計測されたインストール数以上の広告費の支払いを求められる恐れがあります。

ヘッダファイルをインクルード

	#include "Cocos2dxFox.h"

成果通知のコードを追加

	FoxPlugin::sendConversion(“default”);

sendConversionの引数には、通常は上記の通り"default"という文字列を入力してください。デフォルトでは標準で用意されたページが表示されますが、遷移先のURLをF.O.X管理画面上で任意に設定することが可能です。


特定のURLヘ遷移させたい場合や、アプリケーションで動的にURLを生成したい場合には、URLの文字列を設定してください。

	FoxPlugin::sendConversion(“http://yourhost.com/yourpage.html”);


sendConversionメソッドの第二引数に広告主端末IDを渡すことができます。例えば、アプリ起動時にUUIDを生成し、初回起動の成果と紐付けて管理したい場合等に、利用できます。


	FoxPlugin::sendConversion("default", "your unique id");

> sendConversionは起動直後の処理として実装される必要があるため、ログインIDなどのユーザーアクションが伴う値を引数として渡すことはできません。

