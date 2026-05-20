# Morning Hill — 朝活カフェ ランディングページ

> 架空の朝活カフェ「Morning Hill」のLP制作。ポートフォリオ用に **ブリーフ作成から実装・画像生成まで** 一気通貫で行った作品です。

## 🔗 公開URL

**Live サイト**: https://morning-hill-lp.vercel.app
**ソースコード**: https://github.com/eluke0201-boop/morning-hill-lp

## ✨ 制作のポイント

- **ブリーフ起点の設計** — [BRIEF.md](BRIEF.md) に架空クライアントの設定（業態・ターゲット・価格帯・差別化）を先に固め、すべてのデザイン判断をそこから導く
- **AIで19枚の画像を生成** — OpenAI の `gpt-image-2` を使い、「写真9枚＋duotoneアイコン10枚」を統一トーンで一括生成。1コマンドで全画像を再生成できる構成にし、ブランド方針の変更に強い設計
- **レスポンシブ対応** — 375px のスマホから 1280px+ の PC まで、3段階のブレークポイントで崩れずに表示
- **軽量実装** — フレームワーク不使用。Vanilla HTML/CSS/JS のみ。依存ゼロ、読み込み速度を最優先

## 🎨 デザインコンセプト

ブランドのキーワードは **「朝の光・ミニマル・温かみ」**。

- **カラーパレット**: クリーム (`#FFFCF7`) をベースに、朝陽オレンジ (`#E8804A`) をアクセントに
- **タイポグラフィ**: 欧文は Playfair Display（セリフ）、和文は Noto Sans JP（サンセリフ）。見出しに `clamp()` を使い、画面幅に応じて滑らかにサイズ変化
- **余白設計**: 文字より「空気」を見せる構成。各セクション上下に 120px の余白

## 🧱 構成（1ページ完結 / 7セクション）

| # | セクション | 役割 |
|---|---|---|
| 1 | Hero | キャッチコピー＋営業情報チップ |
| 2 | About | お店の説明と3つの特長 |
| 3 | Menu | Drinks 3品／Food 3品 |
| 4 | Space | 設備紹介（Wi-Fi・電源・ゾーニング・朝光） |
| 5 | Community | 月1の朝活イベント |
| 6 | Access | 住所・営業情報・地図プレースホルダ |
| 7 | Footer | SNSリンク・コピーライト |

## 🛠 使用技術

- **HTML5 / CSS3** — CSS Variables、CSS Grid、`clamp()` でフルードタイポグラフィ
- **Vanilla JavaScript** — スクロール検知のヘッダー切替、モバイルナビ開閉
- **Python + OpenAI API** — 画像一括生成スクリプト（内部利用）
- **OpenAI gpt-image-2** — 写真・アイコン両用の画像生成モデル

## 🤖 AI画像生成の工夫

19枚の画像はすべて Python スクリプトで一括生成しました。ポイントは以下：

1. **2系統のスタイル suffix** を切り替え可能にし、写真とアイコンを同じスクリプトで生成
   - 写真系: `"cohesive Japanese specialty cafe brand photography, beige and cream tones..."`
   - アイコン系: `"minimal flat vector icon illustration, two-tone duotone..."`
2. **共通スタイル文字列を全プロンプトに付与** することで、19枚全体のトーンを統一
3. **1コマンドで全画像を再生成可能** — ブランドの方向性が変わっても、プロンプト1行の修正で全画像作り直しが10分以内で完了

**生成コスト**: gpt-image-2 low品質で1枚 約¥0.9。19枚で **約¥17**。

## 📁 ファイル構成

```
morning-hill/
├── index.html      ... 本体LP
├── style.css       ... スタイル
├── script.js       ... モバイルナビ・スクロール挙動
├── images/         ... AI生成画像（19枚）
├── screenshots/    ... ポートフォリオ用キャプチャ（6枚）
├── BRIEF.md        ... 架空クライアントの制作ブリーフ
└── README.md       ... 本ファイル
```

## 📝 制作プロセス

1. クライアント設定書（BRIEF.md）作成
2. 構成・IA決定（7セクション）
3. HTML/CSS/JS 実装（初期版は duotone SVG アイコン）
4. 画像生成スクリプト構築（Python venv + OpenAI SDK）
5. AI画像生成 → アイコン・写真を差し替え
6. レスポンシブ確認・調整

## 🔁 ローカルで動かす

依存関係はないので、`index.html` を直接ブラウザで開くだけで動作確認できます。

```bash
# 簡易サーバーで開く場合（要 Python）
python -m http.server 8765
# → http://localhost:8765/
```

または `index.html` をダブルクリックでもOK。

---

ポートフォリオ作品 / 2026
