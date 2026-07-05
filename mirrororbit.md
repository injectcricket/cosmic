# LinkMap Cortex

LinkMap Cortex 是一个面向技术研究与知识工程领域的外链资源归集与结构化导航系统。项目定位于将分散于各类技术博客、文档站、论坛与代码托管平台中的高质量外部链接进行统一抓取、分类标注、去重校验与版本化存储，为开发者、技术作者与知识库维护者提供可追溯、可检索、可审计的原始链接资产库。

本项目不生产内容，只做链接的忠实搬运与组织。目标用户包括技术文档工程师、开源社区运营者、爬虫策略开发者以及需要批量维护外链可用性的 QA 团队。LinkMap Cortex 通过固定的资源批次划分与严格的原样输出规则，确保每一批纳入系统的 URL 在入库、展示与导出环节均不发生任何协议变更、大小写转换或路径改写，从根本上解决外链迁移过程中普遍存在的链接漂移与格式污染问题。

## 功能概览

**批次化资源录入**：支持按批次导入原始 URL 列表，当前第 186/200 批共收纳 250 个外链条目，每批次独立记录来源与导入时间戳。

**原样输出强制校验**：系统内置格式检查器，对每条 URL 执行协议一致性校验、域名大小写校验与路径后缀完整性校验，拒绝任何自动补全协议头或大小写归一化操作。

**多维度资源检索**：提供按文章 ID、域名前缀、文件扩展名与入库批次号的组合过滤能力，支持快速定位特定来源站点的所有链接。

**链接状态监控**：集成异步 HTTP 状态检查任务，可定期探测每条外链的可达性并记录响应时间与状态码变化趋势。

**结构化数据导出**：支持将当前批次的全部链接以纯文本列表、JSON 数组或 Markdown 无序列表三种格式导出，适配不同下游系统对链接数据格式的需求。

**审计日志追踪**：记录每次链接列表的增删改操作，保留操作人、操作时间与变更前后的原始内容，满足资源管理的可追溯性要求。

## 应用场景

技术文档站点维护：当技术博客或开源项目文档站需要定期更新参考文献或扩展阅读章节时，维护人员可使用 LinkMap Cortex 导入候选外链清单，借助批次管理功能区分不同文章或不同版本的引用资源，并通过原样输出规则确保发布后的链接与作者原始提交保持一致。

爬虫策略测试环境：爬虫开发者在构建链接解析与去重逻辑时，可利用本系统提供的固定批次链接数据作为测试集，验证爬虫程序对大小写敏感路径、非标准扩展名以及纯数字 ID 格式链接的处理正确性，避免因链接格式误判导致的漏抓或错抓。

