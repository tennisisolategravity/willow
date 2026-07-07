# WebLink Navigator

WebLink Navigator 是一个面向技术调研、内容聚合与知识管理场景的开源外链资源汇总平台。该项目专注于对分散于多个内容源站点的文章链接进行统一收集、分类标注与结构化呈现，帮助开发者、研究员与技术内容运营者高效管理外部参考资源。项目本身不存储文章正文，仅提供链接索引与元信息组织能力，适用于构建轻量级个人书签库、团队技术周报素材池或自动化爬虫下游处理链路。

## 功能概览

- 多源链接统一入库：支持从多个指定域名下的文章详情页自动提取 URL，形成扁平化资源清单。
- 批次化资源管理：将资源按批次分组，当前为第 27/60 批，便于追踪收集进度与来源分布。
- 原始链接严格保真：对收录的每一篇文章 URL 进行原样存储，不补全协议、不添加或删除 www 前缀、不修改大小写、不附加尾部斜杠。
- 资源状态标记：每条记录可标注是否已读、是否归档、所属主题标签（如技术栈、业务领域）。
- 导出与集成友好：支持将资源列表导出为纯文本列表、Markdown 列表或 JSON 格式，方便下游脚本处理。
- 基础搜索过滤：提供按域名来源、关键词匹配的快速筛选接口，便于从大批量链接中定位目标文章。
- 可扩展元数据字段：预留自定义字段（如爬取时间、摘要哈希），支持用户根据实际采集需求扩展。

## 应用场景

1. 技术调研期间的参考链接暂存
   在进行新技术选型或竞品分析时，调研人员会同时打开数十篇相关文章。WebLink Navigator 可用于集中记录这些文章的原始链接，避免浏览器书签栏混乱，同时按调研主题分组，后续撰写报告时可快速回溯来源。

2. 团队内部周报素材收集
   技术团队每周需要汇总行业动态与内部技术分享参考文章。使用本项目的资源列表功能，团队成员可将各自发现的优质文章链接追加到同一批次中，由周报负责人统一导出并整理。

3. 爬虫采集任务的去重与进度管理
   对于需要从多个内容源抓取文章元信息的爬虫项目，WebLink Navigator 可作为待抓取 URL 队列的前端管理工具，记录已采集和待采集的链接，避免重复抓取，并提供批次编号用于跟踪采集轮次。

4. 个人知识库的外部引用索引
   在使用 Obsidian、Notion 或其他双链笔记工具构建个人知识库时，可将外部参考文章的链接集中存放在 WebLink Navigator 中，笔记内仅引用资源 ID，降低笔记文件的冗余度，提高链接可维护性。

## 快速开始

以下命令演示了如何将本项目克隆至本地、安装基础依赖并运行开发服务。

```bash
git clone https://github.com/your-org/weblink-navigator.git
cd weblink-navigator
npm install
npm run dev
```

执行完成后，访问控制台输出的本地地址（默认 http://localhost:3000）即可查看资源列表界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，用于执行服务端脚本与构建工具 |
| npm | 9.x 或以上 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统级或内置模块 | 轻量级嵌入式数据库，用于存储资源列表与元数据 |
| Git | 2.30 或以上 | 版本控制工具，用于克隆仓库与提交变更 |
| 现代浏览器 | Chrome 110+ / Firefox 110+ / Edge 110+ | 用于访问管理界面，支持 ES2020 语法 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速运行项目并加载第一批资源数据 |
| 数据格式规范 | docs/data-format.md | 资源列表的 JSON 结构、字段定义与扩展方式 |
| 批次管理操作 | docs/batch-operations.md | 如何创建新批次、切换当前批次、合并批次 |
| 导出与集成 | docs/export-integration.md | 支持哪些导出格式，如何与外部爬虫或笔记工具对接 |

## 资源列表

