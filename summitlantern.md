# MapLink 聚合导航

MapLink 聚合导航是一个面向技术调研、数据采集与内容聚合场景的轻量级外链资源汇总平台。项目定位于为开发者、数据分析师与内容运营人员提供结构化的外部信息入口，通过统一的数据格式与可扩展的目录体系，将散落在多个内容源站点下的文章链接进行集中管理与快速检索。本项目不生产内容，仅提供索引与导航能力，适用于需要批量维护外部链接关系、定期同步更新资源清单或构建自定义导航页面的各类工作流。

## 功能概览

**多源链接统一收录**：支持将来自不同域名、不同路径结构的外部文章链接以标准化条目形式纳入统一索引体系，消除多源数据的手动整理成本。

**分类目录层级管理**：内置可嵌套的目录树结构，允许用户按主题、来源站点、更新批次或业务标签对链接进行多维度归类，满足复杂组织需求。

**原始格式保留输出**：所有外链在输出与展示过程中严格保持用户提交的原始 URL 格式，不自动补全协议头、不添加 www 前缀、不进行大小写转换，确保链接精确可用。

**批量导入与增量更新**：提供基于文本列表的批量链接导入接口，支持新增链接自动追加至对应目录，并记录每次批次的来源与时间戳，便于后续审计。

**链接状态快照查看**：在目录树中为每条链接附带文章标识符与来源站点信息，方便快速定位资源所属站点及内容编号，减少二次查询时间。

**纯静态化输出能力**：项目核心数据可导出为静态 Markdown 或 JSON 格式，无需动态服务端即可部署至任意 Web 容器或本地文件系统，降低运维成本。

## 应用场景

**技术调研期间的参考链接整理**：研发团队在预研新框架或新方案时，往往需要收集大量外部技术文章。使用 MapLink 可将这些分散在多个站点的链接按调研主题归类，并在团队内共享导航页面，避免重复检索。

**数据采集任务的来源清单维护**：数据采集工程师需要定期从固定来源站点抓取特定栏目下的文章。项目可将这些来源链接按站点域名分类管理，每次采集前快速核对链接列表是否有变动，确保采集任务覆盖完整。

**内容聚合站点的外链索引构建**：内容聚合类站点需要为每篇转载或引用文章保留原始出处链接。MapLink 的目录树结构可按文章分类、发布时间或来源站点组织外链，便于编辑人员维护和读者查阅出处。

**知识库外部参考资源的统一挂载**：企业知识库或项目文档中常引用大量外部资料。将外部链接集中托管在 MapLink 导航中，并在文档内通过链接引用该导航条目，可实现外部资源的一处更新、多处同步，避免文档内链接分散导致的维护困难。

## 快速开始

以下指令演示如何在本地环境中获取项目代码、安装基础依赖并启动开发服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/maplink-navigator/maplink-core.git

# 进入项目工作目录
cd maplink-core

# 安装项目依赖（基于 Node.js 18+ 与 npm）
npm install

# 启动本地开发服务器，默认监听 3000 端口
npm run dev
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 项目运行时环境，用于执行构建脚本与开发服务器 |
| npm | 9.x 或更高 | Node.js 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与管理代码变更 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，建议使用 POSIX 兼容环境以获得最佳性能 |
| 磁盘空间 | 至少 200 MB | 用于存放源代码、依赖包及生成的静态资源文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建本地环境并生成第一个链接索引页面 |
| 数据格式规范 | docs/data-format.md | 链接条目的数据结构、必填字段与扩展字段如何定义 |
| 目录树操作 | docs/directory-tree.md | 如何新增、删除或移动分类节点，以及节点间的层级规则 |
| 批量导入流程 | docs/batch-import.md | 如何准备批量链接列表、执行导入命令以及处理导入日志 |

## 资源列表

