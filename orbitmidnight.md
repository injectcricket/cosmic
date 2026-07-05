# Mobile Article Aggregator Service (MAAS)

MAAS 是一个面向移动端内容聚合与结构化访问的开源中间件服务，专门用于对特定来源的移动端文章资源进行统一化采集、索引、缓存与检索。本项目不生产内容，而是为开发者、数据分析师和内容运营人员提供一套标准化的外链管理与文章元数据抽取工具，便于二次开发、数据挖掘和前端展示。目标用户包括个人开发者、爬虫工程师、静态站点生成器使用者以及对移动端内容结构有批量化处理需求的团队。

## 功能概览

**批量文章元数据抓取**：支持对给定 URL 列表进行并发请求，自动解析 HTML 标题、发布时间、正文摘要和分类标签。

**结构化输出适配**：内置 JSON、YAML 和 CSV 三种输出格式，可直接对接 Gatsby、Hugo 或 Eleventy 等静态站点生成器。

**请求频率控制与重试机制**：提供可配置的请求间隔、最大并发数和指数退避重试策略，减少对目标服务器的压力。

**内容去重与变更检测**：基于文章 ID 和内容哈希实现增量更新，仅拉取新增或变更的文档，降低冗余请求。

**自定义字段映射规则**：通过 YAML 配置文件定义 CSS 选择器与输出字段的映射关系，适配不同来源的页面结构变动。

**本地缓存与离线预览**：将已拉取的文章数据存储于 SQLite 数据库中，支持离线状态下的查询和导出操作。

## 应用场景

**个人知识库构建**：开发者可将指定来源的文章链接导入系统，定期自动拉取并生成 Markdown 格式的本地文档库，配合 Obsidian 或 Logseq 进行知识管理。

**移动端内容镜像站建设**：运维人员利用 MAAS 定时抓取文章数据，结合静态站点生成器构建符合自身风格的移动端内容展示站点，用于团队内部分享或存档。

**数据分析与趋势研究**：数据分析师导出 CSV 格式的文章元数据（发布时间、ID 分布、标题关键词），进行时间序列分析或内容热度评估，了解特定站点的更新规律。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/maas-dev/maas-core.git
cd maas-core

