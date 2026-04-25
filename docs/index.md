# 開発生産性の全体マップ

> 「開発生産効率は恐ろしいスピードで高まっているが、複雑性がそれを上回る」— [広木大地](./perspectives/hiroki-daichi.md)

このドキュメント群は、開発生産性を体系的に理解するためのナレッジベースである。広木大地氏の概念整理を入口として、各概念の理論的基盤・測定フレームワーク・実証データを掘り下げていく構成になっている。

---

## I. そもそも「開発生産性」とは何か

### 生産性の定義

**生産性 = 獲得資源（Output） / 投入資源（Input）**

ソフトウェア開発ではアウトプットの測定が根本的に困難であり、「**最適な単一指標は存在しない**」（広木大地）。

### 開発生産性の3階層モデル（広木大地）

| 階層 | 説明 | 性質 | 対応するフレームワーク |
|------|------|------|---------------------|
| **仕事量生産性** | PR数、コード行数などの作業量 | 先行指標 | [DORA Four Keys](./frameworks/dora-four-keys.md)（デプロイ頻度等） |
| **期待付加価値の生産性** | 機能に見込まれた顧客価値 | — | [DX Core 4](./frameworks/dx-core-4.md)（Effectiveness） |
| **実現付加価値の生産性** | 実際に売上に繋がった価値 | 遅行指標 | [DX Core 4](./frameworks/dx-core-4.md)（Business Impact） |

→ 詳細: [広木大地 — 開発生産性に対する考え方](./perspectives/hiroki-daichi.md)

---

## II. 何が生産性を決めるのか — 理論的基盤

### 不確実性と複雑性

> エンジニアリング組織は**不確実性に向き合い、それを削減する営み**である — 広木大地

- ソフトウェアには[本質的複雑性と偶有的複雑性](./foundations/complexity-and-uncertainty.md)がある（Brooks）
- AIは偶有的複雑性を削減するが、本質的複雑性は残る → 複雑性のパラドックス
- 不確実性を削減する手段として「**頻度は質に転化する**」— 小さく頻繁にリリースしてフィードバックを得る

→ 詳細: [複雑性と不確実性](./foundations/complexity-and-uncertainty.md)

### フローとボトルネック

> 「個別工程の効率を上げても、全体のスループットは上がらない」— ゴールドラット

- [制約理論（TOC）](./foundations/toc-theory-of-constraints.md): 制約に集中し、全体最適を図る
- [リーンとフロー](./foundations/lean-and-flow.md): WIP制限、小バッチ、リトルの法則
- AI時代の制約移動: コーディング→レビューにボトルネックが移動（TOCの「惰性を避ける」）

### 組織文化

> セキュリティプラクティスの最大の予測因子は技術ではなく**文化**である — DORA 2022

- [Westrum組織文化モデル](./foundations/organizational-culture.md): 病的 → 官僚的 → 生成的
- 生成的文化は30%高い組織パフォーマンス（DORA 2023実証）
- [心理的安全性](./foundations/organizational-culture.md)がチーム実験・学習の前提条件

---

## III. どう測るか — 測定フレームワーク

```
          DORA (2014)           SPACE (2021)         DX Core 4 (2024)
          デリバリー指標          多次元の生産性        統合フレームワーク
          ┌──────────┐         ┌──────────┐         ┌──────────┐
          │デプロイ頻度│         │Satisfaction│        │ Speed    │
          │リードタイム│    →    │Performance │   →    │Effective.│
          │変更失敗率 │  補完    │Activity    │  統合   │ Quality  │
          │復旧時間  │         │Communic.  │        │Biz Impact│
          │Rework Rate│        │Efficiency │        │          │
          └──────────┘         └──────────┘         └──────────┘
```

| フレームワーク | 焦点 | 詳細 |
|--------------|------|------|
| **[DORA / Four Keys](./frameworks/dora-four-keys.md)** | ソフトウェアデリバリーのスループットと安定性 | 10年の実証研究。2025年に7アーキタイプに進化 |
| **[SPACE](./frameworks/space.md)** | 開発者の生産性を5次元で捕捉 | DORAが捉えない満足度・フロー・協働を補完 |
| **[DX Core 4](./frameworks/dx-core-4.md)** | DORA + SPACEの統合。ビジネスインパクトまで | AI時代を前提に設計。300以上の組織で実証 |
| **[AI Maturity](./frameworks/ai-maturity.md)** | 組織のAI活用成熟度（基盤×差別化の2軸） | Accenture提唱。17ケイパビリティ、4段階の成熟度モデル |

→ 詳細: [フレームワーク比較](./frameworks/comparison.md)

### 測定の落とし穴

