# WebLink Hub

WebLink Hub 是一个面向技术研究者、内容策展人和开发者的外链资产整理与导航工具。该项目将分散的优质文章、技术文档与外部资源统一归集为结构化数据，方便用户以可检索、可导出的方式维护自己的网络书签与引用库。不同于传统的社会化书签服务，WebLink Hub 强调本地优先、纯静态部署与无锁定的数据所有权，适合作为团队内部知识库或公开技术导航站的底层引擎。

本项目当前批次收录 250 个外部资源链接，覆盖移动端开发、后端架构、数据库调优、DevOps 实践以及开源社区动态等方向。WebLink Hub 本身不存储文章内容，仅提供链接元数据的索引与分类能力，所有原始资源仍由源站点独立维护。

## 功能概览

**多源链接导入**：支持从 CSV、JSON 以及浏览器书签导出文件批量导入链接，保留原始 URL、标题与收集时间戳。

**自动元数据补全**：对导入的 URL 自动发起 HEAD 请求，检测状态码、内容类型与最后修改时间，辅助判断资源有效性。

**分类标签系统**：允许用户为每个链接添加自定义标签，支持层级标签（如 `backend/database/mysql`）与布尔筛选。

**全文检索**：基于链接标题、描述与标签构建轻量级倒排索引，支持中文分词与模糊匹配。

**状态监控看板**：定时检测已收录链接的可访问性，以红黄绿状态灯标识正常、重定向与失效，并生成变更报告。

**数据导出与订阅**：支持将当前链接列表导出为 Markdown 表格、JSON 或 RSS 订阅源，便于嵌入其他文档系统或自动化流程。

**去重与合并**：检测重复 URL 与近似标题，提供交互式合并界面，减少冗余条目。

## 应用场景

技术团队内部知识库维护：团队可将项目文档、技术博客与第三方 API 文档链接统一录入 WebLink Hub，通过标签分类实现按模块（前端、网关、数据层）快速定位，取代零散的浏览器收藏夹。

开源项目 README 链接整理：开源维护者需要定期更新 README 中的“相关资源”章节，WebLink Hub 可生成格式化的 Markdown 链接列表，直接复制使用，避免手动排版错误。

个人技术阅读工作流：技术爱好者可使用本项目作为每日阅读看板，将待读文章暂存为“未读”状态，阅读后添加笔记标签，形成个人知识沉淀。

网站内容迁移与改版辅助：当网站需要重构或更换域名时，运维人员可导出全量外链清单，批量检查外部引用是否失效，提前规划重定向或替换策略。

合规审计与链接审查：法务或合规团队可定期导出所有外链，对照公司政策筛查可疑域名或过期协议（如 http 明文传输），生成审计日志。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash。

```bash
# 克隆主仓库
git clone https://github.com/weblink-hub/core.git
cd core

# 安装 Node.js 依赖（要求 Node.js 18+）
npm install

# 复制环境配置模板
cp .env.example .env

# 构建静态资源并启动开发服务器
npm run build
npm run start:dev
```

启动成功后，访问终端输出的本地地址（默认 http://127.0.0.1:3000）即可看到链接列表界面。首次运行将自动创建 SQLite 数据库文件 `data/links.db` 并导入种子数据。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，随 Node.js 一同安装 |
| SQLite3 | 3.35 以上 | 嵌入式数据库，开发环境无需额外安装 |
| Git | 2.30 以上 | 用于克隆仓库和版本控制 |
| curl / wget | 任意现代版本 | 用于健康检查脚本中的网络探测 |
| systemd (Linux) 或 launchd (macOS) | 可选 | 用于配置后台定时监控服务 |
| Python 3.9+ | 可选 | 仅当启用高级数据分析插件时需要 |
| Docker (含 Compose) | 20.10+ | 用于容器化生产部署 |
| Nginx 或 Caddy | 1.20+ | 推荐作为反向代理提供静态缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | `/docs/user-guide/` | 如何导入链接、设置标签、导出列表以及配置监控频率 |
| 开发指南 | `/docs/developer-guide/` | 如何二次开发插件、扩展元数据解析器或替换搜索引擎 |
| 运维手册 | `/docs/operations/` | 如何部署到生产环境、配置 systemd 服务、备份数据库与日志轮转 |
| API 参考 | `/docs/api/` | RESTful API 端点说明，包括分页、筛选、批量操作与状态码定义 |

## 资源列表

