# SPACE フレームワーク

## 概要

開発者の生産性を多面的に捉えるためのフレームワーク。「**単一の指標で開発者の生産性を測ることはできない**」という前提に立つ。

### 論文情報

- **タイトル**: The SPACE of Developer Productivity
- **著者**: Nicole Forsgren, Margaret-Anne Storey, Chandra Maddila, Tom Zimmermann, Brian Houck, Jenna Butler
- **掲載**: ACM Queue, 2021年2月, Vol 19(1): pp. 20-48
- **所属**: Microsoft Research

**Nicole ForsgrenはDORAの創設者でもある。** SPACEはDORAの限界を補完するために設計された面がある。

---

## 5つの次元

### S — Satisfaction and well-being（満足度とウェルビーイング）

開発者が自分の仕事、チーム、ツール、文化にどの程度満足しているか。バーンアウト、帰属意識、自律性の感覚を含む。

- サーベイによる測定が中心
- 例: 「自分のツールに満足しているか」「チームの文化に満足しているか」

### P — Performance（パフォーマンス）

開発者の作業のアウトカム（成果）。コードの品質、信頼性、ユーザーへの影響を含む。

- 例: コードレビューの品質、バグの少なさ、顧客満足度
- **注意**: アウトプット量ではなく、アウトカムの質を指す

### A — Activity（アクティビティ）

開発者の活動量。最も測定しやすいが、単独では生産性の代理指標として不十分。

- 例: コミット数、PR数、コードレビュー数、ドキュメント更新数
- **注意**: アクティビティ指標のみに依存すると、量の追求に陥る危険がある
- AI時代：AI生成コードの量でActivityが膨張するため、単独使用は危険

### C — Communication and collaboration（コミュニケーションと協働）

チームメンバー間のコミュニケーションの質と速度。知識共有、メンタリング、コードレビューの相互作用を含む。

- 例: コードレビューの応答時間、ドキュメントの発見可能性、ミーティングの質
- ネットワーク分析やサーベイで測定

### E — Efficiency and flow（効率とフロー）

中断なく集中して作業を進められる度合い。フロー状態への到達しやすさ、ツールチェーンの摩擦の少なさを含む。

- 例: ビルド時間、CI/CDのフィードバック速度、コンテキストスイッチの頻度
- 開発者体験（DevEx）と密接に関連
- AI時代：プロンプト-応答のレイテンシやコンテキスト喪失が新たな非効率要因に

---

## DORAとSPACEの関係性

| 観点 | DORA | SPACE |
|------|------|-------|
| 創設者 | Nicole Forsgren（共通） | Nicole Forsgren（共通） |
| 測定対象 | ソフトウェアデリバリーのアウトカム | 開発者の生産性（多次元） |
| 粒度 | チーム/組織レベル | 個人〜組織の複数レベル |
| ベンチマーク | あり（→7アーキタイプに移行） | なし（組織固有に設計） |
| 主な用途 | デリバリーパフォーマンスの改善 | 開発者体験の包括的理解 |
| 補完関係 | SPACEの「P」次元にDORAメトリクスを含められる | DORAが捉えない満足度・フロー・協働を補完 |

**推奨**: DORAとSPACEは競合ではなく補完的に使用すべき。DORAメトリクスをSPACEのPerformance次元の一部として位置づけ、他の4次元でデリバリーパフォーマンスの「なぜ」を理解する、という使い方が効果的。

---

## 参照

- Forsgren, N. et al. (2021). The SPACE of Developer Productivity. *ACM Queue*, 19(1), 20-48.
- [SPACE - Microsoft Research](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/)
- [STACK 2024 - SPACE in the Age of AI](https://www.microsoft.com/en-us/research/video/stack-2024-space-in-the-age-ai-measuring-what-matters-for-developer/)
- [DORA / Four Keys](./dora-four-keys.md)
- [DX Core 4](./dx-core-4.md)
- [フレームワーク比較](./comparison.md)
