# TechLink Archive

TechLink Archive 是一个面向技术研究者、开发者与信息分析人员的结构化外链资源汇总平台。本项目针对当前技术文档分散、优质外链缺乏统一索引、历史页面难以回溯的痛点，提供了一套基于静态站点生成的高密度资源导航系统。项目定位为“技术外链的固定锚点”，不提供内容抓取与存储，而是通过严格的 URL 清单管理，为特定技术主题域（如移动端开发、CVS 接口规范、IFC 数据交换、前端工程化等）建立可维护、可审计、可版本化的外部引用基线。

本项目适用于需要长期维护技术文档外链列表的团队、构建领域知识图谱的研究者，以及希望将零散书签转化为可持续开源资产的技术作者。通过将外链列表纳入版本控制，TechLink Archive 使得外部资源的变更可追溯、失效链接可检测、引用关系可分析，从而显著降低技术文档中外链腐烂带来的维护成本。

## 功能概览

**结构化资源索引** 提供统一的 URL 清单管理方式，所有外链以纯文本列表形式维护，便于脚本解析与变更比对。

**批次化导入机制** 支持按批次（每批 200 条）导入原始 URL 数据，并自动校验 URL 格式完整性，适合大规模历史链接的迁移与整理。

**静态站点生成适配** 项目目录结构设计兼容主流静态站点生成器（如 Hugo、Jekyll、VuePress），可直接将资源列表渲染为可浏览的 HTML 页面。

**字段扩展与标注能力** 每条资源可附加自定义元数据（如分类标签、收录日期、失效状态、备注说明），通过独立的数据表或 frontmatter 实现。

**脚本化健康检查** 内置基于 curl 的链接可达性检测脚本，支持定时任务运行，输出失效链接报告，帮助维护者及时发现并处理死链。

**Markdown 原生交付** 所有文档与资源列表均以 Markdown 格式呈现，保证在 GitHub、GitLab、Gitee 等平台上的良好可读性，同时便于本地编辑与离线查看。

## 应用场景

**技术文档外链规范化管理** 当技术团队撰写设计文档、API 参考或架构说明时，需要引用大量外部规范、SDK 下载页或社区讨论帖。TechLink Archive 可作为这些外链的单一事实来源，团队在归档中维护 URL 列表，文档中仅引用列表中的条目 ID，从而避免 URL 散落在各篇文档中难以统一更新。

**领域知识图谱的 URL 基础设施** 研究者在构建移动端开发或数据交换标准领域的知识图谱时，需要将大量相关网页作为证据节点。本项目提供的结构化列表可直接作为图谱的边数据集输入，配合 Python 或 Cypher 脚本批量导入图数据库。

**开源项目 README 外链集中治理** 开源项目的 README 中往往包含多个“参考链接”或“相关项目”外部链接。随着项目迭代，这些链接容易过时。通过将外链迁移至 TechLink Archive 独立管理，并在 README 中统一引用本项目的资源列表章节，可大幅提升链接维护效率。

**历史页面迁移的资源清单重建** 在网站改版或 CMS 系统切换时，历史页面中的外部链接清单往往散乱丢失。本项目可作为中间层，将导出的旧链接清单整理为标准 Markdown 列表，便于后续批量替换或重定向映射。

## 快速开始

以下命令演示了如何将本仓库克隆至本地，安装基础依赖并运行示例索引脚本。

```bash
git clone https://github.com/techlink-archive/techlink-archive.git
cd techlink-archive
npm install -g markdown-link-check@3.11.2
python3 scripts/validate_urls.py --input resources/links.md --output reports/validation.json
```

如需生成静态站点预览，请确保已安装 Node.js 18+ 和 Python 3.9+，然后执行：

```bash
python3 scripts/build_index.py --source resources/ --dist dist/
npx http-server dist/ -p 8080
```

