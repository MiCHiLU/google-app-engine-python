# OAuth

%% OAuthとは
%% これまでの認証方式との違い

本書では、Google Cloud EndpointsはPythonによる実装を前提としています。

## Google Cloud EndpointsとOAuth

## Google Cloud EndpointsのOAuthに関する設定

## JavaScriptクライアントから利用する

このセクションでは、HTMLファイルから利用できる最小のサンプルコードを示します。

### 1. JavaScriptライブラリを読み込む

JavaScriptからGoogle Cloud Endpointsへアクセスするには、Google APIs Client Library for JavaScriptを利用します。

Google APIs Client Library
https://developers.google.com/api-client-library/javascript/

Google APIs Client Library for JavaScriptをブラウザへ読み込むには、HTMLファイルに次の`script`タグを記述します。

{lang=html}
~~~~
<script src="//apis.google.com/js/client.js"></script>
~~~~

### 2. JavaScript初期化処理を記述する

JavaScriptオブジェクトの初期化処理を記述します。
Google APIs Client Libraryは、読み込み完了後の初期化時に、デフォルトで`window.gapi_onload`を呼び出します。
また、JavaScriptファイルのURLに`onload`クエリを記述し、初期化時に呼び出す関数を指定することもできます。
次の例では`init`関数を呼び出します。

{lang=html}
~~~~
<script src="//apis.google.com/js/client.js?onload=init"></script>
~~~~

`gapi_onload`関数はJavaScriptのグローバル空間へ定義します。
次のようなJavaScriptコードになります。

{lang=js}
~~~~
var gapi_onload;
gapi_onload = function() {
  var root;
  root = "https://app-id.appspot.com/_ah/api";
  if (typeof PRODUCTION === "undefined" || PRODUCTION === null) {
    root = "/_ah/api";
  }
  gapi.client.load("api-name", "v1", function() {}, root);
};
~~~~

### 3. OAuth 2.0

Google Cloud Endpointsに、OAuthプロトコルによるアクセス制限を設定している場合は、OAuthプロトコルにおけるログイン処理を記述します。
通常は、ログインボタン押下時に実行されるようにするとよいでしょう。

{lang=js}
~~~~
gapi.auth.authorize({
  client_id: "12345678-abcdefghijklmnop.apps.googleusercontent.com",
  scope: "https://www.googleapis.com/auth/userinfo.email",
  immediate: true
}, callback);
~~~~

`client_id`はGoogle APIs Consoleのページで確認します。

https://console.developers.google.com/project/app-id/apiui/credential?authuser=0

`callback`には、ログイン認証処理が完了した直後に呼び出す関数を指定します。

公式ドキュメント
https://developers.google.com/api-client-library/javascript/reference/referencedocs