- http://map.mobile.cvsifc.cn/Article/43291.shtml
- http://map.mobile.fuvxie.cn/Article/2945884.shtml
- http://map.mobile.fuvxie.cn/Article/4802.shtml
- http://map.mobile.cvsifc.cn/Article/679983.shtml
- http://map.mobile.hcbezg.cn/Article/363727.shtml
- http://map.mobile.cvsifc.cn/Article/2997.shtml
- http://map.mobile.cvsifc.cn/Article/2352.shtml
- http://map.mobile.fuvxie.cn/Article/9543807.shtml
- http://map.mobile.cvsifc.cn/Article/181075.shtml
- http://map.mobile.cvsifc.cn/Article/33401.shtml
- http://map.mobile.cvsifc.cn/Article/46609.shtml
- http://map.mobile.cvsifc.cn/Article/5296853.shtml
- http://map.mobile.cvsifc.cn/Article/7852853.shtml
- http://map.mobile.hcbezg.cn/Article/7696.shtml
- http://map.mobile.hcbezg.cn/Article/124009.shtml
- http://map.mobile.fuvxie.cn/Article/6491.shtml
- http://map.mobile.cvsifc.cn/Article/3021351.shtml
- http://map.mobile.fuvxie.cn/Article/3047.shtml
- http://map.mobile.cvsifc.cn/Article/190930.shtml
- http://map.mobile.fuvxie.cn/Article/74385.shtml
- http://map.mobile.hcbezg.cn/Article/343942.shtml
- http://map.mobile.hcbezg.cn/Article/6856441.shtml
- http://map.mobile.cvsifc.cn/Article/1335.shtml
- http://map.mobile.hcbezg.cn/Article/8659961.shtml
- http://map.mobile.hcbezg.cn/Article/3422.shtml
- http://map.mobile.hcbezg.cn/Article/4762.shtml
- http://map.mobile.hcbezg.cn/Article/2995.shtml
- http://map.mobile.hcbezg.cn/Article/6929.shtml
- http://map.mobile.fuvxie.cn/Article/306547.shtml
- http://map.mobile.hcbezg.cn/Article/2636210.shtml
- http://map.mobile.cvsifc.cn/Article/2620.shtml
- http://map.mobile.hcbezg.cn/Article/38042.shtml
- http://map.mobile.fuvxie.cn/Article/5572594.shtml
- http://map.mobile.cvsifc.cn/Article/0858.shtml
- http://map.mobile.fuvxie.cn/Article/74932.shtml
- http://map.mobile.fuvxie.cn/Article/354961.shtml
- http://map.mobile.fuvxie.cn/Article/9995637.shtml
- http://map.mobile.cvsifc.cn/Article/15722.shtml
- http://map.mobile.cvsifc.cn/Article/079391.shtml
- http://map.mobile.cvsifc.cn/Article/5771.shtml
- http://map.mobile.hcbezg.cn/Article/4315.shtml
- http://map.mobile.hcbezg.cn/Article/6398621.shtml
- http://map.mobile.cvsifc.cn/Article/39493.shtml
- http://map.mobile.hcbezg.cn/Article/361414.shtml
- http://map.mobile.hcbezg.cn/Article/534438.shtml
- http://map.mobile.cvsifc.cn/Article/47463.shtml
- http://map.mobile.hcbezg.cn/Article/725984.shtml
- http://map.mobile.fuvxie.cn/Article/3684.shtml
- http://map.mobile.hcbezg.cn/Article/4077.shtml
- http://map.mobile.cvsifc.cn/Article/884073.shtml
- http://map.mobile.hcbezg.cn/Article/3748.shtml
- http://map.mobile.cvsifc.cn/Article/067791.shtml
- http://map.mobile.fuvxie.cn/Article/87843.shtml
- http://map.mobile.fuvxie.cn/Article/7047.shtml
- http://map.mobile.cvsifc.cn/Article/42392.shtml
- http://map.mobile.cvsifc.cn/Article/3311.shtml
- http://map.mobile.hcbezg.cn/Article/8856.shtml
- http://map.mobile.fuvxie.cn/Article/15044.shtml
- http://map.mobile.cvsifc.cn/Article/5365812.shtml
- http://map.mobile.fuvxie.cn/Article/1472.shtml
- http://map.mobile.fuvxie.cn/Article/7461.shtml
- http://map.mobile.hcbezg.cn/Article/8569.shtml
- http://map.mobile.hcbezg.cn/Article/077179.shtml
- http://map.mobile.fuvxie.cn/Article/1720165.shtml
- http://map.mobile.cvsifc.cn/Article/8252.shtml
- http://map.mobile.hcbezg.cn/Article/802832.shtml
- http://map.mobile.cvsifc.cn/Article/7801.shtml
- http://map.mobile.hcbezg.cn/Article/01916.shtml
- http://map.mobile.hcbezg.cn/Article/3602457.shtml
- http://map.mobile.fuvxie.cn/Article/165494.shtml
- http://map.mobile.fuvxie.cn/Article/237798.shtml
- http://map.mobile.fuvxie.cn/Article/7748111.shtml
- http://map.mobile.cvsifc.cn/Article/3714440.shtml
- http://map.mobile.hcbezg.cn/Article/8769.shtml
- http://map.mobile.hcbezg.cn/Article/404598.shtml
- http://map.mobile.fuvxie.cn/Article/3407618.shtml
- http://map.mobile.fuvxie.cn/Article/8255228.shtml
- http://map.mobile.cvsifc.cn/Article/82953.shtml
- http://map.mobile.cvsifc.cn/Article/905355.shtml
- http://map.mobile.fuvxie.cn/Article/2872.shtml
- http://map.mobile.cvsifc.cn/Article/89012.shtml
- http://map.mobile.fuvxie.cn/Article/174111.shtml
- http://map.mobile.hcbezg.cn/Article/76988.shtml
- http://map.mobile.fuvxie.cn/Article/10673.shtml
- http://map.mobile.fuvxie.cn/Article/120939.shtml
- http://map.mobile.cvsifc.cn/Article/714331.shtml
- http://map.mobile.fuvxie.cn/Article/5266480.shtml
- http://map.mobile.hcbezg.cn/Article/2784687.shtml
- http://map.mobile.fuvxie.cn/Article/3284.shtml
- http://map.mobile.hcbezg.cn/Article/4277676.shtml
- http://map.mobile.hcbezg.cn/Article/00216.shtml
- http://map.mobile.fuvxie.cn/Article/63927.shtml
- http://map.mobile.hcbezg.cn/Article/83950.shtml
- http://map.mobile.fuvxie.cn/Article/7064.shtml
- http://map.mobile.cvsifc.cn/Article/6415926.shtml
- http://map.mobile.cvsifc.cn/Article/959555.shtml
- http://map.mobile.fuvxie.cn/Article/04520.shtml
- http://map.mobile.fuvxie.cn/Article/132506.shtml
- http://map.mobile.cvsifc.cn/Article/058744.shtml
- http://map.mobile.fuvxie.cn/Article/9561.shtml
- http://map.mobile.fuvxie.cn/Article/2696.shtml
- http://map.mobile.hcbezg.cn/Article/11819.shtml
- http://map.mobile.hcbezg.cn/Article/850110.shtml
- http://map.mobile.fuvxie.cn/Article/7609.shtml
- http://map.mobile.hcbezg.cn/Article/00923.shtml
- http://map.mobile.cvsifc.cn/Article/0195.shtml
- http://map.mobile.fuvxie.cn/Article/1707.shtml
- http://map.mobile.hcbezg.cn/Article/76057.shtml
- http://map.mobile.hcbezg.cn/Article/200930.shtml
- http://map.mobile.fuvxie.cn/Article/087421.shtml
- http://map.mobile.cvsifc.cn/Article/2771367.shtml
- http://map.mobile.fuvxie.cn/Article/43308.shtml
- http://map.mobile.fuvxie.cn/Article/7044404.shtml
- http://map.mobile.hcbezg.cn/Article/025583.shtml
- http://map.mobile.cvsifc.cn/Article/7078.shtml
- http://map.mobile.hcbezg.cn/Article/5890.shtml
- http://map.mobile.hcbezg.cn/Article/317169.shtml
- http://map.mobile.hcbezg.cn/Article/713096.shtml
- http://map.mobile.fuvxie.cn/Article/715613.shtml
- http://map.mobile.cvsifc.cn/Article/0392303.shtml
- http://map.mobile.fuvxie.cn/Article/24270.shtml
- http://map.mobile.hcbezg.cn/Article/8439.shtml
- http://map.mobile.fuvxie.cn/Article/16055.shtml
- http://map.mobile.fuvxie.cn/Article/236688.shtml
- http://map.mobile.cvsifc.cn/Article/34103.shtml
- http://map.mobile.hcbezg.cn/Article/3990032.shtml
- http://map.mobile.fuvxie.cn/Article/7703.shtml
- http://map.mobile.fuvxie.cn/Article/863048.shtml
- http://map.mobile.cvsifc.cn/Article/7312406.shtml
- http://map.mobile.hcbezg.cn/Article/6589886.shtml
- http://map.mobile.cvsifc.cn/Article/6235.shtml
- http://map.mobile.cvsifc.cn/Article/3055.shtml
- http://map.mobile.cvsifc.cn/Article/851954.shtml
- http://map.mobile.fuvxie.cn/Article/3167323.shtml
- http://map.mobile.hcbezg.cn/Article/5139094.shtml
- http://map.mobile.hcbezg.cn/Article/4196.shtml
- http://map.mobile.fuvxie.cn/Article/1155.shtml
- http://map.mobile.hcbezg.cn/Article/760983.shtml
- http://map.mobile.cvsifc.cn/Article/3153.shtml
- http://map.mobile.cvsifc.cn/Article/496263.shtml
- http://map.mobile.fuvxie.cn/Article/87349.shtml
- http://map.mobile.fuvxie.cn/Article/05013.shtml
- http://map.mobile.fuvxie.cn/Article/15601.shtml
- http://map.mobile.cvsifc.cn/Article/36794.shtml
- http://map.mobile.cvsifc.cn/Article/2623844.shtml
- http://map.mobile.fuvxie.cn/Article/4083.shtml
- http://map.mobile.hcbezg.cn/Article/9094548.shtml
- http://map.mobile.cvsifc.cn/Article/8677559.shtml
- http://map.mobile.hcbezg.cn/Article/38155.shtml
- http://map.mobile.fuvxie.cn/Article/4979.shtml
- http://map.mobile.cvsifc.cn/Article/7186.shtml
- http://map.mobile.cvsifc.cn/Article/7054988.shtml
- http://map.mobile.cvsifc.cn/Article/85828.shtml
- http://map.mobile.hcbezg.cn/Article/327697.shtml
- http://map.mobile.cvsifc.cn/Article/05762.shtml
- http://map.mobile.fuvxie.cn/Article/90286.shtml
- http://map.mobile.hcbezg.cn/Article/4496.shtml
- http://map.mobile.hcbezg.cn/Article/0221.shtml
- http://map.mobile.hcbezg.cn/Article/8832481.shtml
- http://map.mobile.fuvxie.cn/Article/75345.shtml
- http://map.mobile.fuvxie.cn/Article/319090.shtml
- http://map.mobile.cvsifc.cn/Article/371670.shtml
- http://map.mobile.fuvxie.cn/Article/759401.shtml
- http://map.mobile.hcbezg.cn/Article/8975697.shtml
- http://map.mobile.hcbezg.cn/Article/096606.shtml
- http://map.mobile.cvsifc.cn/Article/595305.shtml
- http://map.mobile.hcbezg.cn/Article/04404.shtml
- http://map.mobile.fuvxie.cn/Article/631326.shtml
- http://map.mobile.hcbezg.cn/Article/5632636.shtml
- http://map.mobile.cvsifc.cn/Article/98986.shtml
- http://map.mobile.fuvxie.cn/Article/974578.shtml
- http://map.mobile.cvsifc.cn/Article/498612.shtml
- http://map.mobile.fuvxie.cn/Article/1211.shtml
- http://map.mobile.cvsifc.cn/Article/893700.shtml
- http://map.mobile.fuvxie.cn/Article/9102.shtml
- http://map.mobile.fuvxie.cn/Article/568583.shtml
- http://map.mobile.cvsifc.cn/Article/7372321.shtml
- http://map.mobile.cvsifc.cn/Article/971748.shtml
- http://map.mobile.hcbezg.cn/Article/031438.shtml
- http://map.mobile.cvsifc.cn/Article/4380.shtml
- http://map.mobile.cvsifc.cn/Article/811345.shtml
- http://map.mobile.hcbezg.cn/Article/6057148.shtml
- http://map.mobile.fuvxie.cn/Article/88656.shtml
- http://map.mobile.cvsifc.cn/Article/9906380.shtml
- http://map.mobile.fuvxie.cn/Article/64063.shtml
- http://map.mobile.fuvxie.cn/Article/71245.shtml
- http://map.mobile.hcbezg.cn/Article/49364.shtml
- http://map.mobile.hcbezg.cn/Article/8881.shtml
- http://map.mobile.fuvxie.cn/Article/2860.shtml
- http://map.mobile.hcbezg.cn/Article/6283.shtml
- http://map.mobile.fuvxie.cn/Article/928787.shtml
- http://map.mobile.hcbezg.cn/Article/39759.shtml
- http://map.mobile.fuvxie.cn/Article/38356.shtml
- http://map.mobile.fuvxie.cn/Article/0580378.shtml
- http://map.mobile.fuvxie.cn/Article/8826.shtml
- http://map.mobile.fuvxie.cn/Article/69265.shtml
- http://map.mobile.cvsifc.cn/Article/73690.shtml
- http://map.mobile.cvsifc.cn/Article/24583.shtml
- http://map.mobile.fuvxie.cn/Article/3401.shtml
- http://map.mobile.hcbezg.cn/Article/076783.shtml
- http://map.mobile.fuvxie.cn/Article/22998.shtml
- http://map.mobile.hcbezg.cn/Article/450857.shtml
- http://map.mobile.fuvxie.cn/Article/0807720.shtml
- http://map.mobile.hcbezg.cn/Article/9471.shtml
- http://map.mobile.cvsifc.cn/Article/785010.shtml
- http://map.mobile.fuvxie.cn/Article/83842.shtml
- http://map.mobile.fuvxie.cn/Article/985863.shtml
- http://map.mobile.hcbezg.cn/Article/721896.shtml
- http://map.mobile.cvsifc.cn/Article/121916.shtml
- http://map.mobile.cvsifc.cn/Article/581837.shtml
- http://map.mobile.fuvxie.cn/Article/468805.shtml
- http://map.mobile.hcbezg.cn/Article/7967.shtml
- http://map.mobile.hcbezg.cn/Article/615095.shtml
- http://map.mobile.cvsifc.cn/Article/124577.shtml
- http://map.mobile.hcbezg.cn/Article/6226.shtml
- http://map.mobile.fuvxie.cn/Article/51705.shtml
- http://map.mobile.cvsifc.cn/Article/66320.shtml
- http://map.mobile.fuvxie.cn/Article/001555.shtml
- http://map.mobile.fuvxie.cn/Article/947108.shtml
- http://map.mobile.cvsifc.cn/Article/0873.shtml
- http://map.mobile.hcbezg.cn/Article/398120.shtml
- http://map.mobile.fuvxie.cn/Article/2508432.shtml
- http://map.mobile.hcbezg.cn/Article/37322.shtml
- http://map.mobile.fuvxie.cn/Article/7428889.shtml
- http://map.mobile.cvsifc.cn/Article/97159.shtml
- http://map.mobile.fuvxie.cn/Article/281794.shtml
- http://map.mobile.cvsifc.cn/Article/628978.shtml
- http://map.mobile.cvsifc.cn/Article/0984.shtml
- http://map.mobile.cvsifc.cn/Article/333569.shtml
- http://map.mobile.hcbezg.cn/Article/7525364.shtml
- http://map.mobile.fuvxie.cn/Article/35604.shtml
- http://map.mobile.hcbezg.cn/Article/710917.shtml
- http://map.mobile.hcbezg.cn/Article/4157133.shtml
- http://map.mobile.fuvxie.cn/Article/19420.shtml
- http://map.mobile.fuvxie.cn/Article/97531.shtml
- http://map.mobile.hcbezg.cn/Article/353124.shtml
- http://map.mobile.cvsifc.cn/Article/00996.shtml
- http://map.mobile.hcbezg.cn/Article/5637.shtml
- http://map.mobile.fuvxie.cn/Article/2147.shtml
- http://map.mobile.hcbezg.cn/Article/3961.shtml
- http://map.mobile.hcbezg.cn/Article/4791.shtml
- http://map.mobile.fuvxie.cn/Article/78570.shtml
- http://map.mobile.fuvxie.cn/Article/90985.shtml
- http://map.mobile.cvsifc.cn/Article/0988081.shtml
- http://map.mobile.fuvxie.cn/Article/89485.shtml
- http://map.mobile.cvsifc.cn/Article/385971.shtml
- http://map.mobile.fuvxie.cn/Article/7614824.shtml
- http://map.mobile.hcbezg.cn/Article/9986386.shtml
- http://map.mobile.hcbezg.cn/Article/0741358.shtml
- http://map.mobile.cvsifc.cn/Article/9264256.shtml

