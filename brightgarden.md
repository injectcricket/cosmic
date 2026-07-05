# WebLink Archive Registry

WebLink Archive Registry 是一个面向技术文献、移动端网页快照与历史内容聚合的轻量级资源索引系统。该项目定位于为开发者、技术研究员及内容归档工作者提供一套结构清晰、可快速检索的外部链接管理方案，特别适用于处理大批量、多批次、来源固定的 URL 数据集。项目本身不存储页面内容，而是通过建立索引映射关系，将原始链接按批次、分类与元数据进行组织，从而降低人工整理成本，提升资源复用效率。目标用户包括需要维护外部参考链接库的文档工程师、进行移动端页面结构分析的安全研究员，以及需要批量导入历史文章链接进行二次开发的技术团队。

本项目以第 96/200 批资源作为初始数据输入，共计包含 250 条源自 fuvxie.cn 移动端域名的文章详情页链接。所有链接均保持原始协议与大小写格式，确保后续采集或跳转行为与源站预期完全一致。系统提供基于文章 ID 的快速过滤、批次状态标记以及链接可用性预检功能，可作为大型外链治理平台的前置处理模块独立运行。

## 功能概览

**批次化导入机制**：支持按批次编号（如 96/200）批量导入 URL 列表，自动解析文章 ID 并生成内部索引记录，同时保留原始 URL 的协议、域名、路径及文件扩展名大小写信息。

**去重与冲突检测**：对导入的链接进行基于完整 URL 的严格去重校验，并检测同一文章 ID 是否在历史批次中已存在，避免重复索引。

**元数据扩展字段**：每条记录预留 tags、status、note 等扩展字段，允许用户自定义标注链接所属技术领域、访问状态（有效/失效）或备注说明。

**多维度检索过滤**：支持按文章 ID、URL 关键词、批次号、导入时间范围进行组合过滤查询，结果支持按字段排序输出。

**状态快照导出**：将当前批次或全量索引导出为 CSV 或 JSON Lines 格式，便于下游数据管道或静态站点生成器消费。

**链接可用性预检**：提供异步 HEAD 请求检测功能，批量检查链接是否返回 2xx/3xx 状态码，并记录响应时间与重定向链，辅助清理失效资源。

**增量更新支持**：允许在同一批次下追加新链接，或对已存在记录的元数据进行补全更新，无需全量重建索引。

## 应用场景

**技术博客外链整理**：技术团队在撰写周报或技术汇总文档时，可将散落在聊天记录或临时笔记中的参考链接统一导入本系统，按批次归档并添加分类标签，后续引用时可直接检索获取原始 URL，避免重复搜索。

**移动端页面结构样本采集**：安全研究人员或前端性能分析团队可利用本系统批量管理用于测试的移动端页面样本链接，结合自动化脚本定期检测页面可访问性变化，及时发现内容下架或域名迁移情况。

**历史内容回溯与引用溯源**：内容运营人员在处理历史文章迁移或版权复核时，可通过本系统按文章 ID 或 URL 关键词快速定位特定链接，并查看其所属批次及导入时间，方便与原始数据源进行对照验证。

## 快速开始

以下步骤指导您在本地环境快速启动 WebLink Archive Registry 服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-archive/registry.git
cd registry

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建表结构
python scripts/init_db.py

# 导入第 96 批次示例数据（包含 250 条链接）
python scripts/import_batch.py --batch 96 --file data/batch_96.links

