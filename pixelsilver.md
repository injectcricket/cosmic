# WebLink Collective

WebLink Collective 是一个面向技术研究者、内容聚合者与信息架构师的开源外链资源归集系统。该项目定位于对分散于互联网各处的结构化文章链接进行系统性收集、分类与持久化存储，解决个人或团队在信息检索过程中面临的链接碎片化、重复采集与元数据缺失等核心问题。与传统书签管理工具不同，WebLink Collective 以项目批次为单位，内置基于 URL 模式识别的自动分类引擎，支持对裸域、子目录、大小写敏感路径及混合协议链接的无损入库，并对外提供稳定的 JSON API 与静态站点生成能力，适用于构建个人知识库镜像、垂直领域导航站或企业内部技术文档索引系统。项目设计遵循 UNIX 哲学，核心采集模块与展示层解耦，允许开发者在不修改主逻辑的前提下自由替换前端模板或数据存储后端。WebLink Collective 已在第 158/200 批次中归集超过 250 个高质量技术文章资源，覆盖移动端开发、后端架构、数据科学及运维工程等方向。

## 功能概览

- **URL 无损入库引擎**：支持对任意格式的 URL 进行原样存储，包括裸域名、带协议前缀、混合大小写扩展名及非常规端口号，入库过程不改变原始字符串的任何一个字符，保证资源可溯源。

- **批次化资源管理**：所有链接以项目批次（Batch）为组织单元，每批最高可容纳 250 个资源，批次内支持按采集时间、域名或自定义标签进行二次排序与筛选。

- **自动化元数据抽取**：从 URL 路径中解析文章 ID、文件类型（如 .sHtML）、目录结构（/Article/details/）等关键字段，生成可供搜索的索引键值对，降低人工标注成本。

- **多格式数据导出**：内置导出适配器支持输出为 JSON、Markdown 表格或纯文本列表，方便将资源集嵌入现有文档系统、静态网站生成器或 CI/CD 流水线。

- **增量同步与校验**：支持通过配置文件设定同步周期，自动检测新增或失效链接，生成变更日志（CHANGELOG）并在控制台输出校验报告。

- **零依赖 Web 预览界面**：基于 Python 内置 http.server 模块与原生 JavaScript 构建轻量级可视化面板，无需安装额外 Web 框架即可快速浏览当前批次所有资源。

- **可插拔的过滤规则**：提供正则表达式与域名黑名单两种过滤策略，允许在入库阶段屏蔽广告跟踪参数或非技术类页面，提升资源纯度。

## 应用场景

**个人技术博客的知识库底座**：独立开发者或技术博主可以使用 WebLink Collective 整理自己写作时参考的数百篇外部文章，通过批次归档功能按主题（如分布式系统、数据库调优）分门别类，并在博客侧边栏嵌入导出生成的链接列表，为读者提供延伸阅读入口。

**企业内部技术文档中心的导航层**：中型企业的技术文档团队往往需要维护一套内部推荐的外部学习资源清单。WebLink Collective 的 JSON API 可被企业门户前端直接调用，实现资源列表的动态渲染，同时利用元数据抽取功能自动标记各篇文章所涉及的技术栈，便于新入职员工按需检索。

**开源项目 README 的资源附录生成**：开源项目维护者需要定期在仓库文档中列出相关生态链接或引用文献。本项目可作为预处理工具，将收集到的 URL 批量导入后一键导出为符合 Markdown 语法的列表块，直接粘贴至 README 的「参考资料」章节，显著减少手工排版错误。

**数据采集管道的前置清洗节点**：在构建垂直搜索引擎或学术论文爬虫时，原始采集的 URL 往往包含大小写不一致的扩展名、冗余查询参数或混合协议。WebLink Collective 的标准化入库流程可作为数据清洗管道的第一步，确保后续去重与链接分析模块获得格式统一的输入数据。

## 快速开始

以下命令演示了如何将本项目克隆至本地、安装依赖并启动内置预览服务，完成对第 158/200 批次资源的首次加载。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-collective/weblink-collective.git
cd weblink-collective

# 安装 Python 依赖（建议使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 系统请使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行数据导入脚本（加载第 158 批次资源）
python scripts/import_batch.py --batch 158 --source data/batch_158.csv

