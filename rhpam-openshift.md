# 6. 参考情報: OpenShift への RHPAM のインストールについて

OpenShift上でのRHPAMのインストールは、Operatorを使用するか、あらかじめ定義されたテンプレートを使用して行うことができます。
これにより、特定の目標を目指した環境を簡単にデプロイすることができます。

> **NOTE**
> 
> _Operatorとは、Kubernetesアプリケーションをパッケージ化し、デプロイし、管理する方法のことです。<br>
> Kubernetesアプリケーションとは、Kubernetes上にデプロイされ、Kubernetes APIとkubectlツールを使用して管理されるアプリケーションのことです。_

そのため、プロセスなどの資産を開発するか、統合するか、テストするか、実行するかによって、選択したニーズを反映した環境を構築するインストール構成を選択することができます。
アーキテクチャが定義されると、ユーザーはテンプレートを介してインストールを行うか、OperatorHubで利用可能なRHPAM Operatorを使用してインストールを行うかを選択することができます。

![RHPAM Operator]({% image_path rhpam-operator.png %}){:width="600px"}

Operator経由でPAMをデプロイする場合、ユーザはKieAppをデプロイします。
yaml経由で設定をカスタマイズしたり、Operatorが提供するOperation Installer UIを利用したりすることが可能です。

![RHPAM Operator Installer UI]({% image_path rhpam-operator-installer-ui.png %}){:width="600px"}

前述のように、PAMをデプロイするためのいくつかの定義されたテンプレートが利用可能です。ここでは、いくつかのオプションの概要を説明します。

- **rhpam-trial**: すぐに設定でき、資産の開発・運用の評価やデモに使えるトライアル環境。Business CentralとProcess Serverが含まれています。この環境は永続的なストレージを使用せず、環境内で行った作業は保存されません。
- **rhpam-authoring**: 業務ユーザーや開発者が、ビジネスオートメーションのプロジェクトやアセット、アプリケーションを開発したいと考えている場合に最適な環境です。Business Centralと実行サーバー（Kie Server）を含むオーサリング環境を提供します。
- **rhpam-authoring-ha**: 前の環境と同じですが、高可用性機能を備えています。これは、Business Centralと実行サーバーのインスタンスが複数（デフォルトでは2つ）デプロイされていることを意味します。
- **rhpam-production**: 既存のサービスをステージングや本番用に動かすための環境。このテンプレートでは、監視・管理環境、Smart Router、2つの実行サーバグループが用意されています。

例えば、ルールやプロセスをオーサリングする環境を作りたい場合は、そのために必要なコンポーネントをすべて含んだ `rhpam79-authoring` を使うことができます。下の画像を参照してください。

![RHPAM Authoring]({% image_path rhpam-authoring.png %}){:width="600px"}

このワークショップでは、オーサリングテンプレートは、あなたのアセットをテストするためのプロセスサーバーを備えた完全なオーサリング環境を提供します。

永続的なストレージを持たないシンプルなテスト環境を提供したい場合は、代わりにエフェメラルテンプレートを使ってインストールすることができます。

![RHPAM Ephemeral]({% image_path rhpam-ephemeral-template.png %}){:width="600px"}