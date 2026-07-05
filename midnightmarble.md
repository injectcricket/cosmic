# WebLink Atlas

WebLink Atlas 是一个面向技术调研、内容聚合与知识管理场景的轻量级外链资源汇总平台。该项目定位于帮助开发者、技术写作人员、运维工程师以及数据分析师，以结构化方式管理和分发大批量 URL 资源，并提供基础的分类索引、状态检测与元数据提取能力。

本项目不依赖数据库，采用纯静态文件加脚本驱动的方式运行，适合部署在各类轻量级 Web 服务器或 Serverless 环境中。用户可以通过本项目快速建立自己的技术书签库、文章归档索引或第三方资源镜像列表。项目内置批次管理逻辑，支持按批次导入、去重、标签化输出，适用于处理超过 200 个链接以上的批量数据场景。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别协议与域名格式。

**自动去重校验** 基于 URL 全路径进行 MD5 去重，避免重复条目污染资源池。

**元数据智能提取** 自动发起 HEAD 请求获取响应状态码、Content-Type 和 Last-Modified 时间，辅助判断链接可用性。

**分类标签管理** 用户可为每条链接添加一个或多个分类标签，支持按标签筛选和导出子集。

**批次状态追踪** 记录每批链接的导入时间、总数、有效数、失效数，方便运维审计。

**多格式导出** 支持将资源列表导出为 Markdown 列表、JSON 数组、纯文本换行格式，便于嵌入文档或脚本使用。

**静态站点生成** 内置简单的模板引擎，可根据资源列表自动生成静态 HTML 目录页，适合内网知识库发布。

**命令行交互工具** 提供 Python 和 Shell 两种 CLI 入口，支持在无图形界面的服务器上完成全部操作。

## 应用场景

**技术文档团队整理外部参考链接** 技术撰稿人在编写方案设计或故障复盘文档时，需要引用大量外部技术博客、官方公告和 GitHub Issue 链接。WebLink Atlas 可以帮助团队在文档撰写前期统一收集、校验这些链接，避免成稿后出现大量死链。

**运维团队监控第三方依赖公告页** 运维工程师可将常用的云服务商状态页、安全漏洞公告栏、镜像站更新日志等链接纳入平台管理，每日定时运行状态检测脚本，快速定位访问异常的依赖源。

**数据分析师归档调研数据来源** 数据分析师在开展行业调研时，需要记录每个数据样本的爬取来源 URL。通过 WebLink Atlas 的批次管理功能，可以将不同调研项目的来源链接分批次存储，并附加备注说明数据时间范围与采集策略。

**个人开发者构建技术书签站** 独立开发者可利用该平台将自己的 GitHub Star 项目、技术周刊推荐链接、在线工具地址统一归档，并通过静态站点生成功能发布为个人导航页。

## 快速开始

以下命令演示了如何获取项目代码、安装依赖并运行基础导入流程。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-atlas/weblink-atlas.git
cd weblink-atlas

# 安装 Python 依赖（推荐使用 Python 3.9 及以上版本）
pip install -r requirements.txt

# 运行导入示例：导入第 14 批资源（共 250 个链接）
python cli.py import --batch 14 --source ./samples/batch_14.txt --output ./output/batch_14.json

# 生成静态 HTML 目录页
python cli.py generate --input ./output/batch_14.json --template ./templates/default.html --out ./docs/index.html
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，用于 CLI 工具和元数据提取 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.28.0 及以上 | 发送 HTTP 请求，用于链接状态检测 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 元数据，辅助提取标题和描述 |
| markdown | 3.4.0 及以上 | 将 Markdown 格式的资源列表转换为 HTML 片段 |
| jinja2 | 3.1.0 及以上 | 模板引擎，用于静态站点生成 |
| 磁盘空间 | 至少 50 MB | 用于存储导入的 JSON 数据、日志和生成的静态文件 |
| 网络访问 | 出站 80/443 端口 | 用于执行链接状态检测和元数据抓取 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何导入一批链接、如何查看状态、如何导出为不同格式 |
| 管理员指南 | docs/admin-guide.md | 如何调整检测超时时间、如何配置代理、如何清理过期数据 |
| 批次管理说明 | docs/batch-management.md | 批次编号规则、批次合并逻辑、批次状态标记含义 |
| API 参考 | docs/api-reference.md | CLI 命令参数详解、JSON 数据字段定义、模板变量列表 |
| 常见问题 | docs/faq.md | 为什么某些链接检测超时、如何忽略 SSL 证书错误、如何批量删除失效链接 |
| 贡献规范 | docs/contributing.md | 代码风格要求、提交信息格式、测试用例编写指南 |

