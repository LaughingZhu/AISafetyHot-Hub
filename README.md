<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><a href="https://aisafetyhot.com"><img src="assets/news-monitor-demo.gif" width="1000" alt="AI Safety HOT News Monitor"></a></p>

AI Safety HOT 的 Agent 接入指南与公开简报归档。新闻、论文和完整阅读入口在 [aisafetyhot.com](https://aisafetyhot.com)。

## 感谢大家，也说一下接口调整

感谢大家的喜欢！AI Safety Hub 上线几天就迎来了大量访问。我们也观察到了一些疑似攻击的访问，并进行了拦截。我们本身研究 AI 安全，也会持续维护网站的防护。

考虑到服务成本、内容积累和长期维护，**我们不再通过匿名接口开放全部数据，但会继续做好近期信息的开放和可用性**：

| 范围 | 现在提供什么 |
| --- | --- |
| 匿名 News 接口 | 原发最近 **7 天**的新闻标题、最多 **160 字**的短摘要、已知原发时间、原文链接和本站链接；支持搜索与分页 |
| 少量精选论文 | 最多 **5 篇**近期精选论文的标题与链接，方便回网站阅读 |
| 日报与事件 | 最近 7 天内日报的 News 简报，以及同一事件的近期新闻摘要与链接 |
| 完整论文解读、正文、历史查询、周报/月报、全量与增量同步 | 需要只读授权，联系 [wuy7117@gmail.com](mailto:wuy7117@gmail.com) |

未知原发日期的材料不会凭收录时间进入近期 News。网站继续免费阅读，公开简报继续无需登录。

<a id="website"></a>

## 在网站阅读

[总览](https://aisafetyhot.com/) · [News](https://aisafetyhot.com/featured) · [论文](https://aisafetyhot.com/papers) · [热点事件](https://aisafetyhot.com/hot) · [日报](https://aisafetyhot.com/daily) · [会议论文](https://aisafetyhot.com/conferences)

新闻和日报按原发时间判断新进展，兼顾北美前一天。当天同一期日报会随新报道更新。论文完整速读与已有解读在详情页阅读。发现内容错误，欢迎在[留言板](https://aisafetyhot.com/board)反馈。

<a id="agent"></a>

## 接入 Agent

公开简报不需要 API Key，连接方式为 **Streamable HTTP**。运行以下命令后重新打开客户端会话：

**Codex**

```bash
codex mcp add aisafetyhot --url https://aisafetyhot.com/api/mcp
```

**Claude Code**

```bash
claude mcp add --transport http --scope user aisafetyhot https://aisafetyhot.com/api/mcp
```

| MCP 工具 | 匿名可用范围 |
| --- | --- |
| `aisafetyhot_get_latest` | 最近 24 小时或 7 天的 News 简报，附少量精选论文链接 |
| `aisafetyhot_search` | 同范围 News 搜索和分页 |
| `aisafetyhot_get_content` | 近期新闻短摘要、当前精选论文链接；`depth=summary` |
| `aisafetyhot_get_hot_topics` | 当前热点标题、排名和阅读入口 |
| `aisafetyhot_get_story` | 事件近期 News 摘要与链接；`depth=summary` |
| `aisafetyhot_get_daily` | 最近 7 天内的日报 News 简报；`period=daily` |
| `aisafetyhot_get_topics` | 话题名称、slug 与定义 |

<a id="examples"></a>

### 怎么用

让 Agent 调用 `get_latest({window:"7d",mode:"all",limit:10})`，再通过返回的 ID 读取短摘要。搜索用 `search({q:"prompt injection",window:"7d",mode:"all"})`。同一筛选下沿 `page.nextCursor` 翻页，直到 `page.hasMore=false`。

`mode=all` 表示同一近期范围内全部 News；`window=all`、`depth=full`、`mode=snapshot/changes` 需要授权。原发时间与收录时间分别保留，不混为一谈。

匿名 MCP、REST 与 RSS 合计每 IP 最多 60 次/分钟、1,000 次/UTC 日；超额返回 429 与 `Retry-After`。只读授权使用 `Authorization: Bearer <令牌>`，不授予管理或写入权限。无效凭证返回 401，超范围返回 403 或 MCP `authorization_required`。

[详细指南](docs/agent.md) · [使用示例](docs/mcp-examples.md) · [Agent Skill](skills/aisafetyhot/SKILL.md) · [OpenAPI](https://aisafetyhot.com/openapi-v1.json)

<a id="daily"></a>

## 最新 AI 安全日报简报

<!-- daily:start -->
### 2026-10-12 · 1 条精选

**当天一期，随新进展更新** · [完整日报](daily/2026/2026-10-12.md) · [在网站阅读](https://aisafetyhot.com/daily/2026-10-12)

点击标题展开导读，每条都附原文链接。

#### 治理与政策

<details>
<summary>1. 白宫改口，英国 AISI 恢复对三家美国实验室模型的发布前测试权</summary>

[白宫改口，英国 AISI 恢复对三家美国实验室模型的发布前测试权](https://www.telegraph.co.uk/news/2026/10/11/britain-get-first-look-ai-systems-after-white-house-u-turn)：白宫撤销了要求美国 AI 公司停止向英国 AISI 共享模型的决定，英国 AI 安全研究所将恢复对 Anthropic、Google DeepMind 和 OpenAI 最新模型的发布前安全测试权限。上个月，白宫国家网络主管办公室下达该要求后，Anthropic 曾限制英国官员审查其新的 Claude Mythos … ——The Telegraph｜[站内](https://aisafetyhot.com/items/vc7xwhti3s1b2uvwgnr93o27u)

</details>
<!-- daily:end -->

完整内容在[网站日报](https://aisafetyhot.com/daily)阅读。Hub 由既有发布器每 15 分钟检查更新，成功同步以正文和远端读回为准。

<a id="papers"></a>

## 论文链接与归档

自 **2026-10-12** 起，每天导出最多 5 篇精选论文的标题、原发时间和链接，保留 Markdown、BibTeX、JSON 格式；不再自动导出论文摘要、速读或六问解读。按本站收录的北京时间自然日归档，原发日期另列，两个日期可能不同。

此前已经公开的归档继续保留；接口调整无法撤回他人已下载的内容。新范围内的导出对账以同一精选链接集合为准，未导出的其他论文仍在网站阅读。

<!-- latest:start -->
| 日期 | 每日精选 | 论文清单 |
|---|---|---|
| 2026-10-12 | [日报](daily/2026/2026-10-12.md) | [4 篇](papers/2026/2026-10-12.md) · [bib](papers/2026/2026-10-12.bib) · [json](papers/2026/2026-10-12.json) |
| 2026-10-11 | [日报](daily/2026/2026-10-11.md) | [12 篇](papers/2026/2026-10-11.md) · [bib](papers/2026/2026-10-11.bib) · [json](papers/2026/2026-10-11.json) |
| 2026-10-10 | [日报](daily/2026/2026-10-10.md) | [12 篇](papers/2026/2026-10-10.md) · [bib](papers/2026/2026-10-10.bib) · [json](papers/2026/2026-10-10.json) |
| 2026-10-09 | [日报](daily/2026/2026-10-09.md) | [164 篇](papers/2026/2026-10-09.md) · [bib](papers/2026/2026-10-09.bib) · [json](papers/2026/2026-10-09.json) |
| 2026-10-08 | [日报](daily/2026/2026-10-08.md) | [189 篇](papers/2026/2026-10-08.md) · [bib](papers/2026/2026-10-08.bib) · [json](papers/2026/2026-10-08.json) |
| 2026-10-07 | [日报](daily/2026/2026-10-07.md) | [97 篇](papers/2026/2026-10-07.md) · [bib](papers/2026/2026-10-07.bib) · [json](papers/2026/2026-10-07.json) |
| 2026-10-06 | [日报](daily/2026/2026-10-06.md) | [118 篇](papers/2026/2026-10-06.md) · [bib](papers/2026/2026-10-06.bib) · [json](papers/2026/2026-10-06.json) |
| 2026-10-05 | [日报](daily/2026/2026-10-05.md) | [98 篇](papers/2026/2026-10-05.md) · [bib](papers/2026/2026-10-05.bib) · [json](papers/2026/2026-10-05.json) |
| 2026-10-04 | [日报](daily/2026/2026-10-04.md) | [143 篇](papers/2026/2026-10-04.md) · [bib](papers/2026/2026-10-04.bib) · [json](papers/2026/2026-10-04.json) |
| 2026-10-03 | [日报](daily/2026/2026-10-03.md) | [82 篇](papers/2026/2026-10-03.md) · [bib](papers/2026/2026-10-03.bib) · [json](papers/2026/2026-10-03.json) |
| 2026-10-02 | [日报](daily/2026/2026-10-02.md) | [56 篇](papers/2026/2026-10-02.md) · [bib](papers/2026/2026-10-02.bib) · [json](papers/2026/2026-10-02.json) |
| 2026-10-01 | [日报](daily/2026/2026-10-01.md) | [550 篇](papers/2026/2026-10-01.md) · [bib](papers/2026/2026-10-01.bib) · [json](papers/2026/2026-10-01.json) |
| 2026-09-30 | [日报](daily/2026/2026-09-30.md) | [39 篇](papers/2026/2026-09-30.md) · [bib](papers/2026/2026-09-30.bib) · [json](papers/2026/2026-09-30.json) |
| 2026-09-29 | [日报](daily/2026/2026-09-29.md) | [0 篇](papers/2026/2026-09-29.md) · [bib](papers/2026/2026-09-29.bib) · [json](papers/2026/2026-09-29.json) |

更早的见 [2026 年目录](archive/2026.md)。

论文清单按北京时间的自然日（0 点到 24 点，按论文在网站时间线上的时间）分天；日报当天一期，按原发时间取前一天 08:00 至当天更新时的材料，随新进展更新。两者的日界不同，所以同一天的日报和论文清单收的不完全是同一批，一篇论文可能出现在相邻一天的日报里。自 2026-10-12 起清单仅含每天最多 5 篇精选论文标题与链接，不导出摘要或速读。最近 7 天内该导出集合的撤下、修正或补进每小时检查一次。

[status.json](status.json) 记录每天的论文数和 ID 摘要，以及同步时限（slaMinutes：导出范围内的精选论文最迟多少分钟内出现在这里）。
<!-- latest:end -->

[日报归档](daily) · [论文清单](papers) · [2026 归档](archive/2026.md) · [同步记录](status.json)

## 支持与反馈

如果这个项目帮你节省了时间，欢迎给仓库一个 Star，或[请作者喝杯咖啡](https://buymeacoffee.com/wuyoscar)。感谢 AIHOT、Security of AI，以及启发了这个项目的公众号、开源框架和社区。

<img src="assets/wechat-pay.png" width="160" alt="微信支持二维码">
