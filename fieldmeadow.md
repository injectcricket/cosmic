# LinkHub Mobile Article Collection

LinkHub 是一个面向移动端开发者和内容聚合场景的轻量级文章外链管理与展示系统。该项目定位于帮助中小型团队、独立开发者以及内容运营人员快速构建一个结构清晰、可检索、可分类的技术文章或资讯外链库，解决碎片化知识散落、链接失效、分类混乱等问题。LinkHub 本身不存储文章正文，而是以元数据索引的方式管理外部 URL，并提供一个响应式的移动端展示界面，适用于内部分享、知识沉淀和轻量级 CMS 替代方案。

## 功能概览

- **文章链接索引管理**：支持批量导入、分类标记和状态管理，对每一条外链记录标题、来源、摘要和标签。
- **移动端优先的响应式布局**：界面针对手机屏幕尺寸优化，在平板和桌面端也有良好表现，适配各种阅读场景。
- **分类与标签过滤系统**：可根据预设分类（如前端、后端、运维、AI、移动开发）和自定义标签快速筛选文章列表。
- **全文检索与模糊匹配**：基于标题和摘要提供轻量级本地搜索能力，帮助用户在大量链接中快速定位目标内容。
- **访问热度统计与排序**：记录每条链接被点击的次数，支持按热度、发布时间或更新时间排序。
- **定期链接可用性检查**：内置一个简单的链接探活脚本，可定期检测外链是否仍然有效，并标记失效链接。
- **导入导出与备份功能**：支持 JSON 和 CSV 格式的数据导入导出，便于迁移、备份或与其他系统对接。

## 应用场景

**技术团队内部知识库**：开发团队可以将日常阅读的优秀技术文章、解决方案、踩坑记录等外链统一录入 LinkHub，形成团队共享的知识索引，减少重复搜索和沟通成本。

**个人开发者学习笔记**：独立开发者或编程学习者可以将各个技术社区、博客、官方文档中的优质内容通过 LinkHub 集中管理，配合标签系统构建个人学习路径。

**内容运营聚合页**：内容运营人员可以将合作方文章、自媒体稿件、活动通知等外部链接聚合在一个品牌域名下，生成一个简洁的移动端文章列表页，方便对外分发和传播。

**开源项目文档外链附录**：开源项目维护者可以在项目文档或 Wiki 中引用 LinkHub 作为“相关资源”或“延伸阅读”板块，统一管理所有对外部资料的引用。

## 快速开始

以下命令将项目克隆到本地、安装依赖并启动开发服务器。

```bash
git clone https://github.com/your-org/linkhub.git
cd linkhub
npm install
npm run dev
```