访问 http://localhost:8080 即可查看生成的资源索引页面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 运行 URL 校验、批次合并与索引生成脚本 |
| Node.js | 18.x LTS 或更新 | 用于本地预览服务器以及可选的 Markdown 链接检查工具 |
| Git | 2.25 及以上 | 克隆仓库和管理版本变更 |
| curl | 7.68 及以上 | 用于链接健康检查脚本中的网络请求 |
| grep | 3.4 及以上 | 配合 curl 提取响应状态码与重定向信息 |
| jq | 1.6 及以上 | 解析和格式化 JSON 格式的校验报告 |
| markdown-link-check | 3.11.2 | 可选依赖，用于深度扫描 Markdown 中的链接 |
| http-server | 14.1.0 | 可选依赖，用于本地预览静态站点 |
| make | 4.2 及以上 | 可选，用于运行 Makefile 中封装的自动化任务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户文档 | docs/user-guide.md | 如何使用本资源列表进行日常查询与引用？如何理解批次编号与条目 ID？ |
| 维护手册 | docs/maintainer-guide.md | 如何新增一个批次？如何运行链接失效检测？如何更新已有条目的元数据？ |
| 脚本参考 | scripts/README.md | validate_urls.py、build_index.py、check_health.sh 各脚本的参数说明与使用示例 |
| 设计文档 | docs/design.md | 项目的目录结构设计决策、数据流说明、以及扩展性考量（如增加分类层级） |
| 贡献指南 | CONTRIBUTING.md | 外部贡献者如何提交新增链接批次、如何报告失效链接、如何改进脚本工具链 |
| 常见问题 | docs/faq.md | 关于 URL 格式要求、协议处理规则、大小写敏感性的详细说明与澄清 |
| 变更日志 | CHANGELOG.md | 记录每个批次新增的条目数量、脚本版本更新、以及重大结构变更 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/details/5854089.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3878.sHtML
- http://www.mobile.cvsifc.cn/Article/details/998813.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2869971.sHtML
- http://www.mobile.cvsifc.cn/Article/details/314535.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5519.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8624.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7403312.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1507534.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3730896.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8936945.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18129.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2899.sHtML
- http://www.mobile.cvsifc.cn/Article/details/00946.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6328327.sHtML
- http://www.mobile.cvsifc.cn/Article/details/137586.sHtML
- http://www.mobile.cvsifc.cn/Article/details/46652.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1587.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7808.sHtML
- http://www.mobile.cvsifc.cn/Article/details/699288.sHtML
- http://www.mobile.cvsifc.cn/Article/details/53977.sHtML
- http://www.mobile.cvsifc.cn/Article/details/20887.sHtML
- http://www.mobile.cvsifc.cn/Article/details/07693.sHtML
- http://www.mobile.cvsifc.cn/Article/details/153449.sHtML
- http://www.mobile.cvsifc.cn/Article/details/62716.sHtML
- http://www.mobile.cvsifc.cn/Article/details/88958.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5402.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8693698.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7451573.sHtML
- http://www.mobile.cvsifc.cn/Article/details/76109.sHtML
- http://www.mobile.cvsifc.cn/Article/details/640473.sHtML
- http://www.mobile.cvsifc.cn/Article/details/429850.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3531.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5386385.sHtML
- http://www.mobile.cvsifc.cn/Article/details/20426.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7316.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1280.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2504257.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6372.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4161376.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2098650.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0055.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4419844.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1259.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7098388.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8586171.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4192170.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1646604.sHtML
- http://www.mobile.cvsifc.cn/Article/details/798789.sHtML
- http://www.mobile.cvsifc.cn/Article/details/15059.sHtML
- http://www.mobile.cvsifc.cn/Article/details/69347.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5831210.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8313457.sHtML
- http://www.mobile.cvsifc.cn/Article/details/621592.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2161.sHtML
- http://www.mobile.cvsifc.cn/Article/details/20680.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9965157.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6495.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4493.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6451181.sHtML
- http://www.mobile.cvsifc.cn/Article/details/457529.sHtML
- http://www.mobile.cvsifc.cn/Article/details/287744.sHtML
- http://www.mobile.cvsifc.cn/Article/details/97999.sHtML
- http://www.mobile.cvsifc.cn/Article/details/92018.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1637.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2891.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5627530.sHtML
- http://www.mobile.cvsifc.cn/Article/details/235728.sHtML
- http://www.mobile.cvsifc.cn/Article/details/898139.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6179.sHtML
- http://www.mobile.cvsifc.cn/Article/details/67744.sHtML
- http://www.mobile.cvsifc.cn/Article/details/36560.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4616627.sHtML
- http://www.mobile.cvsifc.cn/Article/details/793416.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8324.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9271.sHtML
- http://www.mobile.cvsifc.cn/Article/details/422609.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8075.sHtML
- http://www.mobile.cvsifc.cn/Article/details/784937.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9283651.sHtML
- http://www.mobile.cvsifc.cn/Article/details/86988.sHtML
- http://www.mobile.cvsifc.cn/Article/details/717426.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6833036.sHtML
- http://www.mobile.cvsifc.cn/Article/details/338678.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24153.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0476.sHtML
- http://www.mobile.cvsifc.cn/Article/details/715825.sHtML
- http://www.mobile.cvsifc.cn/Article/details/25059.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7622699.sHtML
- http://www.mobile.cvsifc.cn/Article/details/694758.sHtML
- http://www.mobile.cvsifc.cn/Article/details/50276.sHtML
- http://www.mobile.cvsifc.cn/Article/details/592527.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2795771.sHtML
- http://www.mobile.cvsifc.cn/Article/details/21653.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3294.sHtML
- http://www.mobile.cvsifc.cn/Article/details/80836.sHtML
- http://www.mobile.cvsifc.cn/Article/details/89037.sHtML
- http://www.mobile.cvsifc.cn/Article/details/85125.sHtML
- http://www.mobile.cvsifc.cn/Article/details/860123.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2522106.sHtML
- http://www.mobile.cvsifc.cn/Article/details/31289.sHtML
- http://www.mobile.cvsifc.cn/Article/details/41819.sHtML
- http://www.mobile.cvsifc.cn/Article/details/63885.sHtML
- http://www.mobile.cvsifc.cn/Article/details/14072.sHtML
- http://www.mobile.cvsifc.cn/Article/details/515792.sHtML
- http://www.mobile.cvsifc.cn/Article/details/793226.sHtML
- http://www.mobile.cvsifc.cn/Article/details/957893.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24081.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8881281.sHtML
- http://www.mobile.cvsifc.cn/Article/details/89276.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9018659.sHtML
- http://www.mobile.cvsifc.cn/Article/details/60455.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5575.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13215.sHtML
- http://www.mobile.cvsifc.cn/Article/details/76447.sHtML
- http://www.mobile.cvsifc.cn/Article/details/942699.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18995.sHtML
- http://www.mobile.cvsifc.cn/Article/details/083683.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9944001.sHtML
- http://www.mobile.cvsifc.cn/Article/details/156294.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3791597.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0922083.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2018.sHtML
- http://www.mobile.cvsifc.cn/Article/details/110330.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7728467.sHtML
- http://www.mobile.cvsifc.cn/Article/details/04487.sHtML
- http://www.mobile.cvsifc.cn/Article/details/472684.sHtML
- http://www.mobile.cvsifc.cn/Article/details/05800.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7806.sHtML
- http://www.mobile.cvsifc.cn/Article/details/663201.sHtML
- http://www.mobile.cvsifc.cn/Article/details/11154.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4884.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4889552.sHtML
- http://www.mobile.cvsifc.cn/Article/details/07668.sHtML
- http://www.mobile.cvsifc.cn/Article/details/85648.sHtML
- http://www.mobile.cvsifc.cn/Article/details/430108.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2832739.sHtML
- http://www.mobile.cvsifc.cn/Article/details/89739.sHtML
- http://www.mobile.cvsifc.cn/Article/details/79273.sHtML
- http://www.mobile.cvsifc.cn/Article/details/44543.sHtML
- http://www.mobile.cvsifc.cn/Article/details/647128.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1105.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4251.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6055300.sHtML
- http://www.mobile.cvsifc.cn/Article/details/72144.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4872.sHtML
- http://www.mobile.cvsifc.cn/Article/details/33783.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18502.sHtML
- http://www.mobile.cvsifc.cn/Article/details/415303.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0366202.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6419.sHtML
- http://www.mobile.cvsifc.cn/Article/details/573865.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1899.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2395.sHtML
- http://www.mobile.cvsifc.cn/Article/details/14002.sHtML
- http://www.mobile.cvsifc.cn/Article/details/67013.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2487.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9219.sHtML
- http://www.mobile.cvsifc.cn/Article/details/001313.sHtML
- http://www.mobile.cvsifc.cn/Article/details/12387.sHtML
- http://www.mobile.cvsifc.cn/Article/details/15226.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3400.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7166119.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6993.sHtML
- http://www.mobile.cvsifc.cn/Article/details/629642.sHtML
- http://www.mobile.cvsifc.cn/Article/details/228407.sHtML
- http://www.mobile.cvsifc.cn/Article/details/532980.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4807.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9605872.sHtML
- http://www.mobile.cvsifc.cn/Article/details/019945.sHtML
- http://www.mobile.cvsifc.cn/Article/details/240868.sHtML
- http://www.mobile.cvsifc.cn/Article/details/51289.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6451131.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1890.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6235293.sHtML
- http://www.mobile.cvsifc.cn/Article/details/800270.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5964.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9721661.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2434398.sHtML
- http://www.mobile.cvsifc.cn/Article/details/53737.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4725604.sHtML
- http://www.mobile.cvsifc.cn/Article/details/097791.sHtML
- http://www.mobile.cvsifc.cn/Article/details/189173.sHtML
- http://www.mobile.cvsifc.cn/Article/details/160542.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9629164.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3401364.sHtML
- http://www.mobile.cvsifc.cn/Article/details/88403.sHtML
- http://www.mobile.cvsifc.cn/Article/details/101996.sHtML
- http://www.mobile.cvsifc.cn/Article/details/14695.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8059499.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8449045.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2132280.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13315.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6539289.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8204.sHtML
- http://www.mobile.cvsifc.cn/Article/details/36198.sHtML
- http://www.mobile.cvsifc.cn/Article/details/944200.sHtML
- http://www.mobile.cvsifc.cn/Article/details/988354.sHtML
- http://www.mobile.cvsifc.cn/Article/details/79171.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0070122.sHtML
- http://www.mobile.cvsifc.cn/Article/details/62140.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9636.sHtML
- http://www.mobile.cvsifc.cn/Article/details/663892.sHtML
- http://www.mobile.cvsifc.cn/Article/details/645303.sHtML
- http://www.mobile.cvsifc.cn/Article/details/88935.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5844134.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2678.sHtML
- http://www.mobile.cvsifc.cn/Article/details/799876.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2869.sHtML
- http://www.mobile.cvsifc.cn/Article/details/796600.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3415.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6011.sHtML
- http://www.mobile.cvsifc.cn/Article/details/25995.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5162777.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7678818.sHtML
- http://www.mobile.cvsifc.cn/Article/details/291995.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0003.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1659643.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0348323.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24227.sHtML
- http://www.mobile.cvsifc.cn/Article/details/567649.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4949.sHtML
- http://www.mobile.cvsifc.cn/Article/details/07066.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7921894.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9962.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24119.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1847.sHtML
- http://www.mobile.cvsifc.cn/Article/details/016555.sHtML
- http://www.mobile.cvsifc.cn/Article/details/095701.sHtML
- http://www.mobile.cvsifc.cn/Article/details/71773.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3388.sHtML
- http://www.mobile.cvsifc.cn/Article/details/779995.sHtML
- http://www.mobile.cvsifc.cn/Article/details/841294.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1753432.sHtML
- http://www.mobile.cvsifc.cn/Article/details/817054.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0563475.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5765.sHtML
- http://www.mobile.cvsifc.cn/Article/details/840458.sHtML
- http://www.mobile.cvsifc.cn/Article/details/10550.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0181.sHtML
- http://www.mobile.cvsifc.cn/Article/details/99285.sHtML
- http://www.mobile.cvsifc.cn/Article/details/606558.sHtML
- http://www.mobile.cvsifc.cn/Article/details/70205.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5339.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7482167.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8506724.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6640.sHtML
- http://www.mobile.cvsifc.cn/Article/details/319968.sHtML
- http://www.mobile.cvsifc.cn/Article/details/32799.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5997299.sHtML