- http://www.mobile.fuvxie.cn/Article/details/913835.sHtML
- http://www.mobile.fuvxie.cn/Article/details/52176.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6070645.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5043327.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5858503.sHtML
- http://www.mobile.fuvxie.cn/Article/details/94603.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1478649.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1323.sHtML
- http://www.mobile.fuvxie.cn/Article/details/739214.sHtML
- http://www.mobile.fuvxie.cn/Article/details/59865.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6988803.sHtML
- http://www.mobile.fuvxie.cn/Article/details/325054.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0709.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4089.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7305591.sHtML
- http://www.mobile.fuvxie.cn/Article/details/09160.sHtML
- http://www.mobile.fuvxie.cn/Article/details/45608.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4967.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0309546.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7754.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2954.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3545377.sHtML
- http://www.mobile.fuvxie.cn/Article/details/987805.sHtML
- http://www.mobile.fuvxie.cn/Article/details/86196.sHtML
- http://www.mobile.fuvxie.cn/Article/details/07121.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3237271.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4490.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4715.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1230.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8956.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72192.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7534795.sHtML
- http://www.mobile.fuvxie.cn/Article/details/204483.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2633033.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1285347.sHtML
- http://www.mobile.fuvxie.cn/Article/details/723218.sHtML
- http://www.mobile.fuvxie.cn/Article/details/07737.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1723685.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2828478.sHtML
- http://www.mobile.fuvxie.cn/Article/details/341675.sHtML
- http://www.mobile.fuvxie.cn/Article/details/057379.sHtML
- http://www.mobile.fuvxie.cn/Article/details/23618.sHtML
- http://www.mobile.fuvxie.cn/Article/details/893259.sHtML
- http://www.mobile.fuvxie.cn/Article/details/05825.sHtML
- http://www.mobile.fuvxie.cn/Article/details/131430.sHtML
- http://www.mobile.fuvxie.cn/Article/details/048831.sHtML
- http://www.mobile.fuvxie.cn/Article/details/77623.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8966.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3595419.sHtML
- http://www.mobile.fuvxie.cn/Article/details/24081.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2831.sHtML
- http://www.mobile.fuvxie.cn/Article/details/614279.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9225.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9954.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6088636.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4403554.sHtML
- http://www.mobile.fuvxie.cn/Article/details/083545.sHtML
- http://www.mobile.fuvxie.cn/Article/details/147708.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72549.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0739.sHtML
- http://www.mobile.fuvxie.cn/Article/details/45923.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4347278.sHtML
- http://www.mobile.fuvxie.cn/Article/details/507951.sHtML
- http://www.mobile.fuvxie.cn/Article/details/87735.sHtML
- http://www.mobile.fuvxie.cn/Article/details/974104.sHtML
- http://www.mobile.fuvxie.cn/Article/details/014585.sHtML
- http://www.mobile.fuvxie.cn/Article/details/950424.sHtML
- http://www.mobile.fuvxie.cn/Article/details/99875.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2534.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2062524.sHtML
- http://www.mobile.fuvxie.cn/Article/details/22902.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9824227.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0357.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1264.sHtML
- http://www.mobile.fuvxie.cn/Article/details/284352.sHtML
- http://www.mobile.fuvxie.cn/Article/details/40554.sHtML
- http://www.mobile.fuvxie.cn/Article/details/384009.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0929526.sHtML
- http://www.mobile.fuvxie.cn/Article/details/40845.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6331956.sHtML
- http://www.mobile.fuvxie.cn/Article/details/171796.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4134.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7863593.sHtML
- http://www.mobile.fuvxie.cn/Article/details/377407.sHtML
- http://www.mobile.fuvxie.cn/Article/details/970964.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2604499.sHtML
- http://www.mobile.fuvxie.cn/Article/details/516949.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3281819.sHtML
- http://www.mobile.fuvxie.cn/Article/details/75126.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8547.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2659.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72031.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7194.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7427.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9943.sHtML
- http://www.mobile.fuvxie.cn/Article/details/160732.sHtML
- http://www.mobile.fuvxie.cn/Article/details/41467.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1333.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7357837.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6028.sHtML
- http://www.mobile.fuvxie.cn/Article/details/380065.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1414613.sHtML
- http://www.mobile.fuvxie.cn/Article/details/550020.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9251401.sHtML
- http://www.mobile.fuvxie.cn/Article/details/268270.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3282520.sHtML
- http://www.mobile.fuvxie.cn/Article/details/168832.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3238.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1216697.sHtML
- http://www.mobile.fuvxie.cn/Article/details/440275.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0107.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6878817.sHtML
- http://www.mobile.fuvxie.cn/Article/details/516763.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7071.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6125.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5122008.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6054564.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2116786.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2271517.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6067.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8346542.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6762.sHtML
- http://www.mobile.fuvxie.cn/Article/details/627479.sHtML
- http://www.mobile.fuvxie.cn/Article/details/03282.sHtML
- http://www.mobile.fuvxie.cn/Article/details/83756.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7681251.sHtML
- http://www.mobile.fuvxie.cn/Article/details/706931.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9504.sHtML
- http://www.mobile.fuvxie.cn/Article/details/79838.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7599.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8972388.sHtML
- http://www.mobile.fuvxie.cn/Article/details/446083.sHtML
- http://www.mobile.fuvxie.cn/Article/details/595979.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3142652.sHtML
- http://www.mobile.fuvxie.cn/Article/details/835228.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2944990.sHtML
- http://www.mobile.fuvxie.cn/Article/details/14363.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8299.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6732.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0147.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9689786.sHtML
- http://www.mobile.fuvxie.cn/Article/details/86449.sHtML
- http://www.mobile.fuvxie.cn/Article/details/328749.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0693.sHtML
- http://www.mobile.fuvxie.cn/Article/details/66660.sHtML
- http://www.mobile.fuvxie.cn/Article/details/13696.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9242667.sHtML
- http://www.mobile.fuvxie.cn/Article/details/527884.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9464.sHtML
- http://www.mobile.fuvxie.cn/Article/details/45749.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5643968.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5695249.sHtML
- http://www.mobile.fuvxie.cn/Article/details/735461.sHtML
- http://www.mobile.fuvxie.cn/Article/details/583040.sHtML
- http://www.mobile.fuvxie.cn/Article/details/146138.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8927852.sHtML
- http://www.mobile.fuvxie.cn/Article/details/439392.sHtML
- http://www.mobile.fuvxie.cn/Article/details/588235.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0749.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5069129.sHtML
- http://www.mobile.fuvxie.cn/Article/details/064762.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4194948.sHtML
- http://www.mobile.fuvxie.cn/Article/details/56403.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6295.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4856.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8007369.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0139.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9962049.sHtML
- http://www.mobile.fuvxie.cn/Article/details/35182.sHtML
- http://www.mobile.fuvxie.cn/Article/details/24117.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8999110.sHtML
- http://www.mobile.fuvxie.cn/Article/details/236183.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2727201.sHtML
- http://www.mobile.fuvxie.cn/Article/details/363835.sHtML
- http://www.mobile.fuvxie.cn/Article/details/229209.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0550.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5865.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72669.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4239240.sHtML
- http://www.mobile.fuvxie.cn/Article/details/68371.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7405.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4397364.sHtML
- http://www.mobile.fuvxie.cn/Article/details/69258.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8011677.sHtML
- http://www.mobile.fuvxie.cn/Article/details/687955.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5492.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5149.sHtML
- http://www.mobile.fuvxie.cn/Article/details/99332.sHtML
- http://www.mobile.fuvxie.cn/Article/details/282889.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3570.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4665041.sHtML
- http://www.mobile.fuvxie.cn/Article/details/99831.sHtML
- http://www.mobile.fuvxie.cn/Article/details/38317.sHtML
- http://www.mobile.fuvxie.cn/Article/details/926039.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5425.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9597.sHtML
- http://www.mobile.fuvxie.cn/Article/details/09940.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1424.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5848433.sHtML
- http://www.mobile.fuvxie.cn/Article/details/69822.sHtML
- http://www.mobile.fuvxie.cn/Article/details/20659.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9214.sHtML
- http://www.mobile.fuvxie.cn/Article/details/863393.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3040654.sHtML
- http://www.mobile.fuvxie.cn/Article/details/041979.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1379.sHtML
- http://www.mobile.fuvxie.cn/Article/details/221606.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6446050.sHtML
- http://www.mobile.fuvxie.cn/Article/details/80079.sHtML
- http://www.mobile.fuvxie.cn/Article/details/884952.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7836.sHtML
- http://www.mobile.fuvxie.cn/Article/details/259669.sHtML
- http://www.mobile.fuvxie.cn/Article/details/727264.sHtML
- http://www.mobile.fuvxie.cn/Article/details/43907.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8082859.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6618667.sHtML
- http://www.mobile.fuvxie.cn/Article/details/904681.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8213181.sHtML
- http://www.mobile.fuvxie.cn/Article/details/09523.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0815039.sHtML
- http://www.mobile.fuvxie.cn/Article/details/65753.sHtML
- http://www.mobile.fuvxie.cn/Article/details/124060.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8924543.sHtML
- http://www.mobile.fuvxie.cn/Article/details/994754.sHtML
- http://www.mobile.fuvxie.cn/Article/details/57792.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2332.sHtML
- http://www.mobile.fuvxie.cn/Article/details/85149.sHtML
- http://www.mobile.fuvxie.cn/Article/details/41353.sHtML
- http://www.mobile.fuvxie.cn/Article/details/41854.sHtML
- http://www.mobile.fuvxie.cn/Article/details/03832.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3624.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5355786.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0603.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9793.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7708522.sHtML
- http://www.mobile.fuvxie.cn/Article/details/94128.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6218280.sHtML
- http://www.mobile.fuvxie.cn/Article/details/139139.sHtML
- http://www.mobile.fuvxie.cn/Article/details/27033.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7060.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0422231.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2257547.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7111.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5146.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4749497.sHtML
- http://www.mobile.fuvxie.cn/Article/details/04354.sHtML
- http://www.mobile.fuvxie.cn/Article/details/24892.sHtML
- http://www.mobile.fuvxie.cn/Article/details/03769.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2914.sHtML
- http://www.mobile.fuvxie.cn/Article/details/44778.sHtML

