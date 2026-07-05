# CMC-VRR Mobile Article Aggregator

CMC-VRR Mobile Article Aggregator 是一个面向移动端技术内容聚合与检索的开源项目，专门用于采集、索引和呈现 cmcvrr.cn 移动站点下的深度技术文章。项目定位为技术外链资源汇总站，服务于移动开发工程师、前端技术决策者以及内容运营人员，帮助其快速定位与移动端渲染、视频编解码、响应式设计、性能优化等主题相关的高质量技术文档。

该项目通过对目标站点下特定文章 ID 的集中管理与元数据提取，构建起一个可按主题、时间、热度检索的文章导航体系。项目本身不存储文章正文，仅保留文章标题、摘要、分类标签、发布时间等结构化元数据，所有正文内容实时回源获取，确保信息始终与官方站点保持同步。

## 功能概览

**批量文章元数据抓取** 项目内置轻量级爬虫引擎，支持对 cmcvrr.cn 移动站点下的文章详情页进行并发请求，提取标题、发布时间、正文摘要、关键词标签等核心元数据字段。

**结构化索引构建** 抓取到的元数据经清洗与标准化后，存入本地 SQLite 数据库或导出为 JSON 格式，支持按文章 ID、发布时间、标签等多维度建立索引。

**按 ID 精确检索** 用户可通过文章 ID 直接定位特定文章，快速获取该文章的结构化摘要信息与原始链接。

**标签分类导航** 自动从文章正文中提取关键词并聚合为标签云，支持按标签筛选文章列表，便于按技术主题浏览。

**时间序列归档** 按文章发布时间生成年月归档目录，支持按时间维度回溯历史文章。

**全文摘要生成** 对每篇文章正文前 200 字符进行提取，生成标准化摘要，方便用户在不跳转原文的情况下快速判断内容相关性。

**导出与集成接口** 提供 RESTful API 和命令行工具两种交互方式，支持将索引数据导出为 CSV、JSON、Markdown 表格等多种格式，便于嵌入其他文档系统。

## 应用场景

**移动端技术团队内部知识库建设** 技术团队可将本工具集成到内部文档流水线中，定期拉取 cmcvrr.cn 上与移动端渲染、视频播放器优化相关的文章元数据，生成团队内部周报或技术月刊的素材清单。

**技术博客的参考文献链接站** 个人技术博主在撰写移动端性能优化或响应式设计相关文章时，可使用本项目的标签检索功能快速找到 cmcvrr.cn 上的权威参考文献，提升博文的论据可信度。

**内容运营的数据选品辅助** 运营人员可通过本项目的批量导出功能，将文章标题与摘要导出为 Excel 表格，结合阅读量、发布时间等字段进行数据透视分析，筛选出适合社交媒体二次传播的高价值内容。

**开源项目 README 的外部资源引用** 其他开源项目维护者可在自己的 README 中引用本项目的聚合结果，作为 "延伸阅读" 或 "相关技术方案" 章节的外部链接来源，丰富自身项目的文档生态。

## 快速开始

以下命令演示了从克隆代码到完成首次文章元数据抓取的全过程。

