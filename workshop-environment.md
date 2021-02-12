# 4. ワークショップの環境へのアクセス

OpenShift環境はすでにプロビジョニングされています。
ターミナルのコマンドラインからアクセスするか、ウェブベースのコンソールからアクセスすることができます。
このワークショップでは、あなた専用に作成したOpenShiftプロジェクトを使用して作業を行います。

## 環境の詳細

1. [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} へアクセスして下さい。
2. インストラクターから、あなたに割り当てられたユーザー番号を確認しておいてください。
    - OpenShift Console username: `userX` (例: user1)
    - OpenShift Console password: `openshift`

## OpenShift へログイン

このワークショップでは、OpenShiftへアクセスを2つの方法から選択することができます。Webコンソールまたはコマンドラインです。

### Webコンソールを使用

WebコンソールからOpenShiftにアクセスするには

1. ブラウザで [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}) を開きます。
2. ユーザー名: `userX`{{copy}} パスワード: `openshift`{{copy}} でログインします。
3. アクセス可能なプロジェクトの一覧が表示されます。ここでは _rhpam-userX_ プロジェクトのみです。
4. 最後にプロジェクトをクリックして、プロジェクトページを開きます。

### コマンドラインを使用

コマンドラインインターフェース(CLI)経由でログインするためには、ローカル環境にOpenShift CLIツールが必要です。
持っていない場合は、環境に合わせて[OpenShift CLI tool](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.2.25/openshift-client-linux-4.2.25.tar.gz)を選択してダウンロードすることができます。

あるいは、ブラウザベースのOpenShift端末を使用することもできます。必要に応じてインストラクターがこのオプションを教えてくれます。

CLIを使ってOpenShiftにログインする最も簡単な方法は、Webコンソールからアクセスしてログインし、`Copy Login Command`をクリックすることです。

![OCP Copy Login Command]({% image_path ocp-copy-login-command.png %}){:width="600px"}

1. [Openshift Console]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} にログインします。
2. `Copy Login Command` をクリックします。
3. OpenShiftが再度資格情報を要求してきます。ユーザー名とパスワードを入力してください。
4. `Display Token` をクリックします。
5. `Login with this token` に表示されている、以下のようなコマンドをコピーして、CLIでコピーしたコマンドを実行してください。

```
oc login --token=rVO1oDOjspF6CLTW53zddinWRrpxAfDsywzptM0jsiY --server=https://api.cluster-rio-ead1.rio-ead1.example.opentlc.com:6443
```

## OpenShift Platform 上での Red Hat Process Automation Manager

Once you are in the platform, on the left menu you can find the `Home` section, and under it, you shoud click on `Projects`. Select the project `rhpam-userX`, and click on the `Workloads` tab. You can see there are three `Deployment Configs`:

OpenShiftにログインしたら、左側のメニューにある `Home` セクションの下にある `Projects` をクリックしてください。
プロジェクト `rhpam-userX` を選択し、`Workloads` タブをクリックします。
3つの `Deployment Configs` があります。

  - `react-web-app`: REST経由で通信し、PAMエンジン（Kie Server）からビジネスアセットを実行するReactアプリケーション。

  - `rhpam7-kieserver` と `rhpam7-rhpamcentr`: ビジネスアセットの設計、実行、監視ができる環境。

  ![RHPAM Projects]({% image_path rhpam-projects.png %}){:width="600px"}

それぞれの `Deployment Configs` の中には、1つのポッドがリストアップされているはずです。

  - `react-web-app`: reactクライアントアプリケーションが入っているポッド。
  - `rhpam7-kieserver`: PAM 実行エンジン (Kie Server) を含むポッド。
  - `rhpam7-rhpamcentr`: 設計、管理、監視のための Business Central を含むポッド。

OCP にデプロイすると、Red Hat PAM の各コンポーネントはそれ自身のポッド内にプロビジョニングされます。
上記のコンポーネントと環境は、このワークショップで使用するものです。

さて、PAMが動作している環境の詳細がわかったので、アクセスしてみましょう!