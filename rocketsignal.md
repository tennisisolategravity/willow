# MapMobile 外部资源导航系统

MapMobile 外部资源导航系统是一个面向移动端开发者和内容聚合者的轻量级外链管理与导航平台。该项目定位于技术团队、内容运营人员以及个人站长，用于系统化地收集、分类、检索和展示分布在多个二级域名下的海量外部文章链接，解决移动端环境下跨域资源分散、链接失效追踪困难、人工管理效率低下等问题。系统提供统一的数据采集接口、链接状态监控、批量导入导出以及基于标签体系的快速筛选能力，适配日活十万级以下的中小型业务场景。

## 功能概览

- **多源链接统一入库**：支持从多个配置源批量拉取文章类 URL，自动解析元信息并归入统一存储层。
- **链接健康状态探测**：定时对已入库链接进行 HTTP 状态码检测，标记失效、重定向及异常链接，生成可视化报表。
- **标签与分类体系**：允许用户为每条链接自定义多级标签和业务分类，支持模糊检索和组合筛选。
- **移动端自适应展示**：前端页面采用响应式布局，在手机和平板设备上提供流畅的浏览和检索体验。
- **批量操作工具链**：提供命令行脚本和 Web 界面的批量添加、删除、导出功能，支持 CSV 和 JSON 格式互换。
- **访问统计与热度排行**：记录每条链接的被点击次数和最近访问时间，自动生成热门内容排行榜。
- **外部数据源同步**：支持配置多个外部 API 或静态数据源，按周期自动同步新增链接，减少人工维护成本。
- **权限与操作审计**：内置简单的多角色权限控制，记录所有增删改操作日志，便于团队协作和问题追溯。

## 应用场景

- **技术团队内部知识库外链管理**：研发团队在编写技术文档或周报时，需要引用大量外部文章、官方文档和社区讨论。本系统可作为统一的外链收纳平台，避免重复收集和链接失效问题，团队成员可共享标签分类后的高质量资源。
- **内容运营人员批量发布与监控**：内容运营每天需要分发数十篇合作稿件或推广链接到多个移动端页面。系统支持批量导入链接列表，自动检测目标页面是否可访问，并在链接变动时发送告警，显著降低人工检查成本。
- **个人站长构建垂直领域导航站**：个人站长或独立开发者可利用本系统快速搭建一个面向特定领域（如前端开发、AI 工具、开源硬件）的链接导航站点。通过标签筛选和自定义分类，可生成不同主题的聚合页面，提升用户停留时长。
- **数据采集管道中的链接中转层**：在分布式爬虫或数据采集流程中，本系统可作为链接暂存与去重中间件，接收来自多个采集节点的原始 URL，经过去重、状态检查和标签补充后再统一输出给下游存储或分析模块。

## 快速开始

以下操作步骤适用于 Linux / macOS 环境，确保已安装 Git 和 Node.js 18.x 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/mapmobile-nav.git
cd mapmobile-nav

# 安装项目依赖
npm install

# 复制环境变量示例文件并填写必要配置
cp .env.example .env

# 初始化数据库结构（使用 SQLite 作为默认存储）
npm run db:init

