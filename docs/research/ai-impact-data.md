# AI影響の実態データ（2024-2026）

AIコーディングツールの普及がソフトウェア開発に与えている影響の実態データを集約する。

---

## 1. AI生産性パラドックス

個人レベルではタスク完了が加速する一方、組織レベルのデリバリー指標は改善しない、あるいは悪化するという現象。

| 指標 | 変化 |
|------|------|
| 個人タスク完了数 | +21% |
| マージされたPR数 | +98% |
| コードレビュー時間 | +91%（悪化） |
| PRサイズ | +154%（肥大化） |
| バグ率 | +9%（悪化） |
| AIアシストPRのインシデント率 | +23.5%（非AIと比較） |

出典: [Faros AI - DORA Report 2025 Key Takeaways](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025)

## 2. 帰属の不可視性問題

- DORAもSPACEもAI生成コードと人間のコードを区別できない（開発者のコードの約41%がAI生成）
- AI支援PRはレビュー通過後もインシデント率が高いが、従来指標では検出不能
- 複数ツール（Cursor、Claude Code、Copilot等）の同時使用への統合的可視性が欠如

出典: [Exceeds AI](https://blog.exceeds.ai/dora-metrics-vs-modern-productivity/)

## 3. 隠れた検証コスト

- AIはコード生成を高速化するが、節約時間は**監査と検証に再配分**されている
- 開発者の30%がAI生成コードへの信頼度が低い〜ゼロと回答
- エンジニアはすべてのAI生成コードを「潜在的に誤りがある」として扱う必要がある

出典: [DORA - Balancing AI Tensions](https://dora.dev/insights/balancing-ai-tensions/)

## 4. METR研究

2025年7月のMETR研究では、経験豊富なOSS開発者がAIツールを使用するとタスク完了に**19%長くかかる**という結果。開発者自身の認識（速くなったはず）に反する。

2026年2月のアップデートでは選択バイアス等の問題が判明し実験デザインを変更中。

出典: [METR 2025](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/), [METR 2026 Update](https://metr.org/blog/2026-02-24-uplift-update/)

---

## 5. AIツール採用の実態（2025年）

### Jellyfish 12ヶ月データ

| 指標 | 2025年1月 | 2025年10月 | 変化 |
|------|----------|----------|------|
| コードアシスタント採用率 | 49.2% | 69% | +20pt |
| コードレビューエージェント採用率 | 14.8% | 51.4% | +37pt |
| AI生成コード割合 | 〜20% | 〜50% | +30pt |
| PRマージ数（高AI採用企業） | 1.36/人 | 2.9/人 | +113% |
| サイクルタイム | 16.7時間 | 12.7時間 | -24% |

AIツール市場シェア: GitHub Copilot首位、Claude Code 2位、Cursor 3位

出典: [Jellyfish](https://jellyfish.co/blog/2025-ai-metrics-in-review/)

### Cortex 2026ベンチマーク
- PRsあたりのインシデント率 +23.5%
- 変更失敗率 約+30%
- 正式なAI利用ポリシーを持つ組織はわずか45%

出典: [Cortex](https://www.cortex.io/post/ai-is-making-engineering-faster-but-not-better-state-of-ai-benchmark-2026)

---

## 6. 企業の実践例（DX調査、18社）

| 企業 | AI影響の測定方法 |
|------|----------------|
| Dropbox | AIを定期的に使用するエンジニアはPR出荷量+20%、変更失敗率も低下 |
| Webflow | 在籍3年以上のエンジニアがAIの恩恵を最も受け、スループット約+20% |
| Microsoft | 「Bad Developer Days」を追跡し、摩擦の削減を測定 |
| Glassdoor | 月次A/Bテスト数をイノベーション指標として使用 |
| Shopify | リーダーボードで実験を称賛 |

出典: [DX - How 18 Companies Measure AI Impact](https://getdx.com/blog/how-top-companies-measure-ai-impact-in-engineering/)

## 7. AIエンジニアリングの新たなムダ（Thoughtworks）

| ムダ | 内容 |
|------|------|
| プロンプト-応答のレイテンシ | ワークフロー中断 |
| コンテキスト喪失 | 問題の再説明が必要になる |
| 断片化されたツールチェーン | 認知負荷の増大 |
| AI生成コードの検証オーバーヘッド | 「潜在的に誤りがある」として扱う必要 |

出典: [Thoughtworks - 2025 DORA Report Perspective](https://www.thoughtworks.com/insights/articles/the-dora-report-2025--a-thoughtworks-perspective)

---

## 参照

- [DORA 2024 Report](./dora-reports/2024.md)
- [DORA 2025 Report](./dora-reports/2025.md)
- [フレームワーク比較](../frameworks/comparison.md)
- [制約理論 — AI時代のボトルネック移動](../foundations/toc-theory-of-constraints.md)
