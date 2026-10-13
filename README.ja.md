<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><b>コマンド一つで、エージェントが AI 安全を毎日追いかけます：ジェイルブレイク、プロンプトインジェクション、エージェントセキュリティ、評価、インシデント、政策。さらに毎日 30 本の厳選論文。</b></p>

<p align="center">
  <a href="https://aisafetyhot.com/en"><img src="https://img.shields.io/badge/website-aisafetyhot.com-e4572e" alt="website"></a>
  <a href="https://aisafetyhot.com/api/mcp"><img src="https://img.shields.io/badge/MCP-streamable%20http-6f42c1" alt="MCP"></a>
  <a href="#skills"><img src="https://img.shields.io/badge/skills-6-2ea44f" alt="skills"></a>
  <a href="daily-papers"><img src="https://img.shields.io/badge/papers-30%2Fday-0969da" alt="daily papers"></a>
  <a href="https://github.com/wuyoscar/AISafetyHot-Hub/stargazers"><img src="https://img.shields.io/github/stars/wuyoscar/AISafetyHot-Hub?style=flat" alt="stars"></a>
</p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="https://aisafetyhot.com/en"><img src="assets/news-monitor-demo.webp" width="1000" alt="AI Safety HOT"></a></p>

## インストール

**Claude Code**（スキルと MCP をまとめて）

```bash
/plugin marketplace add wuyoscar/AISafetyHot-Hub
/plugin install aisafetyhot@aisafetyhot-hub
```

**Codex / Cursor / その他のエージェント**

```bash
npx skills add wuyoscar/AISafetyHot-Hub
codex mcp add aisafetyhot --url https://aisafetyhot.com/api/mcp
```

API キーは不要です。その他のクライアントは MCP サーバー `https://aisafetyhot.com/api/mcp`（Streamable HTTP）を追加してください。

<a id="skills"></a>

## スキル

普通の言葉で頼むだけで、エージェントがスキルを選びます：

| スキル | 内容 | 例 |
| --- | --- | --- |
| [`aisafety-brief`](skills/aisafety-brief/SKILL.md) | 直近 24 時間 / 7 日の AI 安全ブリーフ | 「今週の AI 安全の大きなニュースは？」 |
| [`aisafety-paper-scout`](skills/aisafety-paper-scout/SKILL.md) | 方向別の論文、一行要約と BibTeX 付き | 「エージェントへのプロンプトインジェクションの論文を 15 本、BibTeX 付きで」 |
| [`aisafety-related-work`](skills/aisafety-related-work/SKILL.md) | 要旨から関連研究の下書き | 「reward hacking の論文の related work を書いて」 |
| [`aisafety-lab-watch`](skills/aisafety-lab-watch/SKILL.md) | 一つのラボの最近の安全動向 | 「Anthropic は今週、安全面で何をした？」 |
| [`aisafety-incident-check`](skills/aisafety-incident-check/SKILL.md) | モデルやツールの最近のインシデント | 「Cursor に最近脆弱性は出た？」 |
| [`aisafetyhot`](skills/aisafetyhot/SKILL.md) | MCP ツールの説明（他のスキルの土台） | — |

MCP ツールと匿名で使える範囲は[エージェントガイド](docs/agent.md)と[例](docs/mcp-examples.md)へ。

## サイトの中身

[aisafetyhot.com](https://aisafetyhot.com/en) は無料で読めます（中国語・英語）。

**[概要](https://aisafetyhot.com/en)**：材料の出どころ、どの方向に落ちるか、いま何が熱いか。

<img src="assets/site-overview.webp" width="900" alt="概要">

**[ニュースフロー](https://aisafetyhot.com/en)**：各ニュースが情報源から方向へ流れ、届いた順にトピックが点灯します。

<img src="assets/site-news-flow.webp" width="900" alt="ニュースフロー">

**[News](https://aisafetyhot.com/en/featured)**：編集部のタイムライン。各記事に短い解説と原文リンク、横に注目トピック。

<img src="assets/site-featured.webp" width="900" alt="News">

**[ホット](https://aisafetyhot.com/en/hot)**：同じ出来事の報道を一つにまとめ、注目度順に、熱度カーブ付きで。

<img src="assets/site-hot.webp" width="900" alt="ホット">

**[論文](https://aisafetyhot.com/en/papers)**：約二千本の AI 安全論文。方向と種類で絞り込め、各論文に一行要約と速読。

<img src="assets/site-papers.webp" width="900" alt="論文">

**[会議](https://aisafetyhot.com/en/conferences)**：ICLR、ICML、NeurIPS、ACL と四大セキュリティ会議（S&P、USENIX Security、CCS、NDSS）の AI 安全論文を方向別に。

<img src="assets/site-conferences.webp" width="900" alt="会議">

**[日報](https://aisafetyhot.com/en/daily)**：毎日一号、方向別、その日のうちに更新。

<img src="assets/site-daily.webp" width="900" alt="日報">

誤りを見つけたら[掲示板](https://aisafetyhot.com/board)へ。

## 毎日の論文

ライブラリから毎日 30 本、重複なし。著名な研究者、トップラボ、有力大学のチームの論文だけを選びます：半分は直近二か月、残りは半年以内とそれ以前（会議論文を含む）、新しいもの優先。今日のリストと方向別索引は [daily-papers](daily-papers)（一行要約は中国語）。

## 支援

役に立ったら Star を、または[作者にコーヒーを](https://buymeacoffee.com/wuyoscar)。

<img src="assets/wechat-pay.png" width="160" alt="WeChat支援QRコード">
