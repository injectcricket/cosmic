# WebLink Navigator

WebLink Navigator 是一个面向技术内容聚合与结构化外链管理的开源解决方案，定位于帮助开发者、技术博主、知识管理团队高效地收集、分类、展示和检索分布在大量独立文章页面中的技术资源。项目通过构建轻量级的外链元数据索引层，将分散的 URL 资源转化为可浏览、可搜索、可维护的知识库，解决传统书签管理方式在面对数百甚至数千条外链时缺乏上下文、无法协作、难以扩展的痛点。目标用户包括开源社区文档维护者、技术教育平台内容运营者、企业技术中台的知识管理工程师以及个人技术博主。

## 功能概览

**多源外链统一入库**：支持将批量提供的文章详情页 URL 自动抓取并归入统一的数据管道，保留原始链接与页面元数据的映射关系，确保每条资源可追溯至原始发布站点。

**结构化元数据提取**：针对移动端适配页面（wap.mobile 子域）的 HTML 结构进行解析，自动提取文章标题、发布时间、正文摘要、关键词标签等核心字段，生成标准化的资源描述记录。

**资源分类与标签体系**：内置可自定义的分类树和标签引擎，允许用户根据技术领域、内容类型、适用场景等维度对资源进行多级归类，支持批量打标签与智能分类建议。

**全文检索与高级过滤**：基于倒排索引实现资源标题、摘要、正文关键词的快速检索，同时提供按域名、发布时间段、内容长度、文件类型等多条件组合过滤能力。

**资源状态跟踪与健康检查**：定期对已收录的 URL 进行可访问性检测，自动标记失效链接、重定向链接和响应缓慢的资源，支持导出异常报告。

**协作式编辑与版本管理**：提供基于角色的访问控制，支持多用户对资源记录进行协同编辑，所有修改操作记录审计日志，并支持回滚至任意历史版本。

**开放 API 与数据导出**：提供 RESTful API 供第三方系统调用资源数据，支持 JSON、CSV、Markdown 表格等多种格式的批量导出，便于与其他知识管理工具集成。

**移动端自适应展示模板**：内置响应式前端页面模板，针对 wap 子域来源的资源提供优化的移动端浏览体验，确保在手机和平板设备上顺畅阅读文章内容。

## 应用场景

技术博客的长期外链资产管理：技术博主在撰写文章时频繁引用外部资料，随时间推移引用的链接可能失效或内容变更。WebLink Navigator 可帮助博主建立个人外链库，定期检测链接健康度，自动提醒失效资源，并在博客迁移或改版时批量更新引用链接。

开源项目文档站的外链整合：开源项目的 README、Wiki 和用户手册中通常包含大量指向第三方工具、依赖库、学习教程的外部链接。维护团队可使用该项目将所有外链统一收录并附加使用场景说明，新贡献者可通过检索快速定位所需资源，减少重复提问。

技术教育平台的课程资料集管理：在线教育平台为每门课程准备数百个补充阅读材料和工具推荐链接。WebLink Navigator 允许课程设计者按教学阶段、难度等级、主题分类组织链接，学员可通过分类浏览或关键词搜索获取推荐资源，提升自主学习效率。

企业技术中台的知识沉淀体系：企业内部的中间件团队、运维团队和业务研发团队在日常工作中积累了大量踩坑记录、调优案例和官方文档链接。通过部署 WebLink Navigator，可将分散在各团队笔记工具中的链接统一汇聚，形成可持续积累的技术知识库，降低信息孤岛风险。

## 快速开始