# 启动内置预览服务器
python -m http.server 8000 --directory public
# 浏览器访问 http://localhost:8000 查看资源列表
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心解析与导入脚本的运行环境，低于 3.8 版本将不支持类型注解语法 |
| pip | 20.0 及以上 | 用于安装 requirements.txt 中列出的第三方库，包括 requests 与 lxml |
| Git | 2.25 及以上 | 克隆仓库及后续拉取更新时的版本控制工具，建议使用最新稳定版 |
| 磁盘空间 | 50 MB 及以上 | 用于存储资源索引文件、日志及静态导出的 HTML 页面，不含原始文章内容 |
| 网络访问 | 外网连通（非强制） | 若启用链接存活校验功能，则需要能够访问所收录资源的原始域名；离线模式下仅处理本地缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | docs/user-guide.md | 如何导入新批次、自定义过滤规则、导出不同格式的资源列表及配置预览界面的端口与主题 |
| 开发者指南 | docs/developer-guide.md | 如何扩展元数据抽取器、编写自定义导出适配器、运行单元测试及提交符合规范的 Pull Request |
| 架构设计 | docs/architecture.md | 解释项目的分层结构（采集层-存储层-展示层）、URL 规范化策略与批次版本管理机制 |
| 运维参考 | docs/operations.md | 涵盖日志轮转策略、数据库索引优化建议、增量同步的定时任务配置及异常告警设置 |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/details/880004.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8944.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/637571.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/00923.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0296088.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4642189.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/01879.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/53133.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8736.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7587804.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88409.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/838502.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0761.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/424371.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2139403.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/989676.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/56549.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/402091.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7112046.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1730.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5814.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1261.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/93724.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6311918.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/375479.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/27430.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2974.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3596630.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/27149.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/274568.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3313.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2076164.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6963128.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8052012.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/520144.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5319.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6263017.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/523516.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/519615.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8022208.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4904.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/496364.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/217380.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/604317.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88148.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/273150.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8690734.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3809.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2954.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9737882.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/235320.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/298294.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1501645.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/37023.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1289705.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/60027.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/030495.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/236943.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5028183.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/437522.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4429.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1394632.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9824.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/533136.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9433473.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/043293.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/217875.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9813446.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2419.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/507141.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6207725.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8761805.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/37423.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5813622.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6148526.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0694.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/503585.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/568939.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/58451.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/72569.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0471701.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6991.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/851515.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3170221.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/517454.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/882645.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8628296.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6662.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3881.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/32967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8175.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/484365.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3378.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/466475.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2680.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/456778.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9303.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3712.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/297536.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2557130.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3216.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2395937.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/952075.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/68339.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8503583.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/89658.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/21508.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9526.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/232501.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6741.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/43112.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7359617.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/015967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/68088.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/590650.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6430606.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0218075.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/09830.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/524920.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1142900.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7288.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/777531.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/00904.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5772.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/393304.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/39305.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7312.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0143529.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/003559.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2941.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/38997.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2323876.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/69090.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8988550.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1800.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/74973.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/695588.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0253.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/723717.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/29458.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9219.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4508117.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3701.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2577.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/53890.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2432.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/806108.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/306719.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8637.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3630387.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/786866.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1006377.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/483725.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/331534.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6499.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/720596.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3723.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/563171.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/81021.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6123.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9740588.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/91802.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/16131.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/153479.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/083008.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2825.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1011394.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2372889.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/365990.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7053.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/53976.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2148.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/488802.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/20429.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8781925.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/15781.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1909536.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0868916.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4406090.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/90146.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3048237.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6367352.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/83025.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9067244.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/144386.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/710486.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/305280.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2895.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6365.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4993696.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5454835.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4761.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9527.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/994209.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/36937.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/85319.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3135967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/08545.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/403026.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9571494.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/98720.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1569441.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/186394.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/697255.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1153.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3958.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/898625.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/32026.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5144.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/599962.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/00419.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/283175.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/237395.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8250.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/17897.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/678032.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/63920.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/48775.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/227636.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5161.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5410.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/42861.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6115.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/55311.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8731.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/671576.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9655027.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2299.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8078697.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1375799.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/115714.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6858274.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/289280.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/123179.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/13775.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2249176.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3066.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5904823.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/374648.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/010123.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0256134.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3900289.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3559295.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8237.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/01975.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/03529.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6916.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6519.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/91271.sHtML

## 项目结构

