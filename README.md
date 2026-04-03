<p align="center">
  <img width="2022" height="863" alt="image" src="https://github.com/user-attachments/assets/6452538c-e111-4e6a-92b3-67034978ee22" />
</p>

<h1 align="center">Zenith Filer</h1>

<p align="center">
  <b>Windows 向け Portable 2ペイン ファイラー</b><br>
  A portable dual-pane file manager for Windows
</p>

<p align="center">
  <a href="https://github.com/sulkyjp/zenithFiler_update/releases/latest"><img src="https://img.shields.io/github/v/release/sulkyjp/zenithFiler_update?style=flat-square&color=blue" alt="Latest Release"></a>
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6?style=flat-square&logo=windows" alt="Windows 10/11">
  <img src="https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet" alt=".NET 8">
  <img src="https://img.shields.io/badge/license-proprietary-gray?style=flat-square" alt="License">
</p>

<!-- スクリーンショットをここに貼り付け -->
<!-- ![Screenshot](assets/screenshot.png) -->

---

## Highlights

- **タブ付き 2ペイン + ナビペイン** — お気に入り・ツリー・履歴・インデックス検索に即アクセスできる 6 ビュー構成のサイドバー
- **内蔵ターミナル (ConPTY)** — ペインのフォルダへ直接 cd でき、ファイル操作とコマンドライン作業をシームレスに行き来
- **50 テーマ × 全カスタマイズ** — キーバインド・エフェクト 12 カテゴリの個別制御など、見た目も操作感も自分好みに

---

## Requirements

| | |
|---|---|
| **OS** | Windows 10 / 11 (x64) |
| **Runtime** | .NET 8 Desktop Runtime |
| **Install** | 不要 — ZIP を展開するだけで使えます (Portable) |

## Download

