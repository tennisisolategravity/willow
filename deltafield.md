# MapMobile 技术资源聚合导航

MapMobile 是一个面向移动端开发者和技术研究人员的结构化外链资源聚合平台。该项目专注于采集、整理和索引来自多个技术内容源的文章与文档链接，帮助开发者在移动开发、前端工程化、跨端方案、性能优化等领域快速定位高质量的技术参考资料。项目定位为技术资源导航站，适用于个人开发者作为技术选型参考，也适用于技术团队内部作为知识库外链补充。

项目通过自动化的链接采集与分类机制，将分散在多个内容服务节点上的技术文章按主题聚合，并提供基础的检索与过滤能力。当前版本已收录超过 250 条有效技术资源链接，覆盖移动端地图应用、前端框架、工程化工具链、性能监控、UI 组件库等多个细分方向。项目不直接存储文章内容，仅提供结构化索引，所有原文内容以原始链接为准。

## 功能概览

**多源链接聚合采集** 系统通过可配置的数据源接入层，从多个内容服务节点定时拉取最新的文章链接，自动去重并入库。

**按技术主题分类索引** 每条链接在采集时根据 URL 结构和页面元信息自动打标分类，支持按移动端、前端、后端、运维等大类筛选。

**链接状态健康检查** 内置链接可用性检测模块，定期对已收录的 URL 执行 HEAD 请求，标记失效链接并生成报告。

**全文元信息提取** 对每个收录链接自动抓取页面标题、发布时间、摘要描述等元数据，生成索引卡片供前端展示。

**基于标签的快速检索** 支持多标签组合检索，用户可通过标签面板快速过滤出特定技术栈或场景下的相关资源。

**链接收藏与分享** 注册用户可将常用链接加入个人收藏夹，并生成短链接分享给团队成员。

**RSS 订阅源生成** 按分类生成 RSS 订阅地址，方便开发者通过阅读器跟踪特定领域的最新更新。

**管理后台链接审核** 提供审核面板，运营人员可对自动采集的链接进行人工复核，确保资源质量。

## 应用场景

移动端开发者在进行地图 SDK 集成或定位功能开发时，可通过本平台快速检索相关技术文章，获取不同版本下的 API 使用注意事项和常见踩坑案例，节省在多个搜索引擎间反复切换的时间。

技术团队的知识库管理员可以利用本平台的链接健康检查功能，定期清理团队文档中引用的失效外链，同时通过 RSS 订阅跟踪外部优质资源的最新发布，及时补充内部知识库。

在校学生或刚入门的开发者在自学移动端技术栈时，可以通过本平台的分类索引体系，系统性地了解从基础组件到工程化工具链的完整学习路径，每个分类下聚合了大量经过初步筛选的参考文章。

技术会议或社区活动的组织者在筹备分享内容时，可以利用本平台的链接收藏功能快速收集和整理多篇参考资料，并通过短链接功能将资源列表分享给参会者。

## 快速开始

以下步骤指导您在本地环境中快速启动 MapMobile 服务。