# 安装项目依赖（使用 pip 和虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行示例抓取任务（使用项目自带的测试 URL 列表）
python maas_cli.py --input sample_urls.txt --output data/ --format json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 或更高 | 核心运行环境，推荐 3.10+ |
| requests | 2.28.0+ | HTTP 请求库，用于发送抓取请求 |
| beautifulsoup4 | 4.11.0+ | HTML 解析库，用于提取文章元数据 |
| lxml | 4.9.0+ | 高性能 XML/HTML 解析器后端 |
| sqlite3 | 3.35.0+ | 本地缓存数据库，Python 内置模块 |
| pyyaml | 6.0+ | 配置文件解析，用于自定义字段映射 |
| pytest | 7.2.0+ | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide/ | 如何配置抓取规则、调整并发参数、导出数据？ |
| 开发指南 | docs/development/ | 项目架构、插件系统设计、如何扩展新的解析器？ |
| 运维参考 | docs/operations/ | 部署建议、日志配置、缓存清理策略和性能调优？ |
| API 参考 | docs/api/ | 命令行参数详解、配置文件完整字段说明和返回值结构？ |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/details/7101613.sHtML
- http://m.mobile.hcbezg.cn/Article/details/32043.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9997681.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8568.sHtML
- http://m.mobile.hcbezg.cn/Article/details/30482.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1208.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2756.sHtML
- http://m.mobile.hcbezg.cn/Article/details/508798.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/560857.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0683168.sHtML
- http://m.mobile.hcbezg.cn/Article/details/756453.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5669919.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0013125.sHtML
- http://m.mobile.hcbezg.cn/Article/details/051152.sHtML
- http://m.mobile.hcbezg.cn/Article/details/543740.sHtML
- http://m.mobile.hcbezg.cn/Article/details/65088.sHtML
- http://m.mobile.hcbezg.cn/Article/details/874472.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0218.sHtML
- http://m.mobile.hcbezg.cn/Article/details/24288.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2839.sHtML
- http://m.mobile.hcbezg.cn/Article/details/041765.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9804760.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8074770.sHtML
- http://m.mobile.hcbezg.cn/Article/details/165093.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7862.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5079800.sHtML
- http://m.mobile.hcbezg.cn/Article/details/947962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5531857.sHtML
- http://m.mobile.hcbezg.cn/Article/details/555117.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4384.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6393068.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6603.sHtML
- http://m.mobile.hcbezg.cn/Article/details/54670.sHtML
- http://m.mobile.hcbezg.cn/Article/details/36931.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1063273.sHtML
- http://m.mobile.hcbezg.cn/Article/details/80135.sHtML
- http://m.mobile.hcbezg.cn/Article/details/23658.sHtML
- http://m.mobile.hcbezg.cn/Article/details/43764.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5455.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5898.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7584406.sHtML
- http://m.mobile.hcbezg.cn/Article/details/417533.sHtML
- http://m.mobile.hcbezg.cn/Article/details/087224.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5151.sHtML
- http://m.mobile.hcbezg.cn/Article/details/866408.sHtML
- http://m.mobile.hcbezg.cn/Article/details/894603.sHtML
- http://m.mobile.hcbezg.cn/Article/details/75823.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6528165.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5250.sHtML
- http://m.mobile.hcbezg.cn/Article/details/67296.sHtML
- http://m.mobile.hcbezg.cn/Article/details/42508.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9659.sHtML
- http://m.mobile.hcbezg.cn/Article/details/51686.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1160.sHtML
- http://m.mobile.hcbezg.cn/Article/details/016319.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8469.sHtML
- http://m.mobile.hcbezg.cn/Article/details/46597.sHtML
- http://m.mobile.hcbezg.cn/Article/details/826199.sHtML
- http://m.mobile.hcbezg.cn/Article/details/51249.sHtML
- http://m.mobile.hcbezg.cn/Article/details/63332.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9591744.sHtML
- http://m.mobile.hcbezg.cn/Article/details/48196.sHtML
- http://m.mobile.hcbezg.cn/Article/details/233396.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1184220.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9446.sHtML
- http://m.mobile.hcbezg.cn/Article/details/45470.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1559.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0252023.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6760936.sHtML
- http://m.mobile.hcbezg.cn/Article/details/182925.sHtML
- http://m.mobile.hcbezg.cn/Article/details/34225.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2866.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4292355.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3530.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6715.sHtML
- http://m.mobile.hcbezg.cn/Article/details/75437.sHtML
- http://m.mobile.hcbezg.cn/Article/details/78541.sHtML
- http://m.mobile.hcbezg.cn/Article/details/40374.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1620222.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39540.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7269574.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6284111.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9365608.sHtML
- http://m.mobile.hcbezg.cn/Article/details/18692.sHtML
- http://m.mobile.hcbezg.cn/Article/details/540577.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8060.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6676962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7108.sHtML
- http://m.mobile.hcbezg.cn/Article/details/32691.sHtML
- http://m.mobile.hcbezg.cn/Article/details/06014.sHtML
- http://m.mobile.hcbezg.cn/Article/details/51616.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5911.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9858.sHtML
- http://m.mobile.hcbezg.cn/Article/details/414492.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4754.sHtML
- http://m.mobile.hcbezg.cn/Article/details/518142.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7376584.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1840160.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0398.sHtML
- http://m.mobile.hcbezg.cn/Article/details/46830.sHtML
- http://m.mobile.hcbezg.cn/Article/details/146589.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5172.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7685785.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7211892.sHtML
- http://m.mobile.hcbezg.cn/Article/details/47955.sHtML
- http://m.mobile.hcbezg.cn/Article/details/36771.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5430579.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3709.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1648.sHtML
- http://m.mobile.hcbezg.cn/Article/details/35651.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1486.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6122685.sHtML
- http://m.mobile.hcbezg.cn/Article/details/214417.sHtML
- http://m.mobile.hcbezg.cn/Article/details/31143.sHtML
- http://m.mobile.hcbezg.cn/Article/details/29569.sHtML
- http://m.mobile.hcbezg.cn/Article/details/94927.sHtML
- http://m.mobile.hcbezg.cn/Article/details/60385.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7112384.sHtML
- http://m.mobile.hcbezg.cn/Article/details/87316.sHtML
- http://m.mobile.hcbezg.cn/Article/details/43734.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0397878.sHtML
- http://m.mobile.hcbezg.cn/Article/details/807243.sHtML
- http://m.mobile.hcbezg.cn/Article/details/759314.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2356.sHtML
- http://m.mobile.hcbezg.cn/Article/details/240027.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8080.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2164.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1189270.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7305.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3597589.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2511450.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0422588.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5167125.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7810.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7336847.sHtML
- http://m.mobile.hcbezg.cn/Article/details/521106.sHtML
- http://m.mobile.hcbezg.cn/Article/details/686792.sHtML
- http://m.mobile.hcbezg.cn/Article/details/40902.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3503.sHtML
- http://m.mobile.hcbezg.cn/Article/details/63227.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3539.sHtML
- http://m.mobile.hcbezg.cn/Article/details/79741.sHtML
- http://m.mobile.hcbezg.cn/Article/details/292951.sHtML
- http://m.mobile.hcbezg.cn/Article/details/04364.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3875.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6281556.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5931884.sHtML
- http://m.mobile.hcbezg.cn/Article/details/821164.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3141852.sHtML
- http://m.mobile.hcbezg.cn/Article/details/010652.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9693.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2460231.sHtML
- http://m.mobile.hcbezg.cn/Article/details/79951.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39673.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5489.sHtML
- http://m.mobile.hcbezg.cn/Article/details/374771.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6508442.sHtML
- http://m.mobile.hcbezg.cn/Article/details/698134.sHtML
- http://m.mobile.hcbezg.cn/Article/details/119822.sHtML
- http://m.mobile.hcbezg.cn/Article/details/272806.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0829.sHtML
- http://m.mobile.hcbezg.cn/Article/details/24413.sHtML
- http://m.mobile.hcbezg.cn/Article/details/65921.sHtML
- http://m.mobile.hcbezg.cn/Article/details/36218.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9711.sHtML
- http://m.mobile.hcbezg.cn/Article/details/032956.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8658.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2896.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6156267.sHtML
- http://m.mobile.hcbezg.cn/Article/details/77194.sHtML
- http://m.mobile.hcbezg.cn/Article/details/24153.sHtML
- http://m.mobile.hcbezg.cn/Article/details/79911.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3789.sHtML
- http://m.mobile.hcbezg.cn/Article/details/22067.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0757850.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7511788.sHtML
- http://m.mobile.hcbezg.cn/Article/details/85922.sHtML
- http://m.mobile.hcbezg.cn/Article/details/37165.sHtML
- http://m.mobile.hcbezg.cn/Article/details/575383.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7201.sHtML
- http://m.mobile.hcbezg.cn/Article/details/761971.sHtML
- http://m.mobile.hcbezg.cn/Article/details/500234.sHtML
- http://m.mobile.hcbezg.cn/Article/details/49178.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4596.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6912.sHtML
- http://m.mobile.hcbezg.cn/Article/details/21564.sHtML
- http://m.mobile.hcbezg.cn/Article/details/789815.sHtML
- http://m.mobile.hcbezg.cn/Article/details/034105.sHtML
- http://m.mobile.hcbezg.cn/Article/details/953301.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9508161.sHtML
- http://m.mobile.hcbezg.cn/Article/details/52528.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6549573.sHtML
- http://m.mobile.hcbezg.cn/Article/details/02347.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0047085.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39437.sHtML
- http://m.mobile.hcbezg.cn/Article/details/28292.sHtML
- http://m.mobile.hcbezg.cn/Article/details/664662.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9585.sHtML
- http://m.mobile.hcbezg.cn/Article/details/18554.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1556750.sHtML
- http://m.mobile.hcbezg.cn/Article/details/366906.sHtML
- http://m.mobile.hcbezg.cn/Article/details/09081.sHtML
- http://m.mobile.hcbezg.cn/Article/details/766670.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9318839.sHtML
- http://m.mobile.hcbezg.cn/Article/details/48388.sHtML
- http://m.mobile.hcbezg.cn/Article/details/641864.sHtML
- http://m.mobile.hcbezg.cn/Article/details/693967.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1020.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3207.sHtML
- http://m.mobile.hcbezg.cn/Article/details/97510.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5683057.sHtML
- http://m.mobile.hcbezg.cn/Article/details/336789.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6337088.sHtML
- http://m.mobile.hcbezg.cn/Article/details/735379.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3446.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9752.sHtML
- http://m.mobile.hcbezg.cn/Article/details/28678.sHtML
- http://m.mobile.hcbezg.cn/Article/details/435948.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4115.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1643.sHtML
- http://m.mobile.hcbezg.cn/Article/details/85691.sHtML
- http://m.mobile.hcbezg.cn/Article/details/897057.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0302775.sHtML
- http://m.mobile.hcbezg.cn/Article/details/73363.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1936.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2835.sHtML
- http://m.mobile.hcbezg.cn/Article/details/780501.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0232085.sHtML
- http://m.mobile.hcbezg.cn/Article/details/55131.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1454.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7001.sHtML
- http://m.mobile.hcbezg.cn/Article/details/58303.sHtML
- http://m.mobile.hcbezg.cn/Article/details/15008.sHtML
- http://m.mobile.hcbezg.cn/Article/details/68852.sHtML
- http://m.mobile.hcbezg.cn/Article/details/25950.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7306605.sHtML
- http://m.mobile.hcbezg.cn/Article/details/341219.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1800.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8543.sHtML
- http://m.mobile.hcbezg.cn/Article/details/12586.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3598.sHtML
- http://m.mobile.hcbezg.cn/Article/details/419007.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5445015.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6478850.sHtML
- http://m.mobile.hcbezg.cn/Article/details/25157.sHtML
- http://m.mobile.hcbezg.cn/Article/details/473702.sHtML
- http://m.mobile.hcbezg.cn/Article/details/580607.sHtML
- http://m.mobile.hcbezg.cn/Article/details/01168.sHtML

