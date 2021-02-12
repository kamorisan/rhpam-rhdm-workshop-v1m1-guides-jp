# 5. Business Central へのアクセス

ここまでで、PAM環境が利用できるOpenShiftへのアクセスの方法を確認しました。<br>
続いて、Business Centralとして知られる、PAMワークベンチにアクセスをします。

Business Central は、開発者だけでなく、業務エキスパートのための設計、管理、監視機能を備えています。

![Collaboration Tools]({% image_path collaboration_tools.png %}){:width="600px"}

Business Central にアクセスしてみましょう。

## Business Central へのアクセス

_すでにOpenShiftにログインしている場合は、Step2にジャンプします。_

1. ブラウザで [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} を開きます。 まだログインしていない場合、またはログアウトされている場合は、以前と同じ認証情報でログインしてください。

	- user: `userX`{{copy}}
	- password: `openshift`{{copy}}

	![OpenShift Console]({% image_path openshift-console.png %}){:width="600px"}

2. `Developer`視点であることを確認してください。左メニューで `Topology` オプションを選択し、`rhpam-userX` プロジェクトが選択されているかどうかを確認します。

3. `rhpam7-rhpamcentr`, `rhpam7-kieserver`, `react-web-app` の3つのコンポーネントが表示されています。

![PAM Project]({% image_path topology-details.png %}){:width="600px"}

4. `rhpam7-rhpamcentr` (上の画像のStep4)のリンクをクリックします。このリンクは、Business Centralにアクセスするための外部OpenShiftルートです。新しいタブが開き、Business Centralのログインページが表示されるはずです。

5. Business Centralでは、次の認証情報でログインできます。

 - user: `pamAdmin`{{copy}}
 - password: `redhatpam1!`{{copy}}

![Business Central Console]({% image_path business-central-console.png %}){:width="600px"}

以上で、ユーザーがビジネスアプリケーションの設計やテストを行うための作業環境にアクセスできることを確認してきました。

次のセクションでは、OpenShift などのクラウド CaaS 環境で Red Hat PAM がどのように動作するのか、概要を説明していきます。