- **Goodhart's Law**: 「指標が目標になると、良い指標でなくなる」
- **McKinsey論争**: 個人の生産性を測定しようとする危険性 → [業界の論争](./perspectives/industry-debates.md)
- **広木氏の警告**: 営利企業の改善志向と実態の複雑性のバランスが重要

---

## IV. 何が起きているか — 実証データ

### DORAレポートの変遷

| 年 | 主要な発見 | 詳細 |
|----|----------|------|
| 2014-2018 | Four Keys確立。「スピードと安定性は相関する」 | [Accelerate](./research/accelerate.md) |
| 2019-2023 | 文化・ドキュメント・ユーザー中心主義の重要性 | [レポート年表](./research/dora-reports/overview.md) |
| 2024 | 5指標化。AIがパフォーマンス悪化と相関（衝撃） | [2024レポート](./research/dora-reports/2024.md) |
| 2025 | 「AIは増幅装置」。7アーキタイプ。AI固有ケイパビリティ | [2025レポート](./research/dora-reports/2025.md) |

### AI時代の実態

> 「AIはチームを修正しない。既にあるものを増幅する」— DORA 2025

- 個人は速くなった（タスク+21%）が、組織は改善していない（レビュー時間+91%、PRサイズ+154%）
- これはTOCの「部分最適の罠」そのもの
- 経験豊富な開発者がAIで19%遅くなったという研究結果も（METR 2025）

→ 詳細: [AI影響の実態データ](./research/ai-impact-data.md)

### コーディングエージェントの台頭（2025年10月〜2026年4月）

- AIコーディングツールが「コード補完」から「自律エージェント」へ転換
- Agent = Model + Harness（ハーネス: ツールオーケストレーション、コンテキスト管理、エラー回復）
- 市場40億ドル。Claude Code（46%支持）、Cursor（19%）、GitHub Copilot（9%）
- SWE-bench Verifiedのトップスコアが65%→80.9%に（2025年初頭→2026年3月）

→ 詳細: [コーディングエージェント最新動向](./research/coding-agents-landscape-2026.md)

---

## V. 誰が何を言っているか — キーパーソン

| 人物 | 主要な貢献 | 詳細 |
|------|----------|------|
| **[広木大地](./perspectives/hiroki-daichi.md)** | 3階層モデル、不確実性、「頻度は質に転化する」 | 日本における開発生産性議論のオピニオンリーダー |
| **[Nicole Forsgren](./perspectives/nicole-forsgren.md)** | DORA、SPACE、DevExの3要素 | 「ほとんどの生産性指標は嘘」 |
| **[業界の論争](./perspectives/industry-debates.md)** | McKinsey論争、AI測定論争 | 個人 vs システムレベルの測定 |

---

## VI. 思索・考察

| テーマ | 内容 | 詳細 |
|--------|------|------|
| **[AIハーネスによる開発生産性と安全性の統合](./notes/ai-harness-productivity-safety.md)** | 生産性×安全性の共進化、消えた生産性のAI版、Layer 1/2/3計測問題、OODAループ設計 | ハーネスエンジニアリングが生産性と安全性をどう接続するか |

---

## ディレクトリ構成

```
docs/
├── index.md                 ← このファイル（全体マップ）
├── foundations/             理論的基盤（時代を超えて有効な理論）
│   ├── toc-theory-of-constraints.md
│   ├── lean-and-flow.md
│   ├── organizational-culture.md
│   └── complexity-and-uncertainty.md
├── frameworks/              測定フレームワーク（何を測るか）
│   ├── dora-four-keys.md
│   ├── space.md
│   ├── dx-core-4.md
│   ├── ai-maturity.md
│   └── comparison.md
├── research/                実証研究・レポート（エビデンス）
│   ├── accelerate.md
│   ├── ai-impact-data.md
│   ├── coding-agents-landscape-2026.md
│   └── dora-reports/
│       ├── overview.md
│       ├── 2024.md
│       └── 2025.md
├── perspectives/            人物・組織の視点
│   ├── hiroki-daichi.md
│   ├── nicole-forsgren.md
│   └── industry-debates.md
└── notes/                   壁打ちメモ・考察（意見）
    ├── ai-harness-productivity-safety.md
    ├── ref-accenture-ai-maturity.md
    ├── ref-fowler-harness-engineering.md
    └── evidence/
```

| レイヤー | 性質 | 更新頻度 |
|---------|------|---------|
| **foundations** | 時代を超えて有効な理論 | 低い |
| **frameworks** | 測定手法 | 中程度 |
| **research** | 特定の研究・レポート | レポート発行時 |
| **perspectives** | 人物の主張・視点 | 中程度 |
| **notes** | 我々の考察・壁打ち | 高い |
