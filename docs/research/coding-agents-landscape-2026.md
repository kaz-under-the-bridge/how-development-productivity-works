# コーディングエージェント最新動向（2025年10月〜2026年4月）

AIによるソフトウェア開発の自動化が「コード補完」から「自律的エージェント」へと転換した期間の包括的整理。

---

## 目次

1. [市場概況](#1-市場概況)
2. [主要プロダクトの進化](#2-主要プロダクトの進化)
3. [アーキテクチャ概念の整理](#3-アーキテクチャ概念の整理)
4. [ベンチマークと評価](#4-ベンチマークと評価)
5. [開発生産性への影響データ](#5-開発生産性への影響データ)
6. [セキュリティリスクと懸念](#6-セキュリティリスクと懸念)
7. [Vibe Codingからの発展](#7-vibe-codingからの発展)
8. [組織導入パターン](#8-組織導入パターン)
9. [標準化とエコシステム](#9-標準化とエコシステム)
10. [キーパーソンと知見](#10-キーパーソンと知見)
11. [考察：何が変わり、何が変わっていないか](#11-考察何が変わり何が変わっていないか)

---

## 1. 市場概況

### 市場規模

- AIコーディング市場は **約40億ドル（約6,300億円）** 規模に到達（2026年1月時点）
- 上位3社（Microsoft/GitHub、Anthropic、OpenAI）が **シェア7割** の寡占状態
- 2025年のエクイティ調達総額は約52億ドル（前年比2倍以上）

出典: [日本経済新聞 2026年1月](https://www.nikkei.com/article/DGXZQOUC194FE0Z10C26A1000000/)

### 採用率

| 指標 | 数値 | 出典 |
|------|------|------|
| AI利用開発者比率 | 92.6%（月1回以上） | [Panto AI](https://www.getpanto.ai/blog/ai-coding-productivity-statistics) |
| 週次以上の利用率 | 95% | [Pragmatic Engineer Survey](https://newsletter.pragmaticengineer.com/p/ai-tooling-2026) |
| 業務の50%以上にAI利用 | 75% | 同上 |
| AIエージェント定常利用者 | 55% | 同上 |
| AI生成コード比率 | 26.9〜50%（測定方法により異なる） | 複数ソース |

### ツール人気ランキング（2026年3月時点）

Pragmatic Engineer調査（Gergely Orosz）より:

| 順位 | ツール | 支持率 |
|------|--------|--------|
| 1 | Claude Code | 46% |
| 2 | Cursor | 19% |
| 3 | GitHub Copilot | 9% |

> Claude Codeは2025年5月のリリースからわずか8ヶ月で最も使われるAIコーディングツールとなった。

出典: [AI Tooling for Software Engineers in 2026](https://newsletter.pragmaticengineer.com/p/ai-tooling-2026)

---

## 2. 主要プロダクトの進化

### 2.1 Claude Code（Anthropic）

**ポジション**: 市場リーダー（2026年3月時点で支持率1位）

**主要機能（2025年10月〜2026年4月）**:

- **バックグラウンドエージェント**（v2.0.60〜）: メインの会話を続けながら、別のエージェントをバックグラウンドで実行可能。完了時に自動で結果を返す
- **Git Worktree連携**（`claude --worktree`）: 各バックグラウンドエージェントが独立したコードコピーで動作し、相互干渉を防止
- **サブエージェント**: フォアグラウンド（ブロッキング）とバックグラウンド（並行）の2モードで実行可能
- **KAIROS**: 常時稼働バックグラウンドエージェント。ユーザーがアイドル中にメモリの統合・整理（autoDream）を自律的に実行
- **/loopコマンド**: スケジュールタスクの定期実行
- **Computer Use**: コンピュータ操作の直接制御

出典: [Claude Code Changelog](https://claudefa.st/blog/guide/changelog), [Claude Code Async](https://claudefa.st/blog/guide/agents/async-workflows)

### 2.2 GitHub Copilot（Microsoft/GitHub）

**主要機能（2025年10月〜2026年4月）**:

- **Agent Mode**（GA: 2026年3月）: VS CodeとJetBrains IDEの両方で利用可能。複数ファイルの横断編集、ターミナルコマンドの実行、エラーの自動反復修正を自律的に実行
- **Coding Agent（自律エージェント）**: GitHubのIssueをCopilotに割り当てると、バックグラウンドでコードを書き、テストを実行し、PRを自動作成
- **Agentic Code Review**（2026年3月〜）: プロジェクト全体のコンテキストを収集してからレビュー提案を行い、修正PRの自動生成まで実行
- **Skills**: ワークフロー別のカスタマイズ、スキル固有のコンテキスト読み込み

出典: [GitHub Newsroom](https://github.com/newsroom/press-releases/agent-mode), [GitHub Docs](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent)

### 2.3 Cursor

**主要機能（2025年10月〜2026年4月）**:

- **Composer 2**: フロンティアレベルのコーディング性能。コードベース全体のセマンティック検索で訓練。同等モデル比4倍高速
- **クラウドエージェント**: エージェントが独自のコンピュータでビルド、テスト、デモまでを実行
- **マルチエージェント並行実行**: 同一プロジェクトで複数エージェントが並行作業（リファクタリング、テスト修正、UIポリッシュなど）
- **Automations**: Slack、Linear、GitHub、PagerDuty等のイベントをトリガーとした自動エージェント実行。クラウドサンドボックスで起動
- **セルフホスト型クラウドエージェント**: コードとツール実行を自社ネットワーク内に保持
- **リアルタイム強化学習**: ユーザーインタラクションからの学習で5時間ごとに改善チェックポイントをデプロイ

出典: [Cursor Changelog](https://cursor.com/changelog), [Cursor March 2026 Updates](https://theagencyjournal.com/cursors-march-2026-glow-up-self-hosted-agents-jetbrains-love-and-smarter-composer/)

### 2.4 Devin（Cognition）

**主要機能（2025年10月〜2026年4月）**:

- **エンドツーエンドテスト**: Computer Useでデスクトップアプリのテストを自動実行。テスト結果の録画をレビュー用に送信
- **Fast Mode**: 同等の知能で約2倍高速（4x ACU/セッション）
- **Devin Wiki**: コードベースのドキュメントを自動生成（アーキテクチャ概要、主要ファイル説明、依存関係マップ）
- **Windsurf（旧Codeium）買収**: 2025年12月に約2.5億ドルでWindsurfを買収。Devinの自律機能とWindsurf IDEの統合を計画
- **実績**: マイグレーション作業で12倍の効率改善、20倍以上のコスト削減を実現した事例あり

出典: [Devin Docs](https://docs.devin.ai/release-notes/overview), [Cognition](https://cognition.ai/)

### 2.5 OpenAI Codex

**主要機能（2025年10月〜2026年4月）**:

- **GPT-5.3-Codex**（2026年2月）: 作業中のモデルとリアルタイムで対話可能（コンテキストを失わずに方向修正が可能）
- **GPT-5.4**（2026年3月5日）: Codexのメインモデルとして搭載
- **GPT-5.4 mini**（2026年3月17日）: アプリ、CLI、IDE、Webの全プラットフォームで利用可能。GPT-5.4の30%のクォータで動作
- **Codex App**: 複数エージェント、並列ワークフロー、長時間タスク管理のコマンドセンター。Windows対応
- **Plugins**: プロダクトスコープのプラグインを起動時に同期
- **Codex Security**: コンテキスト対応のアプリケーションセキュリティレビュー（リサーチプレビュー）

出典: [OpenAI Codex](https://openai.com/codex/), [OpenAI Blog](https://openai.com/index/introducing-gpt-5-3-codex/)

### 2.6 Amazon Q Developer

**主要機能**:

- **/doc**: コードベースのドキュメント自動生成
- **/review**: セキュリティ・コード品質の問題検出と解決
- **/test**: 単体テストの自動生成とカバレッジ向上
- **Transformation Agent**: Java 8→Java 21、Spring Boot 3.xへの自動アップグレード。ビルド、依存関係更新、コード書き換え、テスト実行、PR作成まで自律実行
- 料金: $19/ユーザー/月（Individual tierは無料だが高度な機能に月次上限あり）

出典: [AWS Blog](https://aws.amazon.com/blogs/aws/new-amazon-q-developer-agent-capabilities-include-generating-documentation-code-reviews-and-unit-tests/)

### 2.7 Google Jules / Gemini Code Assist

**Jules**:
- パブリックベータ（ウェイトリストなし）で一般利用可能
- Gemini 2.5 Proを搭載
- GitHubリポジトリをGoogle Cloud VMにクローンし、フルコンテキストで変更を実行
- プライベートバイデフォルト（コードで学習しない）

**Gemini Code Assist Agent Mode**:
- VS CodeとJetBrains IDEで利用可能
- MCPサーバー設定対応

出典: [Jules](https://jules.google), [Gemini Code Assist Docs](https://developers.google.com/gemini-code-assist/docs/agent-mode)

### 2.8 Windsurf（旧Codeium）

- **Cascade**: エージェンティックAIアシスタント。コードベース全体の理解、マルチファイル変更、ターミナルコマンド実行、エラー自動修正、セッション間のプリファレンス記憶
- **バックグラウンドプランニング**: 専門のプランニングエージェントが長期計画を継続的に最適化し、選択モデルが短期アクションを実行
- **2025年12月にCognition AI（Devinの開発元）に約2.5億ドルで買収**

出典: [Windsurf](https://windsurf.com/cascade)

### 2.9 Augment Code

- **Intent Desktop App**: スペック駆動開発のためのマルチエージェントオーケストレーション。複数エージェントを「living spec」で整合
- **Context Engine**: セマンティック検索で大規模コードベースの理解を向上
- **MCP対応**: 他のAIコーディングエージェントへのContext Engine能力の提供
- **ベンチマーク**: Claude Code、Cursor、Codexとの組み合わせで70%以上のコーディング性能改善

出典: [Augment Code](https://www.augmentcode.com/), [VentureBeat](https://venturebeat.com/ai/augment-code-debuts-ai-agent-with-70-win-rate-over-github-copilot-and-record-breaking-swe-bench-score)

### 2.10 JetBrains Central（2026年3月24日発表）

- エージェンティックソフトウェア開発のためのオープンシステム
- ツール、エージェント、インフラストラクチャを接続するレイヤードシステム
- ガバナンス機能: ポリシー適用、セキュリティ制御、監査、コスト管理
- JetBrains IDE、サードパーティIDE、CLI、Web、インテグレーションからエージェントワークフローを管理
- EAP: 2026年Q2開始予定

出典: [JetBrains Blog](https://blog.jetbrains.com/blog/2026/03/24/introducing-jetbrains-central-an-open-system-for-agentic-software-development/)

---

## 3. アーキテクチャ概念の整理

### 3.1 Agent = Model + Harness

2026年のキーコンセプト。「2025年はエージェントの年。2026年はハーネスの年」と言われる。

| 構成要素 | 役割 |
|----------|------|
| **Model** | 要件理解、推論、コード生成 |
| **Harness** | 環境認識、ツールオーケストレーション、エラー回復、安全制約、セッション永続化 |

> モデルが従来のマルチエージェントフレームワークの約80%の機能を吸収。残り20%（永続化、決定論的リプレイ、コスト制御、可観測性、エラー回復）がHarnessの領域。

出典: [NxCode - What Is Harness Engineering](https://www.nxcode.io/resources/news/what-is-harness-engineering-complete-guide-2026), [BSWEN](https://docs.bswen.com/blog/2026-03-25-ai-agent-harness-explained/)

### 3.2 Context Engineering（コンテキストエンジニアリング）

プロンプトエンジニアリングの後継概念。「何を聞くか（how）」ではなく「何をコンテキストに含めるか（what）」に焦点。

**主要パターン**:
- **Progressive Disclosure**: 何をいつロードするかの制御
- **Compression**: 蓄積された履歴の圧縮
- **Routing**: クエリを適切なソースに誘導
- **Evolved Retrieval**: 外部知識のオンデマンド取得
- **Tool Management**: 能力サーフェスの制御

> Anthropicの研究によると、エージェントのツール数が10〜15を超えるとパフォーマンスが大幅に低下する。

出典: [Anthropic - Effective Context Engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents), [Martin Fowler](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)

### 3.3 マルチエージェントアーキテクチャ

**3つの役割モデル**:

| 役割 | 責務 |
|------|------|
| **Planner** | コードベースを探索しタスクを作成 |
| **Worker** | 割り当てられたタスクを独立実行、完了時にpush |
| **Judge** | 各サイクル終了時に継続/停止を判断 |

**3層オペレーションモデル（Addy Osmani）**:

| Tier | 説明 | 用途 |
|------|------|------|
| Tier 1 | プロセス内サブエージェント（ローカル、同期） | インタラクティブ作業 |
| Tier 2 | ローカルオーケストレーター（3-10エージェント） | 並列スプリント |
| Tier 3 | クラウド非同期エージェント | 夜間バッチ処理 |

出典: [Addy Osmani - The Code Agent Orchestra](https://addyosmani.com/blog/code-agent-orchestra/), [Mike Mason](https://mikemason.ca/writing/ai-coding-agents-jan-2026/)

### 3.4 Agentic Workflow vs. 単純コード補完

| 特性 | コード補完 | Agenticワークフロー |
|------|----------|-------------------|
| スコープ | 1行〜数行 | プロジェクト全体 |
| 自律性 | なし | 計画→実行→テスト→反復 |
| 実行時間 | ミリ秒 | 分〜時間〜日 |
| コンテキスト | 現在のファイル | リポジトリ全体+外部ツール |
| 人間の介入 | 毎行 | チェックポイントのみ |

### 3.5 Spec-Driven Development（SDD）

AIにコードを書かせる前に仕様書を中心に据える開発手法。

- 構造化された仕様がエージェントの出力を制御
- アドホックなプロンプトを排除
- Augment Codeの「living spec」が代表例

---

## 4. ベンチマークと評価

### 4.1 SWE-bench Verified（2026年3月時点）

| 順位 | モデル | スコア |
|------|--------|--------|
| 1 | Claude Opus 4.5 | 80.9% |
| 2 | Claude Opus 4.6 | 80.8% |
| 3 | Gemini 3.1 Pro | 80.6% |
| 4 | MiniMax M2.5 | 80.2% |
| 5 | GPT-5.2 | 80.0% |

> 2025年初頭の約65%から2026年3月の80.9%へ大幅に向上。

出典: [SWE-bench Leaderboards](https://www.swebench.com/), [Simon Willison](https://simonwillison.net/2026/Feb/19/swe-bench/)

### 4.2 SWE-bench Pro

| モデル | スコア |
|--------|--------|
| GPT-5.3-Codex | 56.8% |
| GPT-5.2-Codex | 56.4% |
| GPT-5.2 | 55.6% |

> SWE-bench ProはスキャフォルドによりスコアがVeriifedとは大きく異なる。Scale AIのSEALリーダーボードでは標準化スキャフォルドでClaude Opus 4.5が45.9%でリード。

**重要な知見**: 「SWE-Bench Proで46%が81%に勝る理由」 -- ベンチマークのスコアとスキャフォルド（ハーネス）の質は分離して評価すべき。

出典: [SWE-Bench Pro](https://www.morphllm.com/swe-bench-pro), [Scale Labs](https://labs.scale.com/leaderboard/swe_bench_pro_public)

### 4.3 SWE-bench の進化

- **SWE-bench-Live/Windows**（2026年2月）: Windows PowerShell環境でのアクションとWindows固有の実装をテスト
- 500タスクが独立したDockerコンテナ内で実行
- 各タスクは実際のGitHub Issueを代表

### 4.4 ベンチマークの限界

- スキャフォルド（ハーネス）の違いにより同一モデルでもスコアが大幅に変動
- 実世界のパフォーマンスとベンチマーク結果のギャップが存在
- ETH Zurichの研究: AGENTS.mdファイルがエージェントのパフォーマンスを**むしろ阻害**する場合があると報告

---

## 5. 開発生産性への影響データ

### 5.1 METR研究（最重要研究）

**2025年初期調査（RCT）**:
- 16人の経験豊富なOSS開発者、246タスクで実験
- **AI利用群はタスク完了時間が19%増加（遅くなった）**
- 開発者はAIによる24%の速度向上を予想していたが、実際には19%遅延
- 遅延を経験した後も「20%速くなった」と感じ続けた

**2026年2月 実験デザイン変更**:
- **選択バイアス問題**: 30〜50%の開発者がAIなしでやりたくないタスクの提出を拒否
- **リクルート崩壊**: 多くの開発者が$50/時でもAIなしの参加を拒否
- 参加者コメント: 「AIなら2時間で終わるのに20時間かかるIssueは避ける」
- METR自身が「現在のAIは2025年初期より速度向上をもたらしている可能性が高い」と認める

出典: [METR Blog 2025](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/), [METR Blog 2026](https://metr.org/blog/2026-02-24-uplift-update/)

### 5.2 生産性パラドックス

| 観点 | 数値 |
|------|------|
| 開発者の主観的速度向上 | 20% |
| 実際の速度変化（METR） | -19%（遅延） |
| コード品質への影響 | 約1.7倍のメジャーイシュー |
| セキュリティ脆弱性 | 23.7%増加 |
| 週あたりの時間節約 | 約3.6時間 |

> 93%の開発者がAIを使用。だが生産性向上はわずか10%。

出典: [ShiftMag](https://shiftmag.dev/this-cto-says-93-of-developers-use-ai-but-productivity-is-still-10-8013/), [Panto AI](https://www.getpanto.ai/blog/ai-coding-productivity-statistics)

### 5.3 タスクレベル vs. 組織レベル

| レベル | 効果 |
|--------|------|
| スコープされたタスク | 30〜55%の速度改善（一貫して観測） |
| 組織全体のデリバリー | プロセスボトルネック（レビュー、QA、セキュリティ、統合）の解消が必要 |

**NTTドコモビジネスの知見**（小倉真人氏）:
> 「AIツール導入でソフトウェアデリバリースループットとプロダクトパフォーマンスは向上するが、安定性は低下する傾向がある。AIは偉大な増幅器であり、使いこなせる組織とそうでない組織で大きな差が生まれる。」

出典: [NTT Com Speaker Deck](https://speakerdeck.com/nttcom/foundations-and-latest-trends-in-agentic-coding)

---

## 6. セキュリティリスクと懸念

### 6.1 新しい脅威サーフェス

従来のDevSecOpsは「ビルドパイプライン内の意思決定者はプロセスに従うエンジニア」という前提で構築されていた。コーディングエージェントの導入により前提が崩れる。

**主要リスクベクトル**:

| リスク | 詳細 |
|--------|------|
| プロンプトインジェクション | エージェントの行動を悪意のあるプロンプトで操作 |
| ツールチェーンポイズニング | エージェントフレームワークのコンポーネント汚染（43件の脆弱コンポーネント発見） |
| 幻覚依存関係 | 存在しないパッケージ名の生成→タイポスクワッティング攻撃の起点に |
| サプライチェーン攻撃 | エージェントが非推奨/脆弱パッケージを40%高い確率で提案（allowlist制約なし時） |
| 認証情報の横展開 | オーケストレーションエージェント妥協→下流全システムへのアクセス |

### 6.2 実際のインシデント

- **OpenAI Plugin Ecosystem攻撃**: 47のエンタープライズデプロイメントからエージェント認証情報が窃取。6ヶ月間未発見
- **OpenClaw悪意スキル事件**: AIエージェントインフラを標的とした最大規模のサプライチェーン攻撃。エコシステム内パッケージの約5分の1が悪意あるものと確認

出典: [Security Boulevard](https://securityboulevard.com/2026/03/coding-agents-widen-your-supply-chain-attack-surface/), [Dark Reading](https://www.darkreading.com/application-security/coders-adopt-ai-agents-security-pitfalls-lurk-2026)

### 6.3 品質への影響データ

CodeRabbitによる470のOSS PR分析（2025年12月）:

| 指標 | AI生成コード vs 人間のコード |
|------|----------------------------|
| メジャーイシュー | 1.7倍 |
| ロジックエラー | 上昇（不正確な依存関係、制御フロー欠陥） |
| 設定ミス | 75%増加 |
| セキュリティ脆弱性 | 2.74倍 |

---

## 7. Vibe Codingからの発展

### 7.1 経緯

- **2025年2月**: Andrej Karpathyが「Vibe Coding」を提唱。「コードの存在を忘れ、vibeに身を任せる」
- **2026年2月**: Karpathy自身が「Vibe Codingはもう古い」と宣言。代わりに **「Agentic Engineering」** を提唱

### 7.2 Vibe Coding vs Agentic Engineering

| 特性 | Vibe Coding | Agentic Engineering |
|------|------------|-------------------|
| 対象者 | 非プログラマー含む | プロフェッショナルエンジニア |
| 品質管理 | コードを読まない | 人間が監督・レビュー |
| 目的 | プロトタイプ、個人ツール | プロダクション品質のソフトウェア |
| AIの役割 | コード生成者 | 監督下の自律エージェント |

### 7.3 Vibe Codingの問題点

- **品質**: 95%の開発者が「生産的」と感じながら、測定上は低品質のコードを生産
- **OSS影響**: 論文「Vibe Coding Kills Open Source」（2026年1月）-- Vibe CodingがOSSメンテナーとのエンゲージメントを弱め、エコシステムの持続可能性を脅かすと主張
- **技術負債**: 短期的生産性は上がるが、長期的な技術負債が蓄積

出典: [Wikipedia - Vibe Coding](https://en.wikipedia.org/wiki/Vibe_coding), [The New Stack](https://thenewstack.io/vibe-coding-is-passe/), [Hashnode](https://hashnode.com/blog/state-of-vibe-coding-2026)

---

## 8. 組織導入パターン

### 8.1 Anthropic 2026 Agentic Coding Trends Report の8つのトレンド

1. **SDLCの地殻変動**: エンジニアがコーディングからエージェント監督・アーキテクチャ・レビューに移行
2. **エージェントがチームプレイヤーに**: 特化エージェントがオーケストレーター配下で並行作業
3. **エンドツーエンド化**: 数分のタスクから数時間〜数日のプロジェクトへ拡張
4. **助けを求めるタイミングを学習**: 不確実性を検知し、判断が必要な場面で人間に介入を要請
5. **ソフトウェアエンジニア以外への拡大**: COBOL、Fortranなどレガシー言語、セキュリティ・運用・デザイン・データ領域へ
6. **コード量増加、タイムライン短縮**: 週単位の作業が日単位に。ファンディング対象のアイデアが拡大
7. **非エンジニアのAgentic Coding参入**: 営業、法務、マーケ、オペレーションが自前ツール構築
8. **攻撃・防御の両面でスケール**: 深いコードレビューとセキュリティ強化を実現する一方、攻撃者の偵察・エクスプロイト開発のハードルも低下

出典: [Anthropic 2026 Agentic Coding Trends Report](https://resources.anthropic.com/2026-agentic-coding-trends-report)

### 8.2 導入の現状

| セグメント | 数値 |
|----------|------|
| AI導入を積極推進する組織 | 30〜40% |
| 利用許可するが推進しない組織 | 29〜49% |
| トップ四分位の企業のAIコード参加率 | 65% |
| 全体のAI生成/支援コード比率 | 41% |

### 8.3 役割の変化

- **エンジニアの役割**: コード記述→AIエージェントのポートフォリオ管理、コンポーネント・サービスのオーケストレーション
- **ジュニア開発者**: 一部組織で「AI Reliability Engineer（ARE）」にリブランド。AI出力の品質保証が主務
- **スタッフ+エンジニア**: エージェント採用率が最も高い（63.5%）

### 8.4 LangChain State of Agent Engineering 2026

- 1,300人以上の専門家を調査
- **57%がエージェントをプロダクション運用** （前年51%から増加）
- 品質が最大の障壁（32%が指摘）
- **89%が可観測性を導入**、52%が評価（evals）を導入
- 57%がモデルのファインチューニングなし（ベースモデル+プロンプトエンジニアリング+RAG）

出典: [LangChain State of Agent Engineering](https://www.langchain.com/state-of-agent-engineering)

---

## 9. 標準化とエコシステム

### 9.1 MCP（Model Context Protocol）

- 2024年11月: Anthropicが発表
- 2025年3月: OpenAIが公式採用
- 2025年12月: **Agentic AI Foundation（AAIF）に寄贈**。Linux Foundation傘下で、Anthropic、Block、OpenAIが共同設立
- 2026年: エンタープライズ対応に向けたロードマップ（トランスポートスケーラビリティ、エージェント間通信、ガバナンス成熟、エンタープライズレディネス）

出典: [MCP Wikipedia](https://en.wikipedia.org/wiki/Model_Context_Protocol), [MCP Roadmap 2026](http://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)

### 9.2 AGENTS.md

- コーディングエージェント向けのプロジェクトコンテキストファイル仕様
- Linux Foundation傘下のAgentic AI Foundationが管理
- 全主要AIコーディングエージェントがサポート
- **ETH Zurichの研究**: LLM生成のAGENTS.mdはむしろエージェント性能を阻害する可能性。人間が書いたものでも+4%の改善にとどまり、最小限かつ正確な記述が推奨

出典: [AGENTS.md](https://agents.md/), [InfoQ](https://www.infoq.com/news/2026/03/agents-context-file-value-review/)

### 9.3 A2A（Agent-to-Agent Protocol）

- エージェント間通信の標準化プロトコル（開発中）

---

## 10. キーパーソンと知見

### 10.1 Simon Willison -- 「Agentic Engineering Patterns」プロジェクト

2026年2月23日、Agentic Engineeringの実践パターンを体系的にドキュメント化するプロジェクトを開始。デザインパターンの書籍に着想を得た章構成。

**キー定義**: Agentic Engineeringとは「コーディングエージェントを使ってソフトウェアを開発する実践」。特徴は「コードの生成と実行の両方が可能」であること。

**コア原則**:
- 人間の責任は中心に残る。コード記述から問題定義へシフト
- 「LLMは過去の失敗から学ばないが、コーディングエージェントは意図的にinstructionsを更新すれば学べる」
- Vibe Codingの対極として位置づけ（プロフェッショナルの専門知識を増幅）

出典: [Simon Willison - Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/)

### 10.2 Andrej Karpathy

- 2025年2月: 「Vibe Coding」を提唱
- 2026年2月: 「Vibe Codingはもう古い。Agentic Engineeringが新標準」と宣言
- AI利用の進化段階を体現: 無秩序な利用→構造化されたプロフェッショナル実践

出典: [The New Stack](https://thenewstack.io/vibe-coding-is-passe/)

### 10.3 Gergely Orosz（Pragmatic Engineer）

2026年のAI Tooling調査で業界最大規模のサーベイを実施。Claude Codeの急成長、ツール多重利用（70%が2〜4ツール併用）、エージェンティックシフトの進行を定量的に示す。

出典: [AI Tooling for Software Engineers in 2026](https://newsletter.pragmaticengineer.com/p/ai-tooling-2026)

### 10.4 LangChain -- Agent Engineeringの定義

「非決定論的LLMシステムを信頼性のあるプロダクション体験に磨き上げる反復プロセス」と定義。3つのスキルセットを提唱:
1. **Product Thinking**: プロンプト設計、評価基準の設定
2. **Engineering**: ツール構築、ストリーミング、メモリ管理
3. **Data Science**: パフォーマンス測定、障害分析、体系的改善

出典: [LangChain - Agent Engineering: A New Discipline](https://blog.langchain.com/agent-engineering-a-new-discipline/)

### 10.5 Addy Osmani -- マルチエージェントオーケストレーション

「ボトルネックはコード生成から検証にシフトした」と指摘。曖昧な要件は数十の並列実行を通じて伝播し、それぞれが少しずつ間違える。強いエンジニアほど不釣り合いなレバレッジを得る。

出典: [Addy Osmani - The Code Agent Orchestra](https://addyosmani.com/blog/code-agent-orchestra/)

### 10.6 岩瀬義昌（@iwashi86）

NTTコミュニケーションズ エバンジェリスト。Podcast「fukabori.fm」運営。2025年から生成AI/AIエージェント関連プロジェクトを担当。AWS主催イベントで「AIエージェント時代のソフトウェア開発」について講演。

出典: [NTT Com](https://www.ntt.com/about-us/we-are-innovative/evangelist/yoshimasa-iwase.html), [AWS 講演資料](https://pages.awscloud.com/rs/112-TZM-766/images/1-SoftwareDevelopmentWithAIAgent_rev.pdf)

---

## 11. 考察：何が変わり、何が変わっていないか

### 変わったこと

1. **コード補完→自律エージェント**: ツールの性質が根本的に変化。単なる提案から、計画・実行・テスト・反復のサイクルを自律的に回す存在へ
2. **個人ツール→チームインフラ**: エージェントがGitHub Issue、Slack、Linearなどのチームツールと統合し、チーム単位の作業フローに組み込まれた
3. **「速く書く」→「正しく指示する」**: エンジニアの中核スキルが変化。Context Engineering、Spec-Driven Development、AGENTS.mdの整備が新しい専門性に
4. **単一エージェント→マルチエージェント**: Planner/Worker/Judgeの役割分担、並列実行が実用化

### 変わっていないこと

1. **生産性パラドックス**: タスクレベルの速度改善と組織レベルのデリバリー改善は別問題。ボトルネックはコード記述以外にある（TOCの制約理論と一致）
2. **品質リスク**: AI生成コードのセキュリティ脆弱性、バグ率の上昇は継続的な課題
3. **人間の判断の不可欠性**: 「何を作るか」「なぜ作るか」のレベルでは依然として人間の判断が必要
4. **測定の困難さ**: METR研究が示すように、AI生産性の正確な測定は方法論的に極めて難しい

### 今後注視すべきポイント

- **ハーネスエンジニアリング**: モデルの性能差が縮小する中、差別化要因はハーネスの質に移行
- **セキュリティガバナンス**: エージェントのサプライチェーンリスクへの組織的対応
- **コスト管理**: 使用量ベース課金への移行に伴うROI最適化
- **自己改善サイクル**: エージェントが自らのワークフローを改善する能力の進化
- **JetBrains Central等のガバナンスプラットフォーム**: エージェント管理の標準化

---

## 参考資料

### レポート・調査
- [Anthropic 2026 Agentic Coding Trends Report](https://resources.anthropic.com/2026-agentic-coding-trends-report)
- [Pragmatic Engineer - AI Tooling for Software Engineers in 2026](https://newsletter.pragmaticengineer.com/p/ai-tooling-2026)
- [LangChain - State of Agent Engineering](https://www.langchain.com/state-of-agent-engineering)
- [METR - Developer Productivity Study](https://metr.org/blog/2026-02-24-uplift-update/)
- [Faros AI - AI Productivity Paradox](https://www.faros.ai/blog/ai-software-engineering)

### ブログ・ガイド
- [Simon Willison - Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/)
- [Addy Osmani - The Code Agent Orchestra](https://addyosmani.com/blog/code-agent-orchestra/)
- [Martin Fowler - Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html)
- [LangChain - Agent Engineering: A New Discipline](https://blog.langchain.com/agent-engineering-a-new-discipline/)
- [NTT Com - Agentic Codingの基礎と最新動向](https://speakerdeck.com/nttcom/foundations-and-latest-trends-in-agentic-coding)

### ベンチマーク
- [SWE-bench Leaderboards](https://www.swebench.com/)
- [Scale Labs - SWE-Bench Pro](https://labs.scale.com/leaderboard/swe_bench_pro_public)
- [Epoch AI - SWE-bench Verified](https://epoch.ai/benchmarks/swe-bench-verified)

### 標準・仕様
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [AGENTS.md Specification](https://agents.md/)

### セキュリティ
- [Security Boulevard - Coding Agents Widen Attack Surface](https://securityboulevard.com/2026/03/coding-agents-widen-your-supply-chain-attack-surface/)
- [Dark Reading - AI Agents Security Pitfalls](https://www.darkreading.com/application-security/coders-adopt-ai-agents-security-pitfalls-lurk-2026)

### 市場データ
- [日本経済新聞 - AIコーディング市場40億ドル](https://www.nikkei.com/article/DGXZQOUC194FE0Z10C26A1000000/)
