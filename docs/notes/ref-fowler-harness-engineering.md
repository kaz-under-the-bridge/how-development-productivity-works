# Harness Engineering for Coding Agent Users — 日本語整理

> Martin Fowler のサイトに Birgitta Böckeler が寄稿した記事の構造化整理。コーディングエージェントのユーザーがどのようにハーネスを設計すべきかを論じる。

> **原文**: [Harness Engineering for Coding Agent Users](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html)（2026年4月2日公開）
> **著者**: Birgitta Böckeler（Thoughtworks Distinguished Engineer）

> **関連**: [AIハーネスによる開発生産性と安全性の統合](./ai-harness-productivity-safety.md)

---

## 1. ハーネスの定義

> "The term harness has emerged as a shorthand to mean everything in an AI agent except the model itself — Agent = Model + Harness."

ハーネスは3つの同心円で構成される。

| 層 | 名称 | 内容 |
|----|------|------|
| Core | モデル | LLM本体 |
| Middle | Builder's harness | エージェントのインフラ（システムプロンプト、コード検索、ツール統合） |
| Outer | User's harness | ユーザー固有の制御（AGENTS.md、hooks、カスタムセンサー） |

本記事が扱うのは主に **Outer（User's harness）** — ユーザーがコーディングエージェントを自分のプロジェクト・組織に適合させるために構築する部分。

---

## 2. Guides（フィードフォワード制御）と Sensors（フィードバック制御）

ハーネスは2種類の制御メカニズムで構成される。

### Guides（ガイド）= フィードフォワード

エージェントが行動する **前に** 振る舞いを誘導する。良い初期結果の確率を高める。

- AGENTS.md、Skills、アーキテクチャドキュメント
- ブートストラップスクリプト、コーディング規約
- OpenRewriteレシピ等のコード変換ツール

### Sensors（センサー）= フィードバック

エージェントが行動した **後に** 結果を観測し、自己修正を可能にする。

- テスト、リンター、型チェッカー、静的解析
- コードレビューエージェント、LLM-as-Judge
- 構造テスト（ArchUnit等）

> "Separately, you get either an agent that keeps repeating the same mistakes (feedback-only) or an agent that encodes rules but never finds out whether they worked (feedforward-only)."

**両方が必要。** フィードバックだけでは同じミスを繰り返すエージェントになり、フィードフォワードだけではルールの効果が分からないエージェントになる。

---

## 3. Computational vs Inferential

Guides と Sensors はそれぞれ2つの実行方式を持つ。

| | Computational | Inferential |
|---|---|---|
| **実行主体** | CPU（決定論的） | GPU/NPU（非決定論的） |
| **速度** | ms〜s | s〜min |
| **コスト** | 低い | 高い |
| **信頼性** | 高い（決定論的） | 低い（確率的） |
| **例（Guide）** | 言語サーバー、CLI、スクリプト、コードmod | AGENTS.md、Skills、参照ドキュメント |
| **例（Sensor）** | テスト、リンター、型チェッカー、静的解析 | コードレビューエージェント、LLM-as-Judge |

### 2×2マトリクスの具体例

| 方向 | Comp/Inf | 実装例 |
|------|----------|--------|
| コーディング規約 | Inferential feedforward | AGENTS.md、Skills |
| プロジェクトブートストラップ | Both feedforward | Skill + ブートストラップスクリプト |
| コードmod | Computational feedforward | OpenRewriteレシピ |
| 構造テスト | Computational feedback | pre-commit hookでArchUnitテスト |
| レビュー指示 | Inferential feedback | Skills |

---

## 4. ステアリングループ（The Steering Loop）

人間の役割は **個々のAI出力をレビューすること（in the loop）ではなく、ハーネスそのものを改善すること（on the loop）**。

繰り返し発生する問題に対して:
1. 問題のパターンを認識する
2. ガイドまたはセンサーを追加・改善する
3. エージェントの振る舞いが改善されたか検証する

AIはこのプロセス自体を支援できる — カスタムリンタールール、構造テスト、ドラフトルール、ハウツーガイドの生成。

