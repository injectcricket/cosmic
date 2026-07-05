# Map Mobile Article Indexer

Map Mobile Article Indexer 是一个面向移动端技术内容聚合与导航的开源工具，专注于对 map.mobile.cmcvrr.cn 平台下的技术文章进行系统性收录、分类与检索。该项目旨在为移动开发工程师、技术调研人员以及对车载移动服务架构感兴趣的开发者提供一站式的文章索引与快速访问能力。

本项目并非简单的链接收藏夹，而是一个具备分类标签、全文检索、访问热度统计和内容快照功能的轻量级索引系统。通过该项目，用户可以高效定位到特定技术主题的文章，减少在大量历史文章中逐页翻找的时间成本，显著提升技术调研与问题排查的效率。项目采用静态站点生成方案，所有索引数据可离线使用，适用于内网部署或本地开发环境。

## 功能概览

**批量文章索引解析**：自动扫描并解析指定路径下的文章元数据，提取标题、发布时间、内容摘要等关键信息，生成结构化索引条目。

**多维度分类标签系统**：为每篇文章自动生成或手动指定技术领域标签，支持按标签快速筛选相关文章集合。

**全文检索与模糊匹配**：基于标题和摘要内容构建倒排索引，支持关键词模糊搜索，帮助用户在大量文档中快速定位目标内容。

**访问热度与趋势统计**：记录每篇文章的访问频次，生成热度排行与时间趋势图，识别当前关注度较高的技术话题。

**静态数据导出与离线使用**：支持将索引数据导出为 JSON 或 Markdown 格式，便于集成到静态站点生成器或本地知识库中。

**响应式移动端适配界面**：提供针对手机屏幕优化的浏览界面，确保在移动设备上获得良好的阅读和检索体验。

**定时增量更新机制**：通过计划任务自动检测新增文章并更新索引，无需人工干预即可保持数据新鲜度。

## 应用场景

**移动端技术文档查阅**：开发人员在日常工作中需要查阅 map.mobile.cmcvrr.cn 平台上的技术文章时，可通过本项目快速检索和定位，无需逐个浏览历史列表。

**车载移动服务架构调研**：技术架构师在进行车载移动服务技术选型或架构评审前，可使用本项目系统梳理平台上的相关文章，全面了解技术演进脉络。

**技术知识库搭建**：团队内部可将本项目作为数据采集层，将平台文章索引集成到团队知识管理系统中，实现统一的技术文档检索入口。

**历史文章归档与回顾**：对于长期关注该平台的读者，可通过本项目按时间线回顾历史文章，追踪特定技术主题的发展过程。

## 快速开始