## 项目结构

```
maplink-core/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心数据模型与索引引擎
│   │   ├── linkRegistry.js        # 链接注册与查询接口
│   │   └── directoryTree.js       # 目录树节点操作与遍历逻辑
│   ├── parsers/                   # 外部链接格式解析器
│   │   ├── urlNormalizer.js       # URL 格式校验与保留原样输出
│   │   └── batchImporter.js       # 批量列表导入与去重处理
│   ├── generators/                # 静态输出生成器
│   │   ├── markdownRenderer.js    # 将索引数据渲染为 Markdown 列表
│   │   └── jsonExporter.js        # 导出 JSON 格式索引供外部调用
│   ├── cli/                       # 命令行交互入口
│   │   └── commands.js            # 定义 add、list、export 等子命令
│   └── utils/                     # 通用工具函数
│       ├── fileSystem.js          # 文件读写与目录操作封装
│       └── logger.js              # 日志输出与错误追踪
├── config/                        # 项目配置文件
│   ├── default.yaml               # 默认运行参数
│   └── schema.json                # 链接数据结构的 JSON Schema 定义
├── data/                          # 用户数据存储目录（自动生成）
│   ├── links.json                 # 所有链接条目的持久化存储
│   └── tree.json                  # 目录树结构的持久化存储
├── docs/                          # 项目文档
│   ├── getting-started.md         # 快速入门指南
│   ├── data-format.md             # 数据格式规范
│   ├── directory-tree.md          # 目录树操作文档
│   └── batch-import.md            # 批量导入流程说明
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单元测试用例
│   └── fixtures/                  # 测试固定数据样本
├── .gitignore                     # Git 忽略规则
├── package.json                   # Node.js 项目清单与依赖声明
├── README.md                      # 项目说明文档（本文件）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账号，并克隆 fork 后的仓库到本地开发环境。
2. 在本地新建功能分支，分支命名建议采用 `feature/功能简述` 或 `fix/问题简述` 格式，避免在主分支上直接修改。
3. 完成代码修改后，运行测试套件确保现有功能未发生回归，新增功能需补充对应的单元测试用例。
4. 提交代码时遵循项目的提交信息规范，使用 `type(scope): subject` 格式，其中 type 可选 feat、fix、docs、refactor 等。
5. 向原仓库发起 Pull Request，并在 PR 描述中清楚说明变更目的、实现方式及影响范围，等待维护者审查。

## 常见问题

**问：导入链接时是否会自动补全协议头或标准化域名格式？**

答：项目不会对用户提交的原始 URL 做任何自动补全或格式改写。所有链接按照用户输入的原样存储和输出，包括协议头（http 或 https）、域名前缀（www 或裸域名）以及路径大小写。用户需要在提交时自行确保链接的准确性与可访问性。

**问：如何更新已导入的链接内容或调整其所属分类？**

答：项目提供链接更新指令，用户可通过命令行指定目标链接的唯一标识符（基于完整 URL 生成），然后修改其分类路径或补充描述字段。修改操作会同步更新持久化存储文件，并在目录树中自动调整节点归属。具体命令用法请参考 docs/directory-tree.md 文档中的更新章节。

**问：项目是否支持自定义输出模板或扩展字段？**

答：项目核心数据模型预留了扩展字段（extras），用户可在导入时为每条链接附加自定义键值对。输出生成器支持通过配置文件切换渲染模板，用户可参考 config/default.yaml 中的 render 段落自行调整 Markdown 或 JSON 输出格式。更复杂的输出需求可继承 generators 基类实现自定义渲染器。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