---

## 5. タイミング: 品質を左に寄せる（Keep Quality Left）

チェックを開発ライフサイクルのどこに配置するか。コスト・速度・重要度に基づいて分散させる。

```
[インテグレーション前]
  Feedforward: LSP, architecture.md, /how-to-test skill, AGENTS.md, MCP server, API docs
  初回セルフコレクション: code review, eslint, semgrep, coverage, dependency check
  ↓ 人間レビュー
[インテグレーション]
  ↓
[インテグレーション後]
  高コストセンサー: architecture review, detailed review, mutation testing
[継続的]
  ドリフト検出: dead code検出, code-coverage-quality, dependabot
  ランタイムFB: SLO（latency, error rate, availability） → エージェント提案
            response-quality-sampling, log-anomalies → AI Judge
```

### タイミングの判断基準

| 問い | 配置 |
|------|------|
| コミット前に実行すべきものは？ | リンター、高速テスト、基本コードレビューエージェント |
| インテグレーション後に実行すべきものは？ | ミューテーションテスト、包括的コードレビュー |
| ドリフトを継続的に監視すべきものは？ | デッドコード検出、テストカバレッジ分析 |
| エージェントが監視すべきランタイムFBは？ | SLO劣化、レスポンス品質サンプリング |

---

## 6. 規制カテゴリ（Regulation Categories）

ハーネスが「何を」規制するかの3分類。

### 6.1 Maintainability Harness（保守性ハーネス）

内部コード品質と保守性を規制する。**最も実装しやすい** — 既存ツールが豊富。

コーディングエージェントの失敗モードとの対応:

| 検出方法 | 検出できる問題 |
|---------|--------------|
| **Computationalセンサーが確実に検出** | 重複コード、循環的複雑度、テストカバレッジ不足、アーキテクチャドリフト、スタイル違反 |
| **LLMが確率的に部分対応** | 意味的な重複コード、冗長テスト、力技の修正、過剰設計 |
| **どちらも確実には検出できない** | 問題の誤診断、過剰エンジニアリング、指示の誤解、正しさの問題 |

### 6.2 Architecture Fitness Harness（アーキテクチャ適合性ハーネス）

アプリケーションのアーキテクチャ特性を定義・検証する。**Fitness Function** として実装。

例:
- パフォーマンス要件をSkillで提供 → パフォーマンステストがフィードバック
- オブザーバビリティ規約をSkillで記述 → デバッグ指示がログ品質の振り返りを促す

### 6.3 Behaviour Harness（振る舞いハーネス）

機能的な振る舞いを規制する。**現時点で最も弱い（"the elephant in the room"）**。

現在のアプローチ:
- **Feedforward**: 機能仕様（詳細度はさまざま）
- **Feedback**: AI生成テストスイートの合格、カバレッジ評価、一部ミューテーションテスト + 手動テスト

> "This approach puts a lot of faith into the AI-generated tests, that's not good enough yet."

AI生成テストへの過度な依存は不十分。承認済みフィクスチャパターンで成果を出す同僚もいるが、包括的ではない。**監督と手動テストを減らすのに十分な信頼を得るための振る舞いハーネスの設計は、まだ大きな未解決課題。**

---

## 7. Harnessability（ハーネス適用可能性）

> "Not every codebase is equally amenable to harnessing."

コードベースの特性がハーネスの適用しやすさを決定する。

| 特性 | ハーネス適用への影響 |
|------|-------------------|
| 強い型付け言語 | 型チェックが自然なセンサーに |
| 明確なモジュール境界 | アーキテクチャ制約ルールを定義しやすい |
| フレームワーク（Spring等） | 詳細を抽象化し、エージェントの扱う空間を狭める |

### Ambient Affordances（環境が自然に提供する手がかり）

Ned Letcher（Thoughtworks）の概念: 「エージェントが環境内で操作する際に、環境自体が読みやすく、ナビゲートしやすく、扱いやすくする構造的特性」。