**[Latest Release をダウンロード](https://github.com/sulkyjp/zenithFiler_update/releases/latest)**

<!-- download-table:begin -->
| ファイル | 内容 |
|---|---|
| `ZenithFiler_v0.40.31.zip` | **完全版** — .NET ランタイム同梱。初回導入や環境移行に |
| `ZenithFiler_v0.40.31_patch.zip` | **軽量版** — ランタイム除外。既存環境のアップデートに |
| `ZenithFiler_v0.40.31_delta_from_0.40.30.zip` | **差分版** — 前バージョンから変更されたファイルのみ |
<!-- download-table:end -->

> 過去のバージョンは [Releases](https://github.com/sulkyjp/zenithFiler_update/releases) ページから取得できます。

<!-- latest-changes:begin -->
## Latest Changes — [0.40.31] - 2026-04-04 : タブ管理強化・AIテーマ品質向上・テーマカラー拡張

### Added
- **二つ名履歴:** 実績履歴ダイアログに「実績履歴」「二つ名履歴」のタブ切替を追加。過去に生成された二つ名を取得日・合成元バッジ・バックストーリー付きで一覧表示。最大200件保存。タイトルバナークリックで二つ名履歴を直接開く
- **クイックジャンプに新規タブ/上書き切替トグルを追加:** スライド式トグルで、選択したフォルダを新規タブで開くか現在のタブを上書きするかを切替可能に。デフォルトは新規タブ
- **タブ管理ビュー連携:** タブ管理ビュー表示時にA/Bペインのタブバーを非表示にするオプションを追加（タブ設定で切替可能）。ペインのタブバーからタブ管理ビューへのドラッグ&ドロップによるタブ移動・並べ替えに対応
- **タブ管理ビューへのフォルダドロップ:** タブ管理ビューにエクスプローラーやナビペイン（お気に入り・履歴・よく使うフォルダ・ツリー）からフォルダをドロップして新規タブを追加可能に
- **タブ管理ビューにタブ追加ボタン:** A/Bペイン各ヘッダーに＋ボタンを追加。タブバー非表示時でもタブ管理ビューから新規タブを作成可能

### Changed
- **起動後のUI操作ロックを解消:** タブ復元（InitializeAsync）をfire-and-forget化し、画面表示直後からUI操作を受け付けるよう変更。お気に入り読み込みの優先度をBackground に下げ、ユーザー入力を優先
- **AIテーマ生成・カスタマイズの品質向上:** 初期生成・カスタマイズ共通でTemperatureを最適化（生成0.5/カスタマイズ0.4）、WCAGコントラスト事後検証と自動リトライを両方に追加。ホバー色の調和ルール、ナビペイン・コントロールデッキ・チャレンジカード・ダイアログボタンの全色キーをAI生成対象に追加し、テーマ全体の調和とモダンさを向上。カスタマイズではテーマ名・カテゴリ・説明によるアイデンティティ保持も実施
- **AIテーマカスタマイズダイアログを非モーダル化:** カスタマイズ結果の保存確認画面を表示したまま、アプリのファイル一覧やナビペインを操作可能に。実際の画面で適用結果を確認してから保存可能
- **AIテーマカスタマイズのカラーチップ順を統一:** 結果画面の4色カラーチップの並び順をテーマカード・テーマストアと同じ順序（背景→サイドバー→アクセント→テキスト）に修正
- **テーマストアのカテゴリ列間隔を縮小:** カテゴリ区分の左右パディングを縮小し、横方向の隙間を狭めてテーマ一覧の視認性を向上
- **ControlDeck内のホバースタイルを統一:** テーマカード・ストアタイル・カテゴリグループのホバー色を `DeckItemHoverBrush` に統一。ストアタイルにホバー効果（背景色変化+リフトアニメーション）を新規追加。`DeckItemHoverColor` を全テーマJSONに追加し、テーマごとのホバー体験を実現
- **バナーフォント色のテーマ対応:** レベルバナー・二つ名バナー・PROバナーのフォント色をハードコード白からテーマJSON定義（`LevelBadgeTextColor`/`TitleBadgeTextColor`/`ProBadgeTextColor`）に変更。テーマごとにバナーテキスト色をカスタマイズ可能に
- **適用モードタイルのホバー色を統一:** パーソナライズ・自動選択・ペイン個別・スケジュールの4タイルのホバー色を `DeckItemHoverBrush` に変更し、テーマカード等と一貫したホバー体験に
- **テーマカスタマイズからテーマページへの遷移:** カスタマイズウィンドウで DeckItemHoverColor / DeckItemSelectedColor をクリックすると、設定画面のテーマページを直接表示するよう変更
- **タイトルバーアイコンのホバー色をテーマ対応:** ヘッダーアイコンボタン（設定・マニュアル等）のホバー時にアイコン色が `TitleBarIconHoverColor` に変化するよう新スタイルを追加。全テーマ JSON に定義追加
- **チャレンジカード・ダイアログボタンのテーマ対応:** 実績カードの未達成/達成背景色・テキスト色（`ChallengeCardColor`/`ChallengeCardCompletedColor`/`ChallengeCardCompletedTextColor`）、ダイアログボタンの通常/ホバー/主ボタン色（`DialogButtonColor`/`DialogButtonHoverColor`/`DialogPrimaryButtonColor`/`DialogPrimaryButtonHoverColor`）を全テーマ JSON に追加。テーマカスタマイズの「ナビペイン・コントロールデッキ」セクションに新サブグループ「チャレンジカード」「ダイアログボタン」を追加

### Fixed
- **ナビペインの幅自動調整が少し広すぎる問題を修正:** パディングを 24px→8px に縮小し、最終列の右端ぴったりに収まるよう調整
- **左ナビペイン非表示時にリスト部分が空白になる不具合を修正:** SidebarColumn の MaxWidth 制御と初期設定での幅0反映を追加し、ナビペイン非表示時にファイルリストが全幅に広がるよう修正
- **AIテーマカスタマイズのコントラスト自動修正でJSONが途中切れになる不具合を修正:** MaxTokens を 8192→16384 に増加し、色キー増加後のJSON切れを防止。リトライ失敗時は元の結果をそのまま使用するよう改善
- **デフォルトテーマの自動更新でカスタマイズした色が消える不具合を修正:** アップロード時にカスタムオーバーライドがマージされず、ダウンロード元も旧ソース優先だったため一部の色変更が反映されなかった問題を修正
- **新規タブがアドレスモードで開く不具合を修正:** 新しいタブ作成時に常にパンくずモードで開始するよう変更。ホームパスへ自動遷移して表示
- **AI二つ名生成で思考過程が漏出する不具合を修正:** AIレスポンスから「」で囲まれた最初の二つ名のみを抽出するパースロジックを追加。モデルが説明文を含めて返した場合でも正しく二つ名だけを取得
- **デバッグ再生成でバックストーリーが生成されない不具合を修正:** バックストーリー生成フラグがリセットされずスキップされていた問題を修正
- **二つ名履歴が再起動で消える不具合を修正:** 終了時の設定引き継ぎに二つ名履歴が含まれていなかった問題を修正
- **右ナビペインのホバー/選択色がテーマカスタマイズに追従しない不具合を修正:** NavPaneListViewStyle のホバー定義が AppResources レベルで解決されペイン別テーマが効いていなかった問題を修正。全7ビューにインラインスタイルを追加し、ビジュアルツリー内でリソースを解決するよう変更

> 過去の変更履歴は [Releases](https://github.com/sulkyjp/zenithFiler_update/releases) を参照してください。
<!-- latest-changes:end -->

---

## Features — 全 16 カテゴリ・100 以上の機能

<details>
<summary><b>1. ファイル管理（コア）</b></summary>

| 機能 | 説明 |
|---|---|
| デュアルペイン | A（中央）/ B（右）の独立した 2 画面ファイルブラウザ |
| タブブラウジング | ペインごとに複数タブで別々のフォルダを表示 |
| 表示モード | 詳細リスト / 大アイコン / 中アイコン / 小アイコン |
| カラムソート | 名前・更新日・サイズ・拡張子で昇順/降順切替 |
| ファイル操作 | コピー / 移動 / 削除 / リネーム（F2） |
| ドラッグ＆ドロップ | ペイン間のファイル移動・コピー、右ドラッグで操作選択 |
| 操作の取り消し | ファイル操作のアンドゥ |
| シェルサムネイル | 画像ファイルのサムネイル自動生成・キャッシュ |
| 削除確認ダイアログ | ごみ箱移動前の確認（ON/OFF 可） |

</details>

<details>
<summary><b>2. ナビゲーション</b></summary>

| 機能 | 説明 |
|---|---|
| ブレッドクラムバー | 階層パスナビゲーション＋フォルダドロップダウン |
| パス直接入力 | ブレッドクラムとテキスト入力モードの切替 |
| 戻る/進む | フォルダ閲覧履歴のナビゲーション |
| 親フォルダ移動 | ワンクリックで上位ディレクトリへ |
| クイックショートカット | ホーム / デスクトップ / ダウンロードへの即時アクセス |
| 1画面/2画面切替 | ペインレイアウトのトグル |
| タイトルバーパス表示 | 現在フォルダの完全パスを表示（ON/OFF 可） |

</details>

<details>
<summary><b>3. ナビペイン（サイドバー）— 6 つのビュー</b></summary>

| ビュー | 詳細 |
|---|---|
| お気に入り | フォルダ/ファイルのブックマーク、説明タグ、仮想フォルダ、検索、D&D 登録、★ボタンで即登録、TOP5 表示、ロック機能 |
| ディレクトリツリー | 全ドライブのツリー表示、遅延読込、リアルタイム同期、ツリーロック、Ctrl+ダブルクリックで反対ペインに開く |
| 最近使ったファイル | 直近 100 件のファイルアクセス履歴、アクセス回数・日時表示、ソート・検索 |
| 参照履歴 | 閲覧フォルダの日付グループ表示、キーワード検索、クリックでナビゲート |
| インデックス検索設定 | インデックス対象フォルダ管理、差分/完全再構築、進捗表示、一時停止/再開 |
| ターミナル | 埋め込み PowerShell（WPF ネイティブ描画）、複数タブ、A/B ペインパス連動ボタン、ANSI 256 色+RGB 対応、CJK 全角対応 |

</details>

<details>
<summary><b>4. クイックプレビュー</b></summary>

| 対応形式 | 説明 |
|---|---|
| テキストファイル | .txt, .json, .bat, .ps1 等のリアルタイムプレビュー |
| PDF | ページ送りつきの PDF ビューア |
| HTML | Web コンテンツプレビュー |
| 画像 | jpeg, png, bmp, gif, webp 等 |
| Excel/CSV | CSV, TSV, XLS, XLSX（シート選択対応） |
| Office ドキュメント | Word (.docx), PowerPoint (.pptx) |

</details>

<details>
<summary><b>5. 検索・フィルタリング</b></summary>

| 機能 | 説明 |
|---|---|
| 通常検索 | キーワードによるファイル検索 |
| ファイル内容検索（grep） | ripgrep エンジンによる高速なファイル内容検索 |
| インデックス検索 | Lucene.NET + Kuromoji（日本語形態素解析）による全文検索 |
| 検索プリセット | ビルトイン 8 種（今日更新・7日間・30日間・巨大ファイル・画像・Office・実行ファイル・小ファイル）＋ユーザー作成 |
| 検索履歴 | 直近 100 件の検索履歴（通常/インデックス別） |
| サイズフィルタ | 最小/最大ファイルサイズ指定 |
| 日付フィルタ | 更新日の範囲指定 |
| ファイル種別フィルタ | フォルダ, Excel, Word, PPT, PDF, TXT, EXE, 画像 等 |
| 検索動作設定 | 同一ペイン/反対ペイン/即時検索の 3 モード |

</details>

<details>
<summary><b>6. インデックスエンジン</b></summary>

| 機能 | 説明 |
|---|---|
| Lucene.NET 全文検索 | プロフェッショナルな検索バックエンド |
| 差分インデックス更新 | 新規/変更ファイルのみの効率的な更新 |
| 更新モード | 自動（リアルタイム監視）/ 定期（1〜24 時間間隔）/ 手動 |
| エコモード | CPU/ディスク負荷軽減モード |
| ネットワークドライブ対応 | リモート共有向けの軽量処理 |
| アイドル時のみ実行 | CPU 使用率閾値による自動制御 |
| インデックスロック | アーカイブフォルダの自動更新除外 |

</details>

<details>
<summary><b>7. テーマシステム</b></summary>

| 機能 | 説明 |
|---|---|
| 50 テーマ内蔵 | 5 カテゴリ × 10（Standard / Lifestyle / Professional / Premium / RetroTech） |
| 62 色キー | テーマあたり 62 色のきめ細かな配色定義 |
| ペイン別テーマ | A/B/ナビペインに異なるテーマを適用可能 |
| テーマカスタマイズ | 色単位での編集、非破壊保存 |
| ランダムテーマ | 全テーマ or カテゴリ内でランダム切替 |
| テーマ診断 | 6 問のアンケートでおすすめテーマを提案 |

</details>

<details>
<summary><b>8. 外観・エフェクト設定</b></summary>

| 機能 | 説明 |
|---|---|
| 行の高さ | 4 段階（20/24/32/40px） |
| 拡張子表示 | ON/OFF 切替 |
| 隠しファイル表示 | ON/OFF 切替 |
| エフェクト 12 カテゴリ | 起動 / GlowBar / スキャンバー / タブ / ペイン遷移 / テーマ変更 / ステータスバー / プレビュー / リスト / ナビペイン / コントロールデッキ / D&D の個別 ON/OFF |

</details>

<details>
<summary><b>9. 設定・カスタマイズ（Control Deck）</b></summary>

| カテゴリ | 主な設定項目 |
|---|---|
| 一般 | コンテキストメニュー方式、シングルクリック動作、タブ復元、常駐モード、通知時間、ホームフォルダ |
| 検索 | 検索動作モード、パスクリック動作、自動 1 画面切替 |
| インデックス | 更新タイミング、アイドル実行、エコモード、ネットワークドライブ |
| バックアップ | 設定のバックアップ/復元、説明つきスナップショット |
| テーマ | テーマ選択・カスタマイズ・ペイン割当 |
| 表示 | 行高・拡張子・隠しファイル・ソート順 |
| エフェクト | 12 カテゴリのアニメーション ON/OFF |
| ショートカット | 25 以上のアクションのキーバインド変更、JSON エクスポート/インポート |
| 統計 | 21 項目の操作カウント、TOP50 閲覧フォルダランキング |
| 言語 | 10 ヶ国語の即時切替（再起動不要） |

</details>

<details>
<summary><b>10. 多言語対応（i18n）</b></summary>

| 機能 | 説明 |
|---|---|
| 10 言語サポート | 日本語, 英語, 中国語(簡/繁), 韓国語, ドイツ語, スペイン語, フランス語, ロシア語, ポルトガル語 |
| ホットスイッチ | 再起動なしで言語切替 |
| 動的検出 | ユーザー追加の言語ファイル自動認識 |
| フォールバック | 未翻訳キーは日本語にフォールバック |

</details>

<details>
<summary><b>11. プロジェクトセット（ワーキングセット）</b></summary>

| 機能 | 説明 |
|---|---|
| ワークスペース保存 | ペイン数、開いているタブ、表示モード、ソート順を丸ごと保存 |
| ワンクリック復元 | 保存したプロジェクト環境を即座にロード |

</details>

<details>
<summary><b>12. Box Drive 連携</b></summary>

| 機能 | 説明 |
|---|---|
| Box パスマッピング | BOX:// パスの自動検出 |
| 共有リンク取得 | クリップボード監視で box.com URL をキャプチャ |
| Box API 連携 | OAuth 認証で Box API と接続 |

</details>

<details>
<summary><b>13. ウィンドウ管理</b></summary>

| 機能 | 説明 |
|---|---|
| ウィンドウスナップ | 8 方向（半分×4、4分割×4）の配置 |
| 位置・サイズ記憶 | 終了時の状態を復元 |
| マルチディスプレイ対応 | ディスプレイ切断時の自動レスキュー |

<br>
2画面モード<br>
<img width="1949" height="989" alt="image" src="https://github.com/user-attachments/assets/887c8d99-9d15-4324-8e98-695cc8a26dc2" />
<br><br>
1画面モード<br>
<img width="1949" height="989" alt="image" src="https://github.com/user-attachments/assets/5d8aaca4-77e9-4391-87c5-288e1fe9814b" />
</details>

<details>
<summary><b>14. 通知・進捗表示</b></summary>

| 機能 | 説明 |
|---|---|
| トースト通知 | コピー/移動/削除等の結果通知 |
| GlowBar | コピー/移動のリアルタイム速度表示つき進捗バー |
| スキャンバー | 大量ファイルフォルダスキャン時の進捗表示 |
| フィードバック送信 | アプリ内から GitHub へ直接投稿 |

<br>
アプリ設定からフィードバックを送信<br>
<img width="1758" height="989" alt="image" src="https://github.com/user-attachments/assets/8c687bf5-a1e7-47f6-833f-f58199e5fb09" />
</details>

<details>
<summary><b>15. ドキュメント・ヘルプ</b></summary>

| 機能 | 説明 |
|---|---|
| 統合ドキュメントビューア | マニュアル・変更履歴をアプリ内で閲覧 |
| Markdown レンダリング | 目次自動生成、キーワード検索、2 カラム表示 |
| 日英自動切替 | UI 言語に応じてドキュメント言語を自動選択 |

<br>
マニュアルページ<br>
<img width="1386" height="910" alt="image" src="https://github.com/user-attachments/assets/17a139d7-330d-4a0e-be55-f38c875abfec" />
<br><br>
修正履歴ページ<br>
<img width="1386" height="910" alt="image" src="https://github.com/user-attachments/assets/ca2dd9fb-411e-4742-ab45-ec502ad72dc7" />
<br><br>
言語設定が「英語」の際のマニュアル<br>
<img width="1386" height="893" alt="image" src="https://github.com/user-attachments/assets/ef44ceb1-a1f6-4ea4-841c-c334990c318d" />
</details>

<details>
<summary><b>16. システム統合・パフォーマンス</b></summary>

| 機能 | 説明 |
|---|---|
| シェルアイコン抽出 | Windows ネイティブアイコン取得 |
| Explorer コンテキストメニュー | シェル拡張との統合 |
| 自動アップデート | デルタ/パッチ/フルの 3 段階更新戦略 |
| 常駐モード | タスクトレイ常駐 |
| アイコンバッチ読込 | 200 件単位+5ms インターバルで UI フリーズ回避 |

<br>
アプリ独自のコンテキストメニュー<br>
<img width="318" height="378" alt="image" src="https://github.com/user-attachments/assets/8e236a0b-6a1b-45a9-ac46-4a0450921a5e" />
<br><br>
アプリ独自メニューとエクスプローラ互換メニューの切り替え<br>
<img width="644" height="307" alt="image" src="https://github.com/user-attachments/assets/b9409b21-eb70-4f77-8117-49fdcd7318b3" />
<br><br>
自動アップデート機能により再ダウンロード不要<br>
<img width="1948" height="936" alt="image" src="https://github.com/user-attachments/assets/73b23852-1f9e-4928-a505-e4c1f0bf078d" />
<br><br>
常駐オプションONにより、アプリ終了後はタスクバーに格納<br>
<img width="419" height="238" alt="image" src="https://github.com/user-attachments/assets/fca2c198-ca9e-4f34-8dea-47b727c41082" />
<img width="227" height="37" alt="image" src="https://github.com/user-attachments/assets/c7a3aa17-4ee4-406a-8942-82a84825391d" />
</details>

---

<p align="center">
  <sub>Developed by <a href="https://github.com/sulkyjp">sulkyjp</a></sub>
</p>