以下指令演示了从代码仓库克隆、安装项目依赖到启动开发服务的完整流程。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run init-db
npm run dev
```

执行上述命令后，开发服务器默认运行在 http://localhost:3000，管理后台可通过 http://localhost:3000/admin 访问，默认管理员账号为 admin，初始密码在首次启动时由控制台输出。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x LTS 或更高 | 项目运行时环境，推荐使用最新的 Active LTS 版本 |
| npm | 9.x 或更高 | Node.js 包管理器，用于安装项目依赖 |
| PostgreSQL | 14.x 或更高 | 主数据存储，存储资源元数据、用户信息、分类标签和审计日志 |
| Redis | 7.x 或更高 | 缓存与会话存储，用于提升检索性能和保存用户登录状态 |
| Elasticsearch | 8.x 或更高 | 全文检索引擎，为资源标题和摘要提供中文分词与快速搜索能力 |
| Nginx | 1.22 或更高 | 生产环境反向代理服务器，用于负载均衡和静态资源缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/ | 如何使用 WebLink Navigator 进行资源收录、分类、检索和导出，面向日常使用者 |
| 部署手册 | /docs/deployment/ | 如何在生产环境中部署 WebLink Navigator，包括 Docker 编排、环境变量配置和反向代理设置 |
| 开发者文档 | /docs/developer/ | 项目架构设计、核心模块说明、API 接口规范以及如何二次开发和扩展功能 |
| 运维手册 | /docs/operations/ | 数据库备份与恢复策略、缓存预热方案、日志监控和性能调优建议 |

## 资源列表

- http://wap.mobile.fuvxie.cn/Article/details/9720.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/942444.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/86886.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7218211.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/62482.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/531365.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4414.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/53936.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7898853.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3188811.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/625546.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0473.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8508.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6836.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8630965.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/215545.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9923602.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/43715.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8656040.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/369133.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/158398.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8015155.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6678960.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/275100.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/32562.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2667.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3352.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/56473.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9440.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/049475.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1579953.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/239817.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/294535.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0952.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7403757.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2612.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1518830.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8417.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0343.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9824128.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8611794.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/53876.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1816.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/33917.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/10237.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7822.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/432855.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/88732.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2671.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8144.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/621660.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/20588.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/51646.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7912.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0589412.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/234389.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6570097.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7714.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/997093.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2019.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/90297.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5182.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4524.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8681518.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1809.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/256539.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3371832.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3319085.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3413.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7826258.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/574890.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6344951.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4082753.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/70548.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9670662.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/521268.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9114.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/17807.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2178.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/703357.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/72251.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5445.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/24086.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3516.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4525.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2661993.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/66574.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6388070.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/52880.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8294842.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7721543.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0519.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/10073.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0771.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2121079.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9521583.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/792805.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/961983.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5234424.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/256813.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5735841.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9208.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8056.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/850307.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/65995.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6361.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/524791.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9338044.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0764.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/594659.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/583707.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/679275.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/316059.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2709601.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2460.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/18061.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7173766.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9073.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/77172.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/73523.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8022407.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/09024.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/734067.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/32922.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0256.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/208906.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/57761.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1757.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0388335.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9120.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/113647.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7796.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7151.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0071434.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9529576.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3195.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/73820.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/32816.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/42540.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/526168.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2117.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/674771.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9849.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3645.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/460852.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9224.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/156416.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/62095.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0270151.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/86305.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/896874.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0187472.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/732884.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/032718.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0597.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2419.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/194816.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/374849.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/95942.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/964233.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/218551.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/732664.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0678.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/34839.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/436422.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/774933.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0264890.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/67121.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/06499.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4699114.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/209518.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/977469.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/700407.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/18452.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/611628.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/642543.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/80699.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7373360.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/310631.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/64790.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/35383.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0975.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/7155.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/62642.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8216.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4299742.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0825.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/277680.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/07654.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2994744.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/570276.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/10459.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9621.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/11284.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/917837.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/19859.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/68096.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0595097.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/625550.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8979.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/53145.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1493.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/8709505.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/89540.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6961.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5565588.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/315122.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2242.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/548390.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9102268.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1427555.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/314204.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/72462.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/074570.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/51411.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/14401.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/68427.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/5465.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6109.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/391918.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/32321.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/15257.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/12664.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/32072.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/251840.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6628.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/3935027.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/07109.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/402781.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/715903.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4856596.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/50728.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/876229.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/6834.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/45931.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/42748.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/158684.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/4247169.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/9636.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2255987.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0075707.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/18244.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/57078.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/670814.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/2415.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/1855.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/383469.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/0132461.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/11775.sHtML
- http://wap.mobile.fuvxie.cn/Article/details/98919.sHtML

## 项目结构

```
weblink-navigator/
├── packages/
│   ├── backend/                    # 后端服务模块（NestJS + TypeORM）
│   │   ├── src/
│   │   │   ├── modules/
│   │   │   │   ├── resources/      # 资源收录与元数据管理核心逻辑
│   │   │   │   ├── crawler/        # 页面抓取与 HTML 解析引擎
│   │   │   │   ├── search/         # Elasticsearch 索引与查询服务
│   │   │   │   ├── health/         # 链接健康检查调度任务
│   │   │   │   ├── auth/           # JWT 认证与 RBAC 权限控制
│   │   │   │   └── audit/          # 操作审计日志记录与查询
│   │   │   ├── common/             # 公共工具类、管道、拦截器
│   │   │   └── config/             # 环境变量校验与配置加载
│   │   └── test/                   # 单元测试与 e2e 测试用例
│   ├── frontend/                   # 前端展示面板（React + TypeScript）
│   │   ├── src/
│   │   │   ├── pages/              # 资源列表、详情、分类浏览、检索结果页
│   │   │   ├── components/         # 可复用的 UI 组件库
│   │   │   ├── hooks/              # 自定义 React Hooks 封装数据请求逻辑
│   │   │   └── styles/             # 全局样式与移动端响应式适配
│   │   └── public/                 # 静态资源与 favicon 文件
│   └── shared/                     # 前后端共享的类型定义与常量
│       ├── types/                  # TypeScript 接口与枚举定义
│       └── constants/              # 业务常量如分类预设、标签白名单
├── docker/                         # Docker 编排文件与各服务 Dockerfile
│   ├── docker-compose.yml          # 完整服务栈（PostgreSQL + Redis + ES + 应用）
│   └── docker-compose.dev.yml      # 开发环境专用编排配置
├── scripts/                        # 运维与初始化脚本
│   ├── init-db.sql                 # 数据库初始化表结构与索引
│   ├── seed-resources.js           # 资源种子数据导入脚本
│   └── health-check.sh             # 批量链接可访问性探测脚本
├── docs/                           # 完整文档目录（用户指南、部署、开发、运维）
├── .env.example                    # 环境变量配置模板
├── .eslintrc.js                    # 代码风格检查配置
├── .prettierrc                     # 代码格式化配置
├── package.json                    # 项目依赖与 monorepo 工作区配置
├── tsconfig.json                   # TypeScript 全局编译配置
└── README.md                       # 项目入口文档（本文件）
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制到个人账户下，随后使用 git clone 将 fork 后的仓库拉取到本地开发环境。建议在克隆后执行 npm install 安装全部依赖，并运行 npm run dev 验证开发环境是否正常工作。

