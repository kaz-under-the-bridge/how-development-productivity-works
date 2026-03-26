# DORAメトリクス（Four Keys）包括的リサーチ

## 目次

1. [DORAの歴史と背景](#1-doraの歴史と背景)
2. [書籍「Accelerate」の主要な知見](#2-書籍accelerateの主要な知見)
3. [State of DevOps Report 各年の主要な発見](#3-state-of-devops-report-各年の主要な発見)
4. [DORAの理論的フレームワーク](#4-doraの理論的フレームワーク)
5. [DORA Core Model](#5-dora-core-model)
6. [DORAへの批判・限界](#6-doraへの批判限界)
7. [SPACEフレームワーク](#7-spaceフレームワーク)
8. [実践的な導入パターン](#8-実践的な導入パターン)

---

## 1. DORAの歴史と背景

### 創設者

DORA（DevOps Research and Assessment）は以下の3名によって設立された：

- **Nicole Forsgren, PhD** — 組織行動学・情報システムの研究者。統計的手法とサーベイ設計の専門家。DORAのCEO兼チーフサイエンティストを務めた。現在はMicrosoft Research所属
- **Jez Humble** — 「Continuous Delivery」（2010年）の共著者。継続的デリバリーの実践と理論の第一人者
- **Gene Kim** — 「The Phoenix Project」「The DevOps Handbook」の著者。IT Revolution Press創設者

### 研究の始まり（2014年〜）

| 年 | 出来事 |
|---|---|
| 2013年 | Puppet Labsが主催していたState of DevOps Reportの調査方法論を改善するためNicole Forsgrenが参加 |
| 2014年 | DORA研究プログラムの実質的な開始。最初のState of DevOps Reportで4つのパフォーマンス指標を特定 |
| 2018年 | 書籍「Accelerate」出版。4年間の研究成果を体系化 |
| 2018年 | DORAがGoogle Cloudに買収・統合される |
| 2019年〜 | Google Cloud傘下でState of DevOps Reportを継続発行。研究規模を拡大 |
| 2024年 | 10回目のレポート発行。39,000人以上の専門家から調査データを収集 |
| 2025年 | AI時代のソフトウェアデリバリーに関する知見を発表 |

### State of DevOps Reportの位置づけ

学術的に厳密な行動科学の手法を用い、作業慣行がソフトウェアデリバリーパフォーマンスと組織的成果にどのように結びつくかを調査する、長期継続型の研究プログラムである。

出典: https://dora.dev/research/

---

## 2. 書籍「Accelerate」の主要な知見

### 書籍情報

- **タイトル**: Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations
- **著者**: Nicole Forsgren PhD, Jez Humble, Gene Kim
- **出版**: 2018年、IT Revolution Press
- **対象期間**: 2014〜2017年の4年間の研究データ

### 研究方法論

- **クラスタ分析**: チームをパフォーマンスレベル（High / Medium / Low）にクラスタリング。2018年から「Elite」カテゴリを追加
- **構造方程式モデリング（SEM）**: ケイパビリティ→ソフトウェアデリバリーパフォーマンス→組織パフォーマンスの因果関係を統計的に検証
- **サーベイ方式**: Likertスケールを使用した自己申告型調査。回答者バイアスを軽減するための設計手法を採用
- **交差検証**: 年ごとに独立したサンプルで結果を再現し、知見の頑健性を確認

### 核心的発見

**「スピードと安定性はトレードオフではない」**

従来の通念では「速くデプロイすれば安定性が犠牲になる」と考えられていたが、DORAの研究はこれを明確に否定した。高パフォーマンスチームは、スループット（デプロイ頻度・リードタイム）と安定性（変更失敗率・復旧時間）の両方で優れている。

### ソフトウェアデリバリーパフォーマンスと組織パフォーマンスの関係

Accelerateで示された因果モデル：

```
ケイパビリティ（24項目）
  → ソフトウェアデリバリーパフォーマンス（Four Keys）
    → 組織パフォーマンス（収益性、市場シェア、生産性）
      → 非商業的パフォーマンス（品質、顧客満足度、ミッション達成）
```

### 24のケイパビリティ

Accelerateでは以下の24のケイパビリティがソフトウェアデリバリーパフォーマンスを駆動すると特定された：

**継続的デリバリー（Continuous Delivery）**
1. バージョン管理（Version Control）
2. デプロイ自動化（Deployment Automation）
3. 継続的インテグレーション（Continuous Integration）
4. トランクベース開発（Trunk-based Development）
5. テスト自動化（Test Automation）
6. テストデータ管理（Test Data Management）
7. セキュリティのシフトレフト（Shift Left on Security）
8. 継続的デリバリー（Continuous Delivery）

**アーキテクチャ**
9. 疎結合アーキテクチャ（Loosely Coupled Architecture）
10. チームへのツール選択権限付与（Empowering Teams to Choose Tools）

**製品・プロセス**
11. 顧客フィードバック（Customer Feedback）
12. バリューストリームにおける作業の可視性（Visibility of Work in the Value Stream）
13. 小さなバッチでの作業（Working in Small Batches）
14. チーム実験（Team Experimentation）

**リーン管理とモニタリング**
15. 変更承認プロセスの合理化（Streamlining Change Approval）
16. ビジネス判断のためのモニタリング（Monitoring Systems to Inform Business Decisions）
17. プロアクティブな障害通知（Proactive Failure Notification）
18. WIP制限（Work in Process Limits）
19. 作業の可視化管理（Visual Management）

**文化**
20. Westrum型の生成的組織文化（Generative Organizational Culture）
21. 学習する文化（Learning Culture）
22. チーム間の協力（Collaboration Among Teams）
23. 仕事の満足度（Job Satisfaction）
24. 変革型リーダーシップ（Transformational Leadership）

---

## 3. State of DevOps Report 各年の主要な発見

### 2014年
**「DevOpsは技術的なプラクティスだけでなく文化的なシフトであり、ITと組織のパフォーマンスに大きな改善をもたらす」**

- 最初のレポート。4つのパフォーマンス指標を特定
- ただし統計分析の結果、変更失敗率は他の3指標と有意に相関しないことが判明

### 2015年
**「高パフォーマンスのIT組織は、4つのソフトウェアデリバリー指標すべてにおいて一貫して競合を上回る」**

- 「スループット指標」（デプロイ頻度・リードタイム）と「安定性指標」（MTTR・変更失敗率）の二元モデルが安定
- 高パフォーマーがスピードと安定性の両方で優れるという発見が確立

### 2016年
**「品質をすべての段階に統合し、実験的な製品開発を採用することが高パフォーマンスを駆動する」**

### 2017年
**「変革型リーダーシップが高パフォーマンス文化の醸成に重要な役割を果たす」**

### 2018年
**Eliteクラスタの定義、運用パフォーマンス指標の導入**

- パフォーマンスクラスタにElite（最上位）を追加
- 「ITパフォーマンス」から「ソフトウェアデリバリーおよび運用（SDO）パフォーマンス」に用語を変更
- 「可用性（Availability）」を運用健全性の指標として導入

### 2019年
**「コミュニティ・オブ・プラクティスはセンター・オブ・エクセレンスを上回り、重量級の変更承認プロセスはパフォーマンスに悪影響を与える」**

- 集中型の専門家組織（CoE）よりも、草の根型のコミュニティ・オブ・プラクティス（CoP）が効果的
- 外部承認ベースの変更管理プロセスがデリバリーパフォーマンスを低下させることを実証

出典: https://dora.dev/research/2019/

### 2020年
**「DevOpsトランスフォーメーションは組織全体に有意なROIをもたらす」**

出典: https://dora.dev/research/2020/

### 2021年
**「高品質な内部ドキュメンテーションが技術的ケイパビリティの成功的な実装の基盤となる」**

- 「可用性」を「信頼性（Reliability）」に発展。運用パフォーマンスにはアップタイムだけでなくレイテンシ、パフォーマンス、スケーラビリティも含まれることを反映

出典: https://dora.dev/research/2021/

### 2022年
**「組織のアプリケーション開発セキュリティプラクティスの最大の予測因子は、技術的なものではなく文化的なものである」**

主要な発見：
- **信頼性の高い低blame文化**がセキュリティプラクティスの採用を促進
- セキュリティプラクティスが堅固なチームは、そうでないチームと比較して**バーンアウトが1.4倍少ない**
- 強固なセキュリティプラクティスを持つ組織は**1.6倍高い組織パフォーマンス**を示す
- ソフトウェアサプライチェーンセキュリティ（SLSAフレームワーク）は、CIが確立されている場合にのみデリバリーパフォーマンスに寄与
- 技術的ケイパビリティは相互に強化し合う（CD + 疎結合チーム + バージョン管理 + CIの組み合わせが個別効果の合計を上回る）

出典: https://dora.dev/research/2022/

### 2023年
**「ユーザー中心主義は40%高いパフォーマンスを予測し、高品質なドキュメンテーションが技術的ケイパビリティのインパクトを増幅する」**

主要な発見：
- **ユーザーニーズを優先するチーム**は**40%高い組織パフォーマンス**を達成
- **生成的文化**は**30%高い組織パフォーマンス**と相関
- 柔軟なインフラストラクチャ（クラウド対応）は**30%高い組織パフォーマンス**
- 高品質なドキュメンテーションが技術的ケイパビリティの効果を劇的に増幅
- 「リフト＆シフト」型のクラウド移行は逆効果になりうる
- 公平な作業分配がバーンアウトを軽減。過小評価されているグループがより多くの反復的タスクを担う傾向
- メトリクス追求よりも継続的改善を重視すべき
- 用語変更：「MTTR（平均復旧時間）」→「Failed Deployment Recovery Time（失敗デプロイ復旧時間）」

出典: https://dora.dev/research/2023/

### 2024年（10周年記念レポート）
**「プラットフォームエンジニアリングとユーザー中心主義が成功を駆動し、AIがソフトウェアデリバリーの風景を再形成し始めている」**

主要な発見：
- 39,000人以上の専門家からの調査データ（過去最大規模）
- **AIのソフトウェア開発への影響**が本格的に調査対象に
- **プラットフォームエンジニアリング**の可能性と課題
- 5指標モデルへの拡張：**Deployment Rework Rate（デプロイ再作業率）** を追加
- 9言語で公開（日本語版あり）

出典: https://dora.dev/research/2024/

### 2025年
**「AIはアンプリファイアーとして機能するが、最大のリターンは基盤となる社会技術システムに焦点を当てることから得られる」**

- AI固有のケイパビリティモデルを発表
- AIは既存のプラクティスを増幅するが、それ自体が銀の弾丸ではないことを実証

出典: https://dora.dev/research/2025/

---

## 4. DORAの理論的フレームワーク

### Westrum組織文化モデル

社会学者Ron Westrumによる組織文化の3類型モデル。DORAの研究でソフトウェアデリバリーパフォーマンスの強力な予測因子であることが実証された。

| 病的（Pathological） | 官僚的（Bureaucratic） | 生成的（Generative） |
|---|---|---|
| 権力志向 | ルール志向 | パフォーマンス志向 |
| 低い協力 | 中程度の協力 | 高い協力 |
| メッセンジャーを撃つ | メッセンジャーを無視する | メッセンジャーを訓練する |
| 責任を回避する | 狭い責任範囲 | リスクを共有する |
| 橋渡しを阻害する | 橋渡しを容認する | 橋渡しを奨励する |
| 失敗はスケープゴートに | 失敗は裁きに | 失敗は探求に |
| 新規性を潰す | 新規性は問題を生む | 新規性を実装する |

**DORAの発見**: 生成的文化を持つ組織は、30%高い組織パフォーマンスを示す（2023年レポート）。また、セキュリティプラクティスの採用を最も強く予測する因子は文化である（2022年レポート）。

### 継続的デリバリー（Continuous Delivery）

Jez Humbleの著書「Continuous Delivery」（2010年）に基づくプラクティス群。DORAのケイパビリティモデルの中核を構成する。

核心原則：
- **すべての変更をバージョン管理する**（コード、設定、インフラ）
- **ビルド・テスト・デプロイを自動化する**
- **常にリリース可能な状態を維持する**
- **小さなバッチで頻繁にリリースする**
- **フィードバックループを短縮する**

### リーン管理（Lean Management）

トヨタ生産方式に起源を持つ管理手法。DORAはリーン管理の以下の側面がソフトウェアデリバリーに影響することを実証：

- **WIP制限**: 仕掛品の数を制限し、フロー効率を向上
- **作業の可視化**: カンバンボード等による進捗の可視化
- **小バッチ**: 大きな変更を小さな単位に分割
- **バリューストリームの可視化**: 構想からデリバリーまでのフロー全体を可視化

### ケイパビリティモデル全体像

DORAのモデルは以下の因果連鎖を仮定する：

```
[ケイパビリティ]
  ├── 技術的ケイパビリティ（CD, CI, テスト自動化等）
  ├── プロセスケイパビリティ（小バッチ、WIP制限等）
  ├── 文化的ケイパビリティ（Westrum文化、学習文化等）
  └── リーダーシップケイパビリティ（変革型リーダーシップ）
        ↓
[ソフトウェアデリバリーパフォーマンス]
  ├── スループット（デプロイ頻度、リードタイム）
  └── 安定性（変更失敗率、復旧時間）
        ↓
[組織パフォーマンス]
  ├── 収益性・市場シェア
  ├── 生産性
  └── 顧客満足度
        ↓
[ウェルビーイング]
  ├── バーンアウトの軽減
  └── 仕事の満足度
```

---

## 5. DORA Core Model

### 概要

DORA Core Modelは、DORAの研究の中で**最も確立された知見**を集めたコレクションである。研究の最先端よりも意図的に保守的に進化し、概念が繰り返し実証されてから初めてCore Modelに組み込まれる。

出典: https://dora.dev/core/

### 現行の5指標（2024年以降）

#### スループット指標（Software Delivery Throughput）

| 指標 | 説明 |
|------|------|
| **Change Lead Time（変更リードタイム）** | バージョン管理にコミットしてから本番環境にデプロイされるまでの時間 |
| **Deployment Frequency（デプロイ頻度）** | 一定期間内のデプロイ回数、またはデプロイ間の時間 |
| **Failed Deployment Recovery Time（失敗デプロイ復旧時間）** | デプロイ失敗から復旧までの時間（旧MTTR） |

#### 不安定性指標（Software Delivery Instability）

| 指標 | 説明 |
|------|------|
| **Change Fail Rate（変更失敗率）** | デプロイ後に即座の介入を必要とするデプロイの割合 |
| **Deployment Rework Rate（デプロイ再作業率）** | 本番環境のインシデントに起因する計画外デプロイの割合（2024年追加） |

### 指標の進化の歴史

出典: https://dora.dev/insights/dora-metrics-history

| フェーズ | 期間 | 変更内容 |
|---|---|---|
| Phase 1: 起源 | 2014-2015 | 4指標を特定。統計分析で変更失敗率が他の3指標と相関しないことが判明 |
| Phase 2: 標準化 | 2016-2018 | 4指標がベンチマークとして定着。可用性（Availability）を追加 |
| Phase 3: 精緻化 | 2021-2023 | 可用性→信頼性に変更。MTTR→Failed Deployment Recovery Timeに名称変更 |
| Phase 4: 5指標化 | 2024 | Deployment Rework Rateを追加。安定性をInstabilityの2指標に分割 |

### パフォーマンスレベル（2023年版基準）

| レベル | デプロイ頻度 | リードタイム | 復旧時間 | 変更失敗率 |
|--------|-------------|-------------|---------|-----------|
| Elite | オンデマンド（1日複数回） | 1時間未満 | 1時間未満 | 0-15% |
| High | 週1回〜月1回 | 1〜24時間 | 1〜24時間 | 16-30% |
| Medium | 月1回〜四半期1回 | 1〜6ヶ月 | 1〜24時間 | 31-45% |
| Low | 四半期1回未満 | 6ヶ月超 | 24時間超 | 46-100% |

### Technical Capabilities（技術的ケイパビリティ）

- Code Maintainability（コードの保守性）
- Continuous Delivery（継続的デリバリー）
- Continuous Integration（継続的インテグレーション）
- Database Change Management（データベース変更管理）
- Deployment Automation（デプロイ自動化）
- Documentation Quality（ドキュメンテーション品質）
- Flexible Infrastructure（柔軟なインフラストラクチャ）
- Monitoring and Observability（監視と可観測性）
- Pervasive Security（浸透型セキュリティ）
- Test Automation（テスト自動化）
- Test Data Management（テストデータ管理）
- Trunk-based Development（トランクベース開発）
- Version Control（バージョン管理）
- Working in Small Batches（小バッチ作業）

### Process & Organizational Capabilities（プロセスおよび組織ケイパビリティ）

- Empowering Teams to Choose Tools（ツール選択の権限付与）
- Job Satisfaction（仕事の満足度）
- Loosely Coupled Teams（疎結合チーム）
- Streamlining Change Approval（変更承認の合理化）
- Visibility of Work in the Value Stream（バリューストリームの可視化）
- Visual Management（可視化管理）
- Well-being（ウェルビーイング）
- Work in Process Limits（WIP制限）

### Cultural & Leadership Capabilities（文化およびリーダーシップケイパビリティ）

- Generative Organizational Culture（生成的組織文化）
- Learning Culture（学習する文化）
- Team Experimentation（チーム実験）
- Transformational Leadership（変革型リーダーシップ）

### Feedback & Monitoring Capabilities（フィードバックおよびモニタリングケイパビリティ）

- Customer Feedback（顧客フィードバック）
- Monitoring Systems to Inform Business Decisions（ビジネス判断のためのモニタリングシステム）
- Proactive Failure Notification（プロアクティブな障害通知）

### AI-Specific Capabilities（AI固有ケイパビリティ）— 2025年追加

- AI-accessible Internal Data（AI用内部データアクセス）
- Clear and Communicated AI Stance（明確なAI方針の策定と共有）
- Healthy Data Ecosystems（健全なデータエコシステム）
- Platform Engineering（プラットフォームエンジニアリング）
- User-centric Focus（ユーザー中心主義）

出典: https://dora.dev/capabilities/

---

## 6. DORAへの批判・限界

### Goodhart's Law（グッドハートの法則）

**「指標が目標になると、良い指標でなくなる」**

DORAメトリクスを直接的な目標として設定すると、以下のような歪みが生じる：
- デプロイ頻度を上げるために無意味な小さなデプロイを増やす
- 変更失敗率を下げるために「失敗」の定義を変える
- リードタイムを短縮するためにレビューやテストを省略する

DORAチーム自身もこの問題を認識しており、2023年レポートで「メトリクス追求よりも継続的改善を重視すべき」と明記している。

### 自己申告バイアス

DORAの調査は自己申告型サーベイに基づいている。これには以下の限界がある：
- 回答者が自組織のパフォーマンスを過大または過小に評価する可能性
- 「デプロイ」「障害」「復旧」の定義が回答者によって異なる可能性
- 生存者バイアス：調査に回答するのは比較的パフォーマンスの高い組織に偏る可能性

### 組織サイズによる適用の違い

- **大規模組織**: 複数チーム間の依存関係が指標に影響。個別チームのメトリクスと組織全体のメトリクスの乖離が生じる
- **スタートアップ**: デプロイ頻度は高いが、それが本当にケイパビリティの反映なのか、単にコードベースが小さいだけなのか判別困難
- **規制産業**: 金融・医療・航空等では変更承認プロセスが法的に必要。DORAの「変更承認の合理化」が適用しにくい

### 指標のゲーミング問題

- **デプロイ頻度**: フィーチャーフラグを使い、実質的な変更なしにデプロイ回数を増やすことが可能
- **変更失敗率**: インシデント分類基準を変えることで数値操作が可能
- **リードタイム**: コミット戦略の変更（大きなPRを直前に複数コミットに分割）で見かけの数値を改善可能

### コンテキスト依存性

DORAの知見は広範なサンプルに基づくが、個別の組織・チームに適用する際にはコンテキストが重要。2022年レポートで、サプライチェーンセキュリティがデリバリーパフォーマンスに寄与するのは「CIが確立されている場合のみ」であることが示されたように、ケイパビリティの効果はコンテキストに依存する。

### 他のフレームワークとの比較

| 観点 | DORA | SPACE | 従来のアジャイルメトリクス |
|------|------|-------|----------------------|
| 焦点 | ソフトウェアデリバリー | 開発者の生産性全般 | スプリントの効率 |
| 測定対象 | チーム/組織 | 個人〜組織 | チーム |
| 指標の性質 | アウトカム指標 | 多次元（活動〜満足度） | アウトプット指標 |
| 研究基盤 | 10年間の実証研究 | 文献レビュー + 実務知見 | 経験則ベース |
| 限界 | デリバリーに特化 | 具体的ベンチマークなし | プロセス改善に偏重 |

---

## 7. SPACEフレームワーク

### 概要

SPACEフレームワークは、開発者の生産性を多面的に捉えるためのフレームワーク。「単一の指標で開発者の生産性を測ることはできない」という前提に立つ。

### 論文情報

- **タイトル**: The SPACE of Developer Productivity
- **著者**: Nicole Forsgren, Margaret-Anne Storey, Chandra Maddila, Tom Zimmermann, Brian Houck, Jenna Butler
- **掲載**: ACM Queue, 2021年2月, Vol 19(1): pp. 20-48
- **所属**: Microsoft Research（AI Interaction and Learning, SAINTES, Developer Experience Lab）

注目すべき点として、**Nicole ForsgrenはDORAの創設者でもある**。SPACEはDORAの限界を補完するために設計された面がある。

### 5つの次元

#### S — Satisfaction and well-being（満足度とウェルビーイング）

開発者が自分の仕事、チーム、ツール、文化にどの程度満足しているか。バーンアウト、帰属意識、自律性の感覚を含む。

- サーベイによる測定が中心
- 例: 「自分のツールに満足しているか」「チームの文化に満足しているか」

#### P — Performance（パフォーマンス）

開発者の作業のアウトカム（成果）。コードの品質、信頼性、ユーザーへの影響を含む。

- 例: コードレビューの品質、バグの少なさ、顧客満足度
- **注意**: 「パフォーマンス」はアウトプット量ではなく、アウトカムの質を指す

#### A — Activity（アクティビティ）

開発者の活動量。最も測定しやすいが、単独では生産性の代理指標として不十分。

- 例: コミット数、PR数、コードレビュー数、ドキュメント更新数
- **注意**: アクティビティ指標のみに依存すると、量の追求に陥る危険がある

#### C — Communication and collaboration（コミュニケーションと協働）

チームメンバー間のコミュニケーションの質と速度。知識共有、メンタリング、コードレビューの相互作用を含む。

- 例: コードレビューの応答時間、ドキュメントの発見可能性、ミーティングの質
- ネットワーク分析やサーベイで測定

#### E — Efficiency and flow（効率とフロー）

中断なく集中して作業を進められる度合い。フロー状態への到達しやすさ、ツールチェーンの摩擦の少なさを含む。

- 例: ビルド時間、CI/CDのフィードバック速度、コンテキストスイッチの頻度
- 開発者体験（DevEx）と密接に関連

### DORAとSPACEの関係性

| 観点 | DORA | SPACE |
|------|------|-------|
| 創設者 | Nicole Forsgren（共通） | Nicole Forsgren（共通） |
| 測定対象 | ソフトウェアデリバリーのアウトカム | 開発者の生産性（多次元） |
| 粒度 | チーム/組織レベル | 個人〜組織の複数レベル |
| ベンチマーク | あり（Elite/High/Medium/Low） | なし（組織固有に設計） |
| 主な用途 | デリバリーパフォーマンスの改善 | 開発者体験の包括的理解 |
| 補完関係 | SPACEの「P」次元にDORAメトリクスを含められる | DORAが捉えない満足度・フロー・協働を補完 |

**推奨**: DORAとSPACEは競合ではなく補完的に使用すべき。DORAメトリクスをSPACEのPerformance次元の一部として位置づけ、他の4次元でデリバリーパフォーマンスの「なぜ」を理解する、という使い方が効果的。

---

## 8. 実践的な導入パターン

### Four Keysの計測方法

#### Google Cloud Four Keys OSSツール

- **リポジトリ**: https://github.com/dora-team/fourkeys
- **ステータス**: **2024年1月にアーカイブ済み**（メンテナンス終了）
- **アーキテクチャ**: GitHub/GitLabからのWebhook → Cloud Run → Pub/Sub → BigQuery → Grafanaダッシュボード
- **用途**: フォークして独自のメトリクス計測基盤として参考にすることが推奨

#### 代替ツール・アプローチ

| ツール/アプローチ | 特徴 |
|---|---|
| **Sleuth** | DORAメトリクスに特化したSaaSプラットフォーム |
| **LinearB** | Gitデータからの自動メトリクス収集 |
| **Faros AI** | オープンソースのエンジニアリングインテリジェンスプラットフォーム |
| **自社構築** | CI/CDパイプラインのデータを集約してBIツールで可視化 |
| **DORA Quick Check** | https://dora.dev/quickcheck/ でサーベイベースの簡易診断 |

### DORAが推奨する導入ステップ

出典: https://dora.dev/guides/how-to-transform/

#### 1. 目標設定とチーム実験の有効化

4段階モデル：
1. **方向性の確立**: リーダーシップが「ゼロ障害」「10倍の生産性向上」等の理想的な目標（True North）を設定
2. **現状の評価**: DORA Quick CheckやValue Stream Mappingで現在地を測定
3. **ターゲット条件の定義**: OKR等の形式で具体的・測定可能な目標を設定（チーム自身が設定する）
4. **日次実験の実行**: PDCAサイクルで反復的に目標に向かう

#### 2. コミュニティベースの知識共有

高パフォーマーが採用するパターン：
- **コミュニティ・オブ・プラクティス（CoP）**: 草の根型の知識共有
- ボトムアップの改善提案
- PoC（概念実証）テンプレートとシード

#### 3. 継続的改善の原則

| 原則 | 適用 |
|------|------|
| 継続的改善 | 一時的プロジェクトではなく日常的な活動とする |
| 自律性を伴う方向合わせ | リーダーが測定可能な成果を伝え、チームが実行方法を決める |
| 反復的デリバリー | 大きな変更を小バッチに分割し軌道修正可能にする |
| 科学的アプローチ | 命令的な方法ではなくデータ駆動の実験を行う |

### 導入のアンチパターン

#### 1. トランスフォーメーションを一時的なものとして扱う

- 持続的な変化には顧客獲得と同等の継続的な投資が必要
- 「DevOpsチーム」を作って終わりにしない

#### 2. トップダウンでの実装

- チームの意見を聞かない組織再編はストレス・離脱・生産性低下を招く
- リーダーは「何を」を示し、「どうやるか」はチームに委ねるべき

#### 3. 曖昧または矛盾する目標

- 「市場投入時間の短縮」のような測定不能な目標は成功判定が不可能
- 組織内の異なるユニット間で競合する目標を設定しない

#### 4. メトリクスの目的化（Goodhart's Law）

- Four Keysの数値改善そのものを目標にしない
- メトリクスは会話のきっかけであり、改善活動の方向性を示すもの
- チームに対してメトリクスで評価・罰を与えない

#### 5. センター・オブ・エクセレンス（CoE）への過度な依存

- 集中型のCoEはボトルネックを作り、専門家のサイロ化を招く
- 理論と実践を乖離させる
- コミュニティ・オブ・プラクティスの方が効果的（2019年レポート）

### 成熟度に応じたアプローチ

#### 初期段階（Low パフォーマンス）

- まずバージョン管理と基本的なCIを確立する
- デプロイ頻度とリードタイムの現状把握から始める
- 小さな勝利を積み重ねてモメンタムを構築する

#### 成長段階（Medium パフォーマンス）

- テスト自動化とデプロイ自動化に投資
- モニタリングとアラートを整備し、障害検知・復旧時間を短縮
- トランクベース開発への移行を検討

#### 成熟段階（High パフォーマンス）

- 継続的デリバリーの完全な実践
- 疎結合アーキテクチャの推進
- ドキュメンテーション品質の向上（2023年の知見：技術的ケイパビリティの効果を増幅）

#### 最適化段階（Elite パフォーマンス）

- ユーザー中心主義の組織全体への浸透
- プラットフォームエンジニアリングによる開発者体験の最適化
- 生成的文化の醸成と変革型リーダーシップの実践
- AI活用の体系的な導入（2025年の知見）

---

## 参照・出典

### 公式サイト

- DORA公式: https://dora.dev
- DORA Research: https://dora.dev/research/
- DORA Capabilities: https://dora.dev/capabilities/
- DORA Core Model: https://dora.dev/core/
- DORA Quick Check: https://dora.dev/quickcheck/
- DORA Metrics History: https://dora.dev/insights/dora-metrics-history
- How to Transform: https://dora.dev/guides/how-to-transform/
- Four Keys Metrics Guide: https://dora.dev/guides/dora-metrics-four-keys/

### 書籍

- Forsgren, N., Humble, J., & Kim, G. (2018). *Accelerate: The Science of Lean Software and DevOps*. IT Revolution Press.
- Humble, J. & Farley, D. (2010). *Continuous Delivery*. Addison-Wesley.
- Kim, G. et al. (2013). *The Phoenix Project*. IT Revolution Press.
- Kim, G. et al. (2016). *The DevOps Handbook*. IT Revolution Press.

### 論文・レポート

- Forsgren, N. et al. (2021). The SPACE of Developer Productivity. *ACM Queue*, 19(1), 20-48.
- State of DevOps Reports (2014-2025): https://dora.dev/research/
- 2025 DORA AI Capabilities Report: https://cloud.google.com/resources/content/2025-dora-ai-capabilities-model-report

### GitHub

- DORA Team: https://github.com/dora-team/dora.dev
- Four Keys (archived): https://github.com/dora-team/fourkeys

### コミュニティ

- DORA Community: https://dora.community
- LinkedIn: https://www.linkedin.com/company/doradotdev/
- YouTube: https://www.youtube.com/@dora-dev