```bash
git clone https://github.com/your-org/map-mobile-article-indexer.git
cd map-mobile-article-indexer
pip install -r requirements.txt
python run_indexer.py --base-url http://map.mobile.cmcvrr.cn --output ./data
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行索引与解析逻辑 |
| requests | 2.25.0 及以上 | HTTP 请求库，用于获取文章页面内容 |
| beautifulsoup4 | 4.9.0 及以上 | HTML 解析库，用于提取文章元数据 |
| lxml | 4.6.0 及以上 | 高性能 XML/HTML 解析器，作为 BeautifulSoup 的后端 |
| markdown | 3.3.0 及以上 | 用于将文章摘要转换为 Markdown 格式输出 |
| sqlite3 | 系统内置 | 本地轻量级数据库，用于存储索引数据和访问统计 |
| cron / systemd-timer | 任意版本 | 定时任务调度器，用于实现增量更新（生产环境推荐） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide/ | 如何配置索引参数、如何执行搜索、如何查看文章热度统计 |
| 开发者指南 | docs/developer-guide/ | 如何扩展解析器、如何新增字段、如何自定义输出格式 |
| 架构设计 | docs/architecture/ | 索引系统的整体模块划分、数据流转路径、扩展点设计 |
| 部署运维 | docs/deployment/ | 如何将系统部署到生产服务器、如何配置增量更新定时任务 |
| API 参考 | docs/api-reference/ | 核心模块的函数签名、参数说明与返回值格式 |

## 资源列表

- http://map.mobile.cmcvrr.cn/Article/details/2707.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/527705.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/47956.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2260445.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9134.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0145.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4137073.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/51521.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/80416.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/942747.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/519814.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1719.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3976.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3220853.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2739800.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6704073.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/60246.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/88958.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/50904.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7841.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2568.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8899.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8559344.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/17993.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/38119.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3142300.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5003.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/557659.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1958705.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6152764.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3251654.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0353598.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/333329.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/532162.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/88337.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1882829.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5507850.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/59542.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/40192.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5429227.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/16115.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0127871.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/270034.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3919424.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4406510.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/264437.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6454.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4563773.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3577254.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/826732.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7821.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5767.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/45058.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/753341.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9895722.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/749389.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/95464.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/114717.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/983477.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/485724.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/49566.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8102434.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/405010.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2276.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/721165.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/54027.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/307159.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/844433.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/217655.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/468218.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8276155.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2557106.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/88048.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/07742.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/61674.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7461273.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/07208.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3091452.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/634219.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/880778.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3050.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/880430.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/211622.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0809399.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1927.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5987.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/001675.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/637236.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0067916.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7615.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6446.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4923958.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8905121.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/33308.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0821453.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/891381.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0521.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/43272.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1678.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/611174.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/803579.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/388947.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/858751.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/97591.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4148.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/04510.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/72188.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/363034.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/967099.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1904882.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3741593.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/443038.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4457.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/285102.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0312.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4847.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/73998.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/654131.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/521769.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1275.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1463496.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7717151.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/81403.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/03568.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/250672.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8389.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1056374.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4289359.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3673.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4643040.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9614.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9729.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/158294.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3442318.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/80145.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/30430.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4974696.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3826740.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4151.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/81292.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3338.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/210593.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/807994.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6928556.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/991818.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5465.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/947244.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1164.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/77072.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/680330.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/134953.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8413506.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/86424.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/561848.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9732.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/014783.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8088.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/20035.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1725493.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/602083.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/408338.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5937.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0816792.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3746.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/12451.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5253.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1824812.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9043850.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/41093.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9403967.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2140.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8530.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/79482.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7179.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/42427.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/24256.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/245532.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4744985.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8151883.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/76668.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/814236.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/688202.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/74993.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/927306.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7048.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/90141.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1224019.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6269601.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/85006.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/903331.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4157011.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/74157.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6303.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/126749.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6001452.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2929.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/922505.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/370628.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4547820.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3009888.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/864926.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6377032.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/236356.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/13796.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/337700.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6831.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/29946.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/7593948.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1384427.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4180.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2481595.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0933036.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5285.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2611898.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3190.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4391.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6552.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/384409.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5722281.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/2897.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9815421.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9211.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/1198395.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/3427.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/165392.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/38343.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/223609.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/4316.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/260924.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/083910.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/870625.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/5474611.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0632.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6129.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/89461.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/9537.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/995719.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/104633.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/067425.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/8940188.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/871693.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0654.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/708926.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0008919.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/688907.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/06519.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/0563716.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/6040.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/07382.sHtML
- http://map.mobile.cmcvrr.cn/Article/details/089577.sHtML

## 项目结构

```
map-mobile-article-indexer/
├── run_indexer.py                 # 主入口脚本，负责解析命令行参数并调度索引流程
├── requirements.txt               # Python 依赖清单，记录所有外部库及其版本约束
├── config/
│   ├── default.yaml               # 默认配置文件，包含超时、重试、输出路径等基础参数
│   └── schema.json                # 索引数据结构的 JSON Schema 定义，用于数据校验
├── core/
│   ├── fetcher.py                 # HTTP 请求模块，处理页面获取与重试逻辑
│   ├── parser.py                  # HTML 解析模块，基于 BeautifulSoup 提取文章元数据
│   ├── indexer.py                 # 索引构建模块，生成倒排索引和分类标签映射
│   └── storage.py                 # 数据持久化模块，负责 SQLite 读写与 JSON 序列化
├── web/
│   ├── app.py                     # 轻量级 Web 界面，提供搜索和热度排行功能
│   ├── templates/                 # Jinja2 模板目录，存放前端渲染页面
│   └── static/                    # CSS 与 JavaScript 静态资源，优化移动端显示效果
├── scripts/
│   ├── cron_update.sh             # 增量更新 Shell 脚本，可配置到 crontab 定期执行
│   └── export_markdown.py         # 数据导出工具，将索引内容转换为 Markdown 表格格式
├── tests/
│   ├── test_fetcher.py            # fetcher 模块的单元测试用例
│   ├── test_parser.py             # parser 模块的单元测试用例
│   └── fixtures/                  # 测试用 HTML 样本数据
├── docs/                          # 完整文档目录，包含用户手册、开发者指南、架构设计等
└── data/                          # 运行时生成的数据目录，存放 SQLite 数据库和导出文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库到个人账号，然后 clone 到本地开发环境，并按照快速开始步骤安装所有依赖。

2. 新建一个以 feature/ 或 fix/ 为前缀的分支，例如 feature/add-category-filter，用于隔离您的修改内容。

3. 编写或修改代码后，请确保在 tests/ 目录下补充对应的单元测试用例，并执行 pytest 确认所有测试通过。

4. 更新 docs/ 目录下的相关文档，确保您的改动在用户手册或开发者指南中有对应说明。

5. 提交 pull request 到主仓库的 main 分支，并在 PR 描述中清晰说明改动目的、实现方式以及影响范围。

## 常见问题

**问：索引器是否可以处理文章内容中包含动态加载的部分？**

答：当前版本的解析器仅处理服务端渲染的静态 HTML 内容。如果文章正文通过 JavaScript 动态加载，建议在 fetcher 模块中集成 Playwright 或 Selenium 等浏览器自动化工具，项目预留了 fetcher 的扩展接口，用户可自行替换实现。

**问：数据导出后如何集成到静态站点生成器如 Hugo 或 VuePress？**

答：scripts/export_markdown.py 脚本支持将索引数据导出为 Markdown 文件集合，每个文章条目生成一个独立的 .md 文件，并附带 frontmatter 元数据。导出后可将整个 output/ 目录直接复制到 Hugo 或 VuePress 的内容目录中，无需额外转换。

**问：系统是否支持多用户并发访问？**

答：本项目的 Web 界面设计为单机轻量级工具，默认使用 SQLite 数据库，不提供用户认证和会话管理。如需支持多用户并发，建议将 storage 模块替换为 PostgreSQL 或 MySQL 后端，并在 Web 层增加认证中间件。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
