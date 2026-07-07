# MapLink 聚合索引服务

MapLink 聚合索引服务是一个面向技术文档、资讯内容与公开数据资源的轻量级外链汇聚平台。该项目定位于为开发者、研究人员及内容策展者提供结构化的 URL 索引管理能力，通过分类导航与快速检索机制，帮助用户从分散的移动端信息源中高效定位目标文章。

项目本身不存储原始内容，仅维护 URL 元数据与分类标签体系，适用于个人知识库构建、团队资源共享或垂直领域站点导航等场景。MapLink 采用静态生成方式，支持高并发访问，部署成本极低。

## 功能概览

批量导入与自动去重：支持通过文本文件或 API 批量提交 URL，系统自动识别重复条目并合并冲突记录。

多维度标签分类：每条链接可关联多个自定义标签，支持按主题、来源域名、时间范围等多维度筛选。

全文检索与模糊匹配：基于倒排索引实现标题与摘要的快速搜索，支持中文分词与拼音首字母检索。

访问状态监控：定时检测链接可达性，自动标记失效链接并生成报表，支持邮件告警。

自定义输出模板：提供 JSON、XML 及 HTML 三种导出格式，允许用户通过 Handlebars 模板自定义展示样式。

访问统计与热度排序：记录链接点击次数与来源 IP 去重，支持按七日热度、总访问量排序。

开放 API 接口：提供 RESTful API 供第三方系统调用，支持查询、添加、更新及删除操作。

## 应用场景

技术博客聚合站点：开发者可将个人技术博客、社区教程及官方文档链接统一收录，通过标签快速筛选特定框架或语言的相关文章，避免重复搜索。

团队内部知识库导航：企业内部团队可将常用运维手册、设计规范、项目文档等链接集中管理，结合访问监控功能及时发现失效资源，保障知识库可用性。

学术文献索引工具：研究人员可批量导入论文预印本、数据集页面及工具库地址，按研究方向、期刊或作者分类，辅助文献调研与实验复现。

运维监控仪表盘补充：运维人员将内部监控面板、日志查询入口及报警管理页面的链接整合至 MapLink，配合状态检测功能快速定位服务异常。

## 快速开始

以下命令演示如何在 Linux 或 macOS 环境下完成 MapLink 的克隆、安装与启动。

```bash
git clone https://github.com/maplink/maplink-indexer.git
cd maplink-indexer
npm install
npm run build
npm start
```

执行完成后，服务默认监听 3000 端口，可通过 http://localhost:3000 访问 Web 管理界面。生产环境建议通过环境变量配置数据库连接与监听地址。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 运行时环境，建议使用 LTS 版本 |
| npm | >= 9.0.0 | 包管理工具，随 Node.js 一同安装 |
| SQLite3 | >= 3.38.0 | 默认嵌入式数据库，无需额外部署 |
| Redis | >= 6.2.0 （可选） | 用于缓存与会话存储，提升高并发性能 |
| Nginx | >= 1.20.0 （可选） | 推荐作为反向代理，处理静态资源与负载均衡 |
| 系统内存 | >= 512 MB | 最低运行内存，建议 1 GB 以上 |
| 磁盘空间 | >= 1 GB | 用于存储索引数据与日志文件 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，生产环境推荐 Linux |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/quick-start.md | 如何五步内完成 MapLink 的首次部署与数据导入 |
| 配置手册 | /docs/configuration.md | 环境变量、数据库连接、缓存策略与日志级别如何调整 |
| API 参考 | /docs/api-reference.md | 所有 RESTful 接口的请求参数、返回格式与错误码定义 |
| 运维指南 | /docs/operations.md | 备份恢复、性能调优、监控告警与故障排查方案 |

## 资源列表

