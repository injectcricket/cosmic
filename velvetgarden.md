# WebLink Navigator

WebLink Navigator 是一个面向开发人员和技术研究者的结构化外链资源聚合平台。该项目专注于收集、分类和呈现高质量的第三方技术文章、教程及参考资料链接，解决开发者在海量网络信息中难以快速定位有效技术文档的痛点。通过人工筛选和主题索引，WebLink Navigator 帮助目标用户——包括软件工程师、架构师、技术经理和科研人员——节省信息检索时间，提高技术调研和学习的效率。

本项目并非一个传统意义上的爬虫或搜索引擎，而是一个精心维护的“知识路由”表。每个收录的 URL 均经过基础可用性校验，并按技术领域、内容类型和阅读价值进行标签化处理。项目以轻量级静态站点形式发布，支持全文检索和分类浏览，适用于日常技术查阅、项目预研和技术决策支持等严肃场景。

## 功能概览

**多维度分类索引**：所有外链资源按编程语言、框架、基础设施、算法、架构设计等维度进行一级分类，每个分类下设有子标签，便于精确定位。

**链接可用性监控**：系统定期对已收录的 URL 发起 HTTP 请求，检测状态码和响应时间，自动标记失效或响应过慢的链接，并在管理后台生成告警通知。

**全文检索与过滤**：基于倒排索引实现标题、摘要、标签和正文片段的快速检索，支持按发布时间、访问热度、内容评分等多重过滤条件组合查询。

**内容摘要提取**：对于每个收录的链接，自动抓取页面 meta 信息并生成 120-160 字的文本摘要，帮助用户在点击前了解文章核心内容。

**个人收藏与标注**：注册用户可将感兴趣的资源链接加入个人收藏夹，并添加自定义标签和阅读笔记，形成个人知识库。

**数据导入导出**：支持批量导入和导出链接数据，格式包括 JSON、CSV 和 Markdown 表格，方便团队内部共享和二次加工。

**开放 API 接口**：提供 RESTful API 供第三方工具调用链接数据，支持按分类、标签、关键词等参数查询，返回结构化 JSON 数据。

**操作日志与审计**：记录所有链接的增删改查操作以及用户行为日志，满足企业级数据安全和管理合规要求。

## 应用场景

技术团队内部知识库建设：团队技术负责人可使用 WebLink Navigator 统一收集团队成员推荐的优秀技术文章，按项目或技术栈分类，形成团队共享的知识资产，新人入职时可快速了解团队关注的技术方向和最佳实践。

技术选型与方案调研：架构师在进行中间件选型、框架对比或方案设计时，可通过本平台快速检索已收录的评测文章、性能对比报告和落地案例，大幅缩短调研周期，避免重复搜索。

个人技术学习路线规划：开发者可根据自身技术成长目标，订阅平台中相关分类的新增链接，系统定期推送符合兴趣领域的优质内容，辅助制定系统性的学习计划。

开源项目文档外链补充：开源项目维护者可在项目 README 或官网中引用本平台的分类链接列表，作为项目生态的扩展阅读材料，帮助用户更深入地理解项目背景和技术依赖。

技术会议与内部分享素材收集：技术分享主讲人可在平台上按主题标签快速收集多篇参考资料，统一导出为引用列表，用于编写技术分享 PPT 的参考来源章节。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebLink Navigator 开发实例。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装依赖（使用 npm）
npm install

# 配置环境变量
cp .env.example .env
# 根据实际环境修改 .env 中的数据库连接、缓存和 API 密钥配置

# 初始化数据库表结构和基础数据
npm run db:init