# 启动开发服务器（默认监听 3000 端口）
npm run dev
```

访问 http://localhost:3000 即可进入系统首页。生产环境部署请参考 `docs/deployment.md` 使用 PM2 或 Docker 方式运行。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 运行时环境，推荐使用 LTS 版本 |
| npm 或 yarn | >= 8.0.0 | 包管理器，用于安装项目依赖 |
| SQLite 3 | 内置 | 默认数据库引擎，无需额外安装；生产环境可切换为 PostgreSQL 12+ |
| Git | >= 2.25.0 | 用于克隆仓库和版本管理 |
| 操作系统 | Linux / macOS / Windows WSL2 | 开发环境推荐 Ubuntu 20.04 或 macOS Monterey 以上 |
| 内存 | >= 512 MB | 最低运行内存，建议 1 GB 以上 |
| 磁盘空间 | >= 200 MB | 用于存放代码、数据库文件和日志 |
| 网络 | 可访问公网 | 用于链接状态检测和外部数据源同步 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `docs/getting-started.md` | 如何快速搭建开发环境、第一次启动需要做什么配置 |
| 功能使用手册 | `docs/user-guide.md` | 如何导入链接、设置标签、查看统计数据和批量操作 |
| 管理员部署手册 | `docs/deployment.md` | 生产环境部署方案、性能调优参数、日志采集策略 |
| API 参考文档 | `docs/api-reference.md` | 所有 RESTful 接口的请求格式、返回字段和认证方式 |
| 数据模型设计 | `docs/data-model.md` | 数据库表结构设计、索引策略和迁移脚本说明 |
| 常见运维操作 | `docs/operations.md` | 链接状态检测频率配置、数据备份恢复、异常处理流程 |

## 资源列表

- http://map.mobile.hcbezg.cn/Article/20920.shtml
- http://map.mobile.fuvxie.cn/Article/470595.shtml
- http://map.mobile.hcbezg.cn/Article/216047.shtml
- http://map.mobile.cvsifc.cn/Article/1477842.shtml
- http://map.mobile.cvsifc.cn/Article/9762.shtml
- http://map.mobile.cvsifc.cn/Article/492188.shtml
- http://map.mobile.fuvxie.cn/Article/67167.shtml
- http://map.mobile.fuvxie.cn/Article/5816.shtml
- http://map.mobile.cvsifc.cn/Article/774795.shtml
- http://map.mobile.fuvxie.cn/Article/028945.shtml
- http://map.mobile.fuvxie.cn/Article/636253.shtml
- http://map.mobile.fuvxie.cn/Article/904838.shtml
- http://map.mobile.hcbezg.cn/Article/742873.shtml
- http://map.mobile.fuvxie.cn/Article/2668.shtml
- http://map.mobile.fuvxie.cn/Article/6179391.shtml
- http://map.mobile.fuvxie.cn/Article/0061588.shtml
- http://map.mobile.cvsifc.cn/Article/8285393.shtml
- http://map.mobile.hcbezg.cn/Article/459914.shtml
- http://map.mobile.fuvxie.cn/Article/21899.shtml
- http://map.mobile.hcbezg.cn/Article/0955.shtml
- http://map.mobile.hcbezg.cn/Article/650208.shtml
- http://map.mobile.fuvxie.cn/Article/07566.shtml
- http://map.mobile.cvsifc.cn/Article/79657.shtml
- http://map.mobile.cvsifc.cn/Article/0752467.shtml
- http://map.mobile.cvsifc.cn/Article/8122.shtml
- http://map.mobile.hcbezg.cn/Article/882242.shtml
- http://map.mobile.cvsifc.cn/Article/0407.shtml
- http://map.mobile.fuvxie.cn/Article/13849.shtml
- http://map.mobile.cvsifc.cn/Article/04201.shtml
- http://map.mobile.cvsifc.cn/Article/0787.shtml
- http://map.mobile.fuvxie.cn/Article/9676206.shtml
- http://map.mobile.hcbezg.cn/Article/564552.shtml
- http://map.mobile.hcbezg.cn/Article/6302160.shtml
- http://map.mobile.cvsifc.cn/Article/86067.shtml
- http://map.mobile.cvsifc.cn/Article/2927448.shtml
- http://map.mobile.cvsifc.cn/Article/906234.shtml
- http://map.mobile.fuvxie.cn/Article/776123.shtml
- http://map.mobile.fuvxie.cn/Article/927591.shtml
- http://map.mobile.cvsifc.cn/Article/7230.shtml
- http://map.mobile.cvsifc.cn/Article/1875972.shtml
- http://map.mobile.cvsifc.cn/Article/706336.shtml
- http://map.mobile.hcbezg.cn/Article/922995.shtml
- http://map.mobile.hcbezg.cn/Article/1537326.shtml
- http://map.mobile.hcbezg.cn/Article/316906.shtml
- http://map.mobile.hcbezg.cn/Article/4562.shtml
- http://map.mobile.cvsifc.cn/Article/69032.shtml
- http://map.mobile.fuvxie.cn/Article/397298.shtml
- http://map.mobile.hcbezg.cn/Article/6421.shtml
- http://map.mobile.cvsifc.cn/Article/4104936.shtml
- http://map.mobile.cvsifc.cn/Article/1383.shtml
- http://map.mobile.hcbezg.cn/Article/39605.shtml
- http://map.mobile.cvsifc.cn/Article/1458.shtml
- http://map.mobile.fuvxie.cn/Article/23608.shtml
- http://map.mobile.cvsifc.cn/Article/1987.shtml
- http://map.mobile.hcbezg.cn/Article/78022.shtml
- http://map.mobile.cvsifc.cn/Article/2794.shtml
- http://map.mobile.hcbezg.cn/Article/0035.shtml
- http://map.mobile.hcbezg.cn/Article/38866.shtml
- http://map.mobile.hcbezg.cn/Article/3069.shtml
- http://map.mobile.fuvxie.cn/Article/492113.shtml
- http://map.mobile.fuvxie.cn/Article/4541.shtml
- http://map.mobile.fuvxie.cn/Article/5147965.shtml
- http://map.mobile.hcbezg.cn/Article/7281.shtml
- http://map.mobile.cvsifc.cn/Article/3524.shtml
- http://map.mobile.cvsifc.cn/Article/4163439.shtml
- http://map.mobile.hcbezg.cn/Article/2967.shtml
- http://map.mobile.cvsifc.cn/Article/37108.shtml
- http://map.mobile.fuvxie.cn/Article/5896.shtml
- http://map.mobile.hcbezg.cn/Article/23483.shtml
- http://map.mobile.cvsifc.cn/Article/7471.shtml
- http://map.mobile.hcbezg.cn/Article/43695.shtml
- http://map.mobile.fuvxie.cn/Article/0371.shtml
- http://map.mobile.fuvxie.cn/Article/022412.shtml
- http://map.mobile.fuvxie.cn/Article/7773708.shtml
- http://map.mobile.fuvxie.cn/Article/64380.shtml
- http://map.mobile.fuvxie.cn/Article/402024.shtml
- http://map.mobile.cvsifc.cn/Article/2448.shtml
- http://map.mobile.hcbezg.cn/Article/7632245.shtml
- http://map.mobile.hcbezg.cn/Article/120507.shtml
- http://map.mobile.fuvxie.cn/Article/408845.shtml
- http://map.mobile.hcbezg.cn/Article/75510.shtml
- http://map.mobile.cvsifc.cn/Article/602311.shtml
- http://map.mobile.hcbezg.cn/Article/40456.shtml
- http://map.mobile.cvsifc.cn/Article/5286477.shtml
- http://map.mobile.hcbezg.cn/Article/34590.shtml
- http://map.mobile.fuvxie.cn/Article/5310.shtml
- http://map.mobile.hcbezg.cn/Article/9781916.shtml
- http://map.mobile.hcbezg.cn/Article/4131339.shtml
- http://map.mobile.cvsifc.cn/Article/2229.shtml
- http://map.mobile.fuvxie.cn/Article/869281.shtml
- http://map.mobile.cvsifc.cn/Article/3831129.shtml
- http://map.mobile.cvsifc.cn/Article/04855.shtml
- http://map.mobile.fuvxie.cn/Article/5419.shtml
- http://map.mobile.fuvxie.cn/Article/63616.shtml
- http://map.mobile.fuvxie.cn/Article/2699.shtml
- http://map.mobile.hcbezg.cn/Article/13274.shtml
- http://map.mobile.hcbezg.cn/Article/5638.shtml
- http://map.mobile.cvsifc.cn/Article/9409.shtml
- http://map.mobile.cvsifc.cn/Article/7879080.shtml
- http://map.mobile.fuvxie.cn/Article/6867.shtml
- http://map.mobile.fuvxie.cn/Article/358760.shtml
- http://map.mobile.fuvxie.cn/Article/7923.shtml
- http://map.mobile.fuvxie.cn/Article/2422.shtml
- http://map.mobile.fuvxie.cn/Article/734777.shtml
- http://map.mobile.fuvxie.cn/Article/1872609.shtml
- http://map.mobile.fuvxie.cn/Article/049077.shtml
- http://map.mobile.hcbezg.cn/Article/73759.shtml
- http://map.mobile.hcbezg.cn/Article/9944306.shtml
- http://map.mobile.hcbezg.cn/Article/1341666.shtml
- http://map.mobile.cvsifc.cn/Article/051407.shtml
- http://map.mobile.fuvxie.cn/Article/49693.shtml
- http://map.mobile.cvsifc.cn/Article/6118.shtml
- http://map.mobile.hcbezg.cn/Article/4365304.shtml
- http://map.mobile.hcbezg.cn/Article/455872.shtml
- http://map.mobile.cvsifc.cn/Article/636613.shtml
- http://map.mobile.hcbezg.cn/Article/425925.shtml
- http://map.mobile.hcbezg.cn/Article/60701.shtml
- http://map.mobile.cvsifc.cn/Article/113663.shtml
- http://map.mobile.hcbezg.cn/Article/1426.shtml
- http://map.mobile.cvsifc.cn/Article/52138.shtml
- http://map.mobile.fuvxie.cn/Article/777864.shtml
- http://map.mobile.cvsifc.cn/Article/8760.shtml
- http://map.mobile.hcbezg.cn/Article/31075.shtml
- http://map.mobile.fuvxie.cn/Article/562209.shtml
- http://map.mobile.cvsifc.cn/Article/85548.shtml
- http://map.mobile.fuvxie.cn/Article/22061.shtml
- http://map.mobile.hcbezg.cn/Article/38526.shtml
- http://map.mobile.fuvxie.cn/Article/507812.shtml
- http://map.mobile.cvsifc.cn/Article/3658.shtml
- http://map.mobile.fuvxie.cn/Article/4451940.shtml
- http://map.mobile.fuvxie.cn/Article/1437.shtml
- http://map.mobile.cvsifc.cn/Article/1663357.shtml
- http://map.mobile.hcbezg.cn/Article/2638429.shtml
- http://map.mobile.cvsifc.cn/Article/2061.shtml
- http://map.mobile.cvsifc.cn/Article/8137739.shtml
- http://map.mobile.fuvxie.cn/Article/2979805.shtml
- http://map.mobile.hcbezg.cn/Article/2962289.shtml
- http://map.mobile.fuvxie.cn/Article/797682.shtml
- http://map.mobile.hcbezg.cn/Article/6685192.shtml
- http://map.mobile.cvsifc.cn/Article/096797.shtml
- http://map.mobile.hcbezg.cn/Article/55147.shtml
- http://map.mobile.cvsifc.cn/Article/11807.shtml
- http://map.mobile.hcbezg.cn/Article/6203796.shtml
- http://map.mobile.cvsifc.cn/Article/5999005.shtml
- http://map.mobile.fuvxie.cn/Article/0755.shtml
- http://map.mobile.fuvxie.cn/Article/6611.shtml
- http://map.mobile.fuvxie.cn/Article/3907.shtml
- http://map.mobile.hcbezg.cn/Article/14977.shtml
- http://map.mobile.cvsifc.cn/Article/44323.shtml
- http://map.mobile.cvsifc.cn/Article/2902.shtml
- http://map.mobile.cvsifc.cn/Article/611003.shtml
- http://map.mobile.fuvxie.cn/Article/12253.shtml
- http://map.mobile.hcbezg.cn/Article/861287.shtml
- http://map.mobile.cvsifc.cn/Article/85746.shtml
- http://map.mobile.cvsifc.cn/Article/3603.shtml
- http://map.mobile.hcbezg.cn/Article/6428686.shtml
- http://map.mobile.cvsifc.cn/Article/0675.shtml
- http://map.mobile.fuvxie.cn/Article/0737.shtml
- http://map.mobile.hcbezg.cn/Article/370311.shtml
- http://map.mobile.fuvxie.cn/Article/25563.shtml
- http://map.mobile.fuvxie.cn/Article/64175.shtml
- http://map.mobile.cvsifc.cn/Article/485799.shtml
- http://map.mobile.cvsifc.cn/Article/8070.shtml
- http://map.mobile.cvsifc.cn/Article/6265.shtml
- http://map.mobile.fuvxie.cn/Article/28037.shtml
- http://map.mobile.hcbezg.cn/Article/487177.shtml
- http://map.mobile.hcbezg.cn/Article/60568.shtml
- http://map.mobile.cvsifc.cn/Article/12195.shtml
- http://map.mobile.fuvxie.cn/Article/1914.shtml
- http://map.mobile.cvsifc.cn/Article/6217.shtml
- http://map.mobile.cvsifc.cn/Article/8673960.shtml
- http://map.mobile.hcbezg.cn/Article/5686332.shtml
- http://map.mobile.hcbezg.cn/Article/9519999.shtml
- http://map.mobile.cvsifc.cn/Article/739643.shtml
- http://map.mobile.fuvxie.cn/Article/3099795.shtml
- http://map.mobile.hcbezg.cn/Article/64928.shtml
- http://map.mobile.fuvxie.cn/Article/092522.shtml
- http://map.mobile.hcbezg.cn/Article/6154313.shtml
- http://map.mobile.hcbezg.cn/Article/1816281.shtml
- http://map.mobile.cvsifc.cn/Article/857350.shtml
- http://map.mobile.fuvxie.cn/Article/18237.shtml
- http://map.mobile.fuvxie.cn/Article/3453.shtml
- http://map.mobile.fuvxie.cn/Article/54524.shtml
- http://map.mobile.hcbezg.cn/Article/5749.shtml
- http://map.mobile.cvsifc.cn/Article/96979.shtml
- http://map.mobile.cvsifc.cn/Article/493068.shtml
- http://map.mobile.cvsifc.cn/Article/61387.shtml
- http://map.mobile.hcbezg.cn/Article/5577821.shtml
- http://map.mobile.fuvxie.cn/Article/6703117.shtml
- http://map.mobile.hcbezg.cn/Article/457979.shtml
- http://map.mobile.cvsifc.cn/Article/4859.shtml
- http://map.mobile.cvsifc.cn/Article/6374.shtml
- http://map.mobile.hcbezg.cn/Article/9726940.shtml
- http://map.mobile.cvsifc.cn/Article/68808.shtml
- http://map.mobile.fuvxie.cn/Article/464615.shtml
- http://map.mobile.hcbezg.cn/Article/8075.shtml
- http://map.mobile.hcbezg.cn/Article/6494.shtml
- http://map.mobile.fuvxie.cn/Article/961223.shtml
- http://map.mobile.hcbezg.cn/Article/2653129.shtml
- http://map.mobile.hcbezg.cn/Article/3784.shtml
- http://map.mobile.fuvxie.cn/Article/0501.shtml
- http://map.mobile.fuvxie.cn/Article/303829.shtml
- http://map.mobile.fuvxie.cn/Article/7652631.shtml
- http://map.mobile.hcbezg.cn/Article/3358.shtml
- http://map.mobile.fuvxie.cn/Article/78767.shtml
- http://map.mobile.fuvxie.cn/Article/23629.shtml
- http://map.mobile.cvsifc.cn/Article/1042374.shtml
- http://map.mobile.hcbezg.cn/Article/73504.shtml
- http://map.mobile.hcbezg.cn/Article/400717.shtml
- http://map.mobile.hcbezg.cn/Article/7625.shtml
- http://map.mobile.cvsifc.cn/Article/170311.shtml
- http://map.mobile.fuvxie.cn/Article/2975.shtml
- http://map.mobile.hcbezg.cn/Article/84556.shtml
- http://map.mobile.fuvxie.cn/Article/1315900.shtml
- http://map.mobile.hcbezg.cn/Article/8446.shtml
- http://map.mobile.hcbezg.cn/Article/47467.shtml
- http://map.mobile.cvsifc.cn/Article/349221.shtml
- http://map.mobile.hcbezg.cn/Article/43531.shtml
- http://map.mobile.hcbezg.cn/Article/8276349.shtml
- http://map.mobile.fuvxie.cn/Article/044213.shtml
- http://map.mobile.fuvxie.cn/Article/044064.shtml
- http://map.mobile.fuvxie.cn/Article/67667.shtml
- http://map.mobile.cvsifc.cn/Article/967238.shtml
- http://map.mobile.cvsifc.cn/Article/70597.shtml
- http://map.mobile.cvsifc.cn/Article/7126.shtml
- http://map.mobile.fuvxie.cn/Article/6904337.shtml
- http://map.mobile.fuvxie.cn/Article/23431.shtml
- http://map.mobile.cvsifc.cn/Article/7102.shtml
- http://map.mobile.hcbezg.cn/Article/3407178.shtml
- http://map.mobile.cvsifc.cn/Article/45669.shtml
- http://map.mobile.fuvxie.cn/Article/2840343.shtml
- http://map.mobile.fuvxie.cn/Article/7061.shtml
- http://map.mobile.fuvxie.cn/Article/1166321.shtml
- http://map.mobile.cvsifc.cn/Article/99703.shtml
- http://map.mobile.cvsifc.cn/Article/9786.shtml
- http://map.mobile.fuvxie.cn/Article/51180.shtml
- http://map.mobile.fuvxie.cn/Article/9197126.shtml
- http://map.mobile.cvsifc.cn/Article/9645.shtml
- http://map.mobile.hcbezg.cn/Article/86726.shtml
- http://map.mobile.hcbezg.cn/Article/72914.shtml
- http://map.mobile.fuvxie.cn/Article/82284.shtml
- http://map.mobile.cvsifc.cn/Article/146471.shtml
- http://map.mobile.hcbezg.cn/Article/8739051.shtml
- http://map.mobile.cvsifc.cn/Article/8819.shtml
- http://map.mobile.cvsifc.cn/Article/332276.shtml
- http://map.mobile.fuvxie.cn/Article/3750050.shtml
- http://map.mobile.fuvxie.cn/Article/2628938.shtml
- http://map.mobile.fuvxie.cn/Article/06379.shtml
- http://map.mobile.cvsifc.cn/Article/00126.shtml
- http://map.mobile.cvsifc.cn/Article/5022301.shtml

## 项目结构

```
mapmobile-nav/
├── src/                                # 核心源代码目录
│   ├── controllers/                    # 控制器层，处理HTTP请求路由逻辑
│   │   ├── linkController.js          # 链接增删改查及状态检测
│   │   └── tagController.js           # 标签与分类管理
│   ├── services/                       # 业务服务层，封装核心业务逻辑
│   │   ├── linkHealthService.js       # 链接健康状态探测与定时任务
│   │   ├── importService.js           # 批量导入与外部源同步
│   │   └── statsService.js            # 访问统计与排行计算
│   ├── models/                         # 数据模型层，定义数据库表结构与ORM映射
│   │   ├── LinkModel.js               # 链接实体，包含URL、标题、状态等字段
│   │   ├── TagModel.js                # 标签实体，支持层级分类
│   │   └── AuditLogModel.js           # 操作审计日志
│   ├── middleware/                     # 中间件，包含认证、日志、错误处理等
│   │   ├── auth.js                    # 基于JWT的身份校验
│   │   └── logger.js                  # 请求日志记录中间件
│   ├── routes/                         # 路由定义，将URL映射至对应控制器
│   │   ├── api.js                     # RESTful API路由聚合
│   │   └── web.js                     # 前端页面路由（SSR或模板渲染）
│   ├── utils/                          # 通用工具函数
│   │   ├── httpClient.js              # 封装axios用于外部链接检测
│   │   └── validator.js               # URL格式校验与规范化工具
│   └── app.js                          # 应用入口文件，初始化Express服务
├── config/                             # 配置文件目录，支持多环境
│   ├── default.json                    # 默认配置（端口、数据库、日志级别）
│   ├── production.json                 # 生产环境覆盖配置
│   └── development.json                # 开发环境覆盖配置
├── db/                                 # 数据库相关文件
│   ├── migrations/                     # 数据库迁移脚本（按版本号递增）
│   │   └── 001_init_schema.sql        # 初始化建表脚本
│   └── seed/                           # 种子数据，用于开发环境预置标签和分类
│       └── defaultTags.json
├── public/                             # 静态资源目录（前端CSS、JS、图片）
│   ├── css/
│   ├── js/
│   └── images/
├── views/                              # 前端模板文件（EJS或Pug）
│   ├── index.ejs
│   ├── links.ejs
│   └── stats.ejs
├── scripts/                            # 运维与工具脚本
│   ├── healthCheck.js                 # 手动触发全量链接检测
│   ├── exportData.js                  # 导出链接数据为CSV/JSON
│   └── syncExternal.js                # 从外部数据源同步新链接
├── tests/                              # 单元测试与集成测试
│   ├── unit/
│   └── integration/
├── docs/                               # 项目文档（详见文档导航章节）
│   ├── getting-started.md
│   ├── user-guide.md
│   ├── deployment.md
│   ├── api-reference.md
│   ├── data-model.md
│   └── operations.md
├── .env.example                        # 环境变量配置示例
├── .gitignore
├── package.json                        # npm 项目依赖与脚本定义
├── README.md                           # 本文件
└── LICENSE                             # MIT 许可证
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账户，然后将 Fork 后的仓库克隆到本地开发环境，配置 upstream 指向原始仓库以便同步更新。
2. 创建新的功能分支，分支命名格式为 `feature/功能简述` 或 `fix/问题简述`，避免直接在 main 分支上修改。
3. 编写代码时遵循项目已配置的 ESLint 和 Prettier 规则，保持代码风格统一；新增功能需同步编写对应的单元测试，测试覆盖率不低于 80%。
4. 提交代码前运行 `npm run test` 确保所有测试用例通过，运行 `npm run lint` 检查代码规范；提交信息采用 Conventional Commits 格式（如 `feat: 添加链接批量导入功能`）。
5. 向原始仓库的 main 分支发起 Pull Request，在描述中清晰说明改动目的、涉及模块以及测试情况；PR 至少需要一位维护者审核通过后方可合并。