开源项目外部依赖溯源：开源项目的 README 或文档中常引用外部技术资源，当项目需要向合规审查方提交所用外部资源的完整清单时，可通过本系统的资源列表导出功能快速生成一份未经任何格式改写的原始链接台账。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
git clone https://github.com/linkmap/linkmap-cortex.git
cd linkmap-cortex
pip install -r requirements.txt
python scripts/import_batch.py --batch 186 --source ./data/raw/links_186.txt
```

上述命令完成仓库克隆、依赖安装与第 186 批链接数据的导入。导入成功后，可通过本地 Web 界面或命令行工具查看已入库的资源列表。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，用于执行导入脚本与调度任务 |
| SQLite | 3.35 及以上 | 本地轻量级数据库，存储链接元数据与审计日志 |
| requests | 2.28.0 及以上 | 用于链接可达性探测与 HTTP 状态检查 |
| pytest | 7.2.0 及以上 | 单元测试框架，用于验证 URL 原样输出逻辑 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库与管理配置变更 |
| virtualenv | 20.16.0 及以上 | 推荐用于创建隔离的 Python 依赖环境 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | docs/user-guide/batch-import.md | 如何创建新批次并导入原始链接数据 |
| 用户手册 | docs/user-guide/link-query.md | 如何按 ID、域名或批次号检索已入库链接 |
| 开发指南 | docs/developer/url-normalization.md | 系统为何以及如何强制禁止 URL 格式改写 |
| 运维手册 | docs/operations/health-check.md | 如何配置定时任务监控外链可用性 |

## 资源列表

- http://map.mobile.hcbezg.cn/Article/details/3909081.sHtML
- http://map.mobile.hcbezg.cn/Article/details/858917.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8160988.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2877.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8921982.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2677656.sHtML
- http://map.mobile.hcbezg.cn/Article/details/248281.sHtML
- http://map.mobile.hcbezg.cn/Article/details/65607.sHtML
- http://map.mobile.hcbezg.cn/Article/details/71257.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7400894.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3635310.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9197.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6546.sHtML
- http://map.mobile.hcbezg.cn/Article/details/65792.sHtML
- http://map.mobile.hcbezg.cn/Article/details/628810.sHtML
- http://map.mobile.hcbezg.cn/Article/details/22999.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2097.sHtML
- http://map.mobile.hcbezg.cn/Article/details/831255.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6255805.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4560603.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0517752.sHtML
- http://map.mobile.hcbezg.cn/Article/details/859706.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9404094.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9173880.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9096257.sHtML
- http://map.mobile.hcbezg.cn/Article/details/995347.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5955.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6077265.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4718.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3479.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7225038.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9071032.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4802.sHtML
- http://map.mobile.hcbezg.cn/Article/details/773515.sHtML
- http://map.mobile.hcbezg.cn/Article/details/132573.sHtML
- http://map.mobile.hcbezg.cn/Article/details/22989.sHtML
- http://map.mobile.hcbezg.cn/Article/details/43753.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2050937.sHtML
- http://map.mobile.hcbezg.cn/Article/details/772585.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2962.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0991644.sHtML
- http://map.mobile.hcbezg.cn/Article/details/73274.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8847.sHtML
- http://map.mobile.hcbezg.cn/Article/details/903505.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0928.sHtML
- http://map.mobile.hcbezg.cn/Article/details/87152.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1590133.sHtML
- http://map.mobile.hcbezg.cn/Article/details/54175.sHtML
- http://map.mobile.hcbezg.cn/Article/details/13906.sHtML
- http://map.mobile.hcbezg.cn/Article/details/60777.sHtML
- http://map.mobile.hcbezg.cn/Article/details/591069.sHtML
- http://map.mobile.hcbezg.cn/Article/details/74109.sHtML
- http://map.mobile.hcbezg.cn/Article/details/299644.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7381400.sHtML
- http://map.mobile.hcbezg.cn/Article/details/00295.sHtML
- http://map.mobile.hcbezg.cn/Article/details/02254.sHtML
- http://map.mobile.hcbezg.cn/Article/details/10719.sHtML
- http://map.mobile.hcbezg.cn/Article/details/02142.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6527.sHtML
- http://map.mobile.hcbezg.cn/Article/details/77498.sHtML
- http://map.mobile.hcbezg.cn/Article/details/57758.sHtML
- http://map.mobile.hcbezg.cn/Article/details/01686.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4537328.sHtML
- http://map.mobile.hcbezg.cn/Article/details/50705.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3405.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4399.sHtML
- http://map.mobile.hcbezg.cn/Article/details/365506.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3761625.sHtML
- http://map.mobile.hcbezg.cn/Article/details/67310.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3027.sHtML
- http://map.mobile.hcbezg.cn/Article/details/120626.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9496345.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9831.sHtML
- http://map.mobile.hcbezg.cn/Article/details/387899.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6088153.sHtML
- http://map.mobile.hcbezg.cn/Article/details/99754.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1272827.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6021.sHtML
- http://map.mobile.hcbezg.cn/Article/details/541717.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5552934.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5174387.sHtML
- http://map.mobile.hcbezg.cn/Article/details/87577.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9032.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4796025.sHtML
- http://map.mobile.hcbezg.cn/Article/details/803184.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7108899.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1656.sHtML
- http://map.mobile.hcbezg.cn/Article/details/86772.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9575093.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5969.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0026.sHtML
- http://map.mobile.hcbezg.cn/Article/details/66958.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4568188.sHtML
- http://map.mobile.hcbezg.cn/Article/details/34976.sHtML
- http://map.mobile.hcbezg.cn/Article/details/74373.sHtML
- http://map.mobile.hcbezg.cn/Article/details/15030.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4604.sHtML
- http://map.mobile.hcbezg.cn/Article/details/98721.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0980.sHtML
- http://map.mobile.hcbezg.cn/Article/details/35008.sHtML
- http://map.mobile.hcbezg.cn/Article/details/88428.sHtML
- http://map.mobile.hcbezg.cn/Article/details/18021.sHtML
- http://map.mobile.hcbezg.cn/Article/details/637242.sHtML
- http://map.mobile.hcbezg.cn/Article/details/954702.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2477.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0276080.sHtML
- http://map.mobile.hcbezg.cn/Article/details/983875.sHtML
- http://map.mobile.hcbezg.cn/Article/details/723092.sHtML
- http://map.mobile.hcbezg.cn/Article/details/823217.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2462.sHtML
- http://map.mobile.hcbezg.cn/Article/details/15910.sHtML
- http://map.mobile.hcbezg.cn/Article/details/36226.sHtML
- http://map.mobile.hcbezg.cn/Article/details/402557.sHtML
- http://map.mobile.hcbezg.cn/Article/details/631629.sHtML
- http://map.mobile.hcbezg.cn/Article/details/837989.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9500430.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8494.sHtML
- http://map.mobile.hcbezg.cn/Article/details/872477.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7647517.sHtML
- http://map.mobile.hcbezg.cn/Article/details/954284.sHtML
- http://map.mobile.hcbezg.cn/Article/details/72608.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2768457.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8560296.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8439.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2301.sHtML
- http://map.mobile.hcbezg.cn/Article/details/311825.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8281.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9001.sHtML
- http://map.mobile.hcbezg.cn/Article/details/38630.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7321.sHtML
- http://map.mobile.hcbezg.cn/Article/details/422498.sHtML
- http://map.mobile.hcbezg.cn/Article/details/024932.sHtML
- http://map.mobile.hcbezg.cn/Article/details/263715.sHtML
- http://map.mobile.hcbezg.cn/Article/details/099447.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6471.sHtML
- http://map.mobile.hcbezg.cn/Article/details/778078.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6331.sHtML
- http://map.mobile.hcbezg.cn/Article/details/430560.sHtML
- http://map.mobile.hcbezg.cn/Article/details/08148.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3673.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8393.sHtML
- http://map.mobile.hcbezg.cn/Article/details/59343.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0006830.sHtML
- http://map.mobile.hcbezg.cn/Article/details/763594.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7203.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2384.sHtML
- http://map.mobile.hcbezg.cn/Article/details/371275.sHtML
- http://map.mobile.hcbezg.cn/Article/details/63450.sHtML
- http://map.mobile.hcbezg.cn/Article/details/39531.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0434.sHtML
- http://map.mobile.hcbezg.cn/Article/details/865377.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3598216.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5027396.sHtML
- http://map.mobile.hcbezg.cn/Article/details/628468.sHtML
- http://map.mobile.hcbezg.cn/Article/details/327140.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4627175.sHtML
- http://map.mobile.hcbezg.cn/Article/details/43900.sHtML
- http://map.mobile.hcbezg.cn/Article/details/148324.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4377.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7265534.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5447.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2774621.sHtML
- http://map.mobile.hcbezg.cn/Article/details/483162.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9955602.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3335.sHtML
- http://map.mobile.hcbezg.cn/Article/details/864436.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5579207.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9511582.sHtML
- http://map.mobile.hcbezg.cn/Article/details/683762.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5283.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1678601.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5134.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9445457.sHtML
- http://map.mobile.hcbezg.cn/Article/details/777771.sHtML
- http://map.mobile.hcbezg.cn/Article/details/084199.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4433257.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3005.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2086.sHtML
- http://map.mobile.hcbezg.cn/Article/details/660455.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4651258.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1275655.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3436014.sHtML
- http://map.mobile.hcbezg.cn/Article/details/195262.sHtML
- http://map.mobile.hcbezg.cn/Article/details/722481.sHtML
- http://map.mobile.hcbezg.cn/Article/details/017656.sHtML
- http://map.mobile.hcbezg.cn/Article/details/557449.sHtML
- http://map.mobile.hcbezg.cn/Article/details/00838.sHtML
- http://map.mobile.hcbezg.cn/Article/details/421845.sHtML
- http://map.mobile.hcbezg.cn/Article/details/250094.sHtML
- http://map.mobile.hcbezg.cn/Article/details/340561.sHtML
- http://map.mobile.hcbezg.cn/Article/details/911324.sHtML
- http://map.mobile.hcbezg.cn/Article/details/842150.sHtML
- http://map.mobile.hcbezg.cn/Article/details/23811.sHtML
- http://map.mobile.hcbezg.cn/Article/details/64473.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7631.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3187.sHtML
- http://map.mobile.hcbezg.cn/Article/details/78607.sHtML
- http://map.mobile.hcbezg.cn/Article/details/31320.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3913136.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5598.sHtML
- http://map.mobile.hcbezg.cn/Article/details/39772.sHtML
- http://map.mobile.hcbezg.cn/Article/details/856526.sHtML
- http://map.mobile.hcbezg.cn/Article/details/370198.sHtML
- http://map.mobile.hcbezg.cn/Article/details/163443.sHtML
- http://map.mobile.hcbezg.cn/Article/details/65108.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5544.sHtML
- http://map.mobile.hcbezg.cn/Article/details/451347.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9315.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6202636.sHtML
- http://map.mobile.hcbezg.cn/Article/details/771574.sHtML
- http://map.mobile.hcbezg.cn/Article/details/317898.sHtML
- http://map.mobile.hcbezg.cn/Article/details/86293.sHtML
- http://map.mobile.hcbezg.cn/Article/details/70801.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6260.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0800886.sHtML
- http://map.mobile.hcbezg.cn/Article/details/09598.sHtML
- http://map.mobile.hcbezg.cn/Article/details/511200.sHtML
- http://map.mobile.hcbezg.cn/Article/details/01322.sHtML
- http://map.mobile.hcbezg.cn/Article/details/05813.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7713.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5094.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3578.sHtML
- http://map.mobile.hcbezg.cn/Article/details/883607.sHtML
- http://map.mobile.hcbezg.cn/Article/details/73406.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9371.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3404.sHtML
- http://map.mobile.hcbezg.cn/Article/details/10793.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2156.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6819679.sHtML
- http://map.mobile.hcbezg.cn/Article/details/207160.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7038.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5643.sHtML
- http://map.mobile.hcbezg.cn/Article/details/52679.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3886667.sHtML
- http://map.mobile.hcbezg.cn/Article/details/301131.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4137.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8131052.sHtML
- http://map.mobile.hcbezg.cn/Article/details/112235.sHtML
- http://map.mobile.hcbezg.cn/Article/details/591936.sHtML
- http://map.mobile.hcbezg.cn/Article/details/102761.sHtML
- http://map.mobile.hcbezg.cn/Article/details/486493.sHtML
- http://map.mobile.hcbezg.cn/Article/details/271066.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7500650.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4385876.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7462973.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0700926.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5818.sHtML
- http://map.mobile.hcbezg.cn/Article/details/382865.sHtML
- http://map.mobile.hcbezg.cn/Article/details/108325.sHtML
- http://map.mobile.hcbezg.cn/Article/details/92424.sHtML

## 项目结构

```
linkmap-cortex/
├── data/
│   ├── raw/                         # 原始批次链接文件存放目录
│   │   └── links_186.txt            # 第186批原始URL列表，每行一条
│   └── curated/                     # 经过校验与去重后的链接数据
│       └── batch_186_clean.json     # 结构化存储，含入库时间戳与校验状态
├── src/
│   ├── importer/                    # 导入模块：解析原始文件并写入数据库
│   │   ├── file_reader.py           # 逐行读取链接文件，保留原始大小写
│   │   └── batch_validator.py       # 执行协议与路径格式校验
│   ├── storage/                     # 存储模块：SQLite 表结构与ORM映射
│   │   ├── models.py                # 定义 Link 与 Batch 数据模型
│   │   └── repository.py            # 增删改查操作封装
│   ├── monitor/                     # 监控模块：异步HTTP状态检查
│   │   ├── checker.py               # 并发发送HEAD请求探测可达性
│   │   └── scheduler.py             # 定时任务调度器，可配置检查周期
│   └── exporter/                    # 导出模块：支持多种输出格式
│       ├── plain_exporter.py        # 纯文本列表导出
│       └── markdown_exporter.py     # 生成Markdown无序列表
├── scripts/
│   └── import_batch.py              # 命令行入口，接收批次号与源文件路径
├── tests/
│   ├── test_validator.py            # 校验逻辑的单元测试用例
│   └── test_exporter.py             # 导出格式与原始数据一致性测试
├── docs/                            # 文档目录，包含用户手册与开发指南
├── requirements.txt                 # Python依赖清单
└── README.md                        # 项目根文档（即当前文件）
```

## 贡献指南

1. 复刻本仓库至个人账号，在本地创建功能分支，分支命名格式为 feature/batch-{批次号} 或 fix/链接校验逻辑描述。

2. 对导入脚本或校验规则进行修改后，需在 tests 目录下补充对应的单元测试用例，确保新代码覆盖至少 80% 的边界条件，尤其是针对 URL 大小写与协议格式的原始保留逻辑。

3. 提交前执行 pytest 验证全部测试用例通过，并使用 pre-commit 钩子检查代码风格是否符合 PEP 8 规范。

4. 向主仓库发起 Pull Request，在描述中明确说明本次变更影响的批次范围、修改原因以及手动测试结果，等待至少一位维护者审核。

5. 审核通过后由维护者执行合并，合并后自动触发 GitHub Actions 工作流，对最新一批导入的链接执行全量可达性检查并将结果回写至 data/curated 目录。

## 常见问题

问：系统是否会对导入的 URL 自动补全缺失的协议头或统一转为小写？

答：不会。LinkMap Cortex 的核心设计原则之一是原样输出。导入模块在读取文件时逐行保留原始字符串，不在任何环节对协议头、域名大小写、路径大小写或文件扩展名做任何改写。展示与导出时同样使用原始存储值，确保最终输出的链接与用户提供的文本完全一致。

问：如何查看某一批次中所有链接的最新可达性状态？

答：可通过命令行工具执行 python scripts/check_batch.py --batch 186，系统将依次发送 HTTP HEAD 请求并记录状态码与响应时间。检查结果会以表格形式输出至控制台，同时追加至 data/curated/batch_186_status.json 文件中供后续查阅。

问：导入的链接数量很大时，系统如何处理重复条目？

答：系统以完整 URL 字符串作为唯一键，导入过程中自动对当前批次内部执行去重。跨批次重复的链接不会报错，但会在数据库的 link_occurrences 表中记录每次出现的批次号与导入时间，便于后续审计时追踪相同链接在不同批次的分布情况。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