```bash
# 克隆项目仓库
git clone https://github.com/mapmobile/mapmobile-resource-hub.git

# 进入项目目录
cd mapmobile-resource-hub

# 安装依赖（使用 npm）
npm install

# 配置环境变量，复制示例配置文件并修改
cp .env.example .env

# 初始化数据库表结构
npm run db:migrate

# 启动开发服务器
npm run dev

# 服务默认在 localhost:3000 启动
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装项目依赖 |
| PostgreSQL | >= 14.0 | 主数据库，存储链接索引和用户数据 |
| Redis | >= 6.2 | 缓存层，用于链接健康检查状态缓存和会话管理 |
| Elasticsearch | >= 8.0 | 可选组件，用于增强版全文检索功能 |
| Nginx | >= 1.20 | 生产环境反向代理和静态资源服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何快速部署项目、配置环境变量、启动服务 |
| 采集配置 | /docs/crawler-config.md | 如何配置新的数据源节点、调整采集频率和规则 |
| API 参考 | /docs/api-reference.md | 各接口的请求参数、响应格式和鉴权方式 |
| 运维手册 | /docs/operations.md | 如何执行链接健康检查、清理过期数据、备份恢复 |

## 资源列表

- http://map.mobile.hcbezg.cn/Article/4668.shtml
- http://map.mobile.cvsifc.cn/Article/131496.shtml
- http://map.mobile.fuvxie.cn/Article/015208.shtml
- http://map.mobile.hcbezg.cn/Article/86831.shtml
- http://map.mobile.hcbezg.cn/Article/85909.shtml
- http://map.mobile.fuvxie.cn/Article/6800401.shtml
- http://map.mobile.fuvxie.cn/Article/04335.shtml
- http://map.mobile.hcbezg.cn/Article/4205.shtml
- http://map.mobile.hcbezg.cn/Article/424175.shtml
- http://map.mobile.fuvxie.cn/Article/85718.shtml
- http://map.mobile.cvsifc.cn/Article/2935573.shtml
- http://map.mobile.hcbezg.cn/Article/6858.shtml
- http://map.mobile.fuvxie.cn/Article/8488080.shtml
- http://map.mobile.hcbezg.cn/Article/54354.shtml
- http://map.mobile.fuvxie.cn/Article/19243.shtml
- http://map.mobile.hcbezg.cn/Article/6397.shtml
- http://map.mobile.hcbezg.cn/Article/891957.shtml
- http://map.mobile.fuvxie.cn/Article/68064.shtml
- http://map.mobile.hcbezg.cn/Article/4440031.shtml
- http://map.mobile.hcbezg.cn/Article/2933274.shtml
- http://map.mobile.hcbezg.cn/Article/01772.shtml
- http://map.mobile.fuvxie.cn/Article/3876.shtml
- http://map.mobile.cvsifc.cn/Article/4399.shtml
- http://map.mobile.fuvxie.cn/Article/34374.shtml
- http://map.mobile.fuvxie.cn/Article/99230.shtml
- http://map.mobile.cvsifc.cn/Article/1524.shtml
- http://map.mobile.cvsifc.cn/Article/0626180.shtml
- http://map.mobile.fuvxie.cn/Article/3186276.shtml
- http://map.mobile.cvsifc.cn/Article/663059.shtml
- http://map.mobile.hcbezg.cn/Article/2372.shtml
- http://map.mobile.fuvxie.cn/Article/1272.shtml
- http://map.mobile.hcbezg.cn/Article/5771.shtml
- http://map.mobile.fuvxie.cn/Article/390687.shtml
- http://map.mobile.cvsifc.cn/Article/7670.shtml
- http://map.mobile.cvsifc.cn/Article/21064.shtml
- http://map.mobile.hcbezg.cn/Article/872636.shtml
- http://map.mobile.hcbezg.cn/Article/493485.shtml
- http://map.mobile.fuvxie.cn/Article/1392.shtml
- http://map.mobile.fuvxie.cn/Article/9561860.shtml
- http://map.mobile.fuvxie.cn/Article/117065.shtml
- http://map.mobile.fuvxie.cn/Article/9590.shtml
- http://map.mobile.cvsifc.cn/Article/6476.shtml
- http://map.mobile.hcbezg.cn/Article/7072430.shtml
- http://map.mobile.fuvxie.cn/Article/5090071.shtml
- http://map.mobile.fuvxie.cn/Article/194168.shtml
- http://map.mobile.hcbezg.cn/Article/885674.shtml
- http://map.mobile.hcbezg.cn/Article/927979.shtml
- http://map.mobile.fuvxie.cn/Article/6282510.shtml
- http://map.mobile.cvsifc.cn/Article/11927.shtml
- http://map.mobile.hcbezg.cn/Article/81768.shtml
- http://map.mobile.cvsifc.cn/Article/55559.shtml
- http://map.mobile.fuvxie.cn/Article/9469.shtml
- http://map.mobile.fuvxie.cn/Article/5579916.shtml
- http://map.mobile.hcbezg.cn/Article/219729.shtml
- http://map.mobile.hcbezg.cn/Article/038307.shtml
- http://map.mobile.cvsifc.cn/Article/136488.shtml
- http://map.mobile.cvsifc.cn/Article/986994.shtml
- http://map.mobile.fuvxie.cn/Article/497357.shtml
- http://map.mobile.fuvxie.cn/Article/892842.shtml
- http://map.mobile.hcbezg.cn/Article/513618.shtml
- http://map.mobile.cvsifc.cn/Article/9272.shtml
- http://map.mobile.fuvxie.cn/Article/782164.shtml
- http://map.mobile.hcbezg.cn/Article/14816.shtml
- http://map.mobile.hcbezg.cn/Article/728790.shtml
- http://map.mobile.cvsifc.cn/Article/3565.shtml
- http://map.mobile.hcbezg.cn/Article/929876.shtml
- http://map.mobile.hcbezg.cn/Article/9205.shtml
- http://map.mobile.fuvxie.cn/Article/3441.shtml
- http://map.mobile.hcbezg.cn/Article/35212.shtml
- http://map.mobile.cvsifc.cn/Article/8611.shtml
- http://map.mobile.cvsifc.cn/Article/37028.shtml
- http://map.mobile.cvsifc.cn/Article/160705.shtml
- http://map.mobile.fuvxie.cn/Article/1820927.shtml
- http://map.mobile.fuvxie.cn/Article/1138071.shtml
- http://map.mobile.cvsifc.cn/Article/19537.shtml
- http://map.mobile.fuvxie.cn/Article/136520.shtml
- http://map.mobile.hcbezg.cn/Article/391864.shtml
- http://map.mobile.hcbezg.cn/Article/0052622.shtml
- http://map.mobile.fuvxie.cn/Article/6403311.shtml
- http://map.mobile.hcbezg.cn/Article/5932.shtml
- http://map.mobile.cvsifc.cn/Article/58689.shtml
- http://map.mobile.cvsifc.cn/Article/6018011.shtml
- http://map.mobile.hcbezg.cn/Article/9821.shtml
- http://map.mobile.fuvxie.cn/Article/85533.shtml
- http://map.mobile.fuvxie.cn/Article/998943.shtml
- http://map.mobile.fuvxie.cn/Article/8224.shtml
- http://map.mobile.cvsifc.cn/Article/873030.shtml
- http://map.mobile.cvsifc.cn/Article/309248.shtml
- http://map.mobile.fuvxie.cn/Article/36495.shtml
- http://map.mobile.hcbezg.cn/Article/5910712.shtml
- http://map.mobile.cvsifc.cn/Article/8618114.shtml
- http://map.mobile.hcbezg.cn/Article/10478.shtml
- http://map.mobile.hcbezg.cn/Article/69156.shtml
- http://map.mobile.hcbezg.cn/Article/508891.shtml
- http://map.mobile.cvsifc.cn/Article/1798236.shtml
- http://map.mobile.cvsifc.cn/Article/9439254.shtml
- http://map.mobile.hcbezg.cn/Article/1477.shtml
- http://map.mobile.cvsifc.cn/Article/6821.shtml
- http://map.mobile.fuvxie.cn/Article/2025.shtml
- http://map.mobile.cvsifc.cn/Article/94925.shtml
- http://map.mobile.fuvxie.cn/Article/8601.shtml
- http://map.mobile.hcbezg.cn/Article/639442.shtml
- http://map.mobile.fuvxie.cn/Article/1197.shtml
- http://map.mobile.cvsifc.cn/Article/1452974.shtml
- http://map.mobile.cvsifc.cn/Article/372460.shtml
- http://map.mobile.cvsifc.cn/Article/795424.shtml
- http://map.mobile.fuvxie.cn/Article/4200652.shtml
- http://map.mobile.fuvxie.cn/Article/087044.shtml
- http://map.mobile.hcbezg.cn/Article/380500.shtml
- http://map.mobile.cvsifc.cn/Article/9527.shtml
- http://map.mobile.fuvxie.cn/Article/532999.shtml
- http://map.mobile.hcbezg.cn/Article/2000.shtml
- http://map.mobile.cvsifc.cn/Article/178414.shtml
- http://map.mobile.hcbezg.cn/Article/7518.shtml
- http://map.mobile.fuvxie.cn/Article/60161.shtml
- http://map.mobile.fuvxie.cn/Article/50200.shtml
- http://map.mobile.cvsifc.cn/Article/29280.shtml
- http://map.mobile.cvsifc.cn/Article/7325.shtml
- http://map.mobile.hcbezg.cn/Article/4938063.shtml
- http://map.mobile.fuvxie.cn/Article/8389513.shtml
- http://map.mobile.fuvxie.cn/Article/77362.shtml
- http://map.mobile.cvsifc.cn/Article/90553.shtml
- http://map.mobile.cvsifc.cn/Article/1374304.shtml
- http://map.mobile.fuvxie.cn/Article/0981241.shtml
- http://map.mobile.fuvxie.cn/Article/533206.shtml
- http://map.mobile.cvsifc.cn/Article/97025.shtml
- http://map.mobile.fuvxie.cn/Article/5359066.shtml
- http://map.mobile.fuvxie.cn/Article/56757.shtml
- http://map.mobile.hcbezg.cn/Article/5756.shtml
- http://map.mobile.fuvxie.cn/Article/243519.shtml
- http://map.mobile.hcbezg.cn/Article/252097.shtml
- http://map.mobile.cvsifc.cn/Article/2109.shtml
- http://map.mobile.fuvxie.cn/Article/0176.shtml
- http://map.mobile.cvsifc.cn/Article/1019.shtml
- http://map.mobile.fuvxie.cn/Article/9592451.shtml
- http://map.mobile.hcbezg.cn/Article/315597.shtml
- http://map.mobile.hcbezg.cn/Article/33144.shtml
- http://map.mobile.hcbezg.cn/Article/018101.shtml
- http://map.mobile.fuvxie.cn/Article/3233534.shtml
- http://map.mobile.cvsifc.cn/Article/552566.shtml
- http://map.mobile.cvsifc.cn/Article/524231.shtml
- http://map.mobile.fuvxie.cn/Article/77665.shtml
- http://map.mobile.hcbezg.cn/Article/5746.shtml
- http://map.mobile.fuvxie.cn/Article/5426977.shtml
- http://map.mobile.hcbezg.cn/Article/6164.shtml
- http://map.mobile.hcbezg.cn/Article/19364.shtml
- http://map.mobile.hcbezg.cn/Article/1487.shtml
- http://map.mobile.fuvxie.cn/Article/0019.shtml
- http://map.mobile.hcbezg.cn/Article/8468203.shtml
- http://map.mobile.cvsifc.cn/Article/26108.shtml
- http://map.mobile.cvsifc.cn/Article/7162.shtml
- http://map.mobile.hcbezg.cn/Article/035661.shtml
- http://map.mobile.fuvxie.cn/Article/0220467.shtml
- http://map.mobile.hcbezg.cn/Article/0379506.shtml
- http://map.mobile.fuvxie.cn/Article/8927.shtml
- http://map.mobile.hcbezg.cn/Article/0190.shtml
- http://map.mobile.fuvxie.cn/Article/3110862.shtml
- http://map.mobile.cvsifc.cn/Article/7363404.shtml
- http://map.mobile.cvsifc.cn/Article/0748.shtml
- http://map.mobile.hcbezg.cn/Article/41663.shtml
- http://map.mobile.fuvxie.cn/Article/6807.shtml
- http://map.mobile.hcbezg.cn/Article/14625.shtml
- http://map.mobile.fuvxie.cn/Article/792681.shtml
- http://map.mobile.cvsifc.cn/Article/89490.shtml
- http://map.mobile.hcbezg.cn/Article/837849.shtml
- http://map.mobile.fuvxie.cn/Article/0342.shtml
- http://map.mobile.hcbezg.cn/Article/3182.shtml
- http://map.mobile.hcbezg.cn/Article/408857.shtml
- http://map.mobile.hcbezg.cn/Article/1517.shtml
- http://map.mobile.hcbezg.cn/Article/602424.shtml
- http://map.mobile.fuvxie.cn/Article/65836.shtml
- http://map.mobile.hcbezg.cn/Article/12598.shtml
- http://map.mobile.hcbezg.cn/Article/99853.shtml
- http://map.mobile.cvsifc.cn/Article/626734.shtml
- http://map.mobile.fuvxie.cn/Article/013318.shtml
- http://map.mobile.cvsifc.cn/Article/0285.shtml
- http://map.mobile.cvsifc.cn/Article/8929.shtml
- http://map.mobile.fuvxie.cn/Article/2221.shtml
- http://map.mobile.fuvxie.cn/Article/893173.shtml
- http://map.mobile.hcbezg.cn/Article/50129.shtml
- http://map.mobile.fuvxie.cn/Article/6769088.shtml
- http://map.mobile.hcbezg.cn/Article/6760234.shtml
- http://map.mobile.fuvxie.cn/Article/68259.shtml
- http://map.mobile.fuvxie.cn/Article/6368862.shtml
- http://map.mobile.hcbezg.cn/Article/4499.shtml
- http://map.mobile.cvsifc.cn/Article/2605.shtml
- http://map.mobile.fuvxie.cn/Article/237445.shtml
- http://map.mobile.cvsifc.cn/Article/1284731.shtml
- http://map.mobile.hcbezg.cn/Article/0231.shtml
- http://map.mobile.hcbezg.cn/Article/0337209.shtml
- http://map.mobile.fuvxie.cn/Article/589980.shtml
- http://map.mobile.hcbezg.cn/Article/5613.shtml
- http://map.mobile.fuvxie.cn/Article/3344.shtml
- http://map.mobile.cvsifc.cn/Article/7641.shtml
- http://map.mobile.cvsifc.cn/Article/033487.shtml
- http://map.mobile.fuvxie.cn/Article/913004.shtml
- http://map.mobile.cvsifc.cn/Article/344765.shtml
- http://map.mobile.cvsifc.cn/Article/3780367.shtml
- http://map.mobile.hcbezg.cn/Article/093249.shtml
- http://map.mobile.fuvxie.cn/Article/5661.shtml
- http://map.mobile.hcbezg.cn/Article/762141.shtml
- http://map.mobile.fuvxie.cn/Article/9711959.shtml
- http://map.mobile.hcbezg.cn/Article/9745159.shtml
- http://map.mobile.fuvxie.cn/Article/2010.shtml
- http://map.mobile.hcbezg.cn/Article/97997.shtml
- http://map.mobile.cvsifc.cn/Article/6861.shtml
- http://map.mobile.fuvxie.cn/Article/754388.shtml
- http://map.mobile.fuvxie.cn/Article/181774.shtml
- http://map.mobile.hcbezg.cn/Article/0044.shtml
- http://map.mobile.hcbezg.cn/Article/2802.shtml
- http://map.mobile.fuvxie.cn/Article/8688871.shtml
- http://map.mobile.cvsifc.cn/Article/2325680.shtml
- http://map.mobile.hcbezg.cn/Article/1057504.shtml
- http://map.mobile.fuvxie.cn/Article/3231417.shtml
- http://map.mobile.cvsifc.cn/Article/7444.shtml
- http://map.mobile.hcbezg.cn/Article/39616.shtml
- http://map.mobile.fuvxie.cn/Article/863185.shtml
- http://map.mobile.cvsifc.cn/Article/8274978.shtml
- http://map.mobile.cvsifc.cn/Article/3110.shtml
- http://map.mobile.cvsifc.cn/Article/9827.shtml
- http://map.mobile.fuvxie.cn/Article/3887127.shtml
- http://map.mobile.fuvxie.cn/Article/9114.shtml
- http://map.mobile.fuvxie.cn/Article/774695.shtml
- http://map.mobile.fuvxie.cn/Article/1993.shtml
- http://map.mobile.hcbezg.cn/Article/9515.shtml
- http://map.mobile.cvsifc.cn/Article/691955.shtml
- http://map.mobile.hcbezg.cn/Article/2728.shtml
- http://map.mobile.fuvxie.cn/Article/4713.shtml
- http://map.mobile.fuvxie.cn/Article/41551.shtml
- http://map.mobile.cvsifc.cn/Article/5296367.shtml
- http://map.mobile.hcbezg.cn/Article/8766381.shtml
- http://map.mobile.fuvxie.cn/Article/8286530.shtml
- http://map.mobile.cvsifc.cn/Article/702535.shtml
- http://map.mobile.fuvxie.cn/Article/392733.shtml
- http://map.mobile.hcbezg.cn/Article/64909.shtml
- http://map.mobile.cvsifc.cn/Article/559577.shtml
- http://map.mobile.fuvxie.cn/Article/6050.shtml
- http://map.mobile.cvsifc.cn/Article/951876.shtml
- http://map.mobile.cvsifc.cn/Article/02663.shtml
- http://map.mobile.cvsifc.cn/Article/151251.shtml
- http://map.mobile.hcbezg.cn/Article/7616191.shtml
- http://map.mobile.hcbezg.cn/Article/7739201.shtml
- http://map.mobile.fuvxie.cn/Article/6774125.shtml
- http://map.mobile.hcbezg.cn/Article/4014.shtml
- http://map.mobile.fuvxie.cn/Article/11514.shtml
- http://map.mobile.fuvxie.cn/Article/934015.shtml
- http://map.mobile.cvsifc.cn/Article/860886.shtml
- http://map.mobile.hcbezg.cn/Article/4938.shtml
- http://map.mobile.cvsifc.cn/Article/5834.shtml
- http://map.mobile.fuvxie.cn/Article/8144477.shtml

## 项目结构

```
mapmobile-resource-hub/
├── apps/                                 # 应用层代码
│   ├── web/                              # 前端 Web 应用 (Next.js)
│   │   ├── pages/                        # 页面路由组件
│   │   ├── components/                   # 可复用 UI 组件库
│   │   ├── hooks/                        # 自定义 React Hooks
│   │   └── styles/                       # 全局样式与主题配置
│   └── api/                              # 后端 API 服务 (Express)
│       ├── routes/                       # RESTful 路由定义
│       ├── controllers/                  # 业务控制器
│       ├── middleware/                   # 鉴权、日志、限流中间件
│       └── validators/                   # 请求参数校验器
├── packages/                             # 内部共享包
│   ├── crawler/                          # 链接采集核心模块
│   │   ├── sources/                      # 数据源适配器配置
│   │   ├── parsers/                      # HTML 元信息解析器
│   │   └── scheduler/                    # 定时任务调度器
│   ├── db/                               # 数据库操作层
│   │   ├── migrations/                   # 数据库迁移脚本
│   │   ├── models/                       # ORM 模型定义
│   │   └── repositories/                 # 数据访问仓储层
│   ├── checker/                          # 链接健康检查模块
│   │   ├── http/                         # HTTP 状态检测
│   │   └── reporter/                     # 检测报告生成器
│   └── utils/                            # 通用工具函数集合
│       ├── logger/                       # 日志记录工具
│       ├── cache/                        # Redis 缓存封装
│       └── config/                       # 配置加载与验证
├── scripts/                              # 运维与部署脚本
│   ├── setup.sh                          # 环境初始化脚本
│   ├── backup.sh                         # 数据库备份脚本
│   └── health-check.sh                   # 服务健康状态检查脚本
├── tests/                                # 单元测试与集成测试
│   ├── unit/                             # 单元测试用例
│   ├── integration/                      # 集成测试用例
│   └── fixtures/                         # 测试数据固定样本
├── docs/                                 # 项目文档
├── .env.example                          # 环境变量配置示例
├── docker-compose.yml                    # Docker 编排配置
├── Dockerfile                            # 容器镜像构建文件
├── package.json                          # 项目依赖清单
├── tsconfig.json                         # TypeScript 编译配置
└── README.md                             # 项目说明文档
```

## 贡献指南

我们欢迎并感谢所有形式的贡献，包括但不限于新增数据源适配、修复链接检测逻辑、改进前端界面和补充文档。

1. 在 GitHub 上 Fork 本仓库，并在本地克隆您的 Fork 版本。请确保您的开发环境满足安装要求章节中列出的所有依赖版本。
2. 新建一个功能分支，分支命名格式为 `feature/功能简述` 或 `fix/问题简述`。在该分支上完成您的代码修改，并确保所有现有测试用例通过，新增功能需附带对应的单元测试。
3. 提交代码时请遵循 Conventional Commits 规范，提交信息格式为 `<type>: <subject>`，其中 type 包括 feat、fix、docs、style、refactor、test、chore 等。
4. 推送到您的远程分支后，在本仓库中发起 Pull Request。PR 描述中请清晰说明变更内容、关联的 Issue 编号以及测试覆盖情况。PR 将通过 CI 流水线执行自动化构建和测试。
5. 项目维护者将对 PR 进行 Code Review，并根据情况提出修改意见。合并后您的贡献将会在下一版本发布时列入更新日志。

## 常见问题

**Q: 新增数据源节点后，采集任务多久生效？**

A: 新增数据源配置提交并合并后，系统会在下一个采集周期（默认每 6 小时执行一次全量扫描）自动生效。您也可以在管理后台的「数据源管理」面板中手动触发立即采集，无需等待定时任务。如需调整采集频率，可在 `packages/crawler/scheduler/index.ts` 中修改 cron 表达式。

**Q: 链接健康检查显示失效，但实际可以访问，如何解决？**

A: 链接健康检查模块默认使用 HEAD 请求检测，部分站点可能不支持 HEAD 方法或存在防爬策略。您可以登录管理后台，在「链接管理」页面找到对应记录，手动执行「重新检测」操作，该操作会使用 GET 请求并设置更长的超时时间（10 秒）。若多次检测仍为失效状态，请检查目标站点是否要求特定的 User-Agent 或 Referer 头，可在 `packages/checker/http/client.ts` 中配置请求头策略。

**Q: 如何导出已收录的链接列表用于离线分析？**

A: 系统提供了数据导出接口 `/api/links/export`，支持 CSV 和 JSON 两种格式。您可以在管理后台的「数据工具」面板中选择分类、时间范围和导出格式，生成导出任务。导出文件会暂存在服务器本地，有效期为 72 小时。如需自动化定期导出，可调用 API 并配合 `scripts/backup.sh` 脚本实现定时备份。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
