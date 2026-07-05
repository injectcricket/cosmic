# WebLink Navigator

WebLink Navigator 是一个面向技术研究者、内容聚合运营者与信息分析团队的高密度外链资源归集与导航系统。该项目定位于将分散在各类内容源中的结构化文章链接进行统一收录、分类索引与状态监控，解决技术团队在批量外链管理、链接可用性追踪及内容溯源场景下的效率问题。

本项目不对链接内容进行实质性修改或二次分发，仅作为链接元信息的整理与呈现层，适用于需要快速建立外链资产清单、进行批量链接巡检或构建内容地图的运维与开发场景。

## 功能概览

- **批量链接归集**：支持将大量原始链接按来源、批次与收录时间进行结构化存储，并提供批次维度（当前为第 189/200 批，共 250 个资源链接）的元数据标记，便于后续按批巡检与版本比对。

- **链接状态探测**：集成被动式链接健康度检查机制，可定期对已收录的 URL 发起 HEAD 请求，记录响应码、响应时间与重定向链，辅助识别失效或慢速资源。

- **多维筛选与检索**：基于链接路径特征、域名、文件扩展名及 ID 模式提供基础筛选能力，支持按 Article ID 区间、路径层级或文件类型（如 .sHtML）进行快速过滤。

- **原始数据透明呈现**：所有收录的链接均以原始输入形式原样保留，不进行协议补全、域名规范化或路径改写，确保与用户提供的数据源完全一致，避免因自动修正导致的溯源偏差。

- **元数据注解与标签**：允许为每条链接附加自定义标签、备注说明与重要性评级，方便团队内部对链接进行业务维度分类（如“高优先级巡检”、“待人工复核”、“已失效备查”）。

- **导出与集成支持**：提供 JSON、CSV 及纯文本列表格式的链接导出接口，可与其他监控系统、数据看板或自动化脚本集成，形成完整的数据流水线。

- **批次追溯与变更记录**：记录每次批次的收录时间、链接数量及与前一批次的差异（新增/移除/变更），满足审计与变更管理需求。

## 应用场景

**技术文档外链资产整理**  
技术团队在撰写文档或维护知识库时，经常引用大量外部文章。WebLink Navigator 可作为外链引用台账，统一记录所有引用链接的原始地址，方便在文档迁移或外部资源变动时快速定位并更新引用。

**内容聚合平台的链接源管理**  
内容聚合或资讯类应用需要从多个数据源抓取文章详情页链接。本项目可作为链接源的预录入系统，对即将进入抓取队列的链接进行批次管理、去重校验与初步健康检查，降低抓取任务中的无效请求比例。

**SEO 与运营侧的外链巡检**  
运营人员需要定期检查网站外部链接的可用性，避免因链接失效影响用户体验或搜索排名。WebLink Navigator 提供结构化的链接清单与状态记录能力，可与自动化巡检脚本配合，生成每周链接健康报告。

**数据迁移与历史链接归档**  
在系统重构或域名切换时，大量历史文章链接需要被完整记录并映射至新系统。本项目支持按批次导入原始链接数据，保留完整的原始 URL 字符串，为后续的链接重定向规则编写或 301 映射表生成提供原始依据。

## 快速开始

以下步骤指导您在本地环境中快速启动 WebLink Navigator 的核心服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装项目依赖（使用 pip 与 requirements.txt）
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python scripts/init_db.py

# 导入示例批次链接数据（包含当前第 189/200 批）
python scripts/import_batch.py --batch 189 --source data/batch_189.txt

# 启动本地开发服务器
python app.py --host 127.0.0.1 --port 8080
```

启动后，可通过浏览器访问 `http://127.0.0.1:8080` 查看链接列表与批次信息。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.10 或 3.11 LTS 版本 |
| SQLite | 3.35 及以上 | 内置轻量级数据库，用于存储链接元数据与批次信息 |
| requests | 2.28.0 及以上 | 用于发起链接状态探测请求，支持 HTTP/HTTPS 协议 |
| click | 8.1.0 及以上 | 命令行交互框架，用于执行导入、导出与巡检命令 |
| pytest | 7.2.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| flask | 2.2.0 及以上 | Web 界面服务框架（可选，若仅使用 CLI 可忽略） |
| python-dotenv | 1.0.0 及以上 | 环境变量加载，用于配置数据库路径与巡检超时参数 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何导入批次、如何查看链接列表、如何执行手动状态检查 |
| 运维指南 | docs/ops_guide.md | 如何配置巡检频率、如何备份数据库、如何迁移至 PostgreSQL |
| 开发者文档 | docs/dev_guide.md | 数据表结构说明、扩展链接解析器的方法、API 接口规范 |
| 常见问题 | docs/faq.md | 链接状态码含义、导入失败原因分析、批量导出格式说明 |

## 资源列表

- http://map.mobile.hcbezg.cn/Article/details/4957696.sHtML
- http://map.mobile.hcbezg.cn/Article/details/55586.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4311.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2965.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8880.sHtML
- http://map.mobile.hcbezg.cn/Article/details/68638.sHtML
- http://map.mobile.hcbezg.cn/Article/details/479963.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1880334.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0837205.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4953.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8066651.sHtML
- http://map.mobile.hcbezg.cn/Article/details/53863.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2969.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9859.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3921.sHtML
- http://map.mobile.hcbezg.cn/Article/details/21402.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0540.sHtML
- http://map.mobile.hcbezg.cn/Article/details/740917.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2689091.sHtML
- http://map.mobile.hcbezg.cn/Article/details/52266.sHtML
- http://map.mobile.hcbezg.cn/Article/details/75521.sHtML
- http://map.mobile.hcbezg.cn/Article/details/24684.sHtML
- http://map.mobile.hcbezg.cn/Article/details/56406.sHtML
- http://map.mobile.hcbezg.cn/Article/details/45963.sHtML
- http://map.mobile.hcbezg.cn/Article/details/822232.sHtML
- http://map.mobile.hcbezg.cn/Article/details/23196.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7588235.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2981.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8571965.sHtML
- http://map.mobile.hcbezg.cn/Article/details/17734.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7169545.sHtML
- http://map.mobile.hcbezg.cn/Article/details/201497.sHtML
- http://map.mobile.hcbezg.cn/Article/details/011546.sHtML
- http://map.mobile.hcbezg.cn/Article/details/71588.sHtML
- http://map.mobile.hcbezg.cn/Article/details/587984.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8235021.sHtML
- http://map.mobile.hcbezg.cn/Article/details/738277.sHtML
- http://map.mobile.hcbezg.cn/Article/details/269692.sHtML
- http://map.mobile.hcbezg.cn/Article/details/75054.sHtML
- http://map.mobile.hcbezg.cn/Article/details/962039.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4085.sHtML
- http://map.mobile.hcbezg.cn/Article/details/175303.sHtML
- http://map.mobile.hcbezg.cn/Article/details/67913.sHtML
- http://map.mobile.hcbezg.cn/Article/details/557892.sHtML
- http://map.mobile.hcbezg.cn/Article/details/735464.sHtML
- http://map.mobile.hcbezg.cn/Article/details/024268.sHtML
- http://map.mobile.hcbezg.cn/Article/details/96423.sHtML
- http://map.mobile.hcbezg.cn/Article/details/851644.sHtML
- http://map.mobile.hcbezg.cn/Article/details/25534.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2958008.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8095.sHtML
- http://map.mobile.hcbezg.cn/Article/details/241909.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1687.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3752131.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1521.sHtML
- http://map.mobile.hcbezg.cn/Article/details/93261.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6004.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2331.sHtML
- http://map.mobile.hcbezg.cn/Article/details/97896.sHtML
- http://map.mobile.hcbezg.cn/Article/details/394137.sHtML
- http://map.mobile.hcbezg.cn/Article/details/695355.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5237.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2059.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0392.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3327.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7195963.sHtML
- http://map.mobile.hcbezg.cn/Article/details/126550.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1085778.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8769.sHtML
- http://map.mobile.hcbezg.cn/Article/details/531086.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5061.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3246114.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0115267.sHtML
- http://map.mobile.hcbezg.cn/Article/details/37791.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0135391.sHtML
- http://map.mobile.hcbezg.cn/Article/details/31597.sHtML
- http://map.mobile.hcbezg.cn/Article/details/918129.sHtML
- http://map.mobile.hcbezg.cn/Article/details/932730.sHtML
- http://map.mobile.hcbezg.cn/Article/details/92185.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0349356.sHtML
- http://map.mobile.hcbezg.cn/Article/details/468692.sHtML
- http://map.mobile.hcbezg.cn/Article/details/640085.sHtML
- http://map.mobile.hcbezg.cn/Article/details/664040.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4373647.sHtML
- http://map.mobile.hcbezg.cn/Article/details/35150.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4152.sHtML
- http://map.mobile.hcbezg.cn/Article/details/382529.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4014782.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3593.sHtML
- http://map.mobile.hcbezg.cn/Article/details/54826.sHtML
- http://map.mobile.hcbezg.cn/Article/details/14745.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9599.sHtML
- http://map.mobile.hcbezg.cn/Article/details/23570.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8883.sHtML
- http://map.mobile.hcbezg.cn/Article/details/47413.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6068191.sHtML
- http://map.mobile.hcbezg.cn/Article/details/294322.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0022.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7264.sHtML
- http://map.mobile.hcbezg.cn/Article/details/95409.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2463.sHtML
- http://map.mobile.hcbezg.cn/Article/details/620004.sHtML
- http://map.mobile.hcbezg.cn/Article/details/215897.sHtML
- http://map.mobile.hcbezg.cn/Article/details/11924.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4169740.sHtML
- http://map.mobile.hcbezg.cn/Article/details/967982.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6929.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0134.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4893701.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3247262.sHtML
- http://map.mobile.hcbezg.cn/Article/details/644962.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5647376.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2587.sHtML
- http://map.mobile.hcbezg.cn/Article/details/64457.sHtML
- http://map.mobile.hcbezg.cn/Article/details/44106.sHtML
- http://map.mobile.hcbezg.cn/Article/details/819104.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0832.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1736120.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9235.sHtML
- http://map.mobile.hcbezg.cn/Article/details/49230.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7988916.sHtML
- http://map.mobile.hcbezg.cn/Article/details/41330.sHtML
- http://map.mobile.hcbezg.cn/Article/details/25003.sHtML
- http://map.mobile.hcbezg.cn/Article/details/714578.sHtML
- http://map.mobile.hcbezg.cn/Article/details/31159.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6482870.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1993816.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6057.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7744454.sHtML
- http://map.mobile.hcbezg.cn/Article/details/29386.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1149537.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8544337.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9606904.sHtML
- http://map.mobile.hcbezg.cn/Article/details/89473.sHtML
- http://map.mobile.hcbezg.cn/Article/details/498814.sHtML
- http://map.mobile.hcbezg.cn/Article/details/69479.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7870.sHtML
- http://map.mobile.hcbezg.cn/Article/details/276900.sHtML
- http://map.mobile.hcbezg.cn/Article/details/68649.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3586.sHtML
- http://map.mobile.hcbezg.cn/Article/details/605311.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0249895.sHtML
- http://map.mobile.hcbezg.cn/Article/details/94713.sHtML
- http://map.mobile.hcbezg.cn/Article/details/4092912.sHtML
- http://map.mobile.hcbezg.cn/Article/details/36954.sHtML
- http://map.mobile.hcbezg.cn/Article/details/663763.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0946.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3411.sHtML
- http://map.mobile.hcbezg.cn/Article/details/07405.sHtML
- http://map.mobile.hcbezg.cn/Article/details/843659.sHtML
- http://map.mobile.hcbezg.cn/Article/details/545755.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2536.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6205.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6294604.sHtML
- http://map.mobile.hcbezg.cn/Article/details/46372.sHtML
- http://map.mobile.hcbezg.cn/Article/details/939798.sHtML
- http://map.mobile.hcbezg.cn/Article/details/393985.sHtML
- http://map.mobile.hcbezg.cn/Article/details/99646.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6983671.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1342894.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9377.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9051794.sHtML
- http://map.mobile.hcbezg.cn/Article/details/20018.sHtML
- http://map.mobile.hcbezg.cn/Article/details/26434.sHtML
- http://map.mobile.hcbezg.cn/Article/details/00629.sHtML
- http://map.mobile.hcbezg.cn/Article/details/608046.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1568944.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6728.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7011897.sHtML
- http://map.mobile.hcbezg.cn/Article/details/59283.sHtML
- http://map.mobile.hcbezg.cn/Article/details/424134.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0699.sHtML
- http://map.mobile.hcbezg.cn/Article/details/25134.sHtML
- http://map.mobile.hcbezg.cn/Article/details/50002.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2388.sHtML
- http://map.mobile.hcbezg.cn/Article/details/385851.sHtML
- http://map.mobile.hcbezg.cn/Article/details/55112.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1540707.sHtML
- http://map.mobile.hcbezg.cn/Article/details/500533.sHtML
- http://map.mobile.hcbezg.cn/Article/details/915345.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8644997.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8330575.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7152.sHtML
- http://map.mobile.hcbezg.cn/Article/details/47483.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2368570.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9709.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7622255.sHtML
- http://map.mobile.hcbezg.cn/Article/details/242081.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0352890.sHtML
- http://map.mobile.hcbezg.cn/Article/details/28381.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3828749.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3042958.sHtML
- http://map.mobile.hcbezg.cn/Article/details/03799.sHtML
- http://map.mobile.hcbezg.cn/Article/details/361685.sHtML
- http://map.mobile.hcbezg.cn/Article/details/638687.sHtML
- http://map.mobile.hcbezg.cn/Article/details/179487.sHtML
- http://map.mobile.hcbezg.cn/Article/details/491253.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6141146.sHtML
- http://map.mobile.hcbezg.cn/Article/details/903976.sHtML
- http://map.mobile.hcbezg.cn/Article/details/145297.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6103457.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7971027.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8785.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2394307.sHtML
- http://map.mobile.hcbezg.cn/Article/details/23981.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3470561.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7982864.sHtML
- http://map.mobile.hcbezg.cn/Article/details/83257.sHtML
- http://map.mobile.hcbezg.cn/Article/details/01125.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2315942.sHtML
- http://map.mobile.hcbezg.cn/Article/details/66688.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5841604.sHtML
- http://map.mobile.hcbezg.cn/Article/details/56006.sHtML
- http://map.mobile.hcbezg.cn/Article/details/107474.sHtML
- http://map.mobile.hcbezg.cn/Article/details/65085.sHtML
- http://map.mobile.hcbezg.cn/Article/details/7777.sHtML
- http://map.mobile.hcbezg.cn/Article/details/0100042.sHtML
- http://map.mobile.hcbezg.cn/Article/details/8306.sHtML
- http://map.mobile.hcbezg.cn/Article/details/43671.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6995072.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6029.sHtML
- http://map.mobile.hcbezg.cn/Article/details/425955.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3014.sHtML
- http://map.mobile.hcbezg.cn/Article/details/3155.sHtML
- http://map.mobile.hcbezg.cn/Article/details/29701.sHtML
- http://map.mobile.hcbezg.cn/Article/details/64589.sHtML
- http://map.mobile.hcbezg.cn/Article/details/06178.sHtML
- http://map.mobile.hcbezg.cn/Article/details/93043.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1490950.sHtML
- http://map.mobile.hcbezg.cn/Article/details/45339.sHtML
- http://map.mobile.hcbezg.cn/Article/details/71227.sHtML
- http://map.mobile.hcbezg.cn/Article/details/499025.sHtML
- http://map.mobile.hcbezg.cn/Article/details/33410.sHtML
- http://map.mobile.hcbezg.cn/Article/details/29751.sHtML
- http://map.mobile.hcbezg.cn/Article/details/64758.sHtML
- http://map.mobile.hcbezg.cn/Article/details/851614.sHtML
- http://map.mobile.hcbezg.cn/Article/details/084530.sHtML
- http://map.mobile.hcbezg.cn/Article/details/660124.sHtML
- http://map.mobile.hcbezg.cn/Article/details/5832098.sHtML
- http://map.mobile.hcbezg.cn/Article/details/85729.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1053945.sHtML
- http://map.mobile.hcbezg.cn/Article/details/156452.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1827.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9458332.sHtML
- http://map.mobile.hcbezg.cn/Article/details/6098851.sHtML
- http://map.mobile.hcbezg.cn/Article/details/58746.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9581.sHtML
- http://map.mobile.hcbezg.cn/Article/details/2257504.sHtML
- http://map.mobile.hcbezg.cn/Article/details/9157269.sHtML
- http://map.mobile.hcbezg.cn/Article/details/1824.sHtML

## 项目结构

```
weblink-navigator/
├── app/
│   ├── __init__.py                     # 应用工厂与核心配置
│   ├── models.py                       # SQLAlchemy 数据模型（Batch, Link, CheckRecord）
│   ├── cli.py                          # Click 命令行入口（导入、导出、巡检、清理）
│   ├── routes/                         # Flask 路由模块
│   │   ├── index.py                    # 首页与批次概览
│   │   ├── links.py                    # 链接列表与筛选接口
│   │   └── status.py                   # 状态检查触发与结果展示
│   └── utils/
│       ├── fetcher.py                  # 基于 requests 的链接探测封装
│       └── parser.py                   # 原始链接解析与规范化辅助（仅用于展示，不修改原始值）
├── data/
│   ├── batch_189.txt                   # 当前批次原始链接列表（每行一个 URL）
│   └── batch_189_metadata.json         # 批次元数据（收录时间、来源说明、标签）
├── scripts/
│   ├── init_db.py                      # 初始化 SQLite 数据库表结构
│   ├── import_batch.py                 # 从文本文件导入批次链接
│   └── export_formats.py               # 导出为 JSON / CSV / 纯文本
├── tests/
│   ├── test_models.py                  # 数据模型单元测试
│   ├── test_fetcher.py                 # 链接探测功能测试
│   └── test_cli.py                     # 命令行接口集成测试
├── docs/                               # 完整文档目录（见文档导航章节）
├── requirements.txt                    # 生产环境依赖列表
├── requirements-dev.txt                # 开发环境额外依赖
├── .env.example                        # 环境变量配置模板
├── .gitignore
└── README.md                           # 本文件
```