## 资源列表

- http://m.mobile.fuvxie.cn/Article/details/913835.sHtML
- http://m.mobile.fuvxie.cn/Article/details/52176.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6070645.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5043327.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5858503.sHtML
- http://m.mobile.fuvxie.cn/Article/details/94603.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1478649.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1323.sHtML
- http://m.mobile.fuvxie.cn/Article/details/739214.sHtML
- http://m.mobile.fuvxie.cn/Article/details/59865.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6988803.sHtML
- http://m.mobile.fuvxie.cn/Article/details/325054.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0709.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4089.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7305591.sHtML
- http://m.mobile.fuvxie.cn/Article/details/09160.sHtML
- http://m.mobile.fuvxie.cn/Article/details/45608.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4967.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0309546.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7754.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2954.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3545377.sHtML
- http://m.mobile.fuvxie.cn/Article/details/987805.sHtML
- http://m.mobile.fuvxie.cn/Article/details/86196.sHtML
- http://m.mobile.fuvxie.cn/Article/details/07121.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3237271.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4490.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4715.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1230.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8956.sHtML
- http://m.mobile.fuvxie.cn/Article/details/72192.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7534795.sHtML
- http://m.mobile.fuvxie.cn/Article/details/204483.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2633033.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1285347.sHtML
- http://m.mobile.fuvxie.cn/Article/details/723218.sHtML
- http://m.mobile.fuvxie.cn/Article/details/07737.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1723685.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2828478.sHtML
- http://m.mobile.fuvxie.cn/Article/details/341675.sHtML
- http://m.mobile.fuvxie.cn/Article/details/057379.sHtML
- http://m.mobile.fuvxie.cn/Article/details/23618.sHtML
- http://m.mobile.fuvxie.cn/Article/details/893259.sHtML
- http://m.mobile.fuvxie.cn/Article/details/05825.sHtML
- http://m.mobile.fuvxie.cn/Article/details/131430.sHtML
- http://m.mobile.fuvxie.cn/Article/details/048831.sHtML
- http://m.mobile.fuvxie.cn/Article/details/77623.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8966.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3595419.sHtML
- http://m.mobile.fuvxie.cn/Article/details/24081.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2831.sHtML
- http://m.mobile.fuvxie.cn/Article/details/614279.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9225.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9954.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6088636.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4403554.sHtML
- http://m.mobile.fuvxie.cn/Article/details/083545.sHtML
- http://m.mobile.fuvxie.cn/Article/details/147708.sHtML
- http://m.mobile.fuvxie.cn/Article/details/72549.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0739.sHtML
- http://m.mobile.fuvxie.cn/Article/details/45923.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4347278.sHtML
- http://m.mobile.fuvxie.cn/Article/details/507951.sHtML
- http://m.mobile.fuvxie.cn/Article/details/87735.sHtML
- http://m.mobile.fuvxie.cn/Article/details/974104.sHtML
- http://m.mobile.fuvxie.cn/Article/details/014585.sHtML
- http://m.mobile.fuvxie.cn/Article/details/950424.sHtML
- http://m.mobile.fuvxie.cn/Article/details/99875.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2534.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2062524.sHtML
- http://m.mobile.fuvxie.cn/Article/details/22902.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9824227.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0357.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1264.sHtML
- http://m.mobile.fuvxie.cn/Article/details/284352.sHtML
- http://m.mobile.fuvxie.cn/Article/details/40554.sHtML
- http://m.mobile.fuvxie.cn/Article/details/384009.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0929526.sHtML
- http://m.mobile.fuvxie.cn/Article/details/40845.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6331956.sHtML
- http://m.mobile.fuvxie.cn/Article/details/171796.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4134.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7863593.sHtML
- http://m.mobile.fuvxie.cn/Article/details/377407.sHtML
- http://m.mobile.fuvxie.cn/Article/details/970964.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2604499.sHtML
- http://m.mobile.fuvxie.cn/Article/details/516949.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3281819.sHtML
- http://m.mobile.fuvxie.cn/Article/details/75126.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8547.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2659.sHtML
- http://m.mobile.fuvxie.cn/Article/details/72031.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7194.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7427.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9943.sHtML
- http://m.mobile.fuvxie.cn/Article/details/160732.sHtML
- http://m.mobile.fuvxie.cn/Article/details/41467.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1333.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7357837.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6028.sHtML
- http://m.mobile.fuvxie.cn/Article/details/380065.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1414613.sHtML
- http://m.mobile.fuvxie.cn/Article/details/550020.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9251401.sHtML
- http://m.mobile.fuvxie.cn/Article/details/268270.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3282520.sHtML
- http://m.mobile.fuvxie.cn/Article/details/168832.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3238.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1216697.sHtML
- http://m.mobile.fuvxie.cn/Article/details/440275.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0107.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6878817.sHtML
- http://m.mobile.fuvxie.cn/Article/details/516763.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7071.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6125.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5122008.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6054564.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2116786.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2271517.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6067.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8346542.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6762.sHtML
- http://m.mobile.fuvxie.cn/Article/details/627479.sHtML
- http://m.mobile.fuvxie.cn/Article/details/03282.sHtML
- http://m.mobile.fuvxie.cn/Article/details/83756.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7681251.sHtML
- http://m.mobile.fuvxie.cn/Article/details/706931.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9504.sHtML
- http://m.mobile.fuvxie.cn/Article/details/79838.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7599.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8972388.sHtML
- http://m.mobile.fuvxie.cn/Article/details/446083.sHtML
- http://m.mobile.fuvxie.cn/Article/details/595979.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3142652.sHtML
- http://m.mobile.fuvxie.cn/Article/details/835228.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2944990.sHtML
- http://m.mobile.fuvxie.cn/Article/details/14363.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8299.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6732.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0147.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9689786.sHtML
- http://m.mobile.fuvxie.cn/Article/details/86449.sHtML
- http://m.mobile.fuvxie.cn/Article/details/328749.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0693.sHtML
- http://m.mobile.fuvxie.cn/Article/details/66660.sHtML
- http://m.mobile.fuvxie.cn/Article/details/13696.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9242667.sHtML
- http://m.mobile.fuvxie.cn/Article/details/527884.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9464.sHtML
- http://m.mobile.fuvxie.cn/Article/details/45749.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5643968.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5695249.sHtML
- http://m.mobile.fuvxie.cn/Article/details/735461.sHtML
- http://m.mobile.fuvxie.cn/Article/details/583040.sHtML
- http://m.mobile.fuvxie.cn/Article/details/146138.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8927852.sHtML
- http://m.mobile.fuvxie.cn/Article/details/439392.sHtML
- http://m.mobile.fuvxie.cn/Article/details/588235.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0749.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5069129.sHtML
- http://m.mobile.fuvxie.cn/Article/details/064762.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4194948.sHtML
- http://m.mobile.fuvxie.cn/Article/details/56403.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6295.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4856.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8007369.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0139.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9962049.sHtML
- http://m.mobile.fuvxie.cn/Article/details/35182.sHtML
- http://m.mobile.fuvxie.cn/Article/details/24117.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8999110.sHtML
- http://m.mobile.fuvxie.cn/Article/details/236183.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2727201.sHtML
- http://m.mobile.fuvxie.cn/Article/details/363835.sHtML
- http://m.mobile.fuvxie.cn/Article/details/229209.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0550.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5865.sHtML
- http://m.mobile.fuvxie.cn/Article/details/72669.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4239240.sHtML
- http://m.mobile.fuvxie.cn/Article/details/68371.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7405.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4397364.sHtML
- http://m.mobile.fuvxie.cn/Article/details/69258.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8011677.sHtML
- http://m.mobile.fuvxie.cn/Article/details/687955.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5492.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5149.sHtML
- http://m.mobile.fuvxie.cn/Article/details/99332.sHtML
- http://m.mobile.fuvxie.cn/Article/details/282889.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3570.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4665041.sHtML
- http://m.mobile.fuvxie.cn/Article/details/99831.sHtML
- http://m.mobile.fuvxie.cn/Article/details/38317.sHtML
- http://m.mobile.fuvxie.cn/Article/details/926039.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5425.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9597.sHtML
- http://m.mobile.fuvxie.cn/Article/details/09940.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1424.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5848433.sHtML
- http://m.mobile.fuvxie.cn/Article/details/69822.sHtML
- http://m.mobile.fuvxie.cn/Article/details/20659.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9214.sHtML
- http://m.mobile.fuvxie.cn/Article/details/863393.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3040654.sHtML
- http://m.mobile.fuvxie.cn/Article/details/041979.sHtML
- http://m.mobile.fuvxie.cn/Article/details/1379.sHtML
- http://m.mobile.fuvxie.cn/Article/details/221606.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6446050.sHtML
- http://m.mobile.fuvxie.cn/Article/details/80079.sHtML
- http://m.mobile.fuvxie.cn/Article/details/884952.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7836.sHtML
- http://m.mobile.fuvxie.cn/Article/details/259669.sHtML
- http://m.mobile.fuvxie.cn/Article/details/727264.sHtML
- http://m.mobile.fuvxie.cn/Article/details/43907.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8082859.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6618667.sHtML
- http://m.mobile.fuvxie.cn/Article/details/904681.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8213181.sHtML
- http://m.mobile.fuvxie.cn/Article/details/09523.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0815039.sHtML
- http://m.mobile.fuvxie.cn/Article/details/65753.sHtML
- http://m.mobile.fuvxie.cn/Article/details/124060.sHtML
- http://m.mobile.fuvxie.cn/Article/details/8924543.sHtML
- http://m.mobile.fuvxie.cn/Article/details/994754.sHtML
- http://m.mobile.fuvxie.cn/Article/details/57792.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2332.sHtML
- http://m.mobile.fuvxie.cn/Article/details/85149.sHtML
- http://m.mobile.fuvxie.cn/Article/details/41353.sHtML
- http://m.mobile.fuvxie.cn/Article/details/41854.sHtML
- http://m.mobile.fuvxie.cn/Article/details/03832.sHtML
- http://m.mobile.fuvxie.cn/Article/details/3624.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5355786.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0603.sHtML
- http://m.mobile.fuvxie.cn/Article/details/9793.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7708522.sHtML
- http://m.mobile.fuvxie.cn/Article/details/94128.sHtML
- http://m.mobile.fuvxie.cn/Article/details/6218280.sHtML
- http://m.mobile.fuvxie.cn/Article/details/139139.sHtML
- http://m.mobile.fuvxie.cn/Article/details/27033.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7060.sHtML
- http://m.mobile.fuvxie.cn/Article/details/0422231.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2257547.sHtML
- http://m.mobile.fuvxie.cn/Article/details/7111.sHtML
- http://m.mobile.fuvxie.cn/Article/details/5146.sHtML
- http://m.mobile.fuvxie.cn/Article/details/4749497.sHtML
- http://m.mobile.fuvxie.cn/Article/details/04354.sHtML
- http://m.mobile.fuvxie.cn/Article/details/24892.sHtML
- http://m.mobile.fuvxie.cn/Article/details/03769.sHtML
- http://m.mobile.fuvxie.cn/Article/details/2914.sHtML
- http://m.mobile.fuvxie.cn/Article/details/44778.sHtML

