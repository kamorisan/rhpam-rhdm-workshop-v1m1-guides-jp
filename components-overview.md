# 3. RHPAM の機能とアーキテクチャ

Red Hat Process Automation Manager (別名: RHPAM) は、ビジネス上の意思決定とプロセスの自動化・可視化することを可能とし、ビジネスの変化に迅速かつ柔軟に対応可能なシステムに変革します。

次の図は、Red Hat Process Automation Manager (RHPAM) の主な機能を示しています。

![High Level Capability Component]({% image_path high-level-capability-components.png %}){:width="800px"}

## 機能の概要

### ビジネスルール管理

RHPAM には、Red Hat Decision Manager が含まれているため、オープンソースの [Drools](http://www.drools.org) コミュニティプロジェクトをベースにした、高性能で軽量かつスケーラブルなルール実行エンジンが含まれています。

- デシジョンテーブル、ガイド付きルール、drools、DMN(Decision Model and Notation)標準を使用したルールの自動化
- PMMLモデルをビジネス資産として利用し、意思決定やビジネスフローの中でAI/MLモデルを利用できるようにする
- ルールを検証するためのテストシナリオの使用法
- Complex Event Processing（CEP）を用いた、時間ベースのイベントの上で行われる意思決定（不正検知など）

### Business Optimizer

ビジネスリソースのプランニング問題を最適化するAI制約ソルバー。限られたリソース（人、物、金、時間等）内で、様々な制約を満たしつつ、
最良の結果（利益の最大化、コストの削減、作業の平準化等）を得たいというようなケースにおいて、どの組合せが最適かを現実的な時間で探索します。
このエンジンはupstreamの[OptaPlanner](http://www.optaplanner.org)プロジェクトをベースにしています。

### プロセス管理

RHPAMには、オープンソースの[jBPM](http://www.jbpm.org)プロジェクトをベースにした、高性能・軽量・拡張性に優れたBPMN2.0準拠のプロセス実行エンジン(Kie Server)が搭載されています。
ビジネスプロセス管理やヒューマンタスク管理などの機能を提供し、プロセスの自動化・最適化を可能にします。

### ケース管理

[jBPM](http://www.jbpm.org)エンジン(Kie Server)はCMMNに準拠しており、Business Centralを使用することで、ケースとも呼ばれる柔軟なプロセスを設計、実行、管理、監視することができます。
これにより、マイルストーンやケースファイルのような機能をケース内で調整し、他の伝統的なBPMNベースのプロセスとケースを統合することができます。

### ダッシュボード

Red Hat PAM には強力なBusiness Activity Monitoring (BAM)機能が搭載されており、ユーザーは異なるデータソース（CSV、SQL、Kie Server...）に基づいてレポートを作成し、カスタマイズされたページやコンポーネントを使用してレポートを表示することができます。

![High Level Capability Component]({% image_path high-level-capability-components-dashboard.png %}){:width="600px"}

---

## アーキテクチャの構成

製品を構成するためのさまざまな方法を理解し、さまざまなユースケースに対応できるように、プラットフォームのコンポーネントに親しんでみましょう。

このシナリオでは、インストールプラットフォームとして OpenShift を考えています。OpenShiftのコンソールを利用することで、作業環境のプロビジョニング、再作成、破棄が可能となり、他のユーザーとの自律的な連携が可能となります。

Red Hat PAMの主なコンポーネントと機能は、この図のように表示されています。

![RHPAM 7 Components]({% image_path rhpam-components.png %}){:width="800px"}

### Business Central 

プロセス・ルールのモデリング、ビルドおよびデプロイ、KIE Serverの管理、プロセス・タスクの管理、モニタリング等の機能を持つ、Webベースのオーサリングツール。GitおよびMavenにてアセットの管理を行います。（コンテナイメージは、オーサリング機能とモニタリング機能が別々に用意されています）

### KIE Server (Intelligent Process Server)

プロセス・ルールの実行サーバー。
スタンドアローン（Unmanaged）で個別設定のKIE Serverをたてるケースと、複数のKIE ServerをContollerを使用して集中管理するケース（Managed）と選択が可能です。
プロセス状態の永続化のためにデータベースが必要です。

### Asset Repository

コラボレーティブな考え方に基づき、Business Centralを使って開発されたすべてのアセットは、gitベースのアセットリポジトリに保存されます。
これにより、バージョン管理、インデックス作成、検索、作業内容の共有が可能になります。

### Artifact Repository

オーサリングフェーズが完了したら、アセットを_kjar_と呼ばれる_展開ユニットにパッケージ化することができます。
このユニットは標準のJavaアーカイブ(JAR)で、アーティファクトリポジトリ(Nexusなど)に保存されます。

### Controller

KIE  Serverを管理することが可能。
Business Centralには Controller が含まれていますが、Business Central を使わないケースや、Business Central を本番環境にはデプロイしないが、KIE Serverを管理したい場合に利用します。

### Smart Router

複数の KIE Server、クライアントアプリケーション、他のコンポーネント間の統合レイヤーとして使用可能な軽量の Java コンポーネントです。
デプロイメントや実行環境に合わせて、Smart Router は複数の独立した KIE Server インスタンスを単一サーバーのように集約できます。

## PAM のアーキテクチャ

RHPAMはいくつかの異なる方法で設計することができますが、
中でも代表的なアーキテクチャの一つを以下に示しています。

![RHPAM 7 Architecture]({% image_path rhpam-7-architecture.png %}){:width="800px"}

----

**本ワークショップにおける環境について**

デジタル化された製品の重要な機能はサービスとして利用できることなので、スキルやLOB、ソリューションに応じて必要なツールを選択できるセルフサービスコンソールとしてOpenShift Container Platformを活用していきます。
OpenShift内でPAMがどのように振る舞うのか見てみましょう。