# 启动开发服务器（默认监听端口 3000）
npm run dev
```

访问 http://localhost:3000 即可浏览本地实例。生产环境部署请参考 `docs/deployment.md` 文档。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | v18.17.0 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | v9.0.0 或更高 | 包管理器，与 Node.js 捆绑安装 |
| PostgreSQL | v14.0 或更高 | 主数据库，存储链接元数据、用户信息和分类标签 |
| Redis | v7.0 或更高 | 缓存层，用于提升检索响应速度和会话存储 |
| Nginx | v1.22 或更高 | 生产环境反向代理和静态资源服务（可选） |
| Git | v2.30 或更高 | 版本控制，用于克隆和更新项目代码 |

操作系统支持 Linux (Ubuntu 20.04/22.04, CentOS 7+), macOS 12+, Windows Server 2019+ (WSL2 推荐)。最低硬件配置为 2 核 CPU、4GB 内存、20GB 可用磁盘空间。生产环境建议 4 核 CPU、8GB 以上内存。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何注册账号、添加链接、使用检索和收藏功能；如何订阅分类更新和导出数据 |
| 管理员手册 | /docs/admin-guide/ | 如何管理用户权限、审核新链接、配置监控阈值和查看系统操作日志 |
| 开发指南 | /docs/developer-guide/ | 项目目录结构说明、核心模块设计思路、API 接口文档、单元测试编写规范和本地调试方法 |
| 架构设计 | /docs/architecture/ | 系统整体架构图、数据流设计、缓存策略、水平扩展方案和灾备恢复机制 |
| 部署运维 | /docs/deployment/ | 生产环境部署步骤、Nginx 配置模板、SSL 证书安装、日志轮转和性能调优参数 |
| 常见问题 | /docs/faq/ | 收录链接失效如何处理、检索结果不准确如何调整、数据库迁移失败如何恢复、性能瓶颈如何排查 |

## 资源列表

- http://www.mobile.fuvxie.cn/Article/details/09304.sHtML
- http://www.mobile.fuvxie.cn/Article/details/731201.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0355469.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90364.sHtML
- http://www.mobile.fuvxie.cn/Article/details/917401.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7066.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5229022.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5663921.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2882999.sHtML
- http://www.mobile.fuvxie.cn/Article/details/540606.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9690110.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4985594.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0164.sHtML
- http://www.mobile.fuvxie.cn/Article/details/857389.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8432843.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5877.sHtML
- http://www.mobile.fuvxie.cn/Article/details/612777.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5162033.sHtML
- http://www.mobile.fuvxie.cn/Article/details/090168.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5615.sHtML
- http://www.mobile.fuvxie.cn/Article/details/08975.sHtML
- http://www.mobile.fuvxie.cn/Article/details/40842.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9819304.sHtML
- http://www.mobile.fuvxie.cn/Article/details/903109.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1511.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2793149.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4363.sHtML
- http://www.mobile.fuvxie.cn/Article/details/118074.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0910116.sHtML
- http://www.mobile.fuvxie.cn/Article/details/71801.sHtML
- http://www.mobile.fuvxie.cn/Article/details/962674.sHtML
- http://www.mobile.fuvxie.cn/Article/details/92941.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5388063.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2122498.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0263813.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8528225.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1636575.sHtML
- http://www.mobile.fuvxie.cn/Article/details/860114.sHtML
- http://www.mobile.fuvxie.cn/Article/details/61819.sHtML
- http://www.mobile.fuvxie.cn/Article/details/68697.sHtML
- http://www.mobile.fuvxie.cn/Article/details/88602.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6999842.sHtML
- http://www.mobile.fuvxie.cn/Article/details/113463.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8659.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7365373.sHtML
- http://www.mobile.fuvxie.cn/Article/details/76863.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3699.sHtML
- http://www.mobile.fuvxie.cn/Article/details/66908.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7081.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1431.sHtML
- http://www.mobile.fuvxie.cn/Article/details/33696.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4375879.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5371.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4941307.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7616.sHtML
- http://www.mobile.fuvxie.cn/Article/details/425095.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0940175.sHtML
- http://www.mobile.fuvxie.cn/Article/details/53711.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5235.sHtML
- http://www.mobile.fuvxie.cn/Article/details/28790.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6141.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3693213.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4314535.sHtML
- http://www.mobile.fuvxie.cn/Article/details/93585.sHtML
- http://www.mobile.fuvxie.cn/Article/details/486508.sHtML
- http://www.mobile.fuvxie.cn/Article/details/207717.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8092.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6471.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3729.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3007.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2442.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1784988.sHtML
- http://www.mobile.fuvxie.cn/Article/details/975130.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4954.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4363278.sHtML
- http://www.mobile.fuvxie.cn/Article/details/65508.sHtML
- http://www.mobile.fuvxie.cn/Article/details/149679.sHtML
- http://www.mobile.fuvxie.cn/Article/details/87999.sHtML
- http://www.mobile.fuvxie.cn/Article/details/36091.sHtML
- http://www.mobile.fuvxie.cn/Article/details/991305.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7279405.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5398433.sHtML
- http://www.mobile.fuvxie.cn/Article/details/29759.sHtML
- http://www.mobile.fuvxie.cn/Article/details/62104.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1837843.sHtML
- http://www.mobile.fuvxie.cn/Article/details/639693.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3108.sHtML
- http://www.mobile.fuvxie.cn/Article/details/80782.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8526554.sHtML
- http://www.mobile.fuvxie.cn/Article/details/261523.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2631.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2993.sHtML
- http://www.mobile.fuvxie.cn/Article/details/57599.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8330947.sHtML
- http://www.mobile.fuvxie.cn/Article/details/62609.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0102.sHtML
- http://www.mobile.fuvxie.cn/Article/details/612599.sHtML
- http://www.mobile.fuvxie.cn/Article/details/47169.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5114.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2940.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32847.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7053241.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6505.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8755.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1895502.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7775646.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6076.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2215153.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1885.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1771069.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1298.sHtML
- http://www.mobile.fuvxie.cn/Article/details/05618.sHtML
- http://www.mobile.fuvxie.cn/Article/details/30878.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0127900.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6553301.sHtML
- http://www.mobile.fuvxie.cn/Article/details/528325.sHtML
- http://www.mobile.fuvxie.cn/Article/details/518631.sHtML
- http://www.mobile.fuvxie.cn/Article/details/871908.sHtML
- http://www.mobile.fuvxie.cn/Article/details/31944.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2952.sHtML
- http://www.mobile.fuvxie.cn/Article/details/818040.sHtML
- http://www.mobile.fuvxie.cn/Article/details/26737.sHtML
- http://www.mobile.fuvxie.cn/Article/details/012781.sHtML
- http://www.mobile.fuvxie.cn/Article/details/64582.sHtML
- http://www.mobile.fuvxie.cn/Article/details/76349.sHtML
- http://www.mobile.fuvxie.cn/Article/details/49463.sHtML
- http://www.mobile.fuvxie.cn/Article/details/74119.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8733062.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4121382.sHtML
- http://www.mobile.fuvxie.cn/Article/details/091387.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6926.sHtML
- http://www.mobile.fuvxie.cn/Article/details/55450.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4326614.sHtML
- http://www.mobile.fuvxie.cn/Article/details/31657.sHtML
- http://www.mobile.fuvxie.cn/Article/details/13354.sHtML
- http://www.mobile.fuvxie.cn/Article/details/38201.sHtML
- http://www.mobile.fuvxie.cn/Article/details/809550.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7465468.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90718.sHtML
- http://www.mobile.fuvxie.cn/Article/details/033678.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5726.sHtML
- http://www.mobile.fuvxie.cn/Article/details/337714.sHtML
- http://www.mobile.fuvxie.cn/Article/details/91385.sHtML
- http://www.mobile.fuvxie.cn/Article/details/92261.sHtML
- http://www.mobile.fuvxie.cn/Article/details/01041.sHtML
- http://www.mobile.fuvxie.cn/Article/details/452292.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0322.sHtML
- http://www.mobile.fuvxie.cn/Article/details/517713.sHtML
- http://www.mobile.fuvxie.cn/Article/details/71371.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4052712.sHtML
- http://www.mobile.fuvxie.cn/Article/details/040410.sHtML
- http://www.mobile.fuvxie.cn/Article/details/96045.sHtML
- http://www.mobile.fuvxie.cn/Article/details/946105.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0616.sHtML
- http://www.mobile.fuvxie.cn/Article/details/70647.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7151411.sHtML
- http://www.mobile.fuvxie.cn/Article/details/993545.sHtML
- http://www.mobile.fuvxie.cn/Article/details/024835.sHtML
- http://www.mobile.fuvxie.cn/Article/details/29958.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9935914.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2310.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72639.sHtML
- http://www.mobile.fuvxie.cn/Article/details/33319.sHtML
- http://www.mobile.fuvxie.cn/Article/details/903076.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2260574.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7497.sHtML
- http://www.mobile.fuvxie.cn/Article/details/337482.sHtML
- http://www.mobile.fuvxie.cn/Article/details/591155.sHtML
- http://www.mobile.fuvxie.cn/Article/details/74971.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0136185.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1947514.sHtML
- http://www.mobile.fuvxie.cn/Article/details/913183.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2824.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6342.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0399.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6517.sHtML
- http://www.mobile.fuvxie.cn/Article/details/44195.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8241.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6696.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2635960.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3914935.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5610564.sHtML
- http://www.mobile.fuvxie.cn/Article/details/08265.sHtML
- http://www.mobile.fuvxie.cn/Article/details/43449.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8057.sHtML
- http://www.mobile.fuvxie.cn/Article/details/40194.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1808531.sHtML
- http://www.mobile.fuvxie.cn/Article/details/659207.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7302.sHtML
- http://www.mobile.fuvxie.cn/Article/details/43909.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2745053.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6699.sHtML
- http://www.mobile.fuvxie.cn/Article/details/912944.sHtML
- http://www.mobile.fuvxie.cn/Article/details/131570.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2842497.sHtML
- http://www.mobile.fuvxie.cn/Article/details/41762.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7308.sHtML
- http://www.mobile.fuvxie.cn/Article/details/152018.sHtML
- http://www.mobile.fuvxie.cn/Article/details/40028.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4181404.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7799910.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90633.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6368.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8083.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3415.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6837.sHtML
- http://www.mobile.fuvxie.cn/Article/details/75853.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90957.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90103.sHtML
- http://www.mobile.fuvxie.cn/Article/details/73976.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1646.sHtML
- http://www.mobile.fuvxie.cn/Article/details/91400.sHtML
- http://www.mobile.fuvxie.cn/Article/details/157866.sHtML
- http://www.mobile.fuvxie.cn/Article/details/33361.sHtML
- http://www.mobile.fuvxie.cn/Article/details/527504.sHtML
- http://www.mobile.fuvxie.cn/Article/details/531256.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4111401.sHtML
- http://www.mobile.fuvxie.cn/Article/details/415451.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9945793.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2078.sHtML
- http://www.mobile.fuvxie.cn/Article/details/68318.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4899306.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2162740.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4355332.sHtML
- http://www.mobile.fuvxie.cn/Article/details/43351.sHtML
- http://www.mobile.fuvxie.cn/Article/details/57650.sHtML
- http://www.mobile.fuvxie.cn/Article/details/534717.sHtML
- http://www.mobile.fuvxie.cn/Article/details/94616.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6294629.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8825.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0507.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6162555.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2314.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7128126.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8122014.sHtML
- http://www.mobile.fuvxie.cn/Article/details/046804.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6009554.sHtML
- http://www.mobile.fuvxie.cn/Article/details/93345.sHtML
- http://www.mobile.fuvxie.cn/Article/details/572615.sHtML
- http://www.mobile.fuvxie.cn/Article/details/79716.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6536452.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9237662.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1000155.sHtML
- http://www.mobile.fuvxie.cn/Article/details/97213.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7713.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7921.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6284.sHtML
- http://www.mobile.fuvxie.cn/Article/details/96615.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7885.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4600511.sHtML

## 项目结构

```
weblink-navigator/
├── .github/                         # GitHub 工作流配置
│   └── workflows/
│       ├── ci.yml                   # 持续集成：测试、构建、静态检查
│       └── cd.yml                   # 持续部署：自动发布到生产环境
├── apps/                            # 多应用模块
│   ├── web/                         # 主 Web 应用（Next.js）
│   │   ├── src/
│   │   │   ├── pages/               # 页面路由组件
│   │   │   ├── components/          # 可复用 UI 组件
│   │   │   ├── hooks/               # 自定义 React Hooks
│   │   │   └── styles/              # 全局样式和主题变量
│   │   └── public/                  # 静态资源（图片、字体、favicon）
│   └── api/                         # RESTful API 服务（Express）
│       ├── src/
│       │   ├── routes/              # 路由定义（按资源拆分）
│       │   ├── controllers/         # 业务逻辑控制器
│       │   ├── models/              # 数据模型（Sequelize ORM）
│       │   ├── middleware/          # 认证、日志、限流中间件
│       │   └── services/            # 外部服务调用封装
│       └── tests/                   # API 单元测试和集成测试
├── packages/                        # 内部共享包
│   ├── shared-types/                # TypeScript 类型定义
│   ├── link-validator/              # 链接可用性检测工具
│   └── content-extractor/           # 页面摘要抓取和解析模块
├── docs/                            # 项目文档
│   ├── user-guide/                  # 用户手册
│   ├── admin-guide/                 # 管理员手册
│   ├── developer-guide/             # 开发指南
│   ├── architecture/                # 架构设计文档
│   ├── deployment/                  # 部署运维文档
│   └── faq/                         # 常见问题
├── scripts/                         # 运维和工具脚本
│   ├── db-migrate.js                # 数据库迁移脚本
│   ├── seed-data.js                 # 初始化种子数据
│   └── health-check.sh              # 服务健康检查脚本
├── config/                          # 环境配置文件
│   ├── default.json                 # 默认配置
│   ├── development.json             # 开发环境覆盖
│   ├── production.json              # 生产环境覆盖
│   └── test.json                    # 测试环境覆盖
├── logs/                            # 应用日志目录（生产环境）
├── node_modules/                    # 依赖包（git 忽略）
├── .env.example                     # 环境变量模板
├── .eslintrc.js                     # ESLint 代码检查规则
├── .prettierrc                      # Prettier 代码格式化配置
├── docker-compose.yml               # Docker Compose 本地开发编排
├── Dockerfile                       # 应用容器构建文件
├── package.json                     # npm 项目清单和脚本定义
├── package-lock.json                # 依赖版本锁定文件
├── tsconfig.json                    # TypeScript 编译配置
└── README.md                        # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎并鼓励社区贡献者参与 WebLink Navigator 的建设。请遵循以下步骤提交贡献：