## 项目结构

```
techlink-archive/
├── resources/                        # 核心资源清单目录
│   ├── links.md                      # 主资源列表（所有批次汇总）
│   ├── batches/                      # 按批次拆分的原始清单
│   │   ├── batch_121_200.md          # 第 121/200 批原始数据
│   │   └── batch_metadata.json       # 批次元数据（批次号、收录时间、条目数）
│   └── tags/                         # 分类标签索引
│       ├── mobile.md                 # 移动端相关条目聚合
│       └── protocol.md               # 协议规范相关条目聚合
├── scripts/                          # 工具脚本目录
│   ├── validate_urls.py              # URL 格式与协议校验脚本
│   ├── build_index.py                # 从 links.md 生成静态索引页
│   ├── check_health.sh               # 基于 curl 的链接存活检查
│   └── utils/                        # 公共函数库
│       ├── parsers.py                # 解析 Markdown 列表中的 URL
│       └── reporters.py              # 生成 JSON/HTML 格式报告
├── dist/                             # 静态站点输出目录（由脚本生成）
│   ├── index.html                    # 首页索引
│   └── reports/                      # 健康检查报告归档
├── docs/                             # 项目文档
│   ├── user-guide.md                 # 用户指南
│   ├── maintainer-guide.md           # 维护者手册
│   └── design.md                     # 设计文档
├── tests/                            # 单元测试与集成测试
│   ├── test_validator.py             # validate_urls 单元测试
│   └── fixtures/                     # 测试用固定样本数据
├── .github/                          # GitHub 社区配置
│   ├── workflows/                    # CI 工作流（自动运行链接检查）
│   │   └── health-check.yml
│   └── ISSUE_TEMPLATE/               # 问题报告模板（失效链接、新增批次）
├── Makefile                          # 封装常用任务（validate, build, serve）
├── CHANGELOG.md                      # 变更日志
├── CONTRIBUTING.md                   # 贡献指南
└── README.md                         # 本文件
```

