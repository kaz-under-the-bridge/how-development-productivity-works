# セッション引き継ぎメモ（2026-04-11）

> 別セッションでのドキュメント更新ワーク継続用。PRレビュー後の深掘り・拡張に使う素材。

---

## 1. Advisorからの構造フィードバック（未反映分）

### 1.1 §2「消えた生産性」の構成順序の提案

Advisorの指摘: 「パラドックス（症状）」と「消えた生産性（メカニズム）」は別概念であり、混同すると両方が弱まる。

- **パラドックス** = 観測された現象（個人↑、組織→）
- **消えた生産性** = 因果メカニズム（余剰はどこへ行ったか）

提案された改善: §2.1（広木氏の複雑性パラドックス）を先に置き、メカニズムの概念フレームを提示してから、§2.2で3つの吸収メカニズムを展開し、パラドックスのデータを「観測される証拠」として後に配置する。現在は逆順になっている。

### 1.2 §6（ハーネス組織のミッション）の薄さ

ユーザーの元リクエスト: 「the art of AI maturityのステークホルダ、その中でAIハーネスを扱う組織の役割、ミッション、方向性の整理」

Advisorの指摘: 8ステークホルダーを名前だけ挙げてマッピングが浅い。RACIデータはai-maturity-framework.mdに存在する。改善として各ステークホルダーとの相互作用テーブルを追加した（反映済み）が、さらに深掘りの余地あり:

- **RACI未定義の10ケイパビリティ**（Strategy and Sponsorship + Data and AI Core）にハーネスチームがどう関わるかの設計
- Platform Engineeringとの境界線: ハーネスはプラットフォームの「上」か「中」か
- CommitteeとResponsible AIの関係: ハーネスチームはCommitteeの実行部隊だが、SF03（AIコア）とSF04（責任あるAI）の両方にまたがる。この「またがり」をどう組織設計に落とすか

---

## 2. Web検索で得た未使用データ

### 2.1 Martin Fowler「Harness Engineering for Coding Agent Users」（2026/4/2）の詳細

URL: https://martinfowler.com/articles/harness-engineering.html

親ドキュメントではGuides/Sensors、on the loopの概念のみ引用。以下は未使用の重要概念:

#### ハーネスの3層構造（同心円）
- **Core**: LLMモデル
- **Middle**: Builder's harness（エージェントインフラ — システムプロンプト、コード検索）
- **Outer**: User's harness（ユーザー固有の制御）

#### Computational vs Inferential 制御
- **Computational**: 決定論的、高速（ms〜s）。テスト、リンター、型チェッカー。信頼性高い
- **Inferential**: AIによるセマンティック分析、低速・高コスト。コードレビューエージェント、LLMジャッジ。非決定論的だがリッチな判断が可能
- 「別々だと、同じミスを繰り返すエージェント（feedback only）か、ルールはあるが効果がわからないエージェント（feedforward only）になる」

#### ハーネスの3カテゴリ（規制対象別）
1. **Maintainability Harness**: 内部コード品質。最も実装しやすい
2. **Architecture Fitness Harness**: アーキテクチャ特性をfitness functionで強制
3. **Behaviour Harness**: 「the elephant in the room」— 現時点で最も弱い。AI生成テストへの過度な依存は不十分

#### Harnessability（ハーネス適用可能性）
- すべてのコードベースが等しくハーネスを適用しやすいわけではない
- 技術選択、モジュール境界、フレームワークが「ambient affordances」（環境が自然に提供する手がかり）を形成
- Greenfieldは最初からharnessabilityを織り込める。レガシーはハーネスが最も必要だが最も適用が困難

#### Ashbyの法則
- 「制御装置は、制御対象のシステムと同じだけの多様性を持たなければならない」
- 定義されたサービストポロジーにコミットすることで、エージェントが生成しうる空間を狭め、包括的なハーネスを実現可能にする

#### ハーネステンプレートの未来
- 個別ハーネス → サービストポロジーごとのテンプレート（データダッシュボード、CRUDサービス、イベントプロセッサ等）
- 「チームは利用可能なハーネスに基づいて技術スタックや構造を選ぶようになるかもしれない」

#### ハーネスカバレッジの未解決課題
- 「テストのコードカバレッジやミューテーションテストに相当する、ハーネスカバレッジと品質を評価する手法が必要」
- 「センサーが一度も発火しない場合、それは品質が高いのか検出メカニズムが不十分なのか？」

### 2.2 Faros AI「AI Productivity Paradox Research Report」の詳細

URL: https://www.faros.ai/blog/ai-software-engineering

#### Amdahlの法則の適用
- システムは最も遅い構成要素の速度でしか動かない
- AIがコード記述を加速 → レビューキュー膨張 → テスト飽和 → セキュリティ検証遅延 → リリースパイプライン停滞

#### 4つの採用パターン障害
1. **Recent critical mass**: 本格的な利用はここ2-3四半期
2. **Uneven distribution**: 一部チームの加速が組織全体にスケールしない
3. **Skewed toward new employees**: シニアエンジニアが懐疑的。採用は在籍期間の短いスタッフに偏る
4. **Surface-level usage**: 多くの開発者はオートコンプリートのみ使用。高度な機能は未活用