## 常见问题

**Q: 系统支持导入的链接数量上限是多少？单次批量导入最多能处理多少条？**

A: 系统本身不设硬性上限，存储能力取决于所选的数据库（SQLite 建议单表不超过百万级，PostgreSQL 可支撑千万级以上）。单次批量导入通过流式处理可支持 10 万条以下的文件，超过该数量建议分批导入或使用命令行脚本分批执行。内存占用方面，每万条链接约消耗 50-80 MB 内存。

**Q: 链接健康状态检测会影响源站吗？检测频率如何设置？**

A: 系统默认使用 HEAD 请求检测链接可用性，只获取响应头，不下载完整页面内容，对源站服务器压力极小。默认检测间隔为每 24 小时一次，可在 `config/default.json` 中通过 `healthCheck.interval` 参数调整。对于频繁返回 429 或 503 的源站，系统会自动降低检测频率并加入冷静期列表。

**Q: 如何从现有系统迁移数据到本平台？是否支持自定义字段？**

A: 系统提供了通用的 CSV 和 JSON 导入接口，CSV 表头需包含 `url`、`title`、`tags` 等基础列，`tags` 列允许多个标签用逗号分隔。如需存储额外的自定义字段（如作者、发布时间、所属项目），可通过扩展 `LinkModel` 中的 `metadata` JSON 字段来实现，该字段支持任意键值对存储，且可参与高级检索。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