# 启动本地开发服务器
python app.py runserver --port 8080
```

访问 http://localhost:8080 即可进入检索界面，默认展示最近导入的批次概览。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS 版本 |
| SQLite | 3.31.0 及以上 | 内置轻量级数据库，用于存储索引记录与元数据 |
| requests | 2.28.0 及以上 | 用于链接可用性预检模块的 HTTP 请求发送 |
| click | 8.1.0 及以上 | 命令行交互框架，支撑导入/导出/检测等子命令 |
| pytest | 7.0.0 及以上 | 单元测试框架，可选安装用于运行测试套件 |
| flask | 2.2.0 及以上 | Web 检索界面的后端服务框架 |
| python-dotenv | 1.0.0 及以上 | 环境变量管理，用于配置数据库路径与监听地址 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何导入新批次、如何检索链接、如何导出结果、如何配置检测参数 |
| 开发指南 | docs/development.md | 项目模块划分、数据库 ER 图、新增字段或检索条件的扩展方法 |
| API 参考 | docs/api_reference.md | RESTful 接口的请求/响应格式说明，包含批量导入、查询、状态更新等端点 |
| 运维手册 | docs/operations.md | 生产环境部署建议、数据库备份策略、日志轮转配置及性能调优参数 |

## 资源列表

- http://wap.mobile.fuvxie.cn/Article/details/28968.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5411.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5928.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/70700.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/157860.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1495005.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1256.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/590574.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/15545.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9038.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/08678.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6776.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4070.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4720488.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/28108.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/91641.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6405.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0029.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5843.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/41271.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3892.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/075185.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/064700.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/471953.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2125.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9671544.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/163931.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/928440.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9854.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9434.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/01580.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6416.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/98515.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9843327.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/16500.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6838.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2169221.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/85030.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2767828.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8662.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3089.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/68012.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/19029.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/448546.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2153.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/63494.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1565.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8443.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/04079.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3318305.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/06310.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/804254.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7327634.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/92475.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/108359.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/735200.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/023623.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/892848.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/924627.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8244.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/241942.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3672881.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/390286.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0967.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/91373.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/63620.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/04339.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/012448.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5985.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3340423.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9565.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4045164.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/88203.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7439.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3870445.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1746141.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/176152.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/71008.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2530.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4215.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/96359.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3731783.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/685897.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/61658.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/25968.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3553003.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/514242.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2905.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3630950.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7866.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8444882.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/529223.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/465524.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4719.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/963914.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2031390.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6634.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/049006.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9475.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/054912.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2430.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/075131.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/377341.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/464216.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/942628.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3049165.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8880.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/890212.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/15732.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1943434.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1644.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/477820.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0842.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4034.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6406.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9640.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/306768.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/972107.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/35158.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/30296.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4615.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1648.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/556031.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7776299.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9044873.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/640214.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/70692.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/84112.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/85760.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/57593.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/90903.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/541674.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8284.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3053.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8801.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/077151.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/57221.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1309.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8375141.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/17480.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6957640.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4900083.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2672.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9221816.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6292.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/40728.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9012439.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/579210.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6560541.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/34978.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2483.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/98266.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2477.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3437.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/78387.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/51080.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/07386.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3918.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7285.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1892.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5502737.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/07037.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1660736.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/614160.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/40313.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7922.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2747.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/27647.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1306.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/36006.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/56501.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/794614.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7169.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9324989.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3313.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7204998.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/840902.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4147664.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/226504.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5304537.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2615.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/160877.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/85973.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8945049.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0057.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/279395.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/44189.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/63144.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6351103.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0982.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/93834.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/716423.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2682.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/494293.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0168.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/687160.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7851257.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6424.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4071560.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/53298.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2884192.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9658638.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/43972.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9930.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9549370.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8141717.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/392133.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/82304.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4865.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/743781.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6194117.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2828.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/27954.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1632581.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/899834.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/87027.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/809135.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/90943.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/726304.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6009101.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/09421.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/887652.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/71187.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/468109.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2773.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6904596.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5759.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6757234.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/28460.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7739.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/23352.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7585.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/59209.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0082623.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/597828.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1293.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/04835.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7867528.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4509.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/40757.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/270766.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/73270.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/959377.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3175125.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/780433.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1097253.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4951.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2658267.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/31825.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/936751.sHtML

## 项目结构

```
registry/
├── app.py                           # Flask 应用主入口，注册路由与启动服务
├── requirements.txt                 # Python 依赖清单，锁定主要库版本
├── .env.example                     # 环境变量配置模板（数据库路径、日志级别）
├── data/                            # 数据目录
│   ├── batch_96.links               # 第 96 批次原始链接列表（每行一个 URL）
│   └── batch_97.links.example       # 后续批次的示例模板文件
├── scripts/                         # 命令行工具脚本
│   ├── init_db.py                   # 初始化 SQLite 数据库及索引表
│   ├── import_batch.py              # 导入指定批次的链接并去重
│   ├── export_batch.py              # 将指定批次导出为 CSV/JSONL
│   └── check_availability.py        # 异步检测链接可用性并输出报告
├── src/                             # 核心源码包
│   ├── __init__.py
│   ├── models.py                    # 数据模型定义（Batch, LinkRecord）
│   ├── database.py                  # 数据库连接管理与 CRUD 操作
│   ├── parser.py                    # URL 解析与文章 ID 提取逻辑
│   ├── checker.py                   # 链接可用性检测（并发请求、超时控制）
│   └── exporter.py                  # 导出格式转换（CSV, JSON Lines）
├── tests/                           # 单元测试与集成测试
│   ├── test_parser.py               # 测试 URL 解析与 ID 提取准确性
│   ├── test_checker.py              # 模拟 HTTP 响应测试检测模块
│   └── test_models.py               # 数据模型增删改查的单元测试
├── docs/                            # 文档目录（用户手册、API 参考等）
│   ├── user_guide.md
│   ├── development.md
│   ├── api_reference.md
│   └── operations.md
├── templates/                       # Flask 前端模板
│   ├── index.html                   # 检索概览页面
│   └── batch_detail.html            # 单批次链接详情与筛选视图
└── static/                          # 静态资源（CSS 样式、前端 JavaScript）
    └── style.css