## 项目结构

```
maas-core/
├── maas_cli.py                # 命令行入口，解析参数并调度抓取流程
├── requirements.txt           # 生产环境依赖列表（固定版本）
├── config/
│   ├── default.yaml           # 默认抓取配置（并发数、超时、重试）
│   └── selector_maps/         # 字段映射规则目录
│       └── hcbezg.yaml        # 针对 hcbezg.cn 的选择器配置
├── maas/
│   ├── __init__.py
│   ├── fetcher.py             # 并发请求控制器，实现重试与限流
│   ├── parser.py              # HTML 解析引擎，基于 BeautifulSoup
│   ├── cache.py               # SQLite 缓存读写接口
│   ├── exporter.py            # JSON/CSV/YAML 导出模块
│   └── utils.py               # 日志、哈希计算、URL 规范化工具
├── tests/
│   ├── test_fetcher.py        # 请求模块单元测试
│   ├── test_parser.py         # 解析模块单元测试
│   └── fixtures/              # 测试用静态 HTML 样本
├── docs/                      # 完整文档，包含用户手册和 API 参考
│   ├── user-guide/
│   └── development/
├── scripts/                   # 运维辅助脚本
│   ├── clean_cache.py         # 清理过期缓存条目
│   └── batch_import.py        # 批量导入 URL 列表文件
└── .github/
    └── workflows/             # CI 流水线配置（测试与代码检查）
        └── test.yml
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 说明你希望修复的问题或新增的功能，等待维护者确认方向。

2. Fork 项目仓库并在本地开发环境中创建功能分支，分支命名格式为 `feature/简要描述` 或 `fix/问题编号`。

3. 编写代码时需同步更新对应的单元测试（位于 tests/ 目录），确保所有测试用例通过且覆盖率不低于 85%。

4. 更新文档目录中受影响的部分，至少包含配置变更说明或新增命令行参数的使用示例。

5. 提交 pull request 到主仓库的 develop 分支，并在描述中关联相关 issue 编号，等待代码审查和合并。

## 常见问题

**问：目标站点返回 403 或 429 状态码，如何解决？**

答：建议调整配置中的请求间隔（`request_interval` 参数）和并发数（`max_concurrent` 参数），启用 `random_user_agent` 选项并配置 `retry_backoff_factor` 为 2.0 以上。若持续被限制，可考虑使用代理池或降低抓取频率至每分钟不超过 30 次。

**问：抓取的文章标题和正文为空，是什么原因？**

答：通常是因为目标页面结构发生变化，导致预设的 CSS 选择器失效。请使用浏览器开发者工具检查目标文章的最新 DOM 结构，然后修改 `config/selector_maps/` 中对应的 YAML 映射文件，调整 `title_selector` 和 `content_selector` 字段的值。修改后可通过 `--dry-run` 参数进行测试验证。

**问：本地 SQLite 缓存文件体积过大，如何清理？**

答：可以运行项目自带的清理脚本 `scripts/clean_cache.py --days 30` 删除 30 天前的缓存记录。也可以手动执行 `VACUUM` 命令回收磁盘空间。如果缓存数据不再需要，直接删除 `maas_cache.db` 文件即可，下次抓取时会自动重建。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
