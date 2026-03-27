# DORA / Four Keys メトリクス

## 概要

DORA（DevOps Research and Assessment）は、Nicole Forsgren, Jez Humble, Gene Kimによって設立された研究プログラム。ソフトウェアデリバリーパフォーマンスを測定する指標体系（Four Keys）を確立し、書籍「Accelerate」（2018年）で体系化。2018年にGoogle Cloudに統合された。

広木大地氏はFour Keysを「高速で迅速な開発チーム」という定性的目標の定量化と位置づけ、**「頻度は質に転化する」** を中核の解釈としている。

---

## 1. 現行の5指標（2024年以降）

### スループット指標（Software Delivery Throughput）

| 指標 | 説明 |
|------|------|
| **Change Lead Time（変更リードタイム）** | バージョン管理にコミットしてから本番環境にデプロイされるまでの時間 |
| **Deployment Frequency（デプロイ頻度）** | 一定期間内のデプロイ回数、またはデプロイ間の時間 |
| **Failed Deployment Recovery Time（失敗デプロイ復旧時間）** | デプロイ失敗から復旧までの時間（旧MTTR） |

### 不安定性指標（Software Delivery Instability）

| 指標 | 説明 |
|------|------|
| **Change Fail Rate（変更失敗率）** | デプロイ後に即座の介入を必要とするデプロイの割合 |
| **Deployment Rework Rate（デプロイ再作業率）** | 本番環境のインシデントに起因する計画外デプロイの割合（2024年追加） |

### 指標の進化の歴史

| フェーズ | 期間 | 変更内容 |
|---|---|---|
| Phase 1: 起源 | 2014-2015 | 4指標を特定。変更失敗率が他の3指標と相関しないことが判明 |
| Phase 2: 標準化 | 2016-2018 | 4指標がベンチマークとして定着。可用性を追加 |
| Phase 3: 精緻化 | 2021-2023 | 可用性→信頼性に変更。MTTR→Failed Deployment Recovery Timeに名称変更 |
| Phase 4: 5指標化 | 2024 | Deployment Rework Rateを追加。安定性をInstabilityの2指標に分割 |
| Phase 5: アーキタイプ化 | 2025 | Low/Med/High/Eliteの分類を廃止 → 7つの組織アーキタイプに置換 |

出典: https://dora.dev/insights/dora-metrics-history

### パフォーマンスレベル（2023年版基準、2025年に廃止）

| レベル | デプロイ頻度 | リードタイム | 復旧時間 | 変更失敗率 |
|--------|-------------|-------------|---------|-----------|
| Elite | オンデマンド（1日複数回） | 1時間未満 | 1時間未満 | 0-15% |
| High | 週1回〜月1回 | 1〜24時間 | 1〜24時間 | 16-30% |
| Medium | 月1回〜四半期1回 | 1〜6ヶ月 | 1〜24時間 | 31-45% |
| Low | 四半期1回未満 | 6ヶ月超 | 24時間超 | 46-100% |

---

## 2. DORA Core Model

DORA Core Modelは、DORAの研究の中で**最も確立された知見**を集めたコレクション。研究の最先端よりも意図的に保守的に進化し、概念が繰り返し実証されてから初めてCore Modelに組み込まれる。

### ケイパビリティモデル全体像

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

### Technical Capabilities

- Code Maintainability / Continuous Delivery / Continuous Integration
- Database Change Management / Deployment Automation / Documentation Quality
- Flexible Infrastructure / Monitoring and Observability / Pervasive Security
- Test Automation / Test Data Management / Trunk-based Development
- Version Control / Working in Small Batches

### Process & Organizational Capabilities

- Empowering Teams to Choose Tools / Job Satisfaction / Loosely Coupled Teams
- Streamlining Change Approval / Visibility of Work in the Value Stream
- Visual Management / Well-being / Work in Process Limits

### Cultural & Leadership Capabilities