- http://map.mobile.cvsifc.cn/Article/32104.shtml
- http://map.mobile.fuvxie.cn/Article/5640902.shtml
- http://map.mobile.fuvxie.cn/Article/1167128.shtml
- http://map.mobile.hcbezg.cn/Article/588985.shtml
- http://map.mobile.hcbezg.cn/Article/225323.shtml
- http://map.mobile.hcbezg.cn/Article/6124972.shtml
- http://map.mobile.hcbezg.cn/Article/1505.shtml
- http://map.mobile.hcbezg.cn/Article/552297.shtml
- http://map.mobile.cvsifc.cn/Article/1421218.shtml
- http://map.mobile.fuvxie.cn/Article/8989.shtml
- http://map.mobile.cvsifc.cn/Article/803573.shtml
- http://map.mobile.cvsifc.cn/Article/83512.shtml
- http://map.mobile.hcbezg.cn/Article/51233.shtml
- http://map.mobile.fuvxie.cn/Article/349984.shtml
- http://map.mobile.hcbezg.cn/Article/2075.shtml
- http://map.mobile.hcbezg.cn/Article/63383.shtml
- http://map.mobile.hcbezg.cn/Article/372653.shtml
- http://map.mobile.hcbezg.cn/Article/3491.shtml
- http://map.mobile.fuvxie.cn/Article/659939.shtml
- http://map.mobile.cvsifc.cn/Article/70900.shtml
- http://map.mobile.cvsifc.cn/Article/91518.shtml
- http://map.mobile.fuvxie.cn/Article/42856.shtml
- http://map.mobile.hcbezg.cn/Article/674202.shtml
- http://map.mobile.cvsifc.cn/Article/0999.shtml
- http://map.mobile.hcbezg.cn/Article/4528.shtml
- http://map.mobile.fuvxie.cn/Article/40473.shtml
- http://map.mobile.cvsifc.cn/Article/9986.shtml
- http://map.mobile.cvsifc.cn/Article/9962.shtml
- http://map.mobile.fuvxie.cn/Article/024084.shtml
- http://map.mobile.cvsifc.cn/Article/8062899.shtml
- http://map.mobile.hcbezg.cn/Article/9213047.shtml
- http://map.mobile.hcbezg.cn/Article/5641.shtml
- http://map.mobile.cvsifc.cn/Article/8873027.shtml
- http://map.mobile.fuvxie.cn/Article/394605.shtml
- http://map.mobile.fuvxie.cn/Article/3945349.shtml
- http://map.mobile.cvsifc.cn/Article/3066.shtml
- http://map.mobile.hcbezg.cn/Article/738491.shtml
- http://map.mobile.cvsifc.cn/Article/031352.shtml
- http://map.mobile.hcbezg.cn/Article/59420.shtml
- http://map.mobile.cvsifc.cn/Article/8084.shtml
- http://map.mobile.hcbezg.cn/Article/6385.shtml
- http://map.mobile.cvsifc.cn/Article/741398.shtml
- http://map.mobile.fuvxie.cn/Article/39373.shtml
- http://map.mobile.hcbezg.cn/Article/5628263.shtml
- http://map.mobile.hcbezg.cn/Article/34126.shtml
- http://map.mobile.hcbezg.cn/Article/379456.shtml
- http://map.mobile.fuvxie.cn/Article/43562.shtml
- http://map.mobile.fuvxie.cn/Article/2442.shtml
- http://map.mobile.hcbezg.cn/Article/08554.shtml
- http://map.mobile.hcbezg.cn/Article/449426.shtml
- http://map.mobile.fuvxie.cn/Article/5508779.shtml
- http://map.mobile.cvsifc.cn/Article/802973.shtml
- http://map.mobile.fuvxie.cn/Article/01989.shtml
- http://map.mobile.cvsifc.cn/Article/06529.shtml
- http://map.mobile.cvsifc.cn/Article/746327.shtml
- http://map.mobile.fuvxie.cn/Article/4961128.shtml
- http://map.mobile.fuvxie.cn/Article/2050919.shtml
- http://map.mobile.fuvxie.cn/Article/58122.shtml
- http://map.mobile.fuvxie.cn/Article/235865.shtml
- http://map.mobile.hcbezg.cn/Article/3641.shtml
- http://map.mobile.fuvxie.cn/Article/5850183.shtml
- http://map.mobile.hcbezg.cn/Article/92564.shtml
- http://map.mobile.cvsifc.cn/Article/6794683.shtml
- http://map.mobile.cvsifc.cn/Article/5894713.shtml
- http://map.mobile.fuvxie.cn/Article/6884.shtml
- http://map.mobile.cvsifc.cn/Article/3288.shtml
- http://map.mobile.hcbezg.cn/Article/5745.shtml
- http://map.mobile.hcbezg.cn/Article/0353.shtml
- http://map.mobile.hcbezg.cn/Article/4911.shtml
- http://map.mobile.hcbezg.cn/Article/424427.shtml
- http://map.mobile.cvsifc.cn/Article/49854.shtml
- http://map.mobile.hcbezg.cn/Article/767928.shtml
- http://map.mobile.cvsifc.cn/Article/87654.shtml
- http://map.mobile.hcbezg.cn/Article/536530.shtml
- http://map.mobile.cvsifc.cn/Article/9768670.shtml
- http://map.mobile.cvsifc.cn/Article/551735.shtml
- http://map.mobile.hcbezg.cn/Article/7958406.shtml
- http://map.mobile.fuvxie.cn/Article/618566.shtml
- http://map.mobile.fuvxie.cn/Article/6249.shtml
- http://map.mobile.fuvxie.cn/Article/1987.shtml
- http://map.mobile.cvsifc.cn/Article/4555.shtml
- http://map.mobile.fuvxie.cn/Article/1558.shtml
- http://map.mobile.hcbezg.cn/Article/7892.shtml
- http://map.mobile.fuvxie.cn/Article/217771.shtml
- http://map.mobile.fuvxie.cn/Article/1084661.shtml
- http://map.mobile.fuvxie.cn/Article/4015.shtml
- http://map.mobile.hcbezg.cn/Article/1263982.shtml
- http://map.mobile.cvsifc.cn/Article/51545.shtml
- http://map.mobile.cvsifc.cn/Article/84900.shtml
- http://map.mobile.hcbezg.cn/Article/2631.shtml
- http://map.mobile.cvsifc.cn/Article/2521.shtml
- http://map.mobile.hcbezg.cn/Article/489654.shtml
- http://map.mobile.fuvxie.cn/Article/204439.shtml
- http://map.mobile.cvsifc.cn/Article/3135.shtml
- http://map.mobile.cvsifc.cn/Article/2513.shtml
- http://map.mobile.cvsifc.cn/Article/2883.shtml
- http://map.mobile.fuvxie.cn/Article/5829.shtml
- http://map.mobile.hcbezg.cn/Article/5688296.shtml
- http://map.mobile.hcbezg.cn/Article/2344.shtml
- http://map.mobile.fuvxie.cn/Article/5656205.shtml
- http://map.mobile.hcbezg.cn/Article/1997490.shtml
- http://map.mobile.fuvxie.cn/Article/9524.shtml
- http://map.mobile.cvsifc.cn/Article/2752.shtml
- http://map.mobile.hcbezg.cn/Article/92691.shtml
- http://map.mobile.hcbezg.cn/Article/1167515.shtml
- http://map.mobile.cvsifc.cn/Article/76690.shtml
- http://map.mobile.hcbezg.cn/Article/732144.shtml
- http://map.mobile.cvsifc.cn/Article/9446.shtml
- http://map.mobile.cvsifc.cn/Article/75212.shtml
- http://map.mobile.fuvxie.cn/Article/2315476.shtml
- http://map.mobile.fuvxie.cn/Article/336636.shtml
- http://map.mobile.hcbezg.cn/Article/1418.shtml
- http://map.mobile.cvsifc.cn/Article/5767376.shtml
- http://map.mobile.fuvxie.cn/Article/5480.shtml
- http://map.mobile.cvsifc.cn/Article/9174.shtml
- http://map.mobile.fuvxie.cn/Article/579617.shtml
- http://map.mobile.hcbezg.cn/Article/6609966.shtml
- http://map.mobile.cvsifc.cn/Article/975965.shtml
- http://map.mobile.cvsifc.cn/Article/9490.shtml
- http://map.mobile.hcbezg.cn/Article/23595.shtml
- http://map.mobile.cvsifc.cn/Article/679874.shtml
- http://map.mobile.hcbezg.cn/Article/10715.shtml
- http://map.mobile.cvsifc.cn/Article/22126.shtml
- http://map.mobile.cvsifc.cn/Article/941250.shtml
- http://map.mobile.fuvxie.cn/Article/850132.shtml
- http://map.mobile.hcbezg.cn/Article/32819.shtml
- http://map.mobile.hcbezg.cn/Article/6107.shtml
- http://map.mobile.hcbezg.cn/Article/2245999.shtml
- http://map.mobile.fuvxie.cn/Article/6784444.shtml
- http://map.mobile.hcbezg.cn/Article/98595.shtml
- http://map.mobile.fuvxie.cn/Article/4586744.shtml
- http://map.mobile.cvsifc.cn/Article/784357.shtml
- http://map.mobile.hcbezg.cn/Article/817919.shtml
- http://map.mobile.fuvxie.cn/Article/323704.shtml
- http://map.mobile.fuvxie.cn/Article/5741.shtml
- http://map.mobile.fuvxie.cn/Article/6886.shtml
- http://map.mobile.cvsifc.cn/Article/177315.shtml
- http://map.mobile.cvsifc.cn/Article/3836.shtml
- http://map.mobile.hcbezg.cn/Article/5231829.shtml
- http://map.mobile.fuvxie.cn/Article/5335.shtml
- http://map.mobile.fuvxie.cn/Article/826424.shtml
- http://map.mobile.cvsifc.cn/Article/6638175.shtml
- http://map.mobile.hcbezg.cn/Article/41192.shtml
- http://map.mobile.cvsifc.cn/Article/1418.shtml
- http://map.mobile.hcbezg.cn/Article/0840.shtml
- http://map.mobile.fuvxie.cn/Article/624649.shtml
- http://map.mobile.fuvxie.cn/Article/1074.shtml
- http://map.mobile.cvsifc.cn/Article/5170042.shtml
- http://map.mobile.fuvxie.cn/Article/5027.shtml
- http://map.mobile.hcbezg.cn/Article/8785492.shtml
- http://map.mobile.fuvxie.cn/Article/905280.shtml
- http://map.mobile.fuvxie.cn/Article/1720.shtml
- http://map.mobile.cvsifc.cn/Article/1530.shtml
- http://map.mobile.fuvxie.cn/Article/4581.shtml
- http://map.mobile.fuvxie.cn/Article/88611.shtml
- http://map.mobile.cvsifc.cn/Article/8477938.shtml
- http://map.mobile.fuvxie.cn/Article/035910.shtml
- http://map.mobile.hcbezg.cn/Article/099912.shtml
- http://map.mobile.fuvxie.cn/Article/2593.shtml
- http://map.mobile.fuvxie.cn/Article/5995.shtml
- http://map.mobile.cvsifc.cn/Article/0581454.shtml
- http://map.mobile.cvsifc.cn/Article/8827405.shtml
- http://map.mobile.cvsifc.cn/Article/2998843.shtml
- http://map.mobile.fuvxie.cn/Article/65626.shtml
- http://map.mobile.fuvxie.cn/Article/21695.shtml
- http://map.mobile.fuvxie.cn/Article/8191299.shtml
- http://map.mobile.fuvxie.cn/Article/6963649.shtml
- http://map.mobile.cvsifc.cn/Article/5724.shtml
- http://map.mobile.fuvxie.cn/Article/88219.shtml
- http://map.mobile.hcbezg.cn/Article/428483.shtml
- http://map.mobile.hcbezg.cn/Article/489936.shtml
- http://map.mobile.fuvxie.cn/Article/983202.shtml
- http://map.mobile.hcbezg.cn/Article/8770327.shtml
- http://map.mobile.hcbezg.cn/Article/1634.shtml
- http://map.mobile.hcbezg.cn/Article/4045.shtml
- http://map.mobile.cvsifc.cn/Article/0050246.shtml
- http://map.mobile.hcbezg.cn/Article/644399.shtml
- http://map.mobile.fuvxie.cn/Article/0012084.shtml
- http://map.mobile.cvsifc.cn/Article/8956.shtml
- http://map.mobile.hcbezg.cn/Article/9714439.shtml
- http://map.mobile.hcbezg.cn/Article/98973.shtml
- http://map.mobile.cvsifc.cn/Article/1428.shtml
- http://map.mobile.fuvxie.cn/Article/5269224.shtml
- http://map.mobile.cvsifc.cn/Article/84788.shtml
- http://map.mobile.hcbezg.cn/Article/74354.shtml
- http://map.mobile.hcbezg.cn/Article/2370455.shtml
- http://map.mobile.hcbezg.cn/Article/0194.shtml
- http://map.mobile.fuvxie.cn/Article/60925.shtml
- http://map.mobile.fuvxie.cn/Article/6787.shtml
- http://map.mobile.fuvxie.cn/Article/774603.shtml
- http://map.mobile.fuvxie.cn/Article/821155.shtml
- http://map.mobile.hcbezg.cn/Article/77059.shtml
- http://map.mobile.cvsifc.cn/Article/6543.shtml
- http://map.mobile.hcbezg.cn/Article/9742622.shtml
- http://map.mobile.fuvxie.cn/Article/9864.shtml
- http://map.mobile.cvsifc.cn/Article/31932.shtml
- http://map.mobile.hcbezg.cn/Article/615367.shtml
- http://map.mobile.hcbezg.cn/Article/9545917.shtml
- http://map.mobile.hcbezg.cn/Article/6927961.shtml
- http://map.mobile.cvsifc.cn/Article/85936.shtml
- http://map.mobile.cvsifc.cn/Article/3592.shtml
- http://map.mobile.fuvxie.cn/Article/5639533.shtml
- http://map.mobile.fuvxie.cn/Article/376048.shtml
- http://map.mobile.fuvxie.cn/Article/7928890.shtml
- http://map.mobile.hcbezg.cn/Article/8645.shtml
- http://map.mobile.fuvxie.cn/Article/897843.shtml
- http://map.mobile.cvsifc.cn/Article/84486.shtml
- http://map.mobile.fuvxie.cn/Article/7534585.shtml
- http://map.mobile.cvsifc.cn/Article/87192.shtml
- http://map.mobile.cvsifc.cn/Article/215446.shtml
- http://map.mobile.fuvxie.cn/Article/54895.shtml
- http://map.mobile.cvsifc.cn/Article/384385.shtml
- http://map.mobile.hcbezg.cn/Article/0415.shtml
- http://map.mobile.cvsifc.cn/Article/565718.shtml
- http://map.mobile.fuvxie.cn/Article/4692.shtml
- http://map.mobile.cvsifc.cn/Article/65968.shtml
- http://map.mobile.fuvxie.cn/Article/72577.shtml
- http://map.mobile.cvsifc.cn/Article/120844.shtml
- http://map.mobile.cvsifc.cn/Article/280258.shtml
- http://map.mobile.fuvxie.cn/Article/05788.shtml
- http://map.mobile.cvsifc.cn/Article/2397.shtml
- http://map.mobile.cvsifc.cn/Article/1229.shtml
- http://map.mobile.hcbezg.cn/Article/9184.shtml
- http://map.mobile.cvsifc.cn/Article/7382435.shtml
- http://map.mobile.fuvxie.cn/Article/2746756.shtml
- http://map.mobile.hcbezg.cn/Article/791250.shtml
- http://map.mobile.fuvxie.cn/Article/2052135.shtml
- http://map.mobile.cvsifc.cn/Article/4195968.shtml
- http://map.mobile.cvsifc.cn/Article/392943.shtml
- http://map.mobile.fuvxie.cn/Article/137177.shtml
- http://map.mobile.cvsifc.cn/Article/187256.shtml
- http://map.mobile.hcbezg.cn/Article/37600.shtml
- http://map.mobile.fuvxie.cn/Article/608151.shtml
- http://map.mobile.cvsifc.cn/Article/9160.shtml
- http://map.mobile.fuvxie.cn/Article/87067.shtml
- http://map.mobile.hcbezg.cn/Article/7969.shtml
- http://map.mobile.cvsifc.cn/Article/3679.shtml
- http://map.mobile.fuvxie.cn/Article/6874.shtml
- http://map.mobile.fuvxie.cn/Article/6540.shtml
- http://map.mobile.hcbezg.cn/Article/6541914.shtml
- http://map.mobile.fuvxie.cn/Article/134060.shtml
- http://map.mobile.cvsifc.cn/Article/1789.shtml
- http://map.mobile.hcbezg.cn/Article/684730.shtml
- http://map.mobile.fuvxie.cn/Article/11584.shtml
- http://map.mobile.fuvxie.cn/Article/462815.shtml
- http://map.mobile.fuvxie.cn/Article/855355.shtml
- http://map.mobile.fuvxie.cn/Article/820212.shtml
- http://map.mobile.fuvxie.cn/Article/8147271.shtml
- http://map.mobile.cvsifc.cn/Article/5289632.shtml
- http://map.mobile.hcbezg.cn/Article/1308485.shtml

