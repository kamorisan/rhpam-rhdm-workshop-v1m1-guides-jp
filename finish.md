このシナリオでは、RHPAMの主なコンポーネントを説明し、OpenShift上でのインストール方法について情報を提供しました。
また、ビジネスアセットの設計・実行を行うための環境にアクセスをする方法についても案内しました。

次のシナリオでは、このモジュールで説明したユースケースに基づいて、それらのアセットを構築する方法を学びます。

### 環境情報についてのまとめ

WebコンソールからOpenShiftにアクセスするには

1. ブラウザで [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} を開きます。 
2. ユーザー名: `userX`{{copy}} パスワード: `openshift`{{copy}} でログインします。
3. アクセス可能なプロジェクトの一覧が表示されます。ここでは _rhpam-userX_ プロジェクトのみです。
4. 最後にプロジェクトをクリックして、プロジェクトページを開きます。

Business Central へのアクセスするには

1. [Openshift console]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} にログインします。

2. `Developer`視点であることを確認してください。左メニューで `Topology` オプションを選択し、`rhpam-userX` プロジェクトが選択されているかどうかを確認します。

3. `rhpam7-rhpamcentr` (下の画像のStep4)のリンクをクリックし、Business Central にアクセスします。

	![PAM Project]({% image_path topology-details.png %}){:width="600px"}

4. 次の認証情報で、Business Central にログインします。

 - user: `pamAdmin`{{copy}}
 - password: `redhatpam1!`{{copy}}