---
name: new_article_pipeline
description: 18:00稼働。インボックスの案件を3人の専門エージェント（ディレクター、ビジュアルクリエイター、ライター）の分業体制で記事化するパイプライン。
---
# 記事生成 3分業パイプライン（18:00稼働用）

1. \engine/data/affiliate_candidates.md\ を確認し、新規案件があれば1つピックアップする。無ければ終了。

2. 案件をピックアップしたら、自分では執筆・生成を行わず、以下の3名のサブエージェントを順番に\invoke_subagent\で呼び出して（またはメッセージを送って）作業をリレーさせること。

## ① 構成ディレクター（Astra Outline Director）
- **役割:** 案件のLPや公式情報をリサーチし、Astraフレームワーク（三方良し、ROI、下位プランの提示等）に基づいた『最強のセールス記事の構成案（アウトライン）』を作成する。
- **指示:** `engine/data/資料庫/KGI達成ツール集.md` に記載されたツール（alternativeto.net, summarize.tech等）を駆使して競合や一次情報を収集すること。「どこに図解を入れるか」「どこにHyperFramesの動画を入れるか」「アイキャッチ画像はどんな指定にするか」の設計図も作成し、`engine/data/scratch/outline.md` に保存させる。

## ② ビジュアル＆動画クリエイター（Visual & Video Creator）
- **役割:** ①が作った構成案を読み込み、必要な全メディア資産を生成する。
- **指示:** `engine/data/資料庫/KGI達成ツール集.md` に従い、必要なら carbon.now.sh 等も活用。1. `generate_image` でアイキャッチを生成。 2. Mermaid記法でフローチャートや比較表を作成。 3. **HyperFramesスキル** を呼び出し、必要な動画（`faceless-explainer`など）を生成（`docs/assets/`へ保存）。完成したら報告させる。

## ③ セールス・ライター（Final Sales Writer）
- **役割:** ①の構成と、②が生成したアセット（画像、動画、図解）を統合し、最終的なMarkdown記事を執筆する。
- **指示:** 完成した記事を \docs/articles/商材名.md\ に保存し、\mkdocs.yml\ のナビゲーションに追記させる。

3. 3人のリレーが完了したら、インボックスから該当案件を削除し完了報告を行う。