- http://www.mobile.hcbezg.cn/Article/20920.shtml
- http://www.mobile.fuvxie.cn/Article/470595.shtml
- http://www.mobile.hcbezg.cn/Article/216047.shtml
- http://www.mobile.cvsifc.cn/Article/1477842.shtml
- http://www.mobile.cvsifc.cn/Article/9762.shtml
- http://www.mobile.cvsifc.cn/Article/492188.shtml
- http://www.mobile.fuvxie.cn/Article/67167.shtml
- http://www.mobile.fuvxie.cn/Article/5816.shtml
- http://www.mobile.cvsifc.cn/Article/774795.shtml
- http://www.mobile.fuvxie.cn/Article/028945.shtml
- http://www.mobile.fuvxie.cn/Article/636253.shtml
- http://www.mobile.fuvxie.cn/Article/904838.shtml
- http://www.mobile.hcbezg.cn/Article/742873.shtml
- http://www.mobile.fuvxie.cn/Article/2668.shtml
- http://www.mobile.fuvxie.cn/Article/6179391.shtml
- http://www.mobile.fuvxie.cn/Article/0061588.shtml
- http://www.mobile.cvsifc.cn/Article/8285393.shtml
- http://www.mobile.hcbezg.cn/Article/459914.shtml
- http://www.mobile.fuvxie.cn/Article/21899.shtml
- http://www.mobile.hcbezg.cn/Article/0955.shtml
- http://www.mobile.hcbezg.cn/Article/650208.shtml
- http://www.mobile.fuvxie.cn/Article/07566.shtml
- http://www.mobile.cvsifc.cn/Article/79657.shtml
- http://www.mobile.cvsifc.cn/Article/0752467.shtml
- http://www.mobile.cvsifc.cn/Article/8122.shtml
- http://www.mobile.hcbezg.cn/Article/882242.shtml
- http://www.mobile.cvsifc.cn/Article/0407.shtml
- http://www.mobile.fuvxie.cn/Article/13849.shtml
- http://www.mobile.cvsifc.cn/Article/04201.shtml
- http://www.mobile.cvsifc.cn/Article/0787.shtml
- http://www.mobile.fuvxie.cn/Article/9676206.shtml
- http://www.mobile.hcbezg.cn/Article/564552.shtml
- http://www.mobile.hcbezg.cn/Article/6302160.shtml
- http://www.mobile.cvsifc.cn/Article/86067.shtml
- http://www.mobile.cvsifc.cn/Article/2927448.shtml
- http://www.mobile.cvsifc.cn/Article/906234.shtml
- http://www.mobile.fuvxie.cn/Article/776123.shtml
- http://www.mobile.fuvxie.cn/Article/927591.shtml
- http://www.mobile.cvsifc.cn/Article/7230.shtml
- http://www.mobile.cvsifc.cn/Article/1875972.shtml
- http://www.mobile.cvsifc.cn/Article/706336.shtml
- http://www.mobile.hcbezg.cn/Article/922995.shtml
- http://www.mobile.hcbezg.cn/Article/1537326.shtml
- http://www.mobile.hcbezg.cn/Article/316906.shtml
- http://www.mobile.hcbezg.cn/Article/4562.shtml
- http://www.mobile.cvsifc.cn/Article/69032.shtml
- http://www.mobile.fuvxie.cn/Article/397298.shtml
- http://www.mobile.hcbezg.cn/Article/6421.shtml
- http://www.mobile.cvsifc.cn/Article/4104936.shtml
- http://www.mobile.cvsifc.cn/Article/1383.shtml
- http://www.mobile.hcbezg.cn/Article/39605.shtml
- http://www.mobile.cvsifc.cn/Article/1458.shtml
- http://www.mobile.fuvxie.cn/Article/23608.shtml
- http://www.mobile.cvsifc.cn/Article/1987.shtml
- http://www.mobile.hcbezg.cn/Article/78022.shtml
- http://www.mobile.cvsifc.cn/Article/2794.shtml
- http://www.mobile.hcbezg.cn/Article/0035.shtml
- http://www.mobile.hcbezg.cn/Article/38866.shtml
- http://www.mobile.hcbezg.cn/Article/3069.shtml
- http://www.mobile.fuvxie.cn/Article/492113.shtml
- http://www.mobile.fuvxie.cn/Article/4541.shtml
- http://www.mobile.fuvxie.cn/Article/5147965.shtml
- http://www.mobile.hcbezg.cn/Article/7281.shtml
- http://www.mobile.cvsifc.cn/Article/3524.shtml
- http://www.mobile.cvsifc.cn/Article/4163439.shtml
- http://www.mobile.hcbezg.cn/Article/2967.shtml
- http://www.mobile.cvsifc.cn/Article/37108.shtml
- http://www.mobile.fuvxie.cn/Article/5896.shtml
- http://www.mobile.hcbezg.cn/Article/23483.shtml
- http://www.mobile.cvsifc.cn/Article/7471.shtml
- http://www.mobile.hcbezg.cn/Article/43695.shtml
- http://www.mobile.fuvxie.cn/Article/0371.shtml
- http://www.mobile.fuvxie.cn/Article/022412.shtml
- http://www.mobile.fuvxie.cn/Article/7773708.shtml
- http://www.mobile.fuvxie.cn/Article/64380.shtml
- http://www.mobile.fuvxie.cn/Article/402024.shtml
- http://www.mobile.cvsifc.cn/Article/2448.shtml
- http://www.mobile.hcbezg.cn/Article/7632245.shtml
- http://www.mobile.hcbezg.cn/Article/120507.shtml
- http://www.mobile.fuvxie.cn/Article/408845.shtml
- http://www.mobile.hcbezg.cn/Article/75510.shtml
- http://www.mobile.cvsifc.cn/Article/602311.shtml
- http://www.mobile.hcbezg.cn/Article/40456.shtml
- http://www.mobile.cvsifc.cn/Article/5286477.shtml
- http://www.mobile.hcbezg.cn/Article/34590.shtml
- http://www.mobile.fuvxie.cn/Article/5310.shtml
- http://www.mobile.hcbezg.cn/Article/9781916.shtml
- http://www.mobile.hcbezg.cn/Article/4131339.shtml
- http://www.mobile.cvsifc.cn/Article/2229.shtml
- http://www.mobile.fuvxie.cn/Article/869281.shtml
- http://www.mobile.cvsifc.cn/Article/3831129.shtml
- http://www.mobile.cvsifc.cn/Article/04855.shtml
- http://www.mobile.fuvxie.cn/Article/5419.shtml
- http://www.mobile.fuvxie.cn/Article/63616.shtml
- http://www.mobile.fuvxie.cn/Article/2699.shtml
- http://www.mobile.hcbezg.cn/Article/13274.shtml
- http://www.mobile.hcbezg.cn/Article/5638.shtml
- http://www.mobile.cvsifc.cn/Article/9409.shtml
- http://www.mobile.cvsifc.cn/Article/7879080.shtml
- http://www.mobile.fuvxie.cn/Article/6867.shtml
- http://www.mobile.fuvxie.cn/Article/358760.shtml
- http://www.mobile.fuvxie.cn/Article/7923.shtml
- http://www.mobile.fuvxie.cn/Article/2422.shtml
- http://www.mobile.fuvxie.cn/Article/734777.shtml
- http://www.mobile.fuvxie.cn/Article/1872609.shtml
- http://www.mobile.fuvxie.cn/Article/049077.shtml
- http://www.mobile.hcbezg.cn/Article/73759.shtml
- http://www.mobile.hcbezg.cn/Article/9944306.shtml
- http://www.mobile.hcbezg.cn/Article/1341666.shtml
- http://www.mobile.cvsifc.cn/Article/051407.shtml
- http://www.mobile.fuvxie.cn/Article/49693.shtml
- http://www.mobile.cvsifc.cn/Article/6118.shtml
- http://www.mobile.hcbezg.cn/Article/4365304.shtml
- http://www.mobile.hcbezg.cn/Article/455872.shtml
- http://www.mobile.cvsifc.cn/Article/636613.shtml
- http://www.mobile.hcbezg.cn/Article/425925.shtml
- http://www.mobile.hcbezg.cn/Article/60701.shtml
- http://www.mobile.cvsifc.cn/Article/113663.shtml
- http://www.mobile.hcbezg.cn/Article/1426.shtml
- http://www.mobile.cvsifc.cn/Article/52138.shtml
- http://www.mobile.fuvxie.cn/Article/777864.shtml
- http://www.mobile.cvsifc.cn/Article/8760.shtml
- http://www.mobile.hcbezg.cn/Article/31075.shtml
- http://www.mobile.fuvxie.cn/Article/562209.shtml
- http://www.mobile.cvsifc.cn/Article/85548.shtml
- http://www.mobile.fuvxie.cn/Article/22061.shtml
- http://www.mobile.hcbezg.cn/Article/38526.shtml
- http://www.mobile.fuvxie.cn/Article/507812.shtml
- http://www.mobile.cvsifc.cn/Article/3658.shtml
- http://www.mobile.fuvxie.cn/Article/4451940.shtml
- http://www.mobile.fuvxie.cn/Article/1437.shtml
- http://www.mobile.cvsifc.cn/Article/1663357.shtml
- http://www.mobile.hcbezg.cn/Article/2638429.shtml
- http://www.mobile.cvsifc.cn/Article/2061.shtml
- http://www.mobile.cvsifc.cn/Article/8137739.shtml
- http://www.mobile.fuvxie.cn/Article/2979805.shtml
- http://www.mobile.hcbezg.cn/Article/2962289.shtml
- http://www.mobile.fuvxie.cn/Article/797682.shtml
- http://www.mobile.hcbezg.cn/Article/6685192.shtml
- http://www.mobile.cvsifc.cn/Article/096797.shtml
- http://www.mobile.hcbezg.cn/Article/55147.shtml
- http://www.mobile.cvsifc.cn/Article/11807.shtml
- http://www.mobile.hcbezg.cn/Article/6203796.shtml
- http://www.mobile.cvsifc.cn/Article/5999005.shtml
- http://www.mobile.fuvxie.cn/Article/0755.shtml
- http://www.mobile.fuvxie.cn/Article/6611.shtml
- http://www.mobile.fuvxie.cn/Article/3907.shtml
- http://www.mobile.hcbezg.cn/Article/14977.shtml
- http://www.mobile.cvsifc.cn/Article/44323.shtml
- http://www.mobile.cvsifc.cn/Article/2902.shtml
- http://www.mobile.cvsifc.cn/Article/611003.shtml
- http://www.mobile.fuvxie.cn/Article/12253.shtml
- http://www.mobile.hcbezg.cn/Article/861287.shtml
- http://www.mobile.cvsifc.cn/Article/85746.shtml
- http://www.mobile.cvsifc.cn/Article/3603.shtml
- http://www.mobile.hcbezg.cn/Article/6428686.shtml
- http://www.mobile.cvsifc.cn/Article/0675.shtml
- http://www.mobile.fuvxie.cn/Article/0737.shtml
- http://www.mobile.hcbezg.cn/Article/370311.shtml
- http://www.mobile.fuvxie.cn/Article/25563.shtml
- http://www.mobile.fuvxie.cn/Article/64175.shtml
- http://www.mobile.cvsifc.cn/Article/485799.shtml
- http://www.mobile.cvsifc.cn/Article/8070.shtml
- http://www.mobile.cvsifc.cn/Article/6265.shtml
- http://www.mobile.fuvxie.cn/Article/28037.shtml
- http://www.mobile.hcbezg.cn/Article/487177.shtml
- http://www.mobile.hcbezg.cn/Article/60568.shtml
- http://www.mobile.cvsifc.cn/Article/12195.shtml
- http://www.mobile.fuvxie.cn/Article/1914.shtml
- http://www.mobile.cvsifc.cn/Article/6217.shtml
- http://www.mobile.cvsifc.cn/Article/8673960.shtml
- http://www.mobile.hcbezg.cn/Article/5686332.shtml
- http://www.mobile.hcbezg.cn/Article/9519999.shtml
- http://www.mobile.cvsifc.cn/Article/739643.shtml
- http://www.mobile.fuvxie.cn/Article/3099795.shtml
- http://www.mobile.hcbezg.cn/Article/64928.shtml
- http://www.mobile.fuvxie.cn/Article/092522.shtml
- http://www.mobile.hcbezg.cn/Article/6154313.shtml
- http://www.mobile.hcbezg.cn/Article/1816281.shtml
- http://www.mobile.cvsifc.cn/Article/857350.shtml
- http://www.mobile.fuvxie.cn/Article/18237.shtml
- http://www.mobile.fuvxie.cn/Article/3453.shtml
- http://www.mobile.fuvxie.cn/Article/54524.shtml
- http://www.mobile.hcbezg.cn/Article/5749.shtml
- http://www.mobile.cvsifc.cn/Article/96979.shtml
- http://www.mobile.cvsifc.cn/Article/493068.shtml
- http://www.mobile.cvsifc.cn/Article/61387.shtml
- http://www.mobile.hcbezg.cn/Article/5577821.shtml
- http://www.mobile.fuvxie.cn/Article/6703117.shtml
- http://www.mobile.hcbezg.cn/Article/457979.shtml
- http://www.mobile.cvsifc.cn/Article/4859.shtml
- http://www.mobile.cvsifc.cn/Article/6374.shtml
- http://www.mobile.hcbezg.cn/Article/9726940.shtml
- http://www.mobile.cvsifc.cn/Article/68808.shtml
- http://www.mobile.fuvxie.cn/Article/464615.shtml
- http://www.mobile.hcbezg.cn/Article/8075.shtml
- http://www.mobile.hcbezg.cn/Article/6494.shtml
- http://www.mobile.fuvxie.cn/Article/961223.shtml
- http://www.mobile.hcbezg.cn/Article/2653129.shtml
- http://www.mobile.hcbezg.cn/Article/3784.shtml
- http://www.mobile.fuvxie.cn/Article/0501.shtml
- http://www.mobile.fuvxie.cn/Article/303829.shtml
- http://www.mobile.fuvxie.cn/Article/7652631.shtml
- http://www.mobile.hcbezg.cn/Article/3358.shtml
- http://www.mobile.fuvxie.cn/Article/78767.shtml
- http://www.mobile.fuvxie.cn/Article/23629.shtml
- http://www.mobile.cvsifc.cn/Article/1042374.shtml
- http://www.mobile.hcbezg.cn/Article/73504.shtml
- http://www.mobile.hcbezg.cn/Article/400717.shtml
- http://www.mobile.hcbezg.cn/Article/7625.shtml
- http://www.mobile.cvsifc.cn/Article/170311.shtml
- http://www.mobile.fuvxie.cn/Article/2975.shtml
- http://www.mobile.hcbezg.cn/Article/84556.shtml
- http://www.mobile.fuvxie.cn/Article/1315900.shtml
- http://www.mobile.hcbezg.cn/Article/8446.shtml
- http://www.mobile.hcbezg.cn/Article/47467.shtml
- http://www.mobile.cvsifc.cn/Article/349221.shtml
- http://www.mobile.hcbezg.cn/Article/43531.shtml
- http://www.mobile.hcbezg.cn/Article/8276349.shtml
- http://www.mobile.fuvxie.cn/Article/044213.shtml
- http://www.mobile.fuvxie.cn/Article/044064.shtml
- http://www.mobile.fuvxie.cn/Article/67667.shtml
- http://www.mobile.cvsifc.cn/Article/967238.shtml
- http://www.mobile.cvsifc.cn/Article/70597.shtml
- http://www.mobile.cvsifc.cn/Article/7126.shtml
- http://www.mobile.fuvxie.cn/Article/6904337.shtml
- http://www.mobile.fuvxie.cn/Article/23431.shtml
- http://www.mobile.cvsifc.cn/Article/7102.shtml
- http://www.mobile.hcbezg.cn/Article/3407178.shtml
- http://www.mobile.cvsifc.cn/Article/45669.shtml
- http://www.mobile.fuvxie.cn/Article/2840343.shtml
- http://www.mobile.fuvxie.cn/Article/7061.shtml
- http://www.mobile.fuvxie.cn/Article/1166321.shtml
- http://www.mobile.cvsifc.cn/Article/99703.shtml
- http://www.mobile.cvsifc.cn/Article/9786.shtml
- http://www.mobile.fuvxie.cn/Article/51180.shtml
- http://www.mobile.fuvxie.cn/Article/9197126.shtml
- http://www.mobile.cvsifc.cn/Article/9645.shtml
- http://www.mobile.hcbezg.cn/Article/86726.shtml
- http://www.mobile.hcbezg.cn/Article/72914.shtml
- http://www.mobile.fuvxie.cn/Article/82284.shtml
- http://www.mobile.cvsifc.cn/Article/146471.shtml
- http://www.mobile.hcbezg.cn/Article/8739051.shtml
- http://www.mobile.cvsifc.cn/Article/8819.shtml
- http://www.mobile.cvsifc.cn/Article/332276.shtml
- http://www.mobile.fuvxie.cn/Article/3750050.shtml
- http://www.mobile.fuvxie.cn/Article/2628938.shtml
- http://www.mobile.fuvxie.cn/Article/06379.shtml
- http://www.mobile.cvsifc.cn/Article/00126.shtml
- http://www.mobile.cvsifc.cn/Article/5022301.shtml