### グリーンフィールド vs レガシー

- **グリーンフィールド**: 最初からharnessabilityを織り込める
- **レガシー**: ハーネスが**最も必要だが最も適用が困難**。技術的負債がハーネスの構築を阻む

---

## 8. ハーネステンプレート

多くの企業には共通のサービストポロジーがあり、ニーズの約80%をカバーする:
- データダッシュボード（Node）
- CRUDビジネスサービス（JVM）
- イベントプロセッサ（Golang）

これらは **ハーネステンプレート** — ガイドとセンサーのバンドル — に発展する可能性がある。テンプレートがエージェントを構造・規約・技術スタックに縛り付ける。

> 「チームは利用可能なハーネスに基づいて技術スタックや構造を選ぶようになるかもしれない。」

### Ashbyの必要多様性の法則

> "Ashby's Law of Requisite Variety states that a regulator must have at least as much variety as the system it governs."

- LLMベースのエージェントは「ほぼ何でも」生成できる
- **トポロジーへのコミットは多様性の縮減** — エージェントの生成空間を狭め、包括的なハーネスを実現可能にする
- ただし、サービステンプレートと同様の課題あり: インスタンスのドリフト、バージョニングの複雑化、非決定論的なガイド/センサーのテスト困難

---

## 9. 人間の役割

人間の開発者は **暗黙のハーネス** を持っている: スキル、経験、組織的認識。

> "A coding agent has none of this: no social accountability, no aesthetic disgust at a 300-line function, no intuition that 'we don't do it that way here,' and no organisational memory."

エージェントには:
- 社会的説明責任がない
- 300行関数への美的嫌悪感がない
- 「ここではそうしない」という直感がない
- 組織的記憶がない

人間が判断すべきこと:
- どの規約が**構造を支えている**か vs 単なる**習慣**か
- 技術的に正しい解が**チームの目標に合致する**か

> **"A good harness should not necessarily aim to fully eliminate human input, but to direct it to where our input is most important."**

良いハーネスは人間の入力を完全に排除するのではなく、**最も重要な場所に向ける**べき。

---

## 10. 未解決課題

記事が特定した、今後の研究・実践が必要な問題:

| 課題 | 説明 |
|------|------|
| **ハーネスの一貫性維持** | ガイドとセンサーが増えるにつれ、全体としての一貫性をどう保つか |
| **矛盾するシグナルのトレードオフ** | エージェントが矛盾するシグナルを受けたとき、合理的なトレードオフを行えるか |
| **センサー不発火の解釈** | センサーが発火しないとき、品質が高いのか検出メカニズムが不十分なのか |
| **ハーネスカバレッジの評価** | テストのコードカバレッジやミューテーションテストに相当する、ハーネスの品質評価手法 |
| **分散した制御の協調** | デリバリーステップに散在するフィードフォワード/フィードバック制御の全体協調 |

---

## 11. 同時代の実践例

### OpenAI

- レイヤードアーキテクチャをカスタムリンターと構造テストで強制
- 定期的な「ガベージコレクション」スキャンでドリフトを検出し、エージェントが修正提案
- 結論: 「最も困難な課題は現在、環境、フィードバックループ、制御システムの設計に集中している」

### Stripe

- pre-push hookでヒューリスティクスに基づく関連リンターを実行
- フィードバックを左にシフトすることを重視
- 「ブループリント」がフィードバックセンサーをエージェントワークフローに統合

### 新興テクニック

- ミューテーションテスト・構造テストがComputational feedbackセンサーとして復権
- LSPとコードインテリジェンスのエージェント統合
- アーキテクチャドリフトをComputational + Inferentialセンサーで検出

---

## 出典

- [Birgitta Böckeler, "Harness Engineering for Coding Agent Users," martinfowler.com, 2026年4月2日](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html)
- 初版メモ: 2026年2月17日公開
- GenAI（Claude、Claude Code）をリサーチと言語ポリッシュに使用（著者記載）

---

*作成: 2026年4月 / 性質: 外部文献の日本語整理（reference）*