## 项目结构

```
maplink-indexer/
├── src/                                  # 核心源代码目录
│   ├── index.ts                          # 服务入口，初始化应用与启动监听
│   ├── app.ts                            # Express 应用配置，中间件与路由挂载
│   ├── routes/                           # 路由定义层
│   │   ├── api.ts                        # RESTful API 路由，包含增删改查接口
│   │   └── web.ts                        # Web 管理界面路由，渲染前端页面
│   ├── controllers/                      # 控制器层，处理请求与响应逻辑
│   │   ├── linkController.ts             # 链接资源的核心业务控制
│   │   └── tagController.ts              # 标签分类的增删改查控制
│   ├── services/                         # 业务服务层，封装数据操作与外部调用
│   │   ├── indexService.ts               # 索引构建与检索服务
│   │   ├── monitorService.ts             # 链接状态监测与告警服务
│   │   └── statsService.ts               # 访问统计与热度计算服务
│   ├── models/                           # 数据模型定义，对应 SQLite 表结构
│   │   ├── link.ts                       # 链接实体模型，包含 url、title、status 等字段
│   │   ├── tag.ts                        # 标签实体模型，包含 name、color 等字段
│   │   └── clickLog.ts                   # 点击日志模型，记录访问时间与来源 IP
│   ├── utils/                            # 通用工具函数库
│   │   ├── validator.ts                  # URL 格式校验与规范化工具
│   │   ├── crawler.ts                    # 网页标题与摘要抓取工具
│   │   └── logger.ts                     # 日志记录器，支持多级别输出
│   └── config/                           # 配置加载模块
│       ├── index.ts                      # 统一导出配置对象
│       └── env.ts                        # 环境变量解析与默认值设定
├── static/                               # 静态资源目录
│   ├── css/                              # 样式文件，基于 Tailwind 构建
│   ├── js/                               # 前端交互脚本，包含搜索与分页逻辑
│   └── assets/                           # 图片与字体等资源文件
├── templates/                            # 服务端渲染模板
│   ├── layouts/                          # 布局模板，定义页面骨架
│   └── partials/                         # 可复用组件，如导航栏、卡片、分页器
├── tests/                                # 单元测试与集成测试
│   ├── unit/                             # 服务层与工具函数的单元测试
│   └── integration/                      # API 接口与数据库交互的集成测试
├── docs/                                 # 文档目录，包含入门、配置、API 与运维指南
├── scripts/                              # 辅助脚本，如数据迁移、种子数据填充
├── .env.example                          # 环境变量配置示例文件
├── docker-compose.yml                    # Docker Compose 编排文件，用于快速部署
├── Dockerfile                            # 容器镜像构建文件
├── package.json                          # npm 依赖清单与脚本定义
├── tsconfig.json                         # TypeScript 编译配置
└── README.md                             # 项目说明文档（本文件）
```

