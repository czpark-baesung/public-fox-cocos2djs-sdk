# アクセス解析による課金計測
本機能では広告経由および自然流入経由での売上をそれぞれ計測可能です。
アクセス解析機能を利用し、自然流入経由を含めた広告別の課金計測を行うことができます。アクセス解析による課金計測を行うために、次のsendEventメソッドを実装します。

※広告経由の売上のみを計測したい場合はLTV計測で計測可能ですので本機能の実装は必要ありません。<br>※主に自然流入経由の売上を計測したい場合などに本機能を実装してください。|パラメータ|タイプ|最大長|必須|概要|
|:---|:---:|:---:|:---:|:---|
|eventName|String|255|必須|トラッキングを行うイベントを識別できる任意の名前を設定します。<br>イベント名は自由に設定可能です。<br>イベント単位でグルーピングされ、それぞれのイベントごとに集計を行うことができます。||action|String|255|オプション|イベントに属するアクション名を設定します。<br>アクション名は自由に設定可能です。<br>各イベントをドリルダウンすることで、アクションごとに集計を行うことができます。<br>特に指定しない場合は””を設定してください。|
|label|String|255|オプション|アクションに属するラベル名を設定します。<br>ラベル名は自由に設定可能です。<br>各アクションをドリルダウンすることで、ラベルごとに集計を行うことができます。<br>特に指定しない場合は””を設定してください。||orderID|String|255|オプション|注文番号。特に指定いない場合は""を設定してください。|
|sku|String|255|オプション|商品コード。特に指定しない場合は””を設定してください。||itemName|String|255|必須|商品名||price|double||必須|商品単価|
|quantity|int||必須|購入数||currency|String||オプション|通貨コード。指定しなかった場合は"JPY"|JavaScript上では以下のように記述します。
	cc.FoxPlugin.sendEvent(eventName, action, label, orderId, sku, itemName, price, quantity, currency);LTV計測においても課金を成果地点としている場合には、同一の箇所にLTVとアクセス解析のそれぞれの計測処理を実装します。
サンプルとして、以下にアメリカドルで9.99ドルの課金を行った場合の実装例を記載致します。


	// LTV計測による課金計測	cc.FoxPlugin.addParameter("_price", “9.99”);	cc.FoxPlugin.addParameter("_currency", “USD”);	cc.FoxPlugin.sendLtv(成果地点ID);
	// アクセス解析による課金計測
	cc.FoxPlugin.sendEvent(eventName, action, null, orderId, sku, itemName, 9.99, 1, "USD");