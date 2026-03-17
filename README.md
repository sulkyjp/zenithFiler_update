<p align="center">
  <img src="https://raw.githubusercontent.com/sulkyjp/zenithFiler_update/main/assets/icon.png" width="80" alt="Zenith Filer icon">
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
| `ZenithFiler_v0.36.1.zip` | **完全版** — .NET ランタイム同梱。初回導入や環境移行に |
| `ZenithFiler_v0.36.1_patch.zip` | **軽量版** — ランタイム除外。既存環境のアップデートに |
<!-- download-table:end -->

> 過去のバージョンは [Releases](https://github.com/sulkyjp/zenithFiler_update/releases) ページから取得できます。

<!-- latest-changes:begin -->
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

</details>

<details>
<summary><b>14. 通知・進捗表示</b></summary>

| 機能 | 説明 |
|---|---|
| トースト通知 | コピー/移動/削除等の結果通知 |
| GlowBar | コピー/移動のリアルタイム速度表示つき進捗バー |
| スキャンバー | 大量ファイルフォルダスキャン時の進捗表示 |
| フィードバック送信 | アプリ内から GitHub へ直接投稿 |

</details>

<details>
<summary><b>15. ドキュメント・ヘルプ</b></summary>

| 機能 | 説明 |
|---|---|
| 統合ドキュメントビューア | マニュアル・変更履歴をアプリ内で閲覧 |
| Markdown レンダリング | 目次自動生成、キーワード検索、2 カラム表示 |
| 日英自動切替 | UI 言語に応じてドキュメント言語を自動選択 |

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

</details>

---

<p align="center">
  <sub>Developed by <a href="https://github.com/sulkyjp">sulkyjp</a></sub>
</p>