```

## 贡献指南

1. 在 GitHub 仓库的 Issue 区域提交您希望改进的功能或发现的缺陷，等待维护者确认或分配标签。对于新功能建议，请附带使用场景说明。

2. Fork 项目至个人账户，基于 main 分支创建功能分支（命名格式为 feature/简短描述 或 fix/缺陷编号），确保分支命名清晰反映变更内容。

3. 编写代码或文档变更时，请遵循项目已有的 Python 代码风格（PEP8）与注释规范。新增数据库字段或 API 端点时，需同步更新对应单元测试用例和 docs 目录下的相关文档。

4. 提交前运行完整测试套件（pytest tests/），确保所有测试用例通过且无新增警告。若涉及链接检测逻辑变更，请使用 data/ 下的示例文件进行本地验证。

5. 发起 Pull Request 到 main 分支，并在描述中引用关联的 Issue 编号，简要说明变更实现方式与测试覆盖情况。维护者将在 3 个工作日内进行 Review。

## 常见问题

**Q：导入批次时提示文章 ID 重复，但确实需要再次收录同一链接，应该如何处理？**

A：系统默认拒绝完全相同的 URL 重复导入以防止索引膨胀。如果您确实需要重新收录（例如源站内容更新），可以使用 `--force` 参数强制覆盖已存在记录的时间戳与状态，或通过 Web 界面对特定记录执行“重新导入”操作，该操作会更新 updated_at 字段并重置可用性检测标记。

**Q：链接可用性检测返回大量超时或 5xx 错误，是否意味着这些链接全部失效？**

A：不一定。检测模块默认超时时间为 5 秒，对于响应较慢的移动端页面或临时过载的源站，可能出现假阳性。建议调整 `src/checker.py` 中的 `REQUEST_TIMEOUT` 配置为 10 秒或 15 秒，并开启 `--retry` 参数（重试 1 次）后重新检测。同时可结合 `--user-agent` 参数模拟不同移动端设备标识，避免被源站防火墙拦截。

**Q：如何将本系统与我的静态博客生成器（如 Hugo 或 Jekyll）结合使用？**

A：您可以使用导出功能将特定批次或全量索引导出为 JSON Lines 格式，再通过自定义脚本或 Makefile 将 JSON 数据转换为博客生成器可识别的数据文件（例如 Hugo 的 data 目录下的 yaml 文件）。项目文档中的 `docs/operations.md` 提供了与 Hugo 集成的完整示例，包括数据转换模板和自动化构建流程配置。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
