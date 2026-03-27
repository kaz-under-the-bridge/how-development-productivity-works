# 業界の論争と議論

## 1. McKinsey論争（2023-2024）

McKinseyが2023年8月に「開発者生産性は測定できる」と主張。Kent Beck、Gergely Orosz、Dan Northらが反発した。

### McKinseyの主張
- 開発者の生産性は客観的に測定可能
- コーディングとテストに重点を置いた指標で管理すべき

### 主な批判

| 批判者 | 論点 |
|--------|------|
| **Kent Beck** | 個人の貢献測定は「エンジンの中のピストン1つの貢献を測るようなもの」 |
| **Gergely Orosz** | 生産性の過度な単純化。Pragmatic Engineerで2部構成の詳細な反論を発表 |
| **Dan North** | 個人パフォーマンス指標の強調はゲーミング行動・サイロ化・心理的安全性の低下を招く |

### 議論の帰結

- 個人のアウトプット量で測定することへの業界的なコンセンサスが形成：**やるべきでない**
- システムレベル（チーム・組織）の指標が重要という認識が強化
- DX Core 4等の多次元フレームワークが支持を拡大

出典: [Pragmatic Engineer](https://newsletter.pragmaticengineer.com/p/measuring-developer-productivity), [DX](https://getdx.com/blog/mckinsey-developer-productivity/), [Dan North](https://dannorth.net/blog/mckinsey-review/)

---

## 2. AI時代の測定論争

### DORA 2024-2025の衝撃

- 2年連続でAIツール採用がデリバリーパフォーマンス**悪化**と相関
- 主観的認識（75%が生産性向上を実感）と客観的データ（スループット-1.5%、安定性-7.2%）の乖離
- 「AIは増幅装置」— 良いプラクティスも悪いプラクティスも増幅する

### キーパーソンの見解

**Abi Noda（DX CEO）**
- 「AIは悪いプラクティスをさらに悪化させる」
- 採用指標だけでは不十分。成果にAIが寄与しているかを包括的に測定すべき
- DXのデータ: AIを毎日使うエンジニアはオンボーディング速度が2倍

**Margaret-Anne Storey（University of Victoria教授、DX Chief Scientist）**
- CHASE 2025で基調講演
- 「Vibe Coding」の質的理論を提唱 — AIとの会話的インタラクション、共同創造、フローと喜びを中心に
- AIへの信頼が委任と共同創造の連続体に沿った動きを調整する

**Gergely Orosz（Pragmatic Engineer）**
- DXのLaura Tachoと共同で180社以上のデータからAIの実際の影響を分析

出典: [DX Blog](https://getdx.com/blog/ai-amplifies-bad-practices-real-gains-come-from-focusing-aiefforts-on-systems-and-success-depends-on-strong-change-management/), [Margaret-Anne Storey Talks](https://margaretstorey.com/talks/), [ResearchGate](https://www.researchgate.net/publication/388484354_Software_Engineering_by_and_for_Humans_in_an_AI_Era)

---

## 3. 広木大地氏の「単純な測定への警告」

Qiita記事「開発生産性について議論する前に知っておきたいこと」で、単純な測定の危険性を警告。

- 営利企業としての改善志向と実態の複雑性のバランスを論じている
- 「最適な単一指標は存在しない」
- 「**頻度は質に転化する**」が中核的主張であり、指標そのものの数値追求ではなくフィードバックループの短縮が本質

→ [広木大地](./hiroki-daichi.md)

---

## 参照

- [Nicole Forsgren](./nicole-forsgren.md)
- [広木大地](./hiroki-daichi.md)
- [フレームワーク比較](../frameworks/comparison.md)
- [AI影響の実態データ](../research/ai-impact-data.md)