```bash
git clone https://github.com/cmcvrr/article-aggregator.git
cd article-aggregator

pip install -r requirements.txt

cp config.example.yaml config.yaml

python cli.py fetch --ids 2707,527705,47956 --output ./data/articles.json

python cli.py serve --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，用于爬虫引擎与 API 服务 |
| SQLite | 3.35 及以上 | 本地元数据存储数据库，支持 JSON 扩展 |
| requests | 2.31.0 及以上 | HTTP 请求库，用于文章详情页抓取 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，用于提取文章元数据 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的后端 |
| flask | 2.3.0 及以上 | 可选依赖，仅在启用 RESTful API 服务时需要 |
| pytest | 7.4.0 及以上 | 可选依赖，仅在运行单元测试时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | docs/user-guide/quick-start.md | 如何快速完成首次文章抓取？如何配置抓取参数？ |
| 用户指南 | docs/user-guide/search-syntax.md | 如何按标签、时间范围或文章 ID 进行组合检索？ |
| 开发者指南 | docs/developer-guide/architecture.md | 项目的模块划分是怎样的？爬虫引擎如何工作？ |
| 开发者指南 | docs/developer-guide/api-reference.md | RESTful API 的端点定义、请求参数与返回格式是什么？ |
| 运维指南 | docs/ops-guide/deployment.md | 如何将本项目部署为定时任务或容器化服务？ |
| 运维指南 | docs/ops-guide/troubleshooting.md | 抓取超时、解析失败等常见问题如何排查与修复？ |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/details/2707.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/527705.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/47956.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2260445.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9134.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0145.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4137073.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/51521.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/80416.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/942747.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/519814.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1719.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3976.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3220853.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2739800.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6704073.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/60246.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88958.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/50904.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7841.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2568.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8899.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8559344.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/17993.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/38119.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3142300.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5003.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/557659.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1958705.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6152764.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3251654.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0353598.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/333329.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/532162.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88337.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1882829.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5507850.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/59542.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/40192.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5429227.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/16115.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0127871.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/270034.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3919424.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4406510.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/264437.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6454.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4563773.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3577254.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/826732.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7821.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5767.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/45058.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/753341.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9895722.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/749389.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/95464.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/114717.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/983477.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/485724.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/49566.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8102434.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/405010.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2276.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/721165.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/54027.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/307159.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/844433.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/217655.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/468218.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8276155.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2557106.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88048.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/07742.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/61674.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7461273.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/07208.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3091452.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/634219.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/880778.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3050.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/880430.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/211622.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0809399.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1927.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5987.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/001675.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/637236.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0067916.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7615.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6446.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4923958.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8905121.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/33308.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0821453.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/891381.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0521.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/43272.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1678.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/611174.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/803579.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/388947.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/858751.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/97591.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4148.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/04510.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/72188.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/363034.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/967099.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1904882.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3741593.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/443038.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4457.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/285102.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0312.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4847.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/73998.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/654131.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/521769.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1275.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1463496.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7717151.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/81403.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/03568.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/250672.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8389.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1056374.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4289359.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3673.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4643040.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9614.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9729.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/158294.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3442318.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/80145.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/30430.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4974696.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3826740.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4151.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/81292.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3338.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/210593.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/807994.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6928556.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/991818.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5465.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/947244.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1164.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/77072.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/680330.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/134953.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8413506.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/86424.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/561848.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9732.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/014783.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8088.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/20035.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1725493.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/602083.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/408338.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5937.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0816792.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3746.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/12451.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5253.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1824812.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9043850.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/41093.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9403967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2140.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8530.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/79482.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7179.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/42427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/24256.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/245532.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4744985.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8151883.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/76668.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/814236.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/688202.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/74993.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/927306.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7048.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/90141.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1224019.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6269601.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/85006.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/903331.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4157011.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/74157.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6303.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/126749.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6001452.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2929.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/922505.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/370628.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4547820.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3009888.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/864926.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6377032.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/236356.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/13796.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/337700.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6831.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/29946.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7593948.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1384427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4180.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2481595.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0933036.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5285.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2611898.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3190.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4391.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6552.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/384409.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5722281.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2897.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9815421.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9211.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1198395.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/165392.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/38343.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/223609.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4316.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/260924.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/083910.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/870625.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5474611.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0632.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6129.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/89461.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9537.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/995719.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/104633.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/067425.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8940188.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/871693.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0654.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/708926.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0008919.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/688907.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/06519.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0563716.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6040.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/07382.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/089577.sHtML

## 项目结构

```
article-aggregator/
├── cli.py                      # 命令行入口，提供 fetch、serve、export 子命令
├── config.example.yaml         # 配置文件模板，包含并发数、超时时间、数据库路径等
├── requirements.txt            # Python 依赖清单
├── setup.py                    # 项目打包与安装配置
├── README.md                   # 项目说明文档
├── LICENSE                     # MIT 许可证文件
│
├── aggregator/                 # 核心业务模块
│   ├── __init__.py
│   ├── crawler.py              # 爬虫引擎，封装 requests + 并发控制
│   ├── parser.py               # HTML 解析器，提取标题、正文、标签、时间
│   ├── indexer.py              # 索引构建器，将元数据写入 SQLite
│   └── models.py               # 数据模型定义（Article, Tag, Category）
│
├── api/                        # RESTful API 服务模块
│   ├── __init__.py
│   ├── app.py                  # Flask 应用工厂
│   ├── routes.py               # 路由定义（/search, /article/:id, /tags）
│   └── serializers.py          # 响应序列化（JSON 格式化）
│
├── storage/                    # 存储层模块
│   ├── __init__.py
│   ├── database.py             # SQLite 连接管理与 CRUD 操作
│   ├── migrations/             # 数据库迁移脚本
│   │   ├── 001_initial_schema.sql
│   │   └── 002_add_indexes.sql
│   └── exporters/              # 数据导出器
│       ├── json_exporter.py
│       ├── csv_exporter.py
│       └── markdown_exporter.py
│
├── tests/                      # 单元测试与集成测试
│   ├── test_crawler.py
│   ├── test_parser.py
│   ├── test_indexer.py
│   └── fixtures/               # 测试用 HTML 样本
│       └── sample_article.html
│
├── scripts/                    # 运维脚本
│   ├── daily_fetch.sh          # 每日定时抓取脚本（配合 cron）
│   └── export_latest.sh        # 导出最近 7 天文章为 Markdown
│
└── docs/                       # 文档目录
    ├── user-guide/
    ├── developer-guide/
    └── ops-guide/