## 项目结构

```
weblink-atlas/
├── cli.py                      # 命令行入口，整合导入、检测、导出、生成功能
├── requirements.txt            # Python 依赖列表，包含 requests、bs4、markdown、jinja2
├── README.md                   # 项目说明文档，即本文件
├── LICENSE                     # MIT 许可证文件
├── .gitignore                  # Git 忽略规则，排除 output/、logs/、__pycache__/
│
├── core/                       # 核心业务逻辑模块
│   ├── __init__.py
│   ├── importer.py             # 链接导入与去重逻辑，支持 txt/csv 格式
│   ├── checker.py              # HTTP 状态检测与元数据提取，支持超时重试
│   ├── tagger.py               # 标签管理，支持添加、删除、按标签筛选
│   └── exporter.py             # 多格式导出：markdown、json、plain、html
│
├── models/                     # 数据模型与序列化层
│   ├── __init__.py
│   ├── link.py                 # Link 数据类定义，包含 url、status、tags、meta 字段
│   ├── batch.py                # Batch 数据类，记录批次编号、时间戳、统计信息
│   └── storage.py              # JSON 文件读写与索引维护，负责持久化
│
├── utils/                      # 工具函数集合
│   ├── __init__.py
│   ├── network.py              # 网络请求封装，含代理支持和 SSL 容错
│   ├── parser.py               # URL 解析与规范化，处理大小写、尾部斜杠
│   └── logger.py               # 日志记录器，按日期轮转，输出到 logs/ 目录
│
├── templates/                  # 静态站点生成所用的 Jinja2 模板
│   ├── default.html            # 默认的目录页模板，带响应式布局
│   └── compact.html            # 紧凑型模板，仅列表不带样式
│
├── samples/                    # 示例数据，供快速测试使用
│   └── batch_14.txt            # 第 14 批资源的纯文本示例，包含 250 个链接
│
├── output/                     # 运行时生成的数据文件目录（默认被 .gitignore 忽略）
│   └── batch_14.json           # 导入并检测后的完整结构化数据
│
├── docs/                       # 静态站点输出目录，可直接部署为静态网页
│   └── index.html              # 由模板生成的最新目录页
│
└── logs/                       # 日志存储目录，按天切分
    └── weblink.log             # 包含导入、检测、导出全过程的详细日志
```