## 贡献指南

1. 查阅 issue 列表，确认尚未被认领的待办任务，或提交新 issue 描述您希望解决的问题或新增功能。

2. 从主分支 fork 代码仓库，在本地新建一个功能分支，分支命名建议采用 feature/功能简述 或 fix/问题简述 格式。

3. 编写代码并补充对应的单元测试，确保所有测试用例通过，同时遵循项目 ESLint 与 Prettier 代码规范。

4. 提交 pull request 到主分支，在描述中清晰说明改动内容、测试覆盖情况以及是否涉及破坏性变更。

5. 等待维护者代码审查，根据反馈进行修改，合并后即完成贡献。

## 常见问题

Q: 导入大量 URL 时出现超时或内存不足应如何处理？

A: 建议使用分批导入模式，每次提交不超过 500 条记录。可通过环境变量 BATCH_SIZE 调整每批处理数量。同时确保 Node.js 内存限制调整为 --max-old-space-size=1024 或更高。

Q: 如何从其他系统迁移现有书签或收藏夹数据至 MapLink？

A: MapLink 提供 CSV 与 JSON 两种导入格式。Chrome 书签可直接导出为 HTML，再通过社区脚本转换为 CSV；浏览器收藏夹亦可手动整理为 JSON 数组格式后调用 API 导入。迁移工具位于 scripts/migrate 目录下。

Q: 链接状态监控的频率和超时时间是否可以自定义？

A: 支持完全自定义。在配置文件中设置 CHECK_INTERVAL（单位分钟）调整检测周期，设置 CHECK_TIMEOUT（单位毫秒）调整每次请求的超时阈值。监控任务基于 node-cron 实现，支持精确到秒的调度。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
