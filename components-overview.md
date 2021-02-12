# 3. RHPAM の機能とアーキテクチャ

<!-- Red Hat Process Automation Manager (a.k.a. RHPAM ) enables you to automate different pieces of your business requirements like automating the decision making, the flow of the decision making, the interaction between the people and systems. -->

Red Hat Process Automation Manager (別名: RHPAM) は、意思決定の自動化、意思決定のフロー、人とシステムの相互作用など、ビジネス要件のさまざまな部分を自動化することを可能にします。

<!-- The following diagram depicts the main capabilities of Red Hat Process Automation Platform (RHPAM). -->
次の図は、Red Hat Process Automation Manager (RHPAM) の主な機能を示しています。

<!--![High Level Capability Component]({% image_path high-level-capability-components.png %}){:width="600px"} -->
<div align="center">
    <img src=./images/high-level-capability-components.png width="600px">
</div>

## 機能の概要

### ビジネスルール管理
<!-- RHPAM includes all the benefits of Red Hat Decision Manager, therefore, it contains a high-performant, lightweight and scalable rules execution engine based on the open-source [Drools](http://www.drools.org) community project. This being said, PAM allows: -->
RHPAM には、Red Hat Decision Manager が含まれているため、オープンソースの [Drools](http://www.drools.org) コミュニティプロジェクトをベースにした、高性能で軽量かつスケーラブルなルール実行エンジンが含まれています。

<!--
- Automating rules using decision tables, guided rules, drools, and the DMN (Decision Model and Notation) standard;
- Using PMML models as business assets, allowing the usage of AI/ML models within decision making and business flows;
- Usage of test scenario to validate the rules;
- Complex Event Processing, decision made on top of time-based events (i.e. fraud detection);
-->

- 意思決定表、ガイド付きルール、drools、DMN(Decision Model and Notation)標準を使用したルールの自動化
- PMMLモデルをビジネス資産として利用し、意思決定やビジネスフローの中でAI/MLモデルを利用できるようにする
- ルールを検証するためのテストシナリオの使用法
- Complex Event Processing（CEP）という、時間ベースのイベントの上で行われる意思決定（不正検知など）

### Business Optimizer
<!-- An AI Constraint Satisfaction Solver that optimizes business resource planning use cases such as vehicle routing, employee rostering and conference scheduling. The platform optimizes the goal of a problem based on limited resources under specific constraints. The engine is based on the upstream [OptaPlanner](http://www.optaplanner.org) project. -->

ビジネスリソースのプランニング問題を最適化するAI制約ソルバー。限られたリソース（人、物、金、時間等）内で、様々な制約を満たしつつ、
最良の結果（利益の最大化、コストの削減、作業の平準化等）を得たいというようなケースにおいて、どの組合せが最適かを現実的な時間で探索します。
このエンジンはupstreamの[OptaPlanner](http://www.optaplanner.org)プロジェクトをベースにしています。

### プロセス管理
<!-- RHPAM includes a high-performant, lightweight and scalable, BPMN2 compliant, process execution engine (Kie Server), which is based on the open-source [jBPM](http://www.jbpm.org) project. Provides functionality like business process management and human task management, to enable the automation and optimization of processes. -->

RHPAMには、オープンソースの[jBPM](http://www.jbpm.org)プロジェクトをベースにした、高性能・軽量・拡張性に優れたBPMN2準拠のプロセス実行エンジン(Kie Server)が搭載されています。
ビジネスプロセス管理やヒューマンタスク管理などの機能を提供し、プロセスの自動化・最適化を可能にします。

### ケース管理

<!-- The [jBPM](http://www.jbpm.org) engine (Kie Server) is CMMN compliant, and with Business Central, you can author, execute, manage and monitor flexible processes, also called, cases. With this, you can align capabilities like milestones and case files in your cases and integrate your cases with other tradicional BPMN based processes. -->

[jBPM](http://www.jbpm.org)エンジン(Kie Server)はCMMNに準拠しており、Business Centralを使用することで、ケースとも呼ばれる柔軟なプロセスを設計、実行、管理、監視することができます。
これにより、マイルストーンやケースファイルのような機能をケース内で調整し、他の伝統的なBPMNベースのプロセスとケースを統合することができます。

### ダッシュボードレポート

<!-- Red Hat PAM includes a powerfull Business Activity Monitoring (BAM) capability that allows users to build reports based on different data sources (CSV, SQL, Kie Server…), and show them using customized pages and components.  -->

Red Hat PAM には強力なBusiness Activity Monitoring (BAM)機能が搭載されており、ユーザーは異なるデータソース（CSV、SQL、Kie Server...）に基づいてレポートを作成し、
カスタマイズされたページやコンポーネントを使用してレポートを表示することができます。

<!-- ![High Level Capability Component]({% image_path high-level-capability-components-dashboard.png %}){:width="600px"} -->
<div align="center">
    <img src=./images/high-level-capability-components-dashboard.png width="600px">
</div>

---

## アーキテクチャの構成

<!--
Let's get familiar with the platform components so that we can understand the different ways to configure the product and be able to support different use cases.

In this scenario, we are considering OpenShift as the installation platform. The OpenShift self-service console will allow you to provision, recreate, destroy your working environment and be autonomous from other users.

Red Hat PAM main components and capabilities are displayed in this diagram:
 -->

製品を構成するためのさまざまな方法を理解し、さまざまなユースケースに対応できるように、プラットフォームのコンポーネントに親しんでみましょう。

このシナリオでは、インストールプラットフォームとして OpenShift を考えています。OpenShiftのコンソールを利用することで、作業環境のプロビジョニング、再作成、破棄が可能となり、他のユーザーとの自律的な連携が可能となります。

Red Hat PAMの主なコンポーネントと機能は、この図のように表示されています。

<!-- ![RHPAM 7 Components]({% image_path rhpam-components.png %}){:width="600px"} -->
<div align="center">
    <img src=./images/rhpam-components.png width="600px">
</div>

### Business Central Monitoring
<!-- A modern web-based workbench that provides user the tooling to manage and monitor deployed projects, running engines, running instances of process-driven applications and more. -->

デプロイされたプロジェクト、実行中のエンジン、プロセス駆動型アプリケーションのインスタンスの実行などを管理・監視するためのツールを提供する最新のウェブベースのワークベンチです。

### Business Central Authoring
<!-- A web-based workbench used to manage business projects as well as providing powerful tools to build and author the business assets available in RHPAM, like different types of rules, processes, cases, test scenarios, data objects, etc. -->

ビジネスプロジェクトを管理するために使用されるWebベースのワークベンチで、異なるタイプのルール、プロセス、ケース、テストシナリオ、データオブジェクトなど、RHPAMで利用可能なビジネス資産を構築し、オーサリングするための強力なツールを提供します。

### Asset Repository
<!-- Based on a collaborative line-of-thought, all of the assets developed using Business Central are stored in a git-based asset repository. This allows you to version, index, search and share your work with the rest of your team. -->

コラボレーティブな考え方に基づき、Business Centralを使って開発されたすべてのアセットは、gitベースのアセットリポジトリに保存されます。これにより、バージョン管理、インデックス作成、検索、作業内容の共有が可能になります。

### Artifact Repository
<!-- Once you have completed the authoring phase and you are satisfied with the work, you can package your assets into a _Deployment Unit_ known as a _kjar_. This unit is a standard Java Archive (JAR) and will be stored in the artifact repository (i.e. Nexus, etc... ).-->

オーサリングフェーズが完了したら、アセットを_kjar_と呼ばれる_展開ユニットにパッケージ化することができます。このユニットは標準のJavaアーカイブ(JAR)で、アーティファクトリポジトリ(Nexusなど)に保存されます。

### Controller
<!-- The deployment units are deployed to the Execution Engine by the Controller. The Controller abstracts the complexity of the runtime environment through the use of so called _Templates_, or _Server Configurations_. This greatly reduces the complexity of managing clustered and/or heterogeneous topologies, for example topologies in which Execution Engines are deployed and managed per line of business. -->

デプロイメントユニットはコントローラによって実行エンジンにデプロイされます。
コントローラは、_Templates_または_Server Configurations_を使用して、ランタイム環境の複雑さを抽象化します。
これにより、クラスタ化されたネットワークトポロジーの管理の複雑さが大幅に軽減されます。
例えば、実行エンジンがビジネスラインごとにデプロイされて管理されるトポロジーなどです。

### KIE Server (Intelligent Process Server)
<!-- The lightweight, cloud-native, execution engine that runs the rules and processes contained in the deployment unit. KIE-Servers can be scaled horizontally and/or vertically in an automated fashion using the cloud native capabilities of OpenShift Container Platform. Since the state of the processes is stored in a persistent store (by default a relational database) you can consider the KIE-Servers to be stateless when it comes to process execution. -->

デプロイメントユニットに含まれるルールとプロセスを実行する、軽量でクラウドネイティブな実行エンジン。
KIE-Serversは、OpenShift Container Platformのクラウドネイティブ機能を使用して、水平方向および/または垂直方向に自動スケールすることができます。
プロセスの状態は永続的なストア（デフォルトではリレーショナルデータベース）に保存されるため、KIE-Serversはプロセスの実行に関してはステートレスであると考えることができます。

### Smart Router
<!-- Provides a runtime abstraction layer over the KIE-Server topology, allowing clients of this topology to interact with a single endpoint. Smart Router contains the information of which processes and rules (deployment units) are deployed on which runtime engine/KIE-Server, and provides routing functionality to the correct server instance based on the client request. In a classical enterprise environment where you have multiple instances running and different nodes, starting and shutting down in an elastic way, the complexity of tracking these changes in order to correctly load-balance the requests is the responsibility of the Smart Router. -->

KIE-Serverトポロジ上にランタイム抽象化レイヤを提供し、このトポロジのクライアントが単一のエンドポイントと対話をできるようにします。
Smart Routerには、どのプロセスとルール（デプロイメント・ユニット）がどのランタイム・エンジン/KIE-Serverにデプロイされているかの情報が含まれており、クライアントの要求に基づいて正しいサーバー・インスタンスへのルーティング機能を提供します。

## PAM のアーキテクチャ
<!-- RHPAM can be architected in some different ways, this is a represention of one of the possible architectures: -->
RHPAMはいくつかの異なる方法で設計することができますが、
中でも代表的なアーキテクチャの一つを以下に示しています。

<!-- ![RHPAM 7 Architecture]({% image_path rhpam-7-architecture.png %}){:width="600px"} -->
<div align="center">
    <img src=./images/rhpam-7-architecture.png width="600px">
</div>

----

**本ワークショップにおける環境について**

<!-- Because a critical capability of a digitally enabled product is to be available as a service, we are going to leverage  OpenShift Container Platform as a self-service console where you can choose the different tools needed depending on your skills, LOB and solution. Let's see how PAM behaves within OpenShift. -->

デジタル化された製品の重要な機能はサービスとして利用できることなので、スキルやLOB、ソリューションに応じて必要なツールを選択できるセルフサービスコンソールとしてOpenShift Container Platformを活用していきます。
OpenShift内でPAMがどのように振る舞うのか見てみましょう。