启动成功后，访问 http://localhost:5173 即可看到文章列表首页。默认会加载示例数据，您可以在 `src/data` 目录下替换为自己的链接数据文件。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 项目运行时环境，建议使用 LTS 版本 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理工具，用于安装项目依赖 |
| Vue.js | >= 3.4.0 | 前端核心框架，采用 Composition API 开发 |
| Vite | >= 5.0.0 | 构建工具和开发服务器，提供快速热更新 |
| SQLite3 | >= 5.1.0 | 本地数据存储引擎（开发环境使用，生产可切换为 PostgreSQL） |
| TypeScript | >= 5.3.0 | 类型系统支持，所有源码使用 TypeScript 编写 |
| ESLint | >= 8.0.0 | 代码规范检查工具，配合 Prettier 统一风格 |
| Vitest | >= 1.0.0 | 单元测试和组件测试框架 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何录入文章、管理分类、使用搜索和排序功能 |
| 部署指南 | /docs/deployment/ | 如何将 LinkHub 部署到生产服务器（Nginx、Docker、Vercel） |
| 开发者文档 | /docs/developer/ | 项目架构说明、API 设计、数据模型、如何二次开发 |
| 运维手册 | /docs/operations/ | 链接探活配置、数据备份策略、性能调优参数 |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/details/859893.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/082007.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3852.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8099.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/92426.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5014.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7923.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4719.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3591524.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8715371.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9664189.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5284.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7069313.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/46592.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7076949.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/03473.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0967819.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/928681.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/474290.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/28456.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/67877.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/529835.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/283561.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4769.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1281933.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/019010.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/37214.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/676790.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/93881.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6764422.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/115189.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/375944.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3857.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8392110.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/77711.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1810135.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10336.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5268817.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/00508.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/68824.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7862.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6204268.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5791113.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/744225.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1342.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0742.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/678881.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8912.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/730105.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6044789.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/50076.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/25679.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/439804.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/745880.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4490.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/84499.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/81391.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/745774.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4249174.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1608045.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1728.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1402.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/33382.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9627291.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7528.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/72199.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/77112.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/04676.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2832.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3602.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2780.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/821886.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3131.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/80250.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4214693.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9531863.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/055174.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2928229.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2880284.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5259.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/868132.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/77387.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3942.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/871298.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/72235.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9705.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0029486.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/84989.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5755742.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2817.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/793551.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2061164.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0804547.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/766011.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/180359.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/680609.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/60029.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6827562.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5578033.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/13427.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/088943.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9003227.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1966897.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4156633.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1599955.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/39973.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4013.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3194284.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/11899.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4888.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7629.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/06456.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/35360.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1281703.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/14727.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4440624.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/753896.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/80337.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/314026.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5801038.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/152111.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/074946.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1781.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7935436.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/382348.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/947382.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/01864.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/39966.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/915746.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/759923.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2015381.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/15749.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3088.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/54005.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3624790.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0263502.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4515.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4334.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4113.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/51776.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/694404.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/55560.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4077305.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2435.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0852510.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4364.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/57516.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9629724.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1714673.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/75348.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7092.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2192042.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7853629.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4809640.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5353244.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7531.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5348.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6367.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0330.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8530.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/391391.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/18426.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6968.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/09361.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/96087.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/37110.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/90720.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8124784.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/55716.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4795960.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4241749.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/70304.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8431.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/613575.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0407.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/809906.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/33514.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/967500.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1779999.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/197111.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/413450.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/72167.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/52688.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/920633.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/76848.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8746.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1120.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/45786.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/648751.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/122051.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7920.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/031473.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1706507.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2989.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3452.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/503574.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/357692.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/615855.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9498887.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/29579.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7140833.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/334717.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/872154.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/68415.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4546.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1449454.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/88390.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0648255.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/53118.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7814.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/465045.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1033.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/557496.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4481621.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/97201.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/828221.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3248.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4965.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/182001.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2043.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0592.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4510131.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4860.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6668.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/70480.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7420.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/101869.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/721489.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/02479.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/44723.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4341385.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0169305.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1953.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7329260.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/699779.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2080.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/55794.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8494575.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/023356.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/519264.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5188250.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/272770.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/434167.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4803.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8901444.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6740789.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4364886.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10892.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0304900.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/646248.sHtML

## 项目结构