1. 查阅问题跟踪器：访问 GitHub Issues 页面，浏览标记为 `help wanted` 或 `good first issue` 的问题。如需提交新功能建议或报告缺陷，请先搜索是否已有类似议题，避免重复。

2. 派生仓库并创建特性分支：从主仓库派生一份代码副本到个人账号下，然后在本地的派生仓库中新建分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。确保分支基于最新的 `main` 分支。

3. 编写代码并添加测试：在本地环境完成功能开发或缺陷修复后，补充对应的单元测试和集成测试用例，确保测试覆盖率达到 80% 以上。同时更新相关文档，包括 API 文档和使用手册。

4. 提交前检查：运行 `npm run lint` 检查代码风格，运行 `npm run test` 确认所有测试通过，运行 `npm run build` 验证项目可正常构建。提交信息遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`。

5. 发起拉取请求：将特性分支推送至派生仓库，然后向主仓库的 `main` 分支发起 Pull Request。在 PR 描述中清晰说明改动目的、实现方案和测试情况。维护者将在 3 个工作日内进行代码审查，并根据审查意见进行修改直至合并。

## 常见问题

问：收录的链接如果失效了，系统会如何处理？

答：系统后台的链接可用性监控任务每 6 小时执行一次全量扫描。当检测到某个链接返回 HTTP 状态码 4xx 或 5xx，或连续三次超时（超时阈值为 10 秒），系统会自动将该链接标记为“疑似失效”，并在管理后台生成告警。管理员可以在审核后决定将其移至“失效链接”归档区，或重新尝试恢复。普通用户在浏览时，失效链接会显示

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