## 贡献指南

我们欢迎并感谢任何形式的贡献。请遵循以下流程以确保代码质量和项目一致性。

1. 阅读项目文档与代码风格指南  
   在提交代码前，请先阅读 `docs/dev_guide.md` 了解数据模型设计、API 规范及代码风格要求（PEP 8 与 Google Python Style Guide 子集）。所有新增功能需附带对应的单元测试。

2. 提交 Issue 说明变更意图  
   对于新功能或较大规模的修改，请先在 GitHub Issues 中创建一个议题，描述您要解决的问题或要添加的功能，等待维护者确认后再进行开发，以避免重复工作或方向偏离。

3. 创建功能分支并编写代码  
   从 `main` 分支创建新的功能分支，命名格式为 `feature/简述` 或 `fix/简述`。编写代码时请确保所有现有测试通过，并为新增逻辑补充测试用例。

4. 运行完整测试套件  
   在提交 Pull Request 前，请在本地执行 `pytest tests/` 确保所有测试通过，同时使用 `flake8` 和 `pylint` 进行静态检查，消除警告与错误。

5. 发起 Pull Request 并等待 Code Review  
   将分支推送至远程仓库后，发起 Pull Request 并填写标准 PR 模板（包含变更摘要、测试结果及影响范围）。至少需要一位维护者 Approve 后方可合并。

