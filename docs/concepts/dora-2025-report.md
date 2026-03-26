# DORA 2025レポート要点: State of AI-Assisted Software Development

DORA（DevOps Research and Assessment）が2025年に公開したレポートの要点整理。従来のDevOpsデリバリーパフォーマンスから、AI支援ソフトウェア開発に完全にフォーカスした初のレポートとなった。

出典: [DORA 2025 Report](https://dora.dev/research/2025/dora-report/), [Google Cloud版](https://cloud.google.com/resources/content/2025-dora-ai-assisted-software-development-report)

---

## 1. 中心的メッセージ

> **「AIは組織を修正しない。既にあるものを増幅する」**

- AIは万能な生産性向上ツールではなく**増幅装置**として機能する
- 高パフォーマンスチームはAIでさらに良くなり、問題を抱えるチームはAIによって問題が顕在化・悪化する
- AIへの最大のリターンはツール自体ではなく、**基盤となる組織システムへの戦略的フォーカス**から得られる

---

## 2. 調査規模

- 約5,000人の調査回答者
- 100時間以上の定性インタビュー
- 研究パートナー: IT Revolution, GitHub, GitLab, SkillBench, Workhelix

---

## 3. AI採用の実態

### 採用率と認識

| 項目 | データ |
|------|--------|
| AI日常利用率 | 90% |
| AIを重度に利用（コード記述・デバッグ等） | 約66% |
| 生産性向上を実感 | 80%以上 |
| コード品質改善を報告 | 59% |
| 品質悪化を報告 | 10% |
| AI出力の信頼性に懸念 | 30% |

### 主なAI利用用途

**高頻度:** 新規コード記述、既存コード修正、デバッグ、コード説明、テスト生成

**低頻度:** 要件分析、ドキュメント作成、設計計画、アーキテクチャ判断

---

## 4. AI生産性パラドックス

個人レベルの指標は改善するが、組織レベルのデリバリー指標は改善しない、あるいは悪化するという現象。

### 個人指標（改善）

| 指標 | 変化 |
|------|------|
| タスク完了数 | +21% |
| マージされたPR数 | +98% |
| 日次タスクコンテキスト | +9% |
| 日次PR処理数 | +47% |

### 組織指標（悪化）

| 指標 | 変化 |
|------|------|
| コードレビュー時間 | +91%（ボトルネック化） |
| PRサイズ | +154%（肥大化） |
| バグ率 | +9% |

### パラドックスの根本原因

- AIはコード生成を加速するが、**レビュー・テスト・承認プロセスには影響しない**
- AI使用時に**バッチサイズ（変更セット）が大きくなる**傾向がある
- DORAのデータは一貫して大きな変更セットがリスクを導入することを示している
- コード量が増えても、エンジニアリング規律がなければデリバリー成果に転換されない

出典: [Faros AI - DORA Report 2025 Key Takeaways](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025)

---

## 5. DORAメトリクスの進化

### 2024年の変更

- **第5の指標「Rework Rate」** を導入
- メトリクスを**スループット（3指標）** と**不安定性（2指標）** に再分類
- MTTRを「Failed Deployment Recovery Time」に再定義（安定性→スループットに移動）

### 2025年の変更

- **Low/Medium/High/Eliteの4段階分類を廃止**
- 指標ごとのバケット分類 + **7つの組織アーキタイプ**に置換
- AI支援ソフトウェア開発に完全特化

---

## 6. 7つの組織アーキタイプ

従来の線形的なパフォーマンス分類に代わり、組織の状態をより実態に即した形で類型化。

| # | アーキタイプ | 概要 |
|---|------------|------|
| 1 | **Foundational Challenges** | サバイバルモード。プロセスに根本的な欠陥がある |
| 2 | **Legacy Bottleneck** | 優秀なチームだが老朽化したインフラに囚われている |
| 3 | **Constrained by Process** | 承認サイクルや官僚主義がデリバリーを遅延させる |
| 4 | **High Impact, Low Cadence** | 品質は高いがデリバリー頻度が低い |
| 5 | **Stable and Methodical** | 着実かつ高品質だが速度は控えめ |
| 6 | **Pragmatic Performers** | 機能的な環境での高速デリバリー。チームの約40% |
| 7 | **Harmonious High-Achievers** | 持続可能な卓越性の好循環。最上位 |

**設計意図:** 組織は単一の軸上で順番に「登る」のではなく、それぞれ固有のコンテキストと課題を持つ。改善パスもアーキタイプごとに異なる。

---

## 7. AIを増幅させる7つの基盤的能力

AIの個人的な生産性向上を組織的なパフォーマンスに転換するために必要な能力。

| # | 能力 | 説明 |
|---|------|------|
| 1 | **明確な組織のAI姿勢** | AIツール統合に関する明示的なポリシーとガバナンス |
| 2 | **健全なデータエコシステム** | 信頼性が高く構造化された内部情報 |
| 3 | **AIアクセス可能な内部データ** | 高品質なドキュメントと検索可能なリポジトリ |
| 4 | **強力なバージョン管理** | コードレビュー、開発標準などの基盤プラクティス |
| 5 | **小バッチ規律** | インクリメンタルな変更によるレビュー品質向上とリスク低減 |
| 6 | **ユーザー中心主義** | コード量ではなく意味のある機能への注力 |
| 7 | **高品質な内部プラットフォーム** | セルフサービスツール・標準化された環境による複雑性の削減 |

---

## 8. AIエンジニアリングの新たなムダ

Thoughtworks Chris Westerhold（Global Practice Director）による分析。

| ムダ | 内容 |
|------|------|
| プロンプト-応答のレイテンシ | ワークフロー中断 |
| コンテキスト喪失 | 問題の再説明が必要になる |
| 断片化されたツールチェーン | 認知負荷の増大 |
| AI生成コードの検証オーバーヘッド | 「潜在的に誤りがある」として扱う必要 |

> 「エンジニアの本当の価値はもはやコードを書くことだけにあるのではなく、プロンプトエンジニアリング、ソリューションアーキテクチャ、AI生成出力の検証にある」

出典: [Thoughtworks - 2025 DORA Report Perspective](https://www.thoughtworks.com/insights/articles/the-dora-report-2025--a-thoughtworks-perspective)

---

## 9. 開発者体験への影響

- AI採用と燃え尽き症候群・摩擦の増加との間に**相関は見られなかった**
- 開発者は+9%のタスクコンテキストと+47%のPRを日次で処理しているにもかかわらず、ストレス指標はニュートラル
- ただし、30%の開発者がAI生成コードの信頼性に懸念を持つ

---

## 10. 成功のための要件

### リーダーシップへの提言

1. **意図的で体系的な導入** — 急がない。基盤構築が最優先
2. **段階的な実装** — フィードバックループを伴う漸進的アプローチ
3. **人への投資** — ツール導入だけでは不十分。スキル転換と文化変革が必要
4. **システム思考** — ツール・ワークフロー・組織知識の統合
5. **測定の精緻化** — 管理グループ（GitHub teams等）ではなく、実際の協働単位（5-12人）で測定する

### 組織の進化方向

**AI-Augmented**（既存プロセスの支援）→ **AI-First**（インテリジェントエージェントによるソフトウェアデリバリーの再定義）

この移行には、強固なエンジニアリング基盤が前提条件となる。

---

## 参照・出典

### 一次ソース
- [DORA 2025 Report](https://dora.dev/research/2025/dora-report/)
- [Google Cloud 2025 DORA AI Report](https://cloud.google.com/resources/content/2025-dora-ai-assisted-software-development-report)

### 分析・解説
- [Faros AI - DORA Report 2025 Key Takeaways](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025)
- [Thoughtworks - 2025 DORA Report Perspective](https://www.thoughtworks.com/insights/articles/the-dora-report-2025--a-thoughtworks-perspective)
- [Scrum.org - DORA 2025 Summary](https://www.scrum.org/resources/blog/dora-report-2025-summary-state-ai-assisted-software-development)
- [InfoQ - AI DORA Report](https://www.infoq.com/news/2026/03/ai-dora-report/)
