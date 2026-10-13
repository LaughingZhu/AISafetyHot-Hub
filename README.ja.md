<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><a href="https://aisafetyhot.com"><img src="assets/news-monitor-demo.gif" width="1000" alt="AI Safety HOT News Monitor"></a></p>

AI Safety HOTのエージェント接続ガイドと公開ブリーフのアーカイブです。サイトは[中国語](https://aisafetyhot.com/zh)と[英語](https://aisafetyhot.com/en)に対応し、初回は中国語で表示します。英訳は順次追加され、未翻訳の部分は原文のまま表示されます。この日本語READMEは利用案内であり、日本語の本文アーカイブではありません。

## ありがとうございます。公開範囲の変更について

応援ありがとうございます！AI Safety Hubは公開から数日で多くのアクセスをいただきました。攻撃の可能性がある不審なアクセスも確認し、遮断しました。私たち自身がAI安全性を研究しており、今後もサイトの防御を維持します。

運用費用、蓄積したコンテンツと長期的な維持を考慮し、**匿名APIで全データを公開する方式を変更します。直近の情報は引き続き利用しやすく公開します**。

| 範囲 | 公開内容 |
| --- | --- |
| News API | 原文の公開が直近 **7日間**のニュース。タイトル、最大 **160文字**の短い要約、判明している原文公開日時、原文・サイトへのリンク。検索とページ送りに対応 |
| 厳選論文 | 最近の厳選論文を最大 **5本**、タイトルとリンクで紹介 |
| 日報・出来事 | 直近7日間の号のNewsブリーフと、同じ出来事の最近の報道要約・リンク |
| 詳しい論文解説、全文、過去の検索、週報・月報、スナップショット・差分同期 | 読み取り権限が必要。[wuy7117@gmail.com](mailto:wuy7117@gmail.com)へ連絡してください |

原文の日付が不明な記事を収録時刻で新しい記事と扱うことはありません。サイトでの閲覧は引き続き無料で、公開ブリーフにログインは不要です。

<a id="website"></a>

## サイトで読む

[総覧](https://aisafetyhot.com/) · [News](https://aisafetyhot.com/featured) · [論文](https://aisafetyhot.com/papers) · [出来事](https://aisafetyhot.com/hot) · [日報](https://aisafetyhot.com/daily) · [会議論文](https://aisafetyhot.com/conferences)

ニュースの新しさは原文公開日時で判断し、北米の前日のニュースも考慮します。当日の同じ号を新しい報道に合わせて更新します。既存の詳しい論文解説は詳細ページで読めます。誤りは[掲示板](https://aisafetyhot.com/board)へお知らせください。

<a id="agent"></a>

## エージェントを接続

公開ブリーフにAPI Keyは不要です。接続方式は **Streamable HTTP**。以下を実行後、クライアントのセッションを開き直してください。

**Codex**

```bash
codex mcp add aisafetyhot --url https://aisafetyhot.com/api/mcp
```

**Claude Code**

```bash
claude mcp add --transport http --scope user aisafetyhot https://aisafetyhot.com/api/mcp
```

| MCPツール | 匿名の範囲 |
| --- | --- |
| `aisafetyhot_get_latest` | 24h/7dのNewsブリーフと厳選論文リンク |
| `aisafetyhot_search` | 同じ直近News範囲で検索・ページ送り |
| `aisafetyhot_get_content` | 最近のNews要約または現在の厳選論文リンク。`depth=summary` |
| `aisafetyhot_get_hot_topics` | 現在の出来事のタイトル、順位、閲覧リンク |
| `aisafetyhot_get_story` | 出来事の最近のNews要約とリンク。`depth=summary` |
| `aisafetyhot_get_daily` | 直近7日間の号のNewsブリーフ。`period=daily` |
| `aisafetyhot_get_topics` | トピック名、slug、定義 |

<a id="examples"></a>

### 使い方

`get_latest({window:"7d",mode:"all",limit:10})` を呼び、返されたIDで要約を読みます。検索は `search({q:"prompt injection",window:"7d",mode:"all"})`。条件を変えずに `page.nextCursor` をたどり、`page.hasMore=false` まで読みます。

`mode=all` は許可された期間内の全Newsです。`window=all`、`depth=full`、`mode=snapshot/changes` は権限が必要です。原文公開日時とサイト収録日時は別々に記録します。

匿名MCP・REST・RSSはIPごとに合計60回/分、1,000回/UTC日。超過すると429と `Retry-After` を返します。読み取り権限は `Authorization: Bearer <token>` を使用し、管理・書き込み権限は与えません。無効な資格情報は401、範囲外は403またはMCP `authorization_required` です。

[詳細ガイド（中国語）](docs/agent.md) · [例（中国語）](docs/mcp-examples.md) · [Agent Skill](skills/aisafetyhot/SKILL.md) · [OpenAPI](https://aisafetyhot.com/openapi-v1.json)

<a id="daily"></a>

## 日報ブリーフ

[最新号（中国語）](README.md#daily) · [日報アーカイブ](daily) · [サイトの完全な日報](https://aisafetyhot.com/daily)

既存の公開処理が15分ごとに更新を確認します。本文は主に中国語で、このREADMEは日本語の案内を提供します。

<a id="papers"></a>

## 論文リンクとアーカイブ

サイトでは新しい論文に加え、Promptfoo 2026 の論文など過去の研究も収録しています。全件の閲覧・検索は [Paper 論文一覧（中国語）](https://aisafetyhot.com/zh/papers) へ。Hub の表にある件数は出力済みの論文数で、サイトの当日の全収録数ではありません。一括収録した論文をここにすべて掲載するわけではありません。

**2026-10-12** 以降は毎日最大5本の厳選論文のタイトル、原文公開日時とリンクをMarkdown・BibTeX・JSONで出力します。要約、速読、詳しい解説は自動出力しません。ファイルの日付は北京時間の収録日で、原文公開日は別に記録します。

既に公開済みのアーカイブは残ります。APIの変更でダウンロード済みのコピーを回収することはできません。同期の照合は厳選リンク集合を対象とし、その他の論文はサイトで読めます。

[最新のダウンロード（中国語）](README.md#papers) · [論文](papers) · [日報](daily) · [2026アーカイブ](archive/2026.md) · [同期記録](status.json)

## 支援とフィードバック

役に立ったらStarを付けるか、[作者にコーヒーを](https://buymeacoffee.com/wuyoscar)お願いします。AIHOT、Security of AI、そして参考になったメディア、オープンソースのフレームワークとコミュニティに感謝します。

<img src="assets/wechat-pay.png" width="160" alt="WeChat支援QRコード">
