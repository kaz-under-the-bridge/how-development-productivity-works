# AI成熟度フレームワーク — 開発生産性への応用

> Accenture「The Art of AI Maturity」を**開発組織の生産性向上**の文脈で再整理した独自解釈ドキュメント。

> **元フレームワーク**: [Accenture AI成熟度フレームワーク — 公開情報整理](../notes/ref-accenture-ai-maturity.md)

> 💭 本ドキュメントの内容は、Accentureの公開データに基づく独自の解釈・マッピングである。

---

## 他フレームワークとの関係

- [DORA](./dora-four-keys.md) がソフトウェアデリバリーのパフォーマンスを測定するのに対し、本フレームワークは**組織のAI活用成熟度**を評価する
- DORA 2025レポートの「[7つの基盤的能力](../research/dora-reports/2025.md)」と本フレームワークの「基盤的能力」は相互補完的
- [コーディングエージェント](../research/coding-agents-landscape-2026.md)の組織導入における成熟度評価にも応用可能
- Agent = Model + Harness の文脈では、Harnessの組織的整備度を評価する枠組みとして機能する

---

## 1. DORA 2025 7アーキタイプとの対応

💭 DORA 2025レポートは従来のLow/Med/High/Elite分類を廃止し、[7つの組織アーキタイプ](../research/dora-reports/2025.md#6-7つの組織アーキタイプ)に移行した。AI成熟度4段階との大まかな対応：

| AI成熟度 | 対応しうるDORAアーキタイプ |
|----------|--------------------------|
| AI Experimenters | Foundational Challenges, Legacy Bottleneck |
| AI Builders | Constrained by Process, Stable and Methodical |
| AI Innovators | High Impact Low Cadence |
| AI Achievers | Pragmatic Performers, Harmonious High-Achievers |

**接続の論理**: 両フレームワークは「基盤能力が高い組織ほどパフォーマンスが高い」という共通の知見を持つ。DORAが「ソフトウェアデリバリーの基盤」を測定し、AI成熟度が「AI活用の基盤」を測定する。両方の基盤が高い組織がAI時代の高パフォーマーになると考えられる。

---

## 2. 開発組織における17ケイパビリティの解釈

💭 [元フレームワークの17ケイパビリティ](../notes/ref-accenture-ai-maturity.md#17のキーケイパビリティ)を、開発組織の文脈で再解釈する。

| # | ケイパビリティ | 開発生産性での解釈 |
|---|---------------|-------------------|
| 1 | Senior Sponsorship | 経営層がAI活用を公式に推進・予算確保 |
| 2 | AI Strategy | 開発プロセスにおけるAI活用ロードマップ策定 |
| 3 | Proactive vs. Reactive | 先行投資型アプローチで技術負債を予防 |
| 4 | Readily Available AI/ML Tools | GitHub Copilot等の全社展開と標準化 |
| 5 | Readily Available Developer Networks | 社内外のAI開発者コミュニティとの連携 |
| 6 | Build vs. Buy | ツール内製と外部サービス利用の判断基準 |
| 7 | Platform and Technology | 開発プラットフォーム・IDP整備 |
| 8 | Experimentation Data — Change | A/Bテストやフィーチャーフラグの運用改善 |
| 9 | Data Management and Governance | コードベース・ナレッジの品質管理 |
| 10 | Data Management and Governance — Change | データガバナンスの継続的改善 |
| 11 | Mandatory AI Training | 全エンジニア対象のAIツール活用研修 |
| 12 | Employee Competency in AI-Related Skills | AI活用スキルレベルの定義と定期評価 |
| 13 | Innovation Culture Embedded | 組織構造にイノベーション推進を組み込む |
| 14 | Innovation Culture Encouraged | 実験・失敗を許容する報酬・評価制度 |
| 15 | AI Talent Strategy | 採用・育成・リテンションの統合戦略 |
| 16 | Responsible AI | AI利用ポリシー・倫理基準の策定 |
| 17 | Responsible AI — Change | ポリシーの定期見直しとインシデント対応 |

---

## 3. ケイパビリティ間の因果関係

💭 開発組織におけるケイパビリティの依存関係を示す。

```
経営層スポンサーシップ ──→ AI戦略策定
       │
イノベーション文化（定着）──→ AI戦略の実行力
イノベーション文化（推奨）──→ AI推進のリーダーシップ
       │
       ▼
AIスキル診断 ──→ AI人材戦略策定 ──→ 必須AIトレーニング設計
       │                                    ▲
       └────────────────────────────────────┘
       （スキル要素ごとに適したトレーニングを設計）

イノベーション文化 ──→ AI人材戦略に文化醸成を組み込む
```

**DORAとの接続**: DORAの[組織文化（Westrum モデル）](../foundations/organizational-culture.md)における「生成的文化」は、ここでいう「イノベーション文化の定着」に対応する。両方とも組織パフォーマンスの強力な予測因子である。

---

## 4. RACI（責任分担）の設計例

💭 各ケイパビリティに対して、一般的な開発組織における責任分担の例を示す。

| ケイパビリティ | Responsible（実行） | Accountable（最終責任） | Consulted（相談） | Informed（報告） |
|---------------|--------------------|-----------------------|------------------|-----------------|
| AI戦略 | AI推進チーム | CTO/VPoE | 各部門長 | 経営会議 |
| AI人材戦略 | HR + AI推進チーム | CHRO/VPoE | 各部門長 | 経営会議・取締役会 |
| 必須AIトレーニング | HR + AI推進チーム | CHRO | エンジニアリング部門・データ部門 | 経営会議 |
| AIスキル診断 | HR + AI推進チーム | CHRO | エンジニアリング部門・基盤部門 | 経営会議 |
| イノベーション文化 | HR + AI推進チーム | CHRO | AI推進チーム | 経営会議 |
| 責任あるAI | AI推進チーム | AI推進チーム長 | エンジニアリング・データ部門 | 経営会議・取締役会 |
| 責任あるAI（変化管理） | AI推進チーム + エンジ + データ + IT | AI推進チーム長 | AI推進チーム | 経営会議 |
| データガバナンス（変化管理） | データエンジニアリング部門 | データ部門長 | AI推進チーム | 経営会議 |

---

## 5. 開発生産性向上へのアクションプラン

### Phase 1: 基盤構築（AI Experimenters → AI Builders）

- [ ] AI活用に関する経営層のスポンサーシップを正式に獲得
- [ ] 開発者向けAIツール（コード補完、テスト生成）の全社標準を選定・導入
- [ ] AI活用スキルのコンピテンシーマップを定義
- [ ] AI生成コードに関するセキュリティ・品質ガイドラインを策定

### Phase 2: 差別化推進（AI Builders → AI Achievers）

- [ ] CI/CDパイプラインにAIを統合（自動レビュー、テスト生成、障害予測）
- [ ] 全エンジニア必須のAI活用研修を設計・実施
- [ ] [DORA metrics](./dora-four-keys.md)等にAI効果を反映した評価指標を運用
- [ ] イノベーション文化を促進する制度設計（ハッカソン、20%ルール等）
- [ ] 責任あるAI利用のポリシーを定期レビューする仕組みを構築

### Phase 3: 自己改善システムへ（AI Achievers → Self-Evolving）

- [ ] エージェントのワークフローを測定・評価する仕組みの構築（[GAINS Framework](./comparison.md)等）
- [ ] Agent Harness のナレッジを組織横断で共有する Center of Practice の設置
- [ ] エージェントが自身の instructions/AGENTS.md を改善提案するフィードバックループの構築

---

## 参考

- [Accenture AI成熟度フレームワーク — 公開情報整理](../notes/ref-accenture-ai-maturity.md) — 元データ・出典
- [DORA / Four Keys](./dora-four-keys.md) — ソフトウェアデリバリーの測定
- [DORA 2025レポート](../research/dora-reports/2025.md) — 7アーキタイプ、7つの基盤的能力
- [コーディングエージェント最新動向](../research/coding-agents-landscape-2026.md) — Agent=Model+Harness、組織導入パターン
- [組織文化と心理的安全性](../foundations/organizational-culture.md) — Westrum文化モデル
- [フレームワーク比較](./comparison.md) — DORA/SPACE/DX Core 4との位置づけ

---

*作成: 2026年3月 / 性質: 独自解釈・応用ガイド（frameworks）*