```

## 贡献指南

提交代码或文档更新前，请确保已阅读并遵守以下流程。

1.  Fork 本仓库至个人账户，将个人仓库克隆到本地开发环境，并配置 upstream 指向主仓库以保持同步。

2.  创建新的功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式，避免在主分支上直接修改。

3.  编写代码或文档时，严格遵守 PEP 8 编码规范（Python 文件）或 Markdown 语法规范（文档文件），所有新增功能必须附带对应的单元测试用例。

4.  提交代码前，在本地运行完整的测试套件 `pytest tests/` 确保所有已有测试通过，且新增代码的测试覆盖率达到 80% 以上。

5.  发起 Pull Request 到主仓库的 main 分支，PR 描述中需清晰说明改动目的、改动范围以及是否涉及破坏性变更，等待至少一位维护者审核通过后合并。

## 常见问题

**Q: 抓取过程中遇到 HTTP 403 或 429 状态码应如何处理？**

A: 此类状态码通常表示目标站点启用了反爬机制或频率限制。项目已在 `config.yaml` 中提供 `request_delay` 参数，用于控制两次请求之间的间隔秒数，默认值为 1.0 秒。建议将该值调整为 2.0 至 3.0 秒，并启用 `random_delay` 选项以在间隔中增加随机抖动。同时，可配置 `user_agent` 列表实现 User-Agent 轮换。若仍频繁出现限制，请考虑使用代理池或联系站点管理员获取白名单权限。

**Q: 数据库中的文章元数据如何与源站保持同步更新？**

A: 项目提供了增量更新机制。每次执行 `cli.py fetch` 时，可通过 `--since` 参数指定时间范围，仅抓取该时间范围内发布的新文章或更新过的文章。对于已存在的文章 ID，若源站内容发生变更，解析器会对比正文哈希值，仅在检测到变化时更新本地记录。建议运维人员通过 `scripts/daily_fetch.sh` 脚本配置每日定时任务，实现自动化增量同步。

**Q: 能否将索引数据导出为其他文档系统可导入的格式？**

A: 项目内置了三种导出格式支持。执行 `cli.py export --format json` 可导出为标准 JSON 数组；`--format csv` 可导出为 Excel 兼容的 CSV 表格，包含文章 ID、标题、发布时间、标签等所有元数据字段；`--format markdown` 可导出为 Markdown 表格，适合直接粘贴到 GitHub Wiki、Notion 或 Confluence 等文档平台。导出时可通过 `--tag` 和 `--since` 参数进行筛选，仅导出特定主题或时间段的数据。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