```
weblink-collective/
├── cmd/
│   └── cli/                           # 命令行入口模块，解析子命令（import/export/serve）
│       ├── main.go                    # 主程序入口，初始化日志与配置
│       └── commands.go                # 各子命令的具体实现与参数绑定
├── internal/
│   ├── collector/                     # 核心采集器，负责 URL 入库与去重校验
│   │   ├── parser.go                  # URL 结构解析器，提取域名、路径、扩展名
│   │   ├── validator.go               # 链接存活校验器，支持超时与重试策略
│   │   └── batch.go                   # 批次管理器，维护批次元数据与资源映射
│   ├── storage/                       # 存储适配层，支持 JSON 文件与 SQLite 后端
│   │   ├── json_backend.go            # 基于文件的 JSON 存储实现
│   │   └── sqlite_backend.go          # 基于 SQLite 的关系型存储实现（可选）
│   ├── exporter/                      # 导出器集合，负责生成各类格式输出
│   │   ├── markdown.go                # Markdown 列表与表格导出器
│   │   ├── json.go                    # 结构化 JSON 导出器（符合 JSON API 规范）
│   │   └── html.go                    # 独立 HTML 预览页生成器
│   └── filter/                        # 可插拔过滤规则引擎
│       ├── regex_filter.go            # 基于正则表达式的路径过滤
│       └── domain_blacklist.go        # 域名黑名单过滤
├── public/                            # 静态资源目录，供内置预览服务器使用
│   ├── index.html                     # 资源列表渲染模板（原生 JavaScript + CSS）
│   └── assets/                        # 样式表与前端脚本
├── scripts/                           # 辅助运维脚本
│   ├── import_batch.py                # Python 批量导入脚本（兼容旧版本数据）
│   └── migrate_db.sh                  # 数据库迁移与备份脚本
├── docs/                              # 完整项目文档（详见文档导航章节）
├── go.mod                             # Go 模块依赖定义文件
├── go.sum                             # 依赖校验文件
├── Makefile                           # 构建自动化脚本（含 test/build/run 目标）
└── README.md                          # 项目说明文件（本文件）
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制至个人账号下，然后使用 `git clone` 拉取本地副本，并确保通过 `make test` 命令运行所有现有单元测试，确认当前环境无异常。

2. 新建功能分支，分支名称须遵循 `feature/` 或 `fix/` 前缀加简要描述的原则（例如 `feature/add-rss-exporter`），避免在主干分支直接提交代码。

3. 编写代码或文档改动时，请严格遵守项目根目录下的 `.golangci.yml` 与 `.editorconfig` 所定义的代码风格规范，所有导出的函数与结构体必须包含符合 Go Doc 标准的注释说明。

4. 在提交 Pull Request 之前，执行 `make lint` 与 `make test` 确保静态检查与单元测试全部通过，并在 PR 描述中清晰说明本次改动的目的、涉及模块及手动测试步骤。

5. 提交 PR 后，项目维护者将在 72 小时内进行 Code Review，若有改动意见将通过 GitHub 评论反馈，贡献者需及时响应并更新补丁，直至 PR 被合并或关闭。

## 常见问题

**问：为什么我导入的 URL 在输出列表中大小写发生变化，或者被自动补上了 www 前缀？**

答：WebLink Collective 的核心设计原则是「原样存储」。请检查您的导入配置文件中是否误启用了 `normalize_url` 或 `force_www` 开关。默认情况下，这两个开关均为关闭状态。如果仍然出现变化，请确认输入源文件（如 CSV）在保存时是否被 Excel 或其他编辑器自动转换了格式。若问题持续存在，请提交包含原始输入字符串与错误输出字符串的 Issue 至 GitHub 仓库。

**问：内置预览服务器访问时显示空白页，或者资源列表无法加载？**

答：该问题通常源于两个原因：第一，请确认 `public/index.html` 中的 JavaScript 代码默认读取的 JSON 数据路径为 `/data/batch_158.json`，您需要先运行 `make export` 或手动执行导出命令生成该文件；第二，如果您使用 Python 的 `http.server` 模块启动服务，请确保当前工作目录处于项目根目录，否则静态文件路径解析会失败。建议使用项目自带的 `make serve` 命令启动服务，该命令会自动设置正确的工作目录与端口映射。

**问：项目支持 Windows 操作系统吗？**

答：项目核心逻辑基于 Go 语言编写，Go 编译器支持 Windows、Linux 与 macOS 三大平台。但辅助脚本（如 `scripts/import_batch.py`）和 Makefile 中部分命令可能使用了 Unix 风格的路径分隔符与 shell 语法。在 Windows 环境下，推荐使用 Git Bash、WSL 2 或 Cygwin 终端运行相关脚本。纯 PowerShell 环境下，您需要手动将路径分隔符替换为反斜杠，并逐个执行脚本内的命令。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