- Generative Organizational Culture / Learning Culture
- Team Experimentation / Transformational Leadership

### AI-Specific Capabilities（2025年追加）

- AI-accessible Internal Data / Clear and Communicated AI Stance
- Healthy Data Ecosystems / Platform Engineering / User-centric Focus

出典: https://dora.dev/core/, https://dora.dev/capabilities/

---

## 3. 批判・限界

### Goodhart's Law（グッドハートの法則）

**「指標が目標になると、良い指標でなくなる」**

- デプロイ頻度を上げるために無意味な小さなデプロイを増やす
- 変更失敗率を下げるために「失敗」の定義を変える
- リードタイムを短縮するためにレビューやテストを省略する

DORAチーム自身も2023年レポートで「メトリクス追求よりも継続的改善を重視すべき」と明記。

### 自己申告バイアス

- 回答者が自組織のパフォーマンスを過大/過小に評価する可能性
- 「デプロイ」「障害」「復旧」の定義が回答者により異なる可能性
- 生存者バイアス：比較的パフォーマンスの高い組織に偏る可能性

### 組織サイズによる適用の違い

- **大規模組織**: チーム間依存関係が指標に影響
- **スタートアップ**: 高頻度がケイパビリティの反映か、コードベースの小ささか判別困難
- **規制産業**: 変更承認プロセスが法的に必要な場合がある

### 指標のゲーミング問題

- フィーチャーフラグで実質的変更なしにデプロイ回数を増やす
- インシデント分類基準の変更で変更失敗率を操作
- コミット戦略の変更でリードタイムの見かけを改善

### コンテキスト依存性

ケイパビリティの効果はコンテキストに依存する。例：サプライチェーンセキュリティがデリバリーパフォーマンスに寄与するのは「CIが確立されている場合のみ」（2022年レポート）。

---

## 4. 実践的な導入パターン

### 計測ツール

| ツール | 特徴 |
|---|---|
| **Google Cloud Four Keys** | OSSだが2024年1月にアーカイブ済み |
| **Sleuth** | DORAメトリクスに特化したSaaS |
| **LinearB** | Gitデータからの自動メトリクス収集 |
| **Faros AI** | OSSエンジニアリングインテリジェンス |
| **DORA Quick Check** | https://dora.dev/quickcheck/ でサーベイベースの簡易診断 |

### 導入のアンチパターン

1. **トランスフォーメーションを一時的なものとして扱う** — 「DevOpsチーム」を作って終わりにしない
2. **トップダウンでの実装** — リーダーは「何を」を示し、「どうやるか」はチームに委ねる
3. **曖昧または矛盾する目標** — 測定可能で一貫した目標を設定
4. **メトリクスの目的化** — 数値改善そのものを目標にしない
5. **CoEへの過度な依存** — CoP（コミュニティ・オブ・プラクティス）の方が効果的

### 成熟度に応じたアプローチ

| 段階 | 重点 |
|------|------|
| Low | バージョン管理と基本的なCIの確立。デプロイ頻度の現状把握 |
| Medium | テスト自動化、デプロイ自動化、モニタリング整備 |
| High | 継続的デリバリーの完全実践、疎結合アーキテクチャ、ドキュメンテーション品質 |
| Elite | ユーザー中心主義、プラットフォームエンジニアリング、生成的文化、AI活用 |

出典: https://dora.dev/guides/how-to-transform/

---

## 参照

- [DORA公式](https://dora.dev)
- [DORA Metrics History](https://dora.dev/insights/dora-metrics-history)
- [DORA Core Model](https://dora.dev/core/)
- [Four Keys Metrics Guide](https://dora.dev/guides/dora-metrics-four-keys/)
- [How to Transform](https://dora.dev/guides/how-to-transform/)
- [書籍 Accelerate の知見](../research/accelerate.md)
- [State of DevOps Reports](../research/dora-reports/overview.md)
- [フレームワーク比較](./comparison.md)