## 项目结构

```
weblink-hub/
├── apps/                                # 应用入口与路由定义
│   ├── api/                             # REST API 控制器
│   │   ├── links.controller.js          # 链接 CRUD 与筛选接口
│   │   └── health.controller.js         # 健康检查与监控数据接口
│   └── web/                             # 服务端渲染页面路由
│       ├── dashboard.ejs                # 状态看板视图模板
│       └── settings.ejs                 # 系统设置与导出界面
├── core/                                # 核心业务逻辑层
│   ├── crawler/                         # 元数据抓取与链接状态探测
│   │   ├── fetcher.js                   # 基于 node-fetch 的 HTTP 请求封装
│   │   └── parser.js                    # HTML title / meta 提取器
│   ├── index/                           # 倒排索引构建与检索
│   │   ├── tokenizer.js                 # 中文分词与停用词过滤
│   │   └── searcher.js                  # BM25 相似度排序实现
│   └── storage/                         # 数据持久化适配器
│       ├── sqlite.adapter.js            # SQLite3 连接池与迁移管理
│       └── redis.cache.js               # 可选 Redis 缓存层（需配置）
├── data/                                # 数据文件目录（自动生成）
│   ├── links.db                         # SQLite 主数据库文件
│   └── backups/                         # 每日自动备份归档
├── scripts/                             # 运维与工具脚本
│   ├── health-check.js                  # 批量链接可访问性检测任务
│   ├── import-csv.js                    # 从外部 CSV 批量导入工具
│   └── export-rss.js                    # 生成 RSS 订阅文件
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 各模块单元测试（Jest）
│   └── integration/                     # API 端到端测试（Supertest）
├── docs/                                # 完整文档源文件（Markdown）
│   ├── user-guide/                      # 用户手册分章节
│   ├── developer-guide/                 # 开发与扩展指南
│   └── operations/                      # 部署与运维手册
├── .env.example                         # 环境变量配置模板
├── docker-compose.yml                   # 容器化编排（含 SQLite 卷挂载）
├── Dockerfile                           # 多阶段构建生产镜像
├── package.json                         # npm 依赖与脚本定义
└── README.md                            # 项目概览（本文件）
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并 clone 到本地开发环境。建议使用 `--recurse-submodules` 拉取子模块依赖。

2. 创建新的功能分支，分支命名遵循 `feature/` 或 `fix/` 前缀加简要描述，例如 `feature/add-elasticsearch-adapter`。

3. 编写代码时遵守项目 ESLint 与 Prettier 配置，运行 `npm run lint` 检查风格，确保单元测试覆盖核心逻辑。

4. 提交 commit 时使用常规提交规范（Conventional Commits），类型包括 `feat`、`fix`、`docs`、`refactor`、`test` 等，提交信息简洁明了。

5. 提交 Pull Request 前请同步上游 main 分支，解决冲突后推送。PR 描述中需说明变更动机、影响范围以及是否包含破坏性更新。

## 常见问题

**Q：我导入的链接超过 1000 条，界面加载变慢，如何优化？**

A：WebLink Hub 默认使用分页加载，每页 50 条。如果数据库记录数庞大，建议在 `.env` 中调低 `PAGE_SIZE` 至 20，并启用 Redis 缓存层以减轻 SQLite 查询压力。此外，定期运行 `npm run archive:old` 将超过 180 天未访问的链接归档到 `data/archive/` 目录，可保持主表轻量。

**Q：如何从浏览器书签直接导入？**

A：目前不提供一键导入插件，但您可以从 Chrome 或 Firefox 导出书签为 HTML 文件，然后使用 `scripts/import-bookmark.js` 脚本解析该 HTML 并写入数据库。具体用法参见 `docs/user-guide/import.md` 章节。

**Q：状态监控显示大量链接为“失效”，但手动访问正常，是什么原因？**

A：监控脚本默认使用 HEAD 请求检测，部分服务器不支持 HEAD 或返回 405 方法不允许，会导致误判。您可以在 `.env` 中将 `CHECK_METHOD` 改为 `GET`，并增加 `CHECK_TIMEOUT` 至 10000 毫秒。同时，该站点可能设置了反爬策略，建议在 `core/crawler/fetcher.js` 中配置合理的 User-Agent 轮换。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