## 项目结构

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── core/                           # 核心业务逻辑模块
│   │   ├── resource-manager.js         # 资源增删改查与批次管理
│   │   └── validator.js                # URL 格式校验与去重
│   ├── api/                            # HTTP 接口层
│   │   ├── routes.js                   # 路由定义
│   │   └── controllers/                # 控制器：处理请求与响应
│   │       └── resource-controller.js
│   ├── db/                             # 数据库访问层
│   │   ├── sqlite-client.js            # SQLite 连接与初始化
│   │   └── migrations/                 # 表结构迁移文件
│   │       └── 001-initial-schema.sql
│   ├── ui/                             # 前端管理界面
│   │   ├── pages/                      # 页面组件（列表、详情、导入）
│   │   ├── components/                 # 通用 UI 组件（表格、筛选栏）
│   │   └── static/                     # 静态资源（样式、脚本）
│   └── utils/                          # 工具函数
│       ├── logger.js                   # 日志记录
│       └── exporter.js                 # 导出为 JSON / Markdown / TXT
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 核心模块单元测试
│   └── integration/                    # API 接口测试
├── docs/                               # 文档目录（详见文档导航）
├── scripts/                            # 辅助脚本（数据导入、批量校验）
│   └── import-batch.js                 # 从文本文件批量导入链接
├── config/                             # 配置文件目录
│   ├── default.json                    # 默认配置（端口、数据库路径）
│   └── production.json                 # 生产环境覆盖配置
├── .env.example                        # 环境变量示例
├── package.json                        # npm 依赖与脚本定义
├── README.md                           # 项目说明（本文件）
└── LICENSE                             # MIT 许可证
```

## 贡献指南

1. 复刻本仓库并在本地 clone 复刻后的版本，创建功能分支（如 feature/batch-merge）。
2. 按照项目根目录下的 .env.example 创建本地 .env 文件，配置数据库路径与日志级别。
3. 在 src/core/ 或 src/utils/ 下新增或修改功能代码，并同步更新对应的单元测试文件（tests/unit/）。
4. 运行测试套件确保全部用例通过，使用 npm test 命令执行。
5. 提交 pull request 至主仓库的 main 分支，并在描述中注明变更内容与测试覆盖情况。

## 常见问题

Q: 资源列表中的链接是否可以添加自定义标签或备注？
A: 当前版本的数据库表中已预留 meta 字段（JSON 类型），用户可通过调用更新接口向该字段写入自定义键值对，例如标签数组、阅读状态或摘要字数。前端界面暂未提供可视化编辑入口，但可通过 API 直接操作。

Q: 项目是否支持自动抓取链接对应的页面标题或摘要？
A: 本项目定位为纯链接索引工具，不内置爬虫抓取能力。但用户可在外部爬虫中调用本项目的导入接口，将抓取到的标题、发布时间等元数据一并写入 meta 字段。

Q: 批次编号是如何管理的？
A: 批次编号采用项目内全局递增序列，每创建一个新批次自动加一。当前版本不支持删除批次，以避免资源引用断裂。如需废弃某批资源，可将其状态标记为 archived。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