```
linkhub/
├── public/                          # 静态资源目录，存放 favicon 和 robots.txt
├── src/
│   ├── api/                         # 后端 API 路由层（基于 Express 或 Nitro）
│   │   ├── articles.ts              # 文章增删改查接口
│   │   ├── categories.ts            # 分类管理接口
│   │   └── health.ts                # 健康检查接口
│   ├── components/                  # Vue 可复用组件库
│   │   ├── ArticleList.vue          # 文章列表主组件，支持分页和排序
│   │   ├── FilterPanel.vue          # 侧边栏或顶部的分类/标签过滤面板
│   │   ├── SearchBar.vue            # 全局搜索输入框组件
│   │   └── StatusBadge.vue          # 显示文章状态（有效/失效/待检查）
│   ├── composables/                 # Vue Composition API 逻辑复用函数
│   │   ├── useArticles.ts           # 文章数据获取、缓存和状态管理逻辑
│   │   ├── useFilter.ts             # 过滤条件和排序逻辑
│   │   └── usePagination.ts         # 分页逻辑封装
│   ├── layouts/                     # 页面布局模板
│   │   ├── default.vue              # 默认布局，含头部导航和底部信息
│   │   └── fullscreen.vue           # 全屏沉浸式阅读布局
│   ├── pages/                       # 路由页面文件（基于 Vue Router）
│   │   ├── index.vue                # 首页，展示所有文章列表
│   │   ├── category/[id].vue        # 按分类筛选的文章列表页
│   │   └── search.vue               # 搜索结果页面
│   ├── stores/                      # Pinia 状态管理仓库
│   │   ├── articleStore.ts          # 文章列表、当前文章、加载状态等
│   │   └── settingStore.ts          # 用户偏好设置（主题、每页条数等）
│   ├── styles/                      # 全局样式文件（SCSS 变量、重置样式）
│   ├── types/                       # TypeScript 类型定义文件
│   │   ├── article.d.ts             # 文章数据结构接口定义
│   │   └── api.d.ts                 # API 请求响应类型定义
│   ├── utils/                       # 工具函数目录
│   │   ├── formatter.ts             # 日期格式化、字数统计等工具
│   │   ├── validator.ts             # URL 校验、表单验证规则
│   │   └── storage.ts               # 本地存储封装（localStorage 读写）
│   └── main.ts                      # 应用入口文件，初始化 Vue 实例
├── tests/                           # 测试文件目录
│   ├── unit/                        # 单元测试（Vitest）
│   └── e2e/                         # 端到端测试（Playwright）
├── .env.example                     # 环境变量示例文件
├── .eslintrc.cjs                    # ESLint 配置文件
├── .prettierrc                      # Prettier 代码格式化配置
├── index.html                       # HTML 模板文件
├── package.json                     # 项目依赖及脚本定义
├── tsconfig.json                    # TypeScript 编译器配置
├── vite.config.ts                   # Vite 构建工具配置
└── README.md                        # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎并感谢任何形式的贡献，包括但不限于功能建议、Bug 报告、代码提交和文档改进。请遵循以下流程参与贡献。

1. 在 GitHub 上 Fork 本仓库，并在本地克隆您 Fork 后的副本。创建新的功能分支时，请使用 `feature/描述` 或 `fix/描述` 的命名格式。
2. 确保您的开发环境满足安装要求，并成功运行项目。在修改代码前，建议先阅读 `/docs/developer/` 目录下的架构说明，以保持代码风格一致性。
3. 提交代码前，请运行 `npm run lint` 和 `npm run test` 确保所有检查通过，并为新增功能编写相应的单元测试或组件测试用例。
4. 提交 Pull Request 时，请清晰描述您解决的问题或新增的功能，并关联相关的 Issue 编号。PR 标题请遵循 Conventional Commits 规范。
5. 所有 PR 需要至少一名维护者审核通过后方可合并。合并后您的贡献将被列入项目贡献者列表。

## 常见问题

**问：LinkHub 必须联网才能使用吗？**

答：LinkHub 本身是一个纯前端 + 本地存储的应用，开发模式下完全离线可用。生产部署时，如果使用 SQLite 作为数据源，也无需外部网络。但文章链接本身指向外部资源，访问这些链接时自然需要网络。如果您配置了远程 API 或 PostgreSQL 数据库，则相关服务需要网络连接。

**问：如何批量导入我已有的文章链接数据？**

答：LinkHub 支持在后台管理界面通过 JSON 或 CSV 文件批量导入。您需要按照项目文档中提供的导入模板格式准备数据，包含标题、URL、分类、标签等字段。导入前系统会进行格式校验并预览前 5 条记录，确认无误后即可一次性写入数据库。

**问：链接可用性检查多久执行一次？如何手动触发？**

答：默认配置下，链接探活脚本每 24 小时自动执行一次，仅检测状态码为 2xx 或 3xx 的链接。您也可以在管理员面板的“系统工具”中点击“立即检查”按钮手动触发。检查结果会在文章列表中通过状态徽章显示，并支持按“失效”状态筛选。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
