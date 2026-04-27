# DORA Capability: Clear and Communicated AI Stance — 日本語整理

> 組織のAI利用方針を明確にし、全開発者に伝達するケイパビリティ。AI採用の摩擦を低減し、Individual EffectivenessとOrganizational Performanceを増幅する。

> **原文**: [Clear and Communicated AI Stance | DORA](https://dora.dev/capabilities/clear-and-communicated-ai-stance/)（2026年1月12日更新）
> **ライセンス**: CC BY-NC-SA 4.0

> **関連**: [DORA 2026 ROIレポート](./2026-roi.md)、[AIハーネスによる開発生産性と安全性の統合](../../notes/ai-harness-productivity-safety.md)

---

## 1. 定義

> 「開発者に対して、AIをどう使うことが期待されているか、どのツールを使ってよいか、どのようなサポートがあるかを伝える、理解しやすく広く共有されたフレームワーク」

曖昧さ（Ambiguity）は**イノベーションと安全の両方を阻害する**。曖昧さは2つの有害な極端を生む:

- **過度に保守的な行動**: AIを使えば解雇・訴訟されるかもしれないと恐れ、利用を回避
- **未検証ツールの野良採用（Shadow AI）**: 公式プラットフォームが成果を出せない場合、個人が非公認ツールを使い始める

> "Ambiguity stifles adoption. If a developer isn't sure whether using a coding assistant will get them fired or sued, they will likely either hide their usage (shadow AI) or avoid the technology entirely."

---

## 2. 研究知見

DORAの研究は**高い確信度**で以下を確認した:

- 明確なAIスタンスは、AI採用が**Individual Effectiveness**と**Organizational Performance**に与える正の影響を**増幅する**
- AIの通常は中立的なFrictionへの効果を、**有益なFriction低減**に転換する

> "By establishing a clear and communicated AI stance, we aren't just 'checking a compliance box.' We are actively reducing friction."

業界データ: 開発者の**90%**が既にAIを使用しており、その多くがShadow実装か躊躇しながらの利用。

---

## 3. 開発者が認知する4つの柱

| 柱 | 問い |
|---|------|
| **Expectation（期待）** | AIを使うことが期待されていると感じるか |
| **Support（支援）** | 組織はAI実験をサポートしているか |
| **Permission（許可）** | どのツールが許可されているか明確か |
| **Applicability（適用性）** | ポリシーが自分の役割に具体的に適用されるか |

---

## 4. 実装の推奨事項

### 4.1 エグゼクティブスポンサーシップの確保

リーダーシップが明確なAIミッションと採用計画を定義・推進する。戦略的重要性のシグナルとポリシー権限を提供。

### 4.2 クロスファンクショナルなワーキンググループの組成

エンジニアリング、法務、セキュリティ、IT、プロダクトリーダーシップの代表者を含める。

> 法務やセキュリティ部門のみが作ったポリシーは「現実との接触で生き残れない（unlikely to survive contact with reality）」。

### 4.3 Three-Bucket Framework（3バケット分類）

ツールとユースケースを3つのバケットに分類する。

| バケット | 説明 | 例 |
|---------|------|---|
| **Prohibited（禁止）** | 常に不許可の高リスク用途 | 顧客PIIを公開チャットボットに貼り付ける |
| **Permitted with guardrails（条件付き許可）** | 特定の制御の下で許可 | 承認済みエンタープライズツールでのプロプライエタリコード使用 |
| **Allowed（許可）** | 低リスク・高価値な活用を積極的に推奨 | プロプライエタリデータなしのボイラープレート生成やブレインストーミング |

### 4.4 Living Document（生きたドキュメント）として公開

- 静的なPDFを避ける
- 中央の検索可能な開発者ハブに公開
- 公式承認ツールリスト、ポリシー、進化するFAQを含める

### 4.5 社内共有とフィードバックループの確立

- タウンホールやチームミーティングで展開
- 開発者が質問し、新しいツールを提案できるフィードバック機構を作成
- ポリシーを進化させる

---

## 5. よくある失敗パターン

| パターン | 説明 |
|---------|------|
| **「一度きり」ポリシー** | AI技術が月単位で変化するのに、スタンスを静的なものとして扱う |
| **「むち打ち」効果** | チームが適応する時間なく頻繁にポリシーを変更する |
| **視野の狭い執筆** | エンジニアリングの入力なしに単一部門がコントロール → 非実用的なポリシー |

---

## 6. 測定方法

### サーベイ設問

| 次元 | 設問 |
|------|------|
| **Clarity（明確さ）** | 職場でどのAIツールを使用してよく、使用してはいけないかがどの程度明確か |
| **Support（支援）** | 組織はAIの実験をどの程度サポートしているか |
| **Expectation（期待）** | 職場でのAI利用がどの程度義務的と感じるか |
| **Applicability（適用性）** | 組織のAIポリシーが自分の業務にどの程度直接適用されるか |

### システムメトリクス

| メトリクス | 何を見るか |
|-----------|----------|
| **Policy Engagement** | 内部AIポリシードキュメントのページビュー・滞在時間 |
| **Clarification Volume** | 公開チャネルでのツール承認・ポリシー解釈に関する質問数 |

---

## 7. 関連リソース

- [DORA AI Capabilities Model Report](https://dora.dev/ai/capabilities-model/report/)
- [2025 State of AI-assisted Software Development Report](https://dora.dev/research/2025/dora-report/)
- [Fostering Developers' Trust in Generative AI](https://dora.dev/insights/trust-in-ai/)
- [Concerns Beyond the Accuracy of AI Output](https://dora.dev/insights/concerns-beyond-accuracy-of-ai-output/)
- [Helping Developers Adopt Gen AI: Four Practical Strategies](https://dora.dev/insights/adopt-gen-ai/)
- [How to Craft an Acceptable Use Policy for Gen AI（Google Cloud）](https://cloud.google.com/transform/how-to-craft-an-acceptable-use-policy-for-gen-ai-and-look-smart-doing-it)
- [DORA Quick Check](https://dora.dev/quickcheck/)
- [DORA AI Capabilities Model](https://dora.dev/ai/#explore-the-model)

---

*作成: 2026年4月 / 性質: 外部文献の日本語整理（reference）*