2. 创建新的功能分支并切换到该分支，分支命名应遵循约定，例如 feat/ 前缀表示新功能、fix/ 前缀表示缺陷修复、docs/ 前缀表示文档变更，分支名应简明描述变更内容，例如 feat/add-batch-import。

3. 编写代码或文档后，提交前需运行 npm run lint 检查代码风格，运行 npm run test 确保已有测试用例全部通过。若新增功能或修复缺陷，应同步编写对应的单元测试或集成测试用例，测试覆盖率不得低于原有水平。

4. 提交变更时使用规范的提交信息格式，采用 Conventional Commits 约定，提交信息应包含 type、scope 和 subject，例如 fix(search): correct pagination offset calculation。提交后推送至个人远程仓库，并在 GitHub 上向主仓库发起 Pull Request。

5. Pull Request 描述中需清晰说明变更目的、实现方案、测试结果和影响范围。至少一名项目维护者将进行 Code Review，审查通过后由维护者合并至主分支。重大功能变更或架构调整需先通过 Issue 讨论获得共识后再行开发。

## 常见问题

Q：项目启动时提示 Elasticsearch 连接失败，如何解决？

A：请确认 Elasticsearch 服务已正确启动并监听默认端口 9200。若使用 Docker Compose 部署，执行 docker-compose up -d elasticsearch 即可启动容器化的 ES 实例。若使用本地安装的 ES，请检查 config/ 目录下的配置文件中的 host 和 port 参数是否与实际服务地址一致，并确保网络防火墙未阻止相关端口。

Q：批量收录资源时，部分 URL 无法解析出标题和摘要，应如何处理？

A：WebLink Navigator 的解析引擎针对移动端 wap 页面做了特定优化，但不同站点的 HTML 结构存在差异。若解析失败，系统会自动降级使用 URL 中的文件名或路径片段作为资源名称。用户可在管理后台手动编辑资源记录补充标题和摘要。若大量同源 URL 解析失败，可考虑在 crawler 模块中为该站点编写自定义解析适配器。

Q：链接健康检查报告显示大量资源为 404 状态，是否有自动修复机制？

A：目前系统仅提供检测和报告功能，不自动修改或删除记录，以避免误判导致数据丢失。运维人员可定期查看健康检查报告，对失效链接进行人工核实，若确认为永久失效可在管理后台将资源标记为已归档或移除。后续版本计划增加 HTTP 301/302 重定向跟随和链接替换建议功能。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