#### 組織レベルの相関なし
「We observed no significant correlation between AI adoption and improvements at the company level.」
— チームレベルのゲインがあっても、企業指標（スループット、DORA、品質KPI）は有意に改善していない

#### 5つの組織的イネーブラー
1. Workflow design
2. Governance structures
3. Infrastructure modernization
4. Training programs
5. Cross-functional alignment

### 2.3 その他の未使用データポイント

#### AI生成コードの安全閾値（Exceeds AI）
URL: https://blog.exceeds.ai/industry-benchmarks-ai-code-productivity/
- AI生成コード比率は2026年時点でグローバルで41-42%
- **持続可能なベンチマークは25-40%** — これを超えると品質が劣化する
- 変更失敗率の計測方法: リポジトリアクセスによるコードレベル計測が不可欠（従来ツールではAI vs 人間の区別ができない）

#### セキュリティ脆弱性の具体数値
- Veracode: 100以上のLLMを80のコーディングタスクでテスト → **45%がOWASP Top 10脆弱性を導入**
- CodeRabbit: AI生成コードは人間の**2.74倍**のセキュリティ脆弱性を含む
- Cortex 2026: AI支援PRのインシデント率 +23.5%、変更失敗率 約+30%

#### 正式なAI利用ポリシーの普及率
- Cortex 2026: 正式なAI利用ポリシーを持つ組織はわずか**45%**

#### Fortune記事 — 組織レベルの停滞（2026/3/10）
URL: https://fortune.com/2026/03/10/ai-productivity-workers-workday-efficiency/
- AIは個人の作業を増やしているが、労働時間は減っていない
- 組織はAIの効率化分を新たな仕事で埋めている（メカニズム3「慣性吸収」の外部エビデンス）

#### NVIDIA OpenShell / Microsoft Agent Governance Toolkit
- **NVIDIA OpenShell**: オープンソースのポリシー駆動サンドボックスランタイム。Landlock LSM（ファイルシステム）、seccomp BPF（syscall）、OPA/Rego HTTP CONNECTプロキシ（ネットワーク）でカーネルレベルのセキュリティ制約を強制
- **Microsoft Agent Governance Toolkit**: OWASP Agentic AIリスクに対応する7パッケージのランタイムセキュリティツールキット。Agent OS（ポリシーエンジン）、Agent Mesh（エージェント間通信）、Agent Runtime（動的実行リング）

---

## 3. ユーザーの元リクエストと対応状況

| リクエスト | 対応状況 | 残課題 |
|-----------|---------|--------|
| Art of AI Maturityのステークホルダー・ハーネス組織の役割整理 | §6で概要記述 + ステークホルダー相互作用テーブル追加 | RACI未定義10件のハーネスチーム関与設計、PF Engとの境界線 |
| 開発生産性と安全性の2軸に関する最新情報 | §1で最新データ引用、evidence/に裏付け集約 | NVIDIA OpenShell / MS Governance Toolkit等の安全性ツールの整理 |
| AI前提での開発生産性・指標の探索 | §3で Layer 1/2/3問題を整理、候補指標を提案 | 各候補指標の具体的な計測設計（How） |
| 安全とは何か・何が危険かの整理 | §4で5危険類型・4安全性質を定義 | 各危険類型の具体事例の補強、定量的な安全指標の設計 |
| OODAループの構築 | §5で設計を記述 | Observe層の具体的なダッシュボード設計（How） |
| Why/Whatが定まること | §7で整理 | Howの深掘り（短期/中期/長期のロードマップ詳細化） |

---

## 4. 次セッションで検討すべきトピック

### 4.1 evidence/ に追加すべき裏付けドキュメント候補

親ドキュメントの主張のうち、ファクトの裏付けが薄いもの:

- [ ] AI生成コードのセキュリティ脆弱性データ集約（Veracode, CodeRabbit, Cortex, OWASP）
- [ ] 「消えた生産性」メカニズム3（慣性吸収）の外部エビデンス（Fortune記事、パーキンソンの法則の研究等）
- [ ] Layer 2/3指標の先行事例（Glassdoor A/Bテスト、Dropbox AI計測等 — ai-impact-data.mdの企業実践例セクション）

### 4.2 Fowlerのハーネス設計原則の深掘り

Martin Fowlerの記事は非常にリッチで、以下の概念を独立したドキュメントに展開する価値がある:
- Guides vs Sensors の設計パターン集
- Computational vs Inferential の使い分けガイドライン
- Harnessability（ハーネス適用可能性）の評価フレームワーク
- Ashbyの法則のハーネス設計への応用

### 4.3 prd-ai-agent-governance との接続

- harness-engineering.md の4機能（制御、状態管理、段階的開示、改善ループ）とFowlerのGuides/Sensorsの対応関係の明確化
- ai-maturity-framework.md のRACIマトリクスにハーネスチームを明示的にマッピング
- Coding Agent利用ポリシーと§4「安全の定義」の接続（ポリシーのどの条項がどの安全性質に対応するか）

---

*作成: 2026年4月11日 / 性質: セッション引き継ぎ用一時ファイル*
