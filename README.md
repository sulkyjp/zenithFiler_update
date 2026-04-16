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
| `ZenithFiler_v0.46.8.zip` | **完全版** — .NET ランタイム同梱。初回導入や環境移行に |
| `ZenithFiler_v0.46.8_patch.zip` | **軽量版** — ランタイム除外。既存環境のアップデートに |
| `ZenithFiler_v0.46.8_delta_from_0.46.7.zip` | **差分版** — 前バージョンから変更されたファイルのみ |
<!-- download-table:end -->

> 過去のバージョンは [Releases](https://github.com/sulkyjp/zenithFiler_update/releases) ページから取得できます。

<!-- latest-changes:begin -->
## Latest Changes — [0.46.8] - 2026-04-16 : #161 UX 統一ブラッシュアップ（基盤 + 6 ボタンホバー + ControlDeck/NavPane/ダイアログ/タブ トランジション）

### Added
- **今回追加した全アニメーションを Effects 設定と連動させた (#161 アクセシビリティ):** ControlDeck / NavPane の wipe-in と 8 ダイアログ登場アニメを `ShowPaneTransitions` に、タブ追加スライドインを `ShowTabEffects` に紐づけ。OFF にするとアニメなしで即時表示される。モーション過敏の方・低スペック機・トランジションを好まない方に配慮
- **ダイアログの登場アニメーションを追加 (#161 A-3):** 新設 `Helpers/DialogMotion.cs` の Attached Property `DialogMotion.EnableEntrance` を 8 ダイアログ（RenameDialog / AddFolderDialog / SelectFolderDialog / DescriptionEditDialog / AddToFavoritesDialog / FileConflictDialog / EmojiPickerDialog / AiManualDialog）に付与。Loaded 時に Window.Content を `Opacity 0→1` + `TranslateY +8→0` (220ms EaseOut) で下からふわっと登場させる
- **タブ追加時にスライドインアニメーションを追加 (#161 A-3):** `TabListView.xaml` の `ItemBorder` に Loaded EventTrigger を仕込み、新規タブを `TranslateX -20→0` + `Opacity 0→1` (150ms EaseOut) で左からスライドイン。既存タブは影響なし。退場アニメ（タブクローズ / ダイアログ Close）は Close 直前に遅延処理が必要で実装複雑化するため今回は見送り
- **Control Deck カテゴリ切替 / ナビペインビュー切替に wipe-in トランジション (#161 A-2):** `ActiveCategory` 変化時に Control Deck の ContentArea を `Opacity 0→1` + `TranslateX +8→0` (220ms, EaseOut) で右から滑らかに登場させる。ナビペイン（お気に入り / ツリー / 履歴 / インデックス検索）切替時も `RebuildLayout()` 完了後に同じ wipe-in を適用。初回レイアウトは起動負荷を避けるためスキップし、2 回目以降のみアニメーションする。`MotionHelper.AnimateDouble` を再利用して DRY に実装

### Changed
- **6 種類のボタンスタイルにホバースケールアニメーションを追加 (#161):** `IconButton` / `IconToggleButton` / `TextButton` / `AccentButton` / `TitleBarIconButton` / `CaptionCloseButton` の各 ControlTemplate に `ScaleTransform` を仕込み、`IsMouseOver` の EnterActions / ExitActions で `Motion.HoverScale` (1.03) ↔ 等倍を `Motion.Normal` (150ms) でなめらかにアニメーション。WelcomeWindow のテーマカード基準に合わせた "気持ちよさ" をアプリ全体のボタン操作へ展開。パフォーマンス観点で `DropShadowEffect` は含めず、`ScaleX/Y` のみをアニメーション対象とし大量インスタンス環境（ツールバー・ナビペイン等）でも GPU 負荷を抑えた
- **ダイアログのキャンセル/セカンダリボタンに `TextButton` を明示化 (#161 B-4):** RenameDialog / AddFolderDialog / SelectFolderDialog / DescriptionEditDialog / AddToFavoritesDialog のキャンセルボタン、および FileConflictDialog の KeepNewer / KeepLarger / Skip / Rename ボタンに `Style="{StaticResource TextButton}"` を付与。OS 既定の WPF ボタンから統一スタイルへ引き上げ、テーマ連動と上記ホバーアニメーションを適用

### Fixed
- **`tools/jp_input/` の XAML が WPF 一時ビルドに混入してビルドを壊す問題を修正:** `ZenithFiler.csproj` で `tools\**\*.xaml` と `tools\**\*` (Page/ApplicationDefinition/Resource) を除外。外部小プロジェクトを `tools/` に同居させても SDK の自動 glob が拾わないようにした

### Added
- **UX 統一の基盤レイヤーを整備 (#161):** 今後段階的に適用する共通リソースを先行追加
  - `AppResources.xaml` に **Motion リソース群** を新設: `Motion.Fast` / `Motion.Normal` / `Motion.Slow` (100/150/220ms) + `Motion.Ease` / `Motion.EaseInOut` (PowerEase Power=2) + `Motion.HoverScale` (1.03) / `Motion.PressScale` (0.97) + `Motion.IdleShadowOpacity` (0.10) / `Motion.HoverShadowOpacity` (0.22)
  - `AppResources.xaml` に **タイポグラフィスケール** を新設: `FontSize.Display` (22) / `FontSize.Headline` (18) / `FontSize.Subheadline` (15) / `FontSize.Body` (13) / `FontSize.Small` (12) / `FontSize.Caption` (11)
  - `Helpers/MotionHelper.cs` を新規作成し、WelcomeWindow 内で private static として埋もれていた `AnimateScale` / `AnimateDouble` を public static として抽出（WelcomeWindow 側は MotionHelper 呼び出しに置換、挙動は等価）
  - `TargetType="ComboBox"` / `TargetType="PasswordBox"` の暗黙スタイルを追加し、全 73 箇所の ComboBox・API キー入力等 PasswordBox の色・余白・SelectionBrush・CaretBrush をテーマ連動化（Template 差替は regression リスクが高いため今回見送り、後続フェーズで対応）
- **新テーマカラーキーを 4 つ追加:** `GoldAccentColor` / `OverlayBackgroundColor` / `OverlayTextColor` / `SubtleGlassColor`。全 50 テーマに `tools/add_theme_color.py` で一括投入済み、`ThemeService` の `_defaultPalette` と `_colorToBrushName` にも登録

### Changed
- **ハードコード色を `DynamicResource` 参照に置換 (#161):** FavoritesView の警告アイコン `#C4A03C` (2 箇所) → `GoldAccentBrush`、TabContentControl のカードオーバーレイ背景 `#A0000000` → `OverlayBackgroundBrush` と小字テキスト `#E0E0E0` → `OverlayTextBrush`、MainWindow / IndexSearchView のテレメトリ区切り線 `#30FFFFFF` → `SubtleGlassBrush`。今後のテーマ追加や配色見直しが一箇所で完結する

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
