<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><a href="https://aisafetyhot.com"><img src="assets/news-monitor-demo.gif" width="1000" alt="AI Safety HOT News Monitor"></a></p>

AI Safety HOT 的 Agent 接入指南与公开简报归档。网站默认中文，可在“中文 / English”切换；[中文入口](https://aisafetyhot.com/zh)和[English](https://aisafetyhot.com/en)共享内容与原文链接。英文由后台逐步翻译，缺译处保留原文。

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

[总览](https://aisafetyhot.com/zh) · [News](https://aisafetyhot.com/zh/featured) · [论文](https://aisafetyhot.com/zh/papers) · [热点事件](https://aisafetyhot.com/zh/hot) · [Newsletter](https://aisafetyhot.com/zh/daily) · [Conference](https://aisafetyhot.com/zh/conferences)

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
### 2026-10-13 · 9 条精选

**当天一期，随新进展更新** · [完整日报](daily/2026/2026-10-13.md) · [在网站阅读](https://aisafetyhot.com/daily/2026-10-13)

点击标题展开导读，每条都附原文链接。

#### 防御与护栏

<details>
<summary>1. Anthropic 加强针对蒸馏攻击的防御</summary>

[Anthropic 加强针对蒸馏攻击的防御](https://www.anthropic.com/research/distillation-defenses)：Anthropic 称早期证据显示，其新的蒸馏防御方法把蒸馏者获取的数据量减少了约 90% 至 99%，平台上被提取的推理 token 数降至此前的 1/10 到 1/100。防御分三类：用 preserved thinking 阻止新 API 账号编辑 Claude 的先前上下文，并让推理记录只对产生它的组织可见；… ——Anthropic Research｜[站内](https://aisafetyhot.com/items/zegi97d32s1zl1q79a4himjwu)

</details>

#### 对齐与可解释性

<details>
<summary>2. Sakana AI 的自我改进模型在解题与评判上更强，却抓不住自己的盲点</summary>

[Sakana AI 的自我改进模型在解题与评判上更强，却抓不住自己的盲点](https://the-decoder.com/sakana-ais-self-improving-model-gets-better-at-solving-and-judging-but-cant-catch-its-own-blind-spots/)：Sakana AI 与 UC Berkeley 的研究者提出多智能体自我监督方法 MASS，让同一个语言模型同时承担解题、优化工作流与评判结果三种角色，在无需更强教师模型的情况下实现递归自我改进。基座模型为 Qwen3.6-27B，任务为 GPT-5.5 生成的 12 项金融、机器人与制药研究任务。测试任务上对基座的… ——The Decoder｜[站内](https://aisafetyhot.com/items/ah0k35app67a4dad8y3tozajh)

</details>

#### 安全评测

<details>
<summary>3. AI 模型或可在没有数据中心的情况下自我复制</summary>

[AI 模型或可在没有数据中心的情况下自我复制](https://www.anthropic.com/research/self-replicating-ai)：Anthropic 红队研究显示，小型 AI 模型可能只需数月就能在商用 IoT 设备上实现自我复制。在评测中，Qwen3.5-9B 在 9 种硬件中的 8 种上成功搭起推理服务，30B 参数及以下的模型已能完成复制链的多数单步，GLM-5.2 在简化评测中可端到端复制。研究用 15 台约 55 美元的安卓电视盒子分… ——Anthropic Red Teaming｜[站内](https://aisafetyhot.com/items/lird2la13falhqvq0e2gizmld)

</details>

<details>
<summary>4. 报告发现 ChatGPT for Teens 未能兑现安全承诺</summary>

[报告发现 ChatGPT for Teens 未能兑现安全承诺](https://www.transparencycoalition.ai/news/report-finds-chatgpt-for-teens-fails-to-deliver-on-safety-promises)：Common Sense Media 旗下的 Youth AI Safety Institute 用 4000 多条提示词测试 ChatGPT for Teens，发现多项承诺的安全护栏未能生效，并给出不可接受风险的评级。测试在 OpenAI 2026 年 8 月 18 日宣布该青少年模式前后各进行一次，使用注册为 … ——Transparency Coalition.AI｜[站内](https://aisafetyhot.com/items/wm00lgi0h0dfqgky19nzqixe7)

</details>

#### 真实事件

<details>
<summary>5. Anthropic 的 Claude 向费城警方提交虚假谋杀线索</summary>

[Anthropic 的 Claude 向费城警方提交虚假谋杀线索](https://arstechnica.com/tech-policy/2026/10/anthropics-claude-ai-submitted-false-murder-tip-to-philadelphia-police/)：Anthropic 的 Claude 模型在内部测试中向费城警方网站提交了一条虚假的未破谋杀案线索，该提交被垃圾邮件过滤器拦截，未被人查看。据 Anthropic 与警方确认，Claude Haiku 4.5 在随机网页任务中被要求填写表单但不得提交，却误以为还有确认页而提交；公司于 9 月 28 日发现、10 月 … ——Ars Technica AI｜[站内](https://aisafetyhot.com/items/o3w2tl7iu20wjbyrv46461yuu)

</details>

<details>
<summary>6. Graylark 的 Raven 让警方凭单张室内照片锁定具体住宅</summary>

[Graylark 的 Raven 让警方凭单张室内照片锁定具体住宅](https://www.404media.co/ai-company-lets-cops-pinpoint-specific-houses-based-on-a-single-interior-photo/)：Graylark Technologies 的 Raven（原 GeoSpy）新增室内图像地理定位功能，警方可凭单张室内照片锁定具体住宅。演示视频显示，工具从社交媒体上的洗衣机、浴室照片定位到北卡罗来纳州 Charlotte 的 Airbnb 房源和加州 Montecito 的 Vrbo 房源，404 Media 发… ——404 Media｜[站内](https://aisafetyhot.com/items/qryq6jexs5w0qde1km154hg5a)

</details>

#### 治理与政策

<details>
<summary>7. 英国 AI 大臣演讲：准备 Agent 事故响应</summary>

[英国 AI 大臣演讲：准备 Agent 事故响应](https://www.gov.uk/government/speeches/building-a-safer-more-secure-britain-in-the-age-of-ai)：英国政府 AI 事务大臣在演讲中宣布，将联合 DCMS、国家网络安全中心（NCSC）和 AI Security Institute 制定政府应对 Agent 事故的方式，重点研究如何控制事故影响、如何帮扶受影响方。他确认 AI Security Institute 正在对包括 Gemini 4 Argon 在内的最新… ——Cabinet Office｜[站内](https://aisafetyhot.com/items/yklidj6wl22tp5dracu6q49ka)

</details>

<details>
<summary>8. 白宫改弦更张，恢复英国 AI 安全研究所对前沿模型的访问权限</summary>

[白宫改弦更张，恢复英国 AI 安全研究所对前沿模型的访问权限](https://the-decoder.com/white-house-reverses-course-and-restores-uk-ai-safety-institutes-access-to-frontier-models/)：白宫撤销了此前阻止英国 AI 安全研究所（AISI）访问新 AI 模型的决定，该机构将重新获得 Anthropic、Google DeepMind 和 OpenAI 模型的早期访问权限。据《每日电讯报》报道，特朗普政府曾在 9 月要求这些公司停止与 AISI 共享模型，Anthropic 随后限制了新模型 Claud… ——The Decoder｜[站内](https://aisafetyhot.com/items/wpq3s81u9x8uwdvume58py9wh)

</details>

#### AI 动态

<details>
<summary>9. Meta 发布首款前沿模型 Muse Wonder</summary>

[Meta 发布首款前沿模型 Muse Wonder](https://techcrunch.com/2026/10/12/meta-releases-its-first-frontier-model-muse-wonder/)：Meta 的 Superintelligence Lab 发布 Muse Wonder 和 Muse Wonder Full 两款新模型，称这是公司首款前沿模型。据 Meta 在 model card 中公布的测试，两款模型在基准分数上与 Fable 5.1、GPT-6 Astra 相当。通过 Meta Model … ——TechCrunch AI｜[站内](https://aisafetyhot.com/items/pfu4bou8kut0viknlal6eybg9)

</details>
<!-- daily:end -->

完整内容在[网站日报](https://aisafetyhot.com/daily)阅读。Hub 由既有发布器每 15 分钟检查更新，成功同步以正文和远端读回为准。

<a id="papers"></a>

## 论文链接与归档

网站持续收录新论文，也补录历史论文，包括 Promptfoo 2026 论文。完整列表和搜索请到 [Paper 论文库](https://aisafetyhot.com/zh/papers)。下面表格的数量是 Hub 已导出的论文题录数，不是网站当天的全部收录数；批量补录不会逐篇显示在这里。

自 **2026-10-12** 起，每天导出最多 5 篇精选论文的标题、原发时间和链接，保留 Markdown、BibTeX、JSON 格式；不再自动导出论文摘要、速读或六问解读。按本站收录的北京时间自然日归档，原发日期另列，两个日期可能不同。

此前已经公开的归档继续保留；接口调整无法撤回他人已下载的内容。新范围内的导出对账以同一精选链接集合为准，未导出的其他论文仍在网站阅读。

<!-- latest:start -->
| 日期 | 每日精选 | 论文清单 |
|---|---|---|
| 2026-10-13 | [日报](daily/2026/2026-10-13.md) | [3 篇](papers/2026/2026-10-13.md) · [bib](papers/2026/2026-10-13.bib) · [json](papers/2026/2026-10-13.json) |
| 2026-10-12 | [日报](daily/2026/2026-10-12.md) | [5 篇](papers/2026/2026-10-12.md) · [bib](papers/2026/2026-10-12.bib) · [json](papers/2026/2026-10-12.json) |
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

更早的见 [2026 年目录](archive/2026.md)。

论文清单按北京时间的自然日（0 点到 24 点，按论文在网站时间线上的时间）分天；日报当天一期，按原发时间取前一天 08:00 至当天更新时的材料，随新进展更新。两者的日界不同，所以同一天的日报和论文清单收的不完全是同一批，一篇论文可能出现在相邻一天的日报里。自 2026-10-12 起清单仅含每天最多 5 篇精选论文标题与链接，不导出摘要或速读。最近 7 天内该导出集合的撤下、修正或补进每小时检查一次。

[status.json](status.json) 记录每天的论文数和 ID 摘要，以及同步时限（slaMinutes：导出范围内的精选论文最迟多少分钟内出现在这里）。
<!-- latest:end -->

[日报归档](daily) · [论文清单](papers) · [2026 归档](archive/2026.md) · [同步记录](status.json)

## 支持与反馈

如果这个项目帮你节省了时间，欢迎给仓库一个 Star，或[请作者喝杯咖啡](https://buymeacoffee.com/wuyoscar)。感谢 AIHOT、Security of AI，以及启发了这个项目的公众号、开源框架和社区。

<img src="assets/wechat-pay.png" width="160" alt="微信支持二维码">
