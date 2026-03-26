# AI時代における開発生産性指標の変容（2024-2026）

Four Keys（DORAメトリクス）単独では開発生産性を捉えきれなくなりつつある。AIコーディングツールの普及により、従来の指標の前提が崩れ、複合的なフレームワークへの移行が進んでいる。

---

## 1. Four Keysが機能しなくなっている理由

### AI生産性パラドックス

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

### DORA 2024レポートのAI関連所見

39,000人以上の回答者データから：

- **採用率**: 75.9%が業務でAIを利用（コード記述、情報要約、コード説明、最適化、ドキュメント作成）
- **主観的認識**: 75%が生産性向上を感じている
- **客観的データ**: デリバリースループット推定1.5%低下、デリバリー安定性推定7.2%低下
- **2年連続**でAIツーリングがデリバリーパフォーマンスの悪化と相関

根本原因：AI使用時にバッチサイズ（変更セット）が大きくなる傾向がある。DORAのデータは一貫して大きな変更セットがリスクを導入することを示している。

出典: [DORA 2024 Report](https://dora.dev/research/2024/dora-report/), [InfoQ](https://www.infoq.com/news/2024/11/2024-dora-report/), [DX分析](https://getdx.com/blog/2024-dora-report/)

### DORA 2025レポートの変革

2025年レポートはAI支援ソフトウェア開発に特化し、根本的に進化した。

**主要な変更点：**
- **第5の指標「Rework Rate」** を正式導入
- **MTTRを「Failed Deployment Recovery Time」に再定義**（安定性→スループットに移動）
- **Low/Medium/High/Eliteの分類を廃止** → **7つの組織アーキタイプ**に置換

**7つの組織アーキタイプの例：**
- Legacy Bottleneck（レガシーボトルネック）
- Pragmatic Performers（実用主義的パフォーマー）
- Harmonious High-Achievers（調和的ハイアチーバー）等

**中心的発見：「AIはチームを修正しない。既にあるものを増幅する」**

高パフォーマンスチームはAIでさらに良くなり、問題を抱えるチームはAIによって問題が顕在化・悪化する。

**7つの基盤的能力：**
1. 明確な組織のAI姿勢
2. 健全なデータエコシステム
3. AIアクセス可能な内部データ
4. 強力なバージョン管理
5. 小バッチ規律
6. ユーザー中心主義
7. 高品質な内部プラットフォーム

出典: [Google Cloud 2025 DORA Report](https://cloud.google.com/resources/content/2025-dora-ai-assisted-software-development-report), [DORA 2025](https://dora.dev/research/2025/dora-report/), [InfoQ](https://www.infoq.com/news/2026/03/ai-dora-report/), [Scrum.org](https://www.scrum.org/resources/blog/dora-report-2025-summary-state-ai-assisted-software-development)

### 各指標が意味を失うメカニズム

| 指標 | 問題 |
|------|------|
| デプロイ頻度 | AIで頻度が上がっても品質が伴わない。量＝進歩ではない |
| リードタイム | AIはコーディングを加速するがレビュー・テスト・承認には影響しない。ステージ分解しないとボトルネックが見えない |
| 変更失敗率 | Rework Rateと併せないとデプロイ量増加に伴う絶対数増加を見逃す |

出典: [Plandek - DORA Metrics in the Age of AI 2026](https://plandek.com/blog/how-to-measure-dora-metrics-in-the-age-of-ai-2026/)

### 帰属の不可視性問題

- DORAもSPACEもAI生成コードと人間のコードを区別できない（現在、開発者のコードの約41%がAI生成）
- AI支援PRはレビュー通過後もインシデント率が高いが、従来指標では検出不能
- 複数ツール（Cursor、Claude Code、Copilot等）の同時使用への統合的可視性が欠如

出典: [Exceeds AI](https://blog.exceeds.ai/dora-metrics-vs-modern-productivity/)

### 隠れた検証コスト

- AIはコード生成を高速化するが、節約時間は**監査と検証に再配分**されている
- 開発者の30%がAI生成コードへの信頼度が低い〜ゼロと回答
- エンジニアはすべてのAI生成コードを「潜在的に誤りがある」として扱う必要がある

出典: [DORA - Balancing AI Tensions](https://dora.dev/insights/balancing-ai-tensions/)

### METR研究の発見

2025年7月のMETR研究では、経験豊富なOSS開発者がAIツールを使用するとタスク完了に**19%長くかかる**という結果が出た。開発者自身の認識（速くなったはず）に反する。

2026年2月のアップデートでは選択バイアス等の問題が判明し実験デザインを変更中。

出典: [METR 2025](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/), [METR 2026 Update](https://metr.org/blog/2026-02-24-uplift-update/)

---

## 2. 複合フレームワークへの移行

### DX Core 4

DORAの著者Nicole Forsgren、SPACEの著者Margaret-Anne StoreyとThomas Zimmermanらがアドバイザーとして参加。Laura Tacho（DX CTO）とAbi Noda（DX CEO）が開発した統合フレームワーク。

**4つの次元：**

| 次元 | 説明 |
|------|------|
| **Speed（速度）** | チームがどれだけ迅速にソフトウェアを提供するか |
| **Effectiveness（有効性）** | 価値を生む活動に時間が使われているか |
| **Quality（品質）** | 成果物の信頼性と安定性 |
| **Business Impact（ビジネスインパクト）** | 達成された組織的成果 |

**設計原則：**
- 多次元アプローチ（速度のために品質を犠牲にする等のトレードオフを防止）
- 組織全体への適用性（経営層〜フロントラインチーム）
- 迅速な展開（数週間でセットアップ可能）

**実績：** 300以上の組織でテスト・改善。エンジニアリング効率3-12%向上、機能開発R&D時間14%増加。

出典: [DX Core 4 Research](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/), [LeadDev](https://leaddev.com/reporting/dx-core-4-aims-to-unify-developer-productivity-frameworks), [InfoQ](https://www.infoq.com/news/2025/01/dx-core-4-framework/)

### GAINS Framework（Faros AI）

AI生産性を10次元で測定するフレームワーク：

| 次元 | 説明 |
|------|------|
| Adoption | AIツールの普及と一貫性 |
| Usage | 日常業務へのAIの埋め込み頻度と深さ |
| Change Management | ハイブリッド人間-エージェント体制への組織準備度 |
| Velocity | AIによるスループット加速 |
| Quality | コード保守性と欠陥率へのAI影響 |
| Security | ガバナンス・コンプライアンス・リスク管理 |
| Flow | ハンドオフ・アイドル時間・コンテキスト切替の削減 |
| Satisfaction | 開発者のAIツールへの信頼・自信 |
| Onboarding | 新開発者とAIシステムの生産性到達時間 |
| Organizational Efficiency | スケールされたAI影響を支える組織構造 |

出典: [Faros AI](https://www.faros.ai/blog/ai-productivity-metrics)

### Nicole ForsgrenのDevEx 3要素

Forsgren自身が「ほとんどの生産性指標は嘘だ」と述べ、以下を中心に据えるべきと主張：

1. **フィードバックループ** - 作業の質とインパクトに関する迅速で実用的な情報
2. **認知負荷** - より良いツールと明確なプロセスによるメンタル負担の軽減
3. **フロー状態** - 深い集中を妨げない環境の構築

AIがコーディングを加速しても、壊れたプロセスや摩擦ポイントのため、開発者は比例的な速度向上を経験していない。

出典: [Lenny's Newsletter - Nicole Forsgren](https://www.lennysnewsletter.com/p/how-to-measure-ai-developer-productivity)

---

## 3. フレームワーク比較

| 観点 | DORA Four Keys | SPACE | DX Core 4 | GAINS |
|------|---------------|-------|-----------|-------|
| 登場年 | 2014 | 2021 | 2024 | 2025 |
| 焦点 | デリバリーパイプライン | 開発者の生産性全般 | デリバリー+体験+ビジネス成果 | AI固有の生産性 |
| AI対応 | 2025年に拡張 | 原則は有効だが適応が必要 | AI時代を前提に設計 | AI専用 |
| 測定レベル | チーム/組織 | 個人〜組織 | チーム〜組織 | 個人〜組織 |
| ベンチマーク | あり（→7アーキタイプに移行） | なし | あり | あり |
| 研究基盤 | 10年の実証研究 | 文献レビュー+実務 | DORA+SPACE統合 | 実務データ |

---

## 4. 業界ソートリーダーの見解

### Nicole Forsgren（Google シニアディレクター、DORA/SPACE共同著者）
- 「ほとんどの生産性指標は嘘」
- 新著『Frictionless』でAI時代にチームがより速く動くための実践ガイドを発表予定
- DevExの3要素（フィードバックループ、認知負荷、フロー状態）を重視すべき

出典: [Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-to-measure-ai-developer-productivity)

### Abi Noda（DX CEO）
- 「AIは悪いプラクティスをさらに悪化させる」
- 採用指標だけでは不十分。個人・チーム・プロダクト・組織のより良い成果にAIが寄与しているかを包括的に測定すべき
- DXのデータ: AIを毎日使うエンジニアはオンボーディングのマイルストーンを非使用者のほぼ2倍の速度で達成

出典: [DX Blog - 2025 DORA分析](https://getdx.com/blog/ai-amplifies-bad-practices-real-gains-come-from-focusing-aiefforts-on-systems-and-success-depends-on-strong-change-management/)

### Gergely Orosz（Pragmatic Engineer）
- 2023年にKent Beckと共にMcKinseyの開発者生産性測定論に対する詳細な反論を発表
- DXのLaura Tachoと共同で180社以上のデータからAIの実際の影響を分析

出典: [Pragmatic Engineer](https://newsletter.pragmaticengineer.com/p/measuring-developer-productivity)

### Margaret-Anne Storey（University of Victoria教授、DX Chief Scientist）
- CHASE 2025で「AIがソフトウェア開発の生産性に果たす役割の理解」について基調講演
- 「Vibe Coding」の質的理論を提唱 — AIとの会話的インタラクション、共同創造、フローと喜びを中心に据える
- AIへの信頼が委任と共同創造の連続体に沿った動きを調整する

出典: [Margaret-Anne Storey Talks](https://margaretstorey.com/talks/), [ResearchGate](https://www.researchgate.net/publication/388484354_Software_Engineering_by_and_for_Humans_in_an_AI_Era)

### McKinsey論争（2023-2024）の影響
McKinseyが2023年8月に「開発者生産性は測定できる」と主張。Kent Beck、Gergely Orosz、Dan Northらが反発。

主な批判：
- 生産性の過度な単純化（コーディングとテストに偏重）
- 個人の貢献測定は「エンジンの中のピストン1つの貢献を測るようなもの」
- 個人パフォーマンス指標の過度な強調 → ゲーミング行動・サイロ化・心理的安全性の低下

出典: [Pragmatic Engineer](https://newsletter.pragmaticengineer.com/p/measuring-developer-productivity), [DX](https://getdx.com/blog/mckinsey-developer-productivity/), [Dan North](https://dannorth.net/blog/mckinsey-review/)

---

## 5. AIツール採用の実態データ（2025年）

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

### 企業の実践例（DX調査、18社）

| 企業 | AI影響の測定方法 |
|------|----------------|
| Dropbox | AIを定期的に使用するエンジニアはPR出荷量+20%、変更失敗率も低下 |
| Webflow | 在籍3年以上のエンジニアがAIの恩恵を最も受け、スループット約+20% |
| Microsoft | 「Bad Developer Days」を追跡し、摩擦の削減を測定 |
| Glassdoor | 月次A/Bテスト数をイノベーション指標として使用 |
| Shopify | リーダーボードで実験を称賛 |

出典: [DX - How 18 Companies Measure AI Impact](https://getdx.com/blog/how-top-companies-measure-ai-impact-in-engineering/)

---

## 6. 「AIエンジニアリングのムダ」（Thoughtworks）

Chris Westerhold（Global Practice Director）が特定した新しい非効率：

- **プロンプト-応答のレイテンシ**によるワークフロー中断
- **コンテキスト喪失**による問題の再説明
- **断片化されたツールチェーン**による認知負荷増大
- **AI生成コードの検証オーバーヘッド**

「エンジニアの本当の価値はもはやコードを書くことだけにあるのではなく、プロンプトエンジニアリング、ソリューションアーキテクチャ、AI生成出力の検証にある」

出典: [Thoughtworks - 2025 DORA Report Perspective](https://www.thoughtworks.com/insights/articles/the-dora-report-2025--a-thoughtworks-perspective)

---

## 7. まとめ：主要なシフト

| 観点 | 従来（〜2023） | 現在（2025-2026） |
|------|--------------|-------------------|
| 指標フレームワーク | DORA Four Keys単独 | DX Core 4 / GAINS等の複合フレームワーク |
| 測定対象 | デプロイメントパイプライン | 開発者体験 + デリバリー + ビジネス成果 |
| 分類 | Low/Med/High/Elite | 7つの組織アーキタイプ |
| AI観 | 生産性向上ツール | 「増幅装置」（良い面も悪い面も拡大） |
| 重視する指標 | 速度（デプロイ頻度） | 安定性 + Rework Rate |
| 個人 vs 組織 | 個人のアウトプット | システムレベルのボトルネック解消 |
| 「生産性」の意味 | アウトプット量 | 認知負荷・フロー・満足度を含む多面的概念 |

---

## 参照・出典一覧

### DORAレポート
- [DORA 2024 Report](https://dora.dev/research/2024/dora-report/)
- [DORA 2025 Report](https://dora.dev/research/2025/dora-report/)
- [Google Cloud 2025 DORA AI Report](https://cloud.google.com/resources/content/2025-dora-ai-assisted-software-development-report)
- [DORA - Balancing AI Tensions](https://dora.dev/insights/balancing-ai-tensions/)

### フレームワーク
- [DX Core 4 Research](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/)
- [SPACE - Microsoft Research](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/)
- [Faros AI - GAINS Framework](https://www.faros.ai/blog/ai-productivity-metrics)

### 分析・レポート
- [Faros AI - DORA 2025 Key Takeaways](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025)
- [Plandek - DORA in the Age of AI 2026](https://plandek.com/blog/how-to-measure-dora-metrics-in-the-age-of-ai-2026/)
- [Exceeds AI - DORA vs Modern Metrics](https://blog.exceeds.ai/dora-metrics-vs-modern-productivity/)
- [InfoQ - 2024 DORA Report](https://www.infoq.com/news/2024/11/2024-dora-report/)
- [InfoQ - AI DORA Report 2025](https://www.infoq.com/news/2026/03/ai-dora-report/)
- [Jellyfish - 2025 AI Metrics](https://jellyfish.co/blog/2025-ai-metrics-in-review/)
- [Cortex - State of AI Benchmark 2026](https://www.cortex.io/post/ai-is-making-engineering-faster-but-not-better-state-of-ai-benchmark-2026)
- [DX - How 18 Companies Measure AI Impact](https://getdx.com/blog/how-top-companies-measure-ai-impact-in-engineering/)
- [Thoughtworks - 2025 DORA Perspective](https://www.thoughtworks.com/insights/articles/the-dora-report-2025--a-thoughtworks-perspective)
- [Scrum.org - DORA 2025 Summary](https://www.scrum.org/resources/blog/dora-report-2025-summary-state-ai-assisted-software-development)

### 研究
- [METR - AI Developer Study 2025](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/)
- [METR - Uplift Update 2026](https://metr.org/blog/2026-02-24-uplift-update/)
- [ResearchGate - SE for Humans in AI Era](https://www.researchgate.net/publication/388484354_Software_Engineering_by_and_for_Humans_in_an_AI_Era)
- [STACK 2024 - SPACE in Age of AI](https://www.microsoft.com/en-us/research/video/stack-2024-space-in-the-age-ai-measuring-what-matters-for-developer/)

### ソートリーダー
- [Nicole Forsgren - AI Developer Productivity](https://www.lennysnewsletter.com/p/how-to-measure-ai-developer-productivity)
- [DX / Abi Noda - 2025 DORA Analysis](https://getdx.com/blog/ai-amplifies-bad-practices-real-gains-come-from-focusing-aiefforts-on-systems-and-success-depends-on-strong-change-management/)
- [Pragmatic Engineer - McKinsey Response](https://newsletter.pragmaticengineer.com/p/measuring-developer-productivity)
- [DX - McKinsey Developer Productivity](https://getdx.com/blog/mckinsey-developer-productivity/)
- [Dan North - McKinsey Review](https://dannorth.net/blog/mckinsey-review/)
- [Margaret-Anne Storey Talks](https://margaretstorey.com/talks/)
- [LeadDev - DX Core 4](https://leaddev.com/reporting/dx-core-4-aims-to-unify-developer-productivity-frameworks)
- [InfoQ - DX Core 4](https://www.infoq.com/news/2025/01/dx-core-4-framework/)
