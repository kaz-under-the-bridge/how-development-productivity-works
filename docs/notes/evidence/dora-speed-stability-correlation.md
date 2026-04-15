# DORAの実証: スピードと安定性は正の相関を示す

> 「DORAの10年の実証研究は繰り返しスピードと安定性は正の相関であることを示してきた」— この主張を支える証拠の集約。

> **親ドキュメント**: [AIハーネスによる開発生産性と安全性の統合](../ai-harness-productivity-safety.md) §1.2

---

## 1. 主張の概要

従来の通念では「速くデプロイすれば安定性が犠牲になる」と考えられていた。DORAの研究はこれを明確に否定し、**高パフォーマンスチームはスループット（速度）と安定性の両方で優れている**ことを繰り返し実証した。

> "DORA's research has repeatedly demonstrated that speed and stability are not tradeoffs."
> — [DORA Metrics Guide](https://dora.dev/guides/dora-metrics-four-keys/)

> "…the real trade-off, over long periods of time, is between _better software faster_ and _worse software slower._"
> — Dave Farley, 2021（DORAリサーチページにて引用）

---

## 2. エビデンス①: パフォーマンスクラスタ間の比較

### 2.1 4段階分類時代のベンチマーク（2018-2023）

DORAは2018年以降、クラスタ分析によりチームをElite / High / Medium / Lowに分類してきた。**Eliteチームは速度と安定性の両方で他を圧倒する**。

| 指標 | Elite | High | Medium | Low |
|------|-------|------|--------|-----|
| **デプロイ頻度** | オンデマンド（1日複数回） | 1日1回〜週1回 | 週1回〜月1回 | 月1回〜半年に1回 |
| **変更リードタイム** | 1時間未満 | 1日〜1週間 | 1週間〜1ヶ月 | 1ヶ月〜半年 |
| **変更失敗率** | 0-5% | 〜10% | 〜15% | 46-64% |
| **障害復旧時間** | 1時間未満 | 1日未満 | 1日〜1週間 | 1週間〜1ヶ月 |

出典: [Accelerate](../../research/accelerate.md), [2019 State of DevOps Report](https://dora.dev/research/2019/dora-report/2019-dora-accelerate-state-of-devops-report.pdf), [Google Cloud Blog](https://cloud.google.com/blog/products/devops-sre/using-the-four-keys-to-measure-your-devops-performance)

**注目すべきパターン**: Eliteチームはデプロイ頻度がLowの**208倍**であるにもかかわらず、変更失敗率はLowの**約1/7〜1/13**である。「速いから壊れる」のではなく、「速いチームほど壊れにくい」。

### 2.2 2025年のベンチマーク（5指標時代）

2025年レポートでは4段階分類が廃止されたが、上位パフォーマーの水準は一貫している。

| 指標 | 上位15%（Elite相当） | 上位15-30%（High相当） |
|------|---------------------|---------------------|
| **変更リードタイム** | 1日未満（回答者の15%） | 1週間未満（31.9%） |
| **デプロイ頻度** | オンデマンド・複数回/日（16.2%） | 週1回以上（44.6%） |
| **障害復旧時間** | 1時間未満（21.3%） | 1日未満（35.3%） |
| **変更失敗率** | 0-4%（16.7%） | 8%未満（36.2%） |
| **Rework Rate** | 0-4%（12.8%） | — |

出典: [Multitudes - DORA Metrics Guide](https://www.multitudes.com/blog/dora-metrics)

---

## 3. エビデンス②: 年次レポートでの一貫した再現

DORAの知見が一時的な相関ではなく、繰り返し再現されてきた事実を年表で追跡する。

| 年 | 主要な発見（速度×安定性関連） | 出典 |
|----|--------------------------|------|
| **2014** | 4つのパフォーマンス指標を特定。High performerはスループットと安定性の両方で優位 | [DORA Research](https://dora.dev/research/) |
| **2015** | 「高パフォーマンスのIT組織は4指標すべてで競合を上回る」。スループットと安定性の二元モデルが安定 | [overview](../../research/dora-reports/overview.md) |
| **2016** | 品質統合と実験的開発がパフォーマンスを駆動。※この年にスループット-安定性の相関に例外的コホートが出現 | [overview](../../research/dora-reports/overview.md) |
| **2017** | 変革型リーダーシップが文化→パフォーマンスの因果経路を強化 | [overview](../../research/dora-reports/overview.md) |
| **2018** | Eliteクラスタを新設。EliteはHigh/Med/Lowを全指標で上回る。書籍Accelerateで因果モデルを体系化 | [Accelerate](../../research/accelerate.md) |
| **2019** | 「speed and stability are outcomes that enable each other」と明記。6年連続の再現 | [2019 Report](https://dora.dev/research/2019/) |
| **2020** | DevOpsトランスフォーメーションの組織ROIを実証 | [overview](../../research/dora-reports/overview.md) |
| **2021** | 高品質ドキュメンテーションが技術ケイパビリティの基盤。信頼性（Reliability）概念を導入 | [overview](../../research/dora-reports/overview.md) |
| **2022** | Eliteクラスタ消失（3クラスタのみ検出）。しかしクラスタ内でのスループット-安定性相関は維持。セキュリティ堅固なチームはバーンアウト1.4倍少なく、組織パフォーマンス1.6倍 | [overview](../../research/dora-reports/overview.md) |
| **2023** | 生成的文化→30%高い組織パフォーマンス。ユーザー中心主義→40%高いパフォーマンス | [overview](../../research/dora-reports/overview.md) |
| **2024** | Rework Rate追加（5指標化）。クラスタ内では速度-安定性相関を維持。ただしクラスタ間で一部の例外（§5参照） | [2024 Report](../../research/dora-reports/2024.md) |
| **2025** | 4段階分類を廃止し7アーキタイプへ。AI時代も「基盤が強いチームはAIでさらに良くなる」 | [2025 Report](../../research/dora-reports/2025.md) |

---

## 4. エビデンス③: 因果メカニズムの説明

相関だけでなく、**なぜ速度と安定性が共存するのか**を説明するメカニズム。

### 4.1 小バッチ → リスク低減 → 速い復旧

```
デプロイ頻度↑ → バッチサイズ↓ → 変更あたりのリスク↓ → 変更失敗率↓
                                                        ↓
                              障害発生時の影響範囲↓ → 復旧時間↓
```

DORAのデータは一貫して「大きな変更セットがリスクを導入する」ことを示している（[2024 Report](../../research/dora-reports/2024.md)）。逆に、小バッチで頻繁にデプロイすることは、1回あたりの変更範囲を小さくし、障害の局所化と高速な復旧を可能にする。

これは広木大地氏の「**頻度は質に転化する**」の理論的説明でもある（[広木大地](../../perspectives/hiroki-daichi.md)）。

### 4.2 フィードバックループの短縮

```
頻繁なデプロイ → 市場への早期曝露 → 迅速なフィードバック → 問題の早期発見
                                                            ↓
                                      修正コスト↓ → 安定性↑ → さらに頻繁なデプロイへ
```

不確実性を早く市場に曝露することで、フィードバックループが短くなり、問題を小さいうちに検出・修正できる。これは[制約理論（TOC）](../../foundations/toc-theory-of-constraints.md)のフロー原理と[リーンの小バッチ](../../foundations/lean-and-flow.md)の実証的裏付けである。

### 4.3 ケイパビリティの共通基盤

Accelerateが特定した[24のケイパビリティ](../../research/accelerate.md)は、スループットと安定性の**両方**を同時に駆動する。

| ケイパビリティ | スループットへの寄与 | 安定性への寄与 |
|-------------|-------------------|-------------|
| 継続的インテグレーション | マージ頻度の向上 | 統合問題の早期検出 |
| テスト自動化 | リリース承認の高速化 | リグレッションの防止 |
| トランクベース開発 | ブランチ統合の高速化 | マージコンフリクトの削減 |
| 疎結合アーキテクチャ | 独立デプロイの実現 | 障害の局所化 |
| セキュリティのシフトレフト | セキュリティ承認の高速化 | 脆弱性の事前排除 |
| 生成的文化（Westrum） | 情報共有の促進 | 障害時の協力的対応 |

**これらのケイパビリティはスループットと安定性のどちらか一方ではなく、両方を向上させる。** だからこそ、これらのケイパビリティを高めたチームはスピードと安定性の両方で優れた結果を出す。

### 4.4 構造方程式モデリング（SEM）による因果検証

Accelerateの研究は単なる相関分析ではなく、**構造方程式モデリング（SEM）**を用いて因果関係を統計的に検証している。

```
ケイパビリティ（24項目）
  → ソフトウェアデリバリーパフォーマンス（Four Keys）
    → 組織パフォーマンス（収益性、市場シェア、生産性）
      → 非商業的パフォーマンス（品質、顧客満足度）
```

出典: [Accelerate](../../research/accelerate.md)

この因果モデルは4年間（2014-2017）の独立サンプルで交差検証されており、年ごとに再現された。

---

## 5. ニュアンスと例外

### 5.1 変更失敗率の「異常」（2014年、2016年、2024年）

速度-安定性の正の相関は大筋で頑健だが、**変更失敗率（Change Failure Rate）は他の3指標と常に綺麗に相関するわけではない**。

- **2014年**: 初年度から変更失敗率は他の3指標と有意に相関しないことが判明
- **2016年**: スループット-安定性の相関に例外的コホートが出現
- **2024年**: Mediumクラスタの変更失敗率がHighクラスタより低いという逆転現象

> "Within all four clusters, throughput and stability are correlated. This correlation persists even in the medium performance cluster, where throughput is lower and stability is higher than in the high performance cluster."
> — [RedMonk DORA 2024分析](https://redmonk.com/rstephens/2024/11/26/dora2024/)

**解釈**: クラスタ**内**では相関が維持されるが、クラスタ**間**では単純な線形関係ではない。これが2025年に4段階分類を廃止し7アーキタイプに移行した理由の一つ。

### 5.2 Rework Rate導入の意味（2024年）

変更失敗率の「異常」への対処として、2024年にRework Rate（デプロイ再作業率）が第5の指標として追加された。

DORAチームは指標カテゴリも再編した:
- **スループット**: デプロイ頻度、変更リードタイム、障害復旧時間（← 安定性から移動）
- **不安定性**: 変更失敗率、Rework Rate（新規）

障害復旧時間を「安定性」から「スループット」に移動したのは、「速く復旧できる＝安定している」ではなく「速く復旧できる＝フロー回復のスループットが高い」という再解釈。

出典: [DORA 2025レポート](../../research/dora-reports/2025.md)

### 5.3 2022年のEliteクラスタ消失

2022年のレポートではクラスタ分析がEliteを検出せず、3クラスタ（High / Medium / Low）のみとなった。しかしこれはスピード-安定性の相関が崩れたのではなく、**Eliteに該当するチームが統計的に独立したクラスタを形成するほどの量がなかった**ことを意味する。

### 5.4 AI時代の新たな緊張（2024-2025）

2024年レポートでは**2年連続でAIツール採用がデリバリーパフォーマンス悪化と相関**した（スループット推定-1.5%、安定性推定-7.2%）。これは「スピードと安定性の正の相関」自体が崩れたのではなく、**AIがスループットを加速する一方で安定性を損ねる形で使われている**ことを示す。

2025年レポートの解釈:

> 「AIは組織を修正しない。既にあるものを増幅する」

**基盤（ケイパビリティ）が強いチームはAIでさらに良くなり**（スピード↑ + 安定性↑）、**基盤が弱いチームはAIで問題が顕在化する**（スピード↑ + 安定性↓↓）。

出典: [DORA 2025レポート](../../research/dora-reports/2025.md), [AI影響の実態データ](../../research/ai-impact-data.md)

---

## 6. メタ分析・外部検証

DORAの知見は内部研究だけでなく、外部の研究・分析でも支持されている。

| 出典 | 知見 |
|------|------|
| **ResearchGate メタ分析（2025）** | CI/CDパフォーマンスのメタ分析。成熟したDevOps採用はデプロイ頻度+45%、リードタイム-38%、変更失敗率-32%と関連 |
| **Dave Farley（2021）** | 「長期的な本当のトレードオフは、_better software faster_ と _worse software slower_ の間にある」 |
| **DORA成熟度と収益（2025）** | DORA成熟度の高い組織は収益目標を超過する可能性が2倍 |

出典: [ResearchGate](https://www.researchgate.net/publication/396361616_Redefining_Speed_and_Stability_A_Meta_Analysis_of_CICD_Performance_through_DORA_Metrics), [Multitudes](https://www.multitudes.com/blog/dora-metrics)

---

## 7. 要約: なぜ速いチームは安定しているのか

| # | メカニズム | 説明 |
|---|----------|------|
| 1 | **小バッチ効果** | 頻繁なデプロイ → バッチサイズ↓ → リスク↓ → 失敗率↓ → 復旧↑ |
| 2 | **フィードバック加速** | 頻繁な曝露 → 早期検出 → 修正コスト↓ |
| 3 | **ケイパビリティの共通基盤** | 同じプラクティス（CI、テスト自動化、疎結合等）がスピードと安定性の両方を駆動する |
| 4 | **文化の効果** | 生成的文化 → 情報共有↑ → スピード↑ & 障害対応↑ |
| 5 | **因果ではなく共通原因** | スピードと安定性は直接の因果関係ではなく、共通のケイパビリティ群に駆動される |

**「スピードか安全性か」は誤った二項対立である。正しい問いは「両方を駆動する基盤（ケイパビリティ）が整っているか」である。**

---

## 出典一覧

### 一次ソース
- [DORA Research](https://dora.dev/research/) — 全年次レポートへの入口
- [DORA Metrics Guide](https://dora.dev/guides/dora-metrics-four-keys/) — 指標定義と速度-安定性の関係
- [2019 State of DevOps Report（PDF）](https://dora.dev/research/2019/dora-report/2019-dora-accelerate-state-of-devops-report.pdf) — 「speed and stability enable each other」の明記
- Forsgren, N., Humble, J., & Kim, G. (2018). *Accelerate*. IT Revolution Press. — SEM因果モデル、24ケイパビリティ

### 分析・二次ソース
- [RedMonk - DORA 2024: Throughput and Stability](https://redmonk.com/rstephens/2024/11/26/dora2024/) — 2024年の例外的コホート分析
- [Multitudes - DORA Metrics Guide](https://www.multitudes.com/blog/dora-metrics) — 2025年ベンチマークデータ
- [Octopus Deploy - Understanding DORA Metrics](https://octopus.com/devops/metrics/dora-metrics/) — 年次ベンチマーク推移
- [ResearchGate - Meta Analysis of CI/CD Performance through DORA Metrics](https://www.researchgate.net/publication/396361616_Redefining_Speed_and_Stability_A_Meta_Analysis_of_CICD_Performance_through_DORA_Metrics) — 外部メタ分析

### 本リポジトリ内
- [Accelerate書籍の知見](../../research/accelerate.md)
- [DORA年次レポート年表](../../research/dora-reports/overview.md)
- [DORA 2024レポート](../../research/dora-reports/2024.md)
- [DORA 2025レポート](../../research/dora-reports/2025.md)
- [広木大地 — 「頻度は質に転化する」](../../perspectives/hiroki-daichi.md)
- [制約理論（TOC）](../../foundations/toc-theory-of-constraints.md)
- [リーンとフロー](../../foundations/lean-and-flow.md)

---

*作成: 2026年4月 / 性質: ファクト集約（evidence）*
