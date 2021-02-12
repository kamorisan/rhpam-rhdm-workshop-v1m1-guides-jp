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
5. `Login with this token` に表示されている、以下のようなコマンドをコピーします。

```
oc login --token=rVO1oDOjspF6CLTW53zddinWRrpxAfDsywzptM0jsiY --server=https://api.cluster-rio-ead1.rio-ead1.example.opentlc.com:6443
```

## Red Hat Process Automation Manager on OpenShift Platform

Once you are in the platform, on the left menu you can find the `Home` section, and under it, you shoud click on `Projects`. Select the project `rhpam-userX`, and click on the `Workloads` tab. You can see there are three `Deployment Configs`:

  - `react-web-app`: A react application which communicates via REST and consumes business assets from PAM engine (Kie Server);

  - `rhpam7-kieserver` and `rhpam7-rhpamcentr`: An environment that allows authoring, execution and monitoring of business assets; 

  ![RHPAM Projects]({% image_path rhpam-projects.png %}){:width="600px"}

Inside each `Deployment Configs` you should see one pods listed:

  - `react-web-app`: Pod containing the react client application;
  - `rhpam7-kieserver`: Pod containing PAM execution engine (Kie Server);
  - `rhpam7-rhpamcentr`: Por containing Business Central, for authoring, management and monitoring;

As you can notice, when deployed on OCP, each component of Red Hat PAM is provisioned within it's own pod. The components above and environment are the ones which we are going to use during this workshop.

<!-- ### Provisioning PAM from scratch

The Workloads page shows the  current working environment provisioned for you. But what if you have special needs of tools and components? Or you simply want to know what you are working on.

Let's go ahead and create a whole new project using Red Hat PAM Templates and starting a new deployment based on your requirements.

RHPAM 7.5 brings with it an OpenShift operator that can simplify the installation process. The operator creates for the deployed environment an YAML, and based on it, it ensures that the environment remains consistent in all times.  
 -->
<!---
#### RHPAM Operator

 Since Red Hat PAM 7.5, Red Hat PAM brings OpenShift Operators to help on easily deploying new instances. Let's use the provided operator to create a new environment.

 [#TODO] will require pre-provisioning the operator in each user namespace;

//// -->

Now that we know more details about the environment where PAM is running, let's access it!
