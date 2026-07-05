# LinkVault Resource Aggregator

LinkVault is a curated, machine-readable resource index designed for developers, data researchers, and content archivers who need to systematically catalog and reference distributed web articles. The project maintains a high-fidelity URL registry with version-controlled metadata, enabling automated retrieval, link-rot detection, and bulk processing of externally hosted content. Unlike general-purpose bookmark managers, LinkVault treats each entry as a first-class data record with persistent identifiers, checksum validation, and origin timestamps.

Target users include infrastructure engineers building custom crawlers, academic researchers conducting longitudinal web studies, and system administrators who require reproducible resource manifests. The project does not host or proxy content; it provides a deterministic, audited listing layer that external toolchains can consume via plain-text extracts, JSON exports, or SQLite snapshots.

## 功能概览

- **Deterministic URL Registry** – Each resource is stored with its original protocol, host, path, and file extension exactly as provided, without normalization or autocorrection.

- **Batch Import Pipeline** – Ingest up to 250 entries per batch with automatic deduplication, format validation, and collision detection against existing indices.

- **Versioned Snapshot Artifacts** – Every batch commit generates a timestamped manifest file (JSON Lines and CSV) suitable for diff-based change tracking.

- **Link-Rot Health Checks** – Scheduled HEAD requests verify resource availability; stale entries are flagged in the status dashboard without modification to the original record.

- **Tag-Free Categorization** – Resources are organized by batch number and entry sequence rather than subjective topic tags, preserving the integrity of the original submission order.

- **Export Adapters** – Native support for plain-text URL lists, Markdown tables, HTML `<ul>` fragments, and Wget-compatible input files.

- **Integrity Hooks** – SHA-256 checksums are computed for each URL string to enable cross-system consistency verification.

- **Query Filtering** – Filter by batch ID, entry ID range, domain pattern, or file extension using regular expression predicates.

## 应用场景

- **Automated Content Mirroring** – System administrators can feed the resource list into recursive wget or httrack sessions to create local mirrors of distributed article collections, using the batch number as a session label.

- **Academic Citation Auditing** – Researchers tracking the longevity of cited web sources import the manifest into a monitoring pipeline that periodically rechecks each URL and records HTTP status transitions over time.

- **Data Pipeline Seeding** – Data engineering teams use the exported JSON array as the seed list for distributed scraping jobs, with each entry mapped to a unique job ID derived from the entry sequence.

- **Manual Reference Browsing** – Developers and technical writers consult the resource list as a supplementary bibliography when cross-referencing implementation details across multiple external articles.

- **Regression Test Suites** – QA engineers incorporate the URL list into integration tests that validate external content availability before deployment, failing the build if a configurable threshold of links is unreachable.

## 快速开始

Clone the repository, install the Python dependencies, and run the import command with the batch file.

```bash
git clone https://github.com/linkvault/linkvault-core.git
cd linkvault-core
pip install -r requirements.txt
python linkvault.py import --batch 152 --file resources/batch_152.txt
```

To validate the imported entries and generate the Markdown report:

```bash
python linkvault.py validate --batch 152
python linkvault.py export --batch 152 --format markdown --output README.md
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 或更高 | 核心运行时，用于 CLI 工具和调度脚本 |
| pip | 22.0 或更高 | 依赖项安装管理器 |
| requests | 2.31.0 | HTTP 客户端，用于健康检查和状态探测 |
| pydantic | 2.5.0 | 数据模型校验，确保 URL 格式严格匹配 |
| click | 8.1.7 | CLI 命令解析和参数路由 |
| pytest | 8.0.0 | 单元测试和集成测试框架（仅开发依赖） |
| sqlite3 | 系统内置 | 本地缓存和状态存储引擎 |
| git | 2.30.0 | 版本控制和提交钩子（仅开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何安装、配置、导入批次、导出清单以及执行健康检查 |
| API 参考 | docs/api-reference.md | CLI 命令的完整参数列表、环境变量和退出代码含义 |
| 批处理规范 | docs/batch-spec.md | 批次文件的格式要求、编码约定、校验规则和错误处理策略 |
| 运维指南 | docs/operations.md | 定期清理、日志轮转、性能调优和故障恢复流程 |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/details/29962.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2488349.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9705.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9612.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/59858.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/251775.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/14311.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6521.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6006741.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1267.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/56826.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/223250.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5558.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/473229.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0158.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6974114.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1230106.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2167540.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/915298.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4456.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3903425.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9854.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4696250.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/48513.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8166485.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/67642.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/609987.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/62731.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0435.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9312.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8338.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/96270.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0234186.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6134.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/882559.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6907235.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/534232.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/15088.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6939758.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/28556.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/16057.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7716644.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/472967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/45906.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4384.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/30682.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/222110.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7853889.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9561.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9120.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1416327.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0669080.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5034532.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0078.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/01580.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1814168.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/42818.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/04504.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/411658.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/68269.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/706273.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/471290.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/629037.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/244867.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/59445.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4773.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/33374.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/730481.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/12280.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/755501.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6446685.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/746502.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/23360.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3517278.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/231925.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8176480.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4434.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/28160.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/19820.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5730.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3312955.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2968.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/42064.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2457208.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/754859.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/669891.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8828.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7122.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/26664.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1892276.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8162471.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3768352.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2106.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4141.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/47438.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1339.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/62853.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/172492.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3226.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1211049.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/35267.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5808.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2204.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4684626.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/70806.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3553684.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4061.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4345093.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7108883.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2188871.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0930.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3360.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8469.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/34102.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9650104.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/683095.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/396425.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2314.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8672780.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2296214.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0666984.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6215393.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7573.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4483677.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/284878.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/244894.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9315.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/97607.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/232641.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/77898.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0240.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/864729.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/975134.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4496467.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9215939.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3806537.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2529.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1385.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9220740.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1143848.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6739826.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5846.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0161755.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/322967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5966564.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5475.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2007.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/69814.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1916.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8237844.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2017.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/39369.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1641580.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3086197.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2025.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/665447.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2562865.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/02553.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4864.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/636864.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2306421.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0591186.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/245721.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4178.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8386.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4871.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/342359.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8848.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1286687.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7154.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/303733.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/582307.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5233642.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3399598.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/85824.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/43081.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/666520.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/33800.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5992239.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9027.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/130351.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/32420.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1246173.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7377393.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2023250.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7056.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4862527.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/53157.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/224403.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8607.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1780781.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4865.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/276788.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/91518.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/54292.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0009.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8416178.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/124165.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/30152.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1221399.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6761.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/39058.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/65435.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/16417.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/44620.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/913614.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/887421.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/057433.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3747727.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6562379.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0943066.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2574580.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0897.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3617466.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8223.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8624420.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9029.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/393462.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/65701.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/154324.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/07914.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/22322.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5968473.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/57438.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/702464.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6531.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/78889.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/16545.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7768852.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9093.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/480212.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/35553.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/69965.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/86507.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5229.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7303.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0912537.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/99673.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3621890.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/50012.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2005500.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/288594.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/84504.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5316.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2778.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/04343.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7772.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9299.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0891.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2735.sHtML

## 项目结构

```
linkvault-core/
├── src/
│   ├── linkvault/
│   │   ├── __init__.py          # 包入口，导出核心类
│   │   ├── cli.py               # Click 命令定义：import, validate, export, health
│   │   ├── models/
│   │   │   ├── entry.py         # ResourceEntry Pydantic 模型，含 URL 校验器
│   │   │   └── batch.py         # BatchManifest 模型，含批次元数据
│   │   ├── storage/
│   │   │   ├── sqlite_store.py  # SQLite 持久化实现，含迁移脚本
│   │   │   └── file_store.py    # JSON/CSV 文件读写适配器
│   │   ├── checks/
│   │   │   ├── http_head.py     # 并发 HEAD 请求调度器
│   │   │   └── reporter.py      # 健康报告生成器
│   │   └── utils/
│   │       ├── hasher.py        # SHA-256 字符串哈希工具
│   │       └── normalizer.py    # 仅用于显示，不修改原始 URL
├── tests/
│   ├── test_models.py           # 单元测试：数据模型校验
│   ├── test_cli.py              # 集成测试：命令端到端执行
│   └── fixtures/
│       └── batch_152.txt        # 本批次原始输入文件
├── docs/                         # 完整文档（见文档导航章节）
├── resources/                    # 归档的历史批次清单
├── requirements.txt             # 生产依赖锁定文件
├── setup.py                      # setuptools 打包配置
└── README.md                    # 本文件
```

## 贡献指南

1.  **Fork 仓库并创建功能分支** – 从主分支 checkout 一个新的分支，分支命名遵循 `feature/` 或 `fix/` 前缀，例如 `feature/add-json-export-stream`。

2.  **运行本地测试套件** – 在执行任何修改后，使用 `pytest tests/` 运行全部单元测试和集成测试，确保现有功能未发生回归。新增功能必须附带对应的测试用例。

3.  **遵循提交信息规范** – 提交信息使用约定式提交格式（Conventional Commits），例如 `feat: add streaming JSON export` 或 `fix: handle empty batch gracefully`。提交信息正文需说明修改动机和影响范围。

4.  **更新相关文档** – 如果修改了 CLI 参数、配置项或数据模型，必须同步更新 `docs/` 目录下对应的用户手册或 API 参考文档。文档变更应包含在同一个 Pull Request 中。

5.  **提交 Pull Request 并标记审阅者** – 推送到远程分支后，在 GitHub 上发起 Pull Request，填写变更摘要模板，并至少邀请两名维护者进行代码审阅。通过 CI 检查并获得批准后方可合并。

## 常见问题

**问：为什么资源列表中的 URL 不统一转为 HTTPS 或去除 "www" 前缀？**

答：LinkVault 的核心原则是忠实记录用户提供的原始资源定位符。任何自动化的协议升级、子域名规范化或路径重写都会引入不可预测的偏差，破坏引用完整性。用户应自行在消费端根据策略决定是否进行协议重定向或域名归一化。

**问：如何处理资源列表中的重复 URL？**

答：导入管道会在写入持久化存储前对完整 URL 字符串执行大小写敏感的精确去重。如果检测到重复条目，系统会记录一条警告日志，但仅保留首次出现的记录。重复项不会覆盖原有记录，也不会计入批次条目总数。

**问：健康检查发现某个 URL 返回 404 或超时，LinkVault 会自动删除该条目吗？**

答：不会。LinkVault 的设计哲学是保持注册表的历史不变性。健康检查只更新条目的 `last_status` 和 `last_checked_at` 字段，并在报告中标记为 "unreachable"。是否移除或替换失效链接由下游消费者根据自身策略决定，项目本身不执行自动删除操作。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