## 贡献指南

**提交 Issue 报告问题** 在提交 Issue 前，请先查阅现有 Issue 列表和 FAQ 文档。报告时应提供完整的运行环境信息（Python 版本、操作系统、依赖版本）、复现步骤以及相关的日志片段。如果涉及特定链接检测失败，请附上 URL 示例。

**遵循代码风格规范** 本项目使用 PEP 8 作为 Python 代码风格基准，行宽限制为 120 字符。所有新增函数必须包含 docstring，说明参数类型、返回值以及可能抛出的异常。提交前请使用 flake8 和 black 进行格式检查。

**编写单元测试** 所有新增的核心功能模块应配套对应的单元测试，测试文件放置在 tests/ 目录下，命名格式为 test_模块名.py。测试框架使用 pytest，覆盖率目标不低于 80%。现有测试用例可在提交前运行 pytest 进行验证。

**提交 Pull Request 流程** 请从 main 分支创建新的功能分支，命名格式为 feature/简短描述 或 fix/问题编号。提交信息应遵循 Conventional Commits 规范，首行不超过 72 字符，内容清晰说明变更意图。PR 描述中需关联相关 Issue，并说明测试覆盖情况。

**更新文档与示例** 任何影响用户可见行为的变更，均需同步更新 README 中对应的章节，以及 samples/ 目录下的示例数据格式说明。若新增了 CLI 参数，需在 docs/api-reference.md 中补充说明。