## 常见问题

**Q：为什么我导入的链接在列表中显示时，协议或域名与原始输入不一致？**  
A：本项目严格遵循“原始数据透明呈现”原则，所有链接在数据库与展示层均以用户输入的原始字符串形式存储和渲染。如果您看到不一致，请检查导入时使用的源文件内容是否被外部编辑器自动修正（如某些编辑器会自动将 http 改为 https）。建议使用纯文本编辑器（如 VSCode 的 Plain Text 模式）编辑源文件。

**Q：链接状态检查显示超时或失败，但我在浏览器中能正常打开，是什么原因？**  
A：状态检查模块默认使用 requests 库的 HEAD 方法，并设置 5 秒超时。部分服务器可能对 HEAD 请求响应较慢或不支持，导致超时。您可以通过修改 `.env` 文件中的 `FETCH_TIMEOUT` 和 `FETCH_METHOD` 参数（可切换为 GET）来调整探测策略。另外，某些网站可能会对非浏览器 User-Agent 进行限制，请在配置中更新 `USER_AGENT` 字段。

**Q：批次导入时提示重复链接，是否会影响已有数据？**  
A：导入脚本默认对同一批次内的链接进行去重，并跳过与历史批次完全相同的 URL 字符串（大小写敏感）。跳过操作不会修改或删除已存在的链接记录，您可以在导入日志中查看被跳过的条目。如需强制更新已有记录的元数据，请使用 `--force-update` 参数。

## 许可证

MIT License

Copyright (c) 2026 WebLink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