## 贡献指南

**提交新增资源批次** 如果希望扩充资源列表，请先将新 URL 整理为 Markdown 无序列表格式，置于 resources/batches/ 下新的批次文件中。命名遵循 batch_{起始编号}_{结束编号}.md 规范。随后运行 validate_urls.py 进行格式预检，通过后发起 Pull Request。

**报告失效链接** 若发现资源列表中的 URL 返回 4xx 或 5xx 状态码，请通过 GitHub Issues 提交报告。报告模板需包含失效 URL 的完整条目、检测时间以及预期可访问的新地址（如果已知）。项目维护者将定期合并失效报告并更新列表。

**改进脚本工具链** 项目接受关于 validate_urls.py、check_health.sh 等脚本的功能增强与性能优化。提交前请确保已通过 tests/ 目录下的全部单元测试，并在 PR 描述中说明修改动机、兼容性影响以及新增测试用例。

**完善项目文档** 欢迎对 docs/ 目录下的用户指南、维护手册或设计文档进行补充与勘误。文档更新应保持与技术实现同步，涉及命令行示例的部分需经过实际运行验证。

**参与社区讨论** 在 GitHub Discussions 中可围绕项目发展方向、批次分类策略、链接检测频率等问题展开讨论。具有共识的改进建议将纳入项目路线图。

## 常见问题

**问：为什么资源列表中的 URL 必须保持原样，不能统一补充 http:// 或 https:// 前缀？**

答：本项目定位为外链的精确锚点，而非链接修复工具。原始数据中的协议、域名、路径大小写以及文件扩展名（如 .sHtML）均视为条目指纹的一部分。统一改写会导致引用失真，且破坏与上游数据源的严格对应关系。所有脚本工具均以“原样存储、原样输出”为第一原则。

**问：如何判断一个 URL 是否已经在列表中？如何避免重复收录？**

答：项目维护者可使用 scripts/utils/parsers.py 中的 extract_urls 函数提取全部现有条目，然后通过 Python 的集合运算进行去重检查。建议在新增批次前先运行 --dedup 模式，该模式会输出与主列表重复的条目列表，并给出建议的跳过或合并操作。

**问：项目是否支持自动检测并重定向失效链接到新的地址？**

答：本项目不自动改写或重定向任何 URL。check_health.sh 脚本仅报告链接状态（如 301 重定向、404 不存在、超时等），但不会自动替换列表中的内容。维护者根据报告人工核实后，再决定是否更新条目。这种设计保证了变更的可审计性和可回溯性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