## 常见问题

**问：检测链接状态时大量超时，如何优化？**

答：链接检测超时通常由目标服务器响应缓慢或网络防火墙限制引起。建议按以下步骤排查：首先检查 cli.py 中的 --timeout 参数，默认值为 10 秒，可适当增加至 30 秒。其次，若处于代理环境，请在 core/checker.py 中配置 HTTP_PROXY 和 HTTPS_PROXY 环境变量。最后，对于大批量检测，建议使用 --rate-limit 参数控制每秒请求数，避免被目标服务器封禁。若仍有大量超时，可启用 --skip-ssl 跳过 SSL 证书验证。

**问：如何将本项目的资源列表嵌入到其他 Markdown 文档中？**

答：使用 exporter.py 的 --format markdown 选项可直接生成标准 Markdown 无序列表。若需要嵌入到特定章节，可导出后手动复制。若希望自动化集成，可编写脚本调用 core/exporter.py 中的 export_markdown 函数，并指定输出文件路径。对于 Jekyll、Hugo 等静态站点生成器，建议使用 --format json 导出数据，再通过模板语言自行渲染。

**问：项目是否支持对链接进行分类或添加备注？**

答：支持。每条链接可关联多个标签，通过 tagger.py 中的 add_tag 和 remove_tag 函数管理。在导入时，可在源文件中以特定前缀（如 #tech、#blog）标记标签，cli.py 的 import 命令支持 --tag-prefix 参数自动识别。备注信息存储在 Link 数据类的 meta 字段中，为自由格式的字典，可通过 --meta 参数以 JSON 字符串形式传入。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
