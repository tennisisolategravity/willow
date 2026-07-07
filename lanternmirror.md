# LinkArchive Core

LinkArchive Core 是一个面向技术内容聚合与长期外链管理的结构化资源归档系统。该项目定位于解决技术团队、内容运营者以及独立研究者面临的分散链接难以追踪、失效风险高、分类维度缺失等问题。LinkArchive Core 不提供图形界面，而是通过标准的目录结构与元数据约定，将来自多个内容源的文章链接、静态资源与外部引用统一收纳于可版本控制的文件系统中，便于后续的自动化处理、静态站点生成或数据迁移。

目标用户包括：需要维护技术博客外链索引的开发者、进行行业信息汇总的分析人员、以及希望建立可持久化资源池的开源社区维护者。LinkArchive Core 以极低的运维成本，帮助用户从杂乱的浏览器书签或零散文档中解脱出来，形成有序、可查询、可审计的资源清单。

## 功能概览

多源文章条目归集：支持按来源域名划分存储目录，自动生成条目唯一标识，保留原始文章元数据。

批量导入与去重检查：提供脚本化工具，可将新链接列表与现有索引进行比对，避免重复收录。

元数据补全与标记：允许为每个资源条目补充标题、摘要、关键词、入库时间与状态标签。

全文索引与检索接口：内置基于文件名的模糊检索功能，可快速定位包含特定关键词的资源条目。

导出为静态站点数据：支持将已归档的链接清单导出为 JSON、YAML 或 Markdown 表格格式，供其他系统消费。

更新状态监控：提供简单的脚本检查每个链接的 HTTP 响应状态，输出失效链接报告。

权限分级访问：支持基于文件系统权限的用户组隔离，便于多人在同一归档库中协作。

## 应用场景

技术博客外链库维护：技术团队可将日常阅读中积累的参考文章、API 文档、解决方案链接统一纳入 LinkArchive Core，并按主题、来源或时间建立子目录，形成团队共享的知识索引。当需要回顾某个技术决策依据时，可通过检索快速定位原始出处。

行业事件与资讯追踪：市场分析人员或安全研究员可将不同渠道发布的行业动态、漏洞公告、版本发布信息以链接形式收录到系统中，配合日期与标签组织为时间线，便于定期生成简报或态势报告。

项目依赖与文档溯源：开源项目维护者可将项目依赖的规范标准、参考实现、第三方库主页等链接集中归档，避免因外部链接失效导致项目文档或构建脚本中的引用不可追溯。

多来源内容聚合发布：内容聚合站点或导航站运营者可以使用 LinkArchive Core 作为后台数据源，通过对已归档链接进行筛选与排序，快速生成特定主题的推荐列表或精选集，而不必重复手动编写 HTML。

## 快速开始

以下操作步骤演示了如何获取 LinkArchive Core 的基础版本，并完成首次环境配置与运行。

```bash
# 克隆项目仓库
git clone https://github.com/linkarchive/core.git linkarchive-core

# 进入项目目录
cd linkarchive-core

# 安装基础依赖（Python 3.8+ 与 pip）
pip install -r requirements.txt

# 初始化归档索引数据库（SQLite）
python scripts/init_db.py

# 运行导入示例数据
python scripts/import_links.py --source examples/sample_links.csv

# 启动本地检索服务（默认端口 8080）
python app.py --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 核心运行环境，用于执行导入、检索与导出脚本 |
| pip | 20.0 或更高 | Python 包管理器，用于安装 requirements.txt 中列出的库 |
| SQLite | 3.31 或更高 | 轻量级嵌入式数据库，用于存储资源索引与元数据 |
| Git | 2.25 或更高 | 用于克隆仓库及版本管理（非运行时强制，但建议） |
| 磁盘空间 | 至少 200 MB | 用于存储索引文件与缓存资源快照（不包含原始内容，仅链接与元数据） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何最快搭建一个可用实例，以及首次归档需要执行哪些命令 |
| 数据格式规范 | docs/data-spec.md | 导入文件应采用何种 CSV 或 JSON 结构，字段定义与数据类型是什么 |
| 检索与导出 | docs/query.md | 如何通过命令行或 HTTP 接口进行检索，支持哪些过滤条件和导出格式 |
| 运维与故障排查 | docs/maintenance.md | 如何更新链接状态、处理失效链接、备份数据库以及解决常见错误 |

## 资源列表

- http://m.mobile.cvsifc.cn/Article/020767.shtml
- http://m.mobile.cvsifc.cn/Article/48094.shtml
- http://m.mobile.hcbezg.cn/Article/3852873.shtml
- http://m.mobile.fuvxie.cn/Article/0094.shtml
- http://m.mobile.fuvxie.cn/Article/2978.shtml
- http://m.mobile.fuvxie.cn/Article/107516.shtml
- http://m.mobile.hcbezg.cn/Article/5392397.shtml
- http://m.mobile.cvsifc.cn/Article/094990.shtml
- http://m.mobile.cvsifc.cn/Article/44212.shtml
- http://m.mobile.cvsifc.cn/Article/841782.shtml
- http://m.mobile.hcbezg.cn/Article/6139350.shtml
- http://m.mobile.hcbezg.cn/Article/871626.shtml
- http://m.mobile.hcbezg.cn/Article/1389.shtml
- http://m.mobile.cvsifc.cn/Article/511632.shtml
- http://m.mobile.fuvxie.cn/Article/693634.shtml
- http://m.mobile.fuvxie.cn/Article/854547.shtml
- http://m.mobile.cvsifc.cn/Article/9406123.shtml
- http://m.mobile.cvsifc.cn/Article/8454033.shtml
- http://m.mobile.fuvxie.cn/Article/229695.shtml
- http://m.mobile.fuvxie.cn/Article/4244.shtml
- http://m.mobile.hcbezg.cn/Article/94083.shtml
- http://m.mobile.hcbezg.cn/Article/407967.shtml
- http://m.mobile.fuvxie.cn/Article/929024.shtml
- http://m.mobile.cvsifc.cn/Article/8451363.shtml
- http://m.mobile.fuvxie.cn/Article/3127.shtml
- http://m.mobile.hcbezg.cn/Article/8412.shtml
- http://m.mobile.hcbezg.cn/Article/7452260.shtml
- http://m.mobile.cvsifc.cn/Article/58234.shtml
- http://m.mobile.cvsifc.cn/Article/39366.shtml
- http://m.mobile.hcbezg.cn/Article/5650109.shtml
- http://m.mobile.cvsifc.cn/Article/56055.shtml
- http://m.mobile.cvsifc.cn/Article/38214.shtml
- http://m.mobile.fuvxie.cn/Article/7803015.shtml
- http://m.mobile.fuvxie.cn/Article/103605.shtml
- http://m.mobile.hcbezg.cn/Article/63919.shtml
- http://m.mobile.fuvxie.cn/Article/2924.shtml
- http://m.mobile.hcbezg.cn/Article/9537.shtml
- http://m.mobile.cvsifc.cn/Article/986625.shtml
- http://m.mobile.cvsifc.cn/Article/5838423.shtml
- http://m.mobile.fuvxie.cn/Article/95291.shtml
- http://m.mobile.fuvxie.cn/Article/32687.shtml
- http://m.mobile.cvsifc.cn/Article/606072.shtml
- http://m.mobile.hcbezg.cn/Article/9146.shtml
- http://m.mobile.fuvxie.cn/Article/3115949.shtml
- http://m.mobile.fuvxie.cn/Article/5172.shtml
- http://m.mobile.hcbezg.cn/Article/71680.shtml
- http://m.mobile.fuvxie.cn/Article/15391.shtml
- http://m.mobile.cvsifc.cn/Article/4061.shtml
- http://m.mobile.cvsifc.cn/Article/0288012.shtml
- http://m.mobile.hcbezg.cn/Article/93737.shtml
- http://m.mobile.cvsifc.cn/Article/54286.shtml
- http://m.mobile.cvsifc.cn/Article/43819.shtml
- http://m.mobile.cvsifc.cn/Article/145051.shtml
- http://m.mobile.hcbezg.cn/Article/105138.shtml
- http://m.mobile.cvsifc.cn/Article/9216.shtml
- http://m.mobile.fuvxie.cn/Article/0080213.shtml
- http://m.mobile.cvsifc.cn/Article/7674223.shtml
- http://m.mobile.fuvxie.cn/Article/925787.shtml
- http://m.mobile.fuvxie.cn/Article/1279.shtml
- http://m.mobile.fuvxie.cn/Article/87722.shtml
- http://m.mobile.fuvxie.cn/Article/9770331.shtml
- http://m.mobile.hcbezg.cn/Article/97697.shtml
- http://m.mobile.hcbezg.cn/Article/18206.shtml
- http://m.mobile.cvsifc.cn/Article/8435.shtml
- http://m.mobile.cvsifc.cn/Article/097561.shtml
- http://m.mobile.fuvxie.cn/Article/9388090.shtml
- http://m.mobile.cvsifc.cn/Article/1988811.shtml
- http://m.mobile.fuvxie.cn/Article/7400368.shtml
- http://m.mobile.fuvxie.cn/Article/8308.shtml
- http://m.mobile.cvsifc.cn/Article/43768.shtml
- http://m.mobile.cvsifc.cn/Article/099734.shtml
- http://m.mobile.hcbezg.cn/Article/3502.shtml
- http://m.mobile.cvsifc.cn/Article/837452.shtml
- http://m.mobile.fuvxie.cn/Article/431855.shtml
- http://m.mobile.hcbezg.cn/Article/682007.shtml
- http://m.mobile.fuvxie.cn/Article/95707.shtml
- http://m.mobile.cvsifc.cn/Article/060372.shtml
- http://m.mobile.hcbezg.cn/Article/4076180.shtml
- http://m.mobile.cvsifc.cn/Article/035341.shtml
- http://m.mobile.fuvxie.cn/Article/59104.shtml
- http://m.mobile.hcbezg.cn/Article/002433.shtml
- http://m.mobile.fuvxie.cn/Article/9607.shtml
- http://m.mobile.hcbezg.cn/Article/66030.shtml
- http://m.mobile.fuvxie.cn/Article/5768.shtml
- http://m.mobile.fuvxie.cn/Article/28237.shtml
- http://m.mobile.fuvxie.cn/Article/760886.shtml
- http://m.mobile.fuvxie.cn/Article/2246.shtml
- http://m.mobile.fuvxie.cn/Article/687400.shtml
- http://m.mobile.fuvxie.cn/Article/881346.shtml
- http://m.mobile.cvsifc.cn/Article/6634273.shtml
- http://m.mobile.cvsifc.cn/Article/71527.shtml
- http://m.mobile.cvsifc.cn/Article/40318.shtml
- http://m.mobile.hcbezg.cn/Article/37790.shtml
- http://m.mobile.fuvxie.cn/Article/0966.shtml
- http://m.mobile.hcbezg.cn/Article/743839.shtml
- http://m.mobile.fuvxie.cn/Article/557832.shtml
- http://m.mobile.fuvxie.cn/Article/7358554.shtml
- http://m.mobile.fuvxie.cn/Article/3996.shtml
- http://m.mobile.hcbezg.cn/Article/526002.shtml
- http://m.mobile.hcbezg.cn/Article/6921772.shtml
- http://m.mobile.fuvxie.cn/Article/9236.shtml
- http://m.mobile.fuvxie.cn/Article/296479.shtml
- http://m.mobile.cvsifc.cn/Article/546584.shtml
- http://m.mobile.cvsifc.cn/Article/4742962.shtml
- http://m.mobile.cvsifc.cn/Article/2334.shtml
- http://m.mobile.fuvxie.cn/Article/9359.shtml
- http://m.mobile.hcbezg.cn/Article/17438.shtml
- http://m.mobile.fuvxie.cn/Article/2705.shtml
- http://m.mobile.hcbezg.cn/Article/0946643.shtml
- http://m.mobile.hcbezg.cn/Article/529464.shtml
- http://m.mobile.hcbezg.cn/Article/4282784.shtml
- http://m.mobile.fuvxie.cn/Article/67288.shtml
- http://m.mobile.fuvxie.cn/Article/6972576.shtml
- http://m.mobile.cvsifc.cn/Article/060843.shtml
- http://m.mobile.hcbezg.cn/Article/02394.shtml
- http://m.mobile.hcbezg.cn/Article/6838.shtml
- http://m.mobile.cvsifc.cn/Article/85971.shtml
- http://m.mobile.hcbezg.cn/Article/751372.shtml
- http://m.mobile.fuvxie.cn/Article/7580.shtml
- http://m.mobile.fuvxie.cn/Article/7423.shtml
- http://m.mobile.hcbezg.cn/Article/7552.shtml
- http://m.mobile.fuvxie.cn/Article/364495.shtml
- http://m.mobile.hcbezg.cn/Article/5401.shtml
- http://m.mobile.hcbezg.cn/Article/056439.shtml
- http://m.mobile.cvsifc.cn/Article/4876.shtml
- http://m.mobile.hcbezg.cn/Article/9531.shtml
- http://m.mobile.cvsifc.cn/Article/928502.shtml
- http://m.mobile.hcbezg.cn/Article/38395.shtml
- http://m.mobile.cvsifc.cn/Article/14472.shtml
- http://m.mobile.hcbezg.cn/Article/4643871.shtml
- http://m.mobile.fuvxie.cn/Article/06875.shtml
- http://m.mobile.fuvxie.cn/Article/1549.shtml
- http://m.mobile.fuvxie.cn/Article/643962.shtml
- http://m.mobile.fuvxie.cn/Article/9887.shtml
- http://m.mobile.hcbezg.cn/Article/56045.shtml
- http://m.mobile.fuvxie.cn/Article/300954.shtml
- http://m.mobile.cvsifc.cn/Article/2476.shtml
- http://m.mobile.cvsifc.cn/Article/5540.shtml
- http://m.mobile.cvsifc.cn/Article/931570.shtml
- http://m.mobile.fuvxie.cn/Article/4787900.shtml
- http://m.mobile.cvsifc.cn/Article/3007565.shtml
- http://m.mobile.fuvxie.cn/Article/1689.shtml
- http://m.mobile.cvsifc.cn/Article/370485.shtml
- http://m.mobile.cvsifc.cn/Article/01657.shtml
- http://m.mobile.fuvxie.cn/Article/4019.shtml
- http://m.mobile.cvsifc.cn/Article/2242.shtml
- http://m.mobile.hcbezg.cn/Article/1089603.shtml
- http://m.mobile.hcbezg.cn/Article/786377.shtml
- http://m.mobile.fuvxie.cn/Article/6744173.shtml
- http://m.mobile.cvsifc.cn/Article/2100156.shtml
- http://m.mobile.fuvxie.cn/Article/5266.shtml
- http://m.mobile.fuvxie.cn/Article/062460.shtml
- http://m.mobile.fuvxie.cn/Article/2940.shtml
- http://m.mobile.hcbezg.cn/Article/09446.shtml
- http://m.mobile.hcbezg.cn/Article/632767.shtml
- http://m.mobile.hcbezg.cn/Article/96048.shtml
- http://m.mobile.fuvxie.cn/Article/0409593.shtml
- http://m.mobile.hcbezg.cn/Article/990846.shtml
- http://m.mobile.hcbezg.cn/Article/754542.shtml
- http://m.mobile.cvsifc.cn/Article/29394.shtml
- http://m.mobile.hcbezg.cn/Article/914605.shtml
- http://m.mobile.cvsifc.cn/Article/57603.shtml
- http://m.mobile.hcbezg.cn/Article/56044.shtml
- http://m.mobile.fuvxie.cn/Article/44698.shtml
- http://m.mobile.fuvxie.cn/Article/77807.shtml
- http://m.mobile.cvsifc.cn/Article/1148299.shtml
- http://m.mobile.hcbezg.cn/Article/2694528.shtml
- http://m.mobile.fuvxie.cn/Article/16255.shtml
- http://m.mobile.fuvxie.cn/Article/505114.shtml
- http://m.mobile.cvsifc.cn/Article/250030.shtml
- http://m.mobile.hcbezg.cn/Article/1116249.shtml
- http://m.mobile.cvsifc.cn/Article/697844.shtml
- http://m.mobile.cvsifc.cn/Article/591884.shtml
- http://m.mobile.hcbezg.cn/Article/10928.shtml
- http://m.mobile.hcbezg.cn/Article/5258056.shtml
- http://m.mobile.cvsifc.cn/Article/8674.shtml
- http://m.mobile.hcbezg.cn/Article/429985.shtml
- http://m.mobile.hcbezg.cn/Article/21582.shtml
- http://m.mobile.cvsifc.cn/Article/6466364.shtml
- http://m.mobile.fuvxie.cn/Article/60128.shtml
- http://m.mobile.cvsifc.cn/Article/25120.shtml
- http://m.mobile.hcbezg.cn/Article/90357.shtml
- http://m.mobile.hcbezg.cn/Article/491034.shtml
- http://m.mobile.fuvxie.cn/Article/5302646.shtml
- http://m.mobile.hcbezg.cn/Article/1851151.shtml
- http://m.mobile.fuvxie.cn/Article/2382.shtml
- http://m.mobile.fuvxie.cn/Article/1729.shtml
- http://m.mobile.hcbezg.cn/Article/4125.shtml
- http://m.mobile.hcbezg.cn/Article/624548.shtml
- http://m.mobile.fuvxie.cn/Article/0644948.shtml
- http://m.mobile.fuvxie.cn/Article/4376.shtml
- http://m.mobile.fuvxie.cn/Article/6129540.shtml
- http://m.mobile.hcbezg.cn/Article/601715.shtml
- http://m.mobile.cvsifc.cn/Article/6957583.shtml
- http://m.mobile.cvsifc.cn/Article/9217165.shtml
- http://m.mobile.hcbezg.cn/Article/3365.shtml
- http://m.mobile.fuvxie.cn/Article/797147.shtml
- http://m.mobile.hcbezg.cn/Article/3900468.shtml
- http://m.mobile.hcbezg.cn/Article/09685.shtml
- http://m.mobile.fuvxie.cn/Article/63880.shtml
- http://m.mobile.cvsifc.cn/Article/5263527.shtml
- http://m.mobile.fuvxie.cn/Article/30010.shtml
- http://m.mobile.fuvxie.cn/Article/80505.shtml
- http://m.mobile.fuvxie.cn/Article/13574.shtml
- http://m.mobile.hcbezg.cn/Article/69455.shtml
- http://m.mobile.cvsifc.cn/Article/6434.shtml
- http://m.mobile.hcbezg.cn/Article/1915.shtml
- http://m.mobile.fuvxie.cn/Article/7079970.shtml
- http://m.mobile.fuvxie.cn/Article/8724949.shtml
- http://m.mobile.fuvxie.cn/Article/7855187.shtml
- http://m.mobile.fuvxie.cn/Article/35322.shtml
- http://m.mobile.fuvxie.cn/Article/75371.shtml
- http://m.mobile.cvsifc.cn/Article/7339.shtml
- http://m.mobile.cvsifc.cn/Article/76056.shtml
- http://m.mobile.cvsifc.cn/Article/6594.shtml
- http://m.mobile.fuvxie.cn/Article/2598514.shtml
- http://m.mobile.cvsifc.cn/Article/44760.shtml
- http://m.mobile.hcbezg.cn/Article/474122.shtml
- http://m.mobile.cvsifc.cn/Article/57177.shtml
- http://m.mobile.fuvxie.cn/Article/1002.shtml
- http://m.mobile.fuvxie.cn/Article/0817.shtml
- http://m.mobile.fuvxie.cn/Article/9044.shtml
- http://m.mobile.hcbezg.cn/Article/2547117.shtml
- http://m.mobile.hcbezg.cn/Article/9830.shtml
- http://m.mobile.hcbezg.cn/Article/3453.shtml
- http://m.mobile.hcbezg.cn/Article/84502.shtml
- http://m.mobile.cvsifc.cn/Article/056585.shtml
- http://m.mobile.fuvxie.cn/Article/852186.shtml
- http://m.mobile.cvsifc.cn/Article/1997116.shtml
- http://m.mobile.hcbezg.cn/Article/146632.shtml
- http://m.mobile.cvsifc.cn/Article/813101.shtml
- http://m.mobile.hcbezg.cn/Article/8336.shtml
- http://m.mobile.cvsifc.cn/Article/6517261.shtml
- http://m.mobile.fuvxie.cn/Article/6754.shtml
- http://m.mobile.cvsifc.cn/Article/3709.shtml
- http://m.mobile.cvsifc.cn/Article/3547667.shtml
- http://m.mobile.hcbezg.cn/Article/622435.shtml
- http://m.mobile.cvsifc.cn/Article/02061.shtml
- http://m.mobile.hcbezg.cn/Article/295804.shtml
- http://m.mobile.hcbezg.cn/Article/229200.shtml
- http://m.mobile.hcbezg.cn/Article/70264.shtml
- http://m.mobile.fuvxie.cn/Article/7572154.shtml
- http://m.mobile.cvsifc.cn/Article/7219.shtml
- http://m.mobile.hcbezg.cn/Article/6632.shtml
- http://m.mobile.hcbezg.cn/Article/418088.shtml
- http://m.mobile.fuvxie.cn/Article/5135.shtml
- http://m.mobile.cvsifc.cn/Article/69349.shtml
- http://m.mobile.cvsifc.cn/Article/5814989.shtml
- http://m.mobile.cvsifc.cn/Article/3641.shtml
- http://m.mobile.fuvxie.cn/Article/39551.shtml

## 项目结构

项目采用分层目录组织，按功能模块分离核心逻辑、配置、数据与工具脚本，便于维护与扩展。

```
linkarchive-core/
├── app.py                         # 命令行入口与简易 HTTP 服务启动器
├── requirements.txt               # Python 依赖清单（Flask, requests, sqlite3 等）
├── config/
│   ├── settings.yaml              # 全局配置（数据库路径、端口、缓存策略）
│   └── sources.toml               # 预定义的内容源域名与分类映射规则
├── core/
│   ├── __init__.py
│   ├── indexer.py                 # 索引建立与更新核心逻辑
│   ├── query.py                   # 检索与过滤引擎
│   ├── validator.py               # URL 格式校验、去重与状态检查
│   └── exporter.py                # 导出为 JSON / YAML / Markdown 的渲染器
├── data/
│   ├── archive.db                 # SQLite 主数据库文件（自动生成）
│   ├── snapshots/                 # 按日期存放的链接快照（只读归档）
│   └── imports/                   # 存放待导入的 CSV 或 JSON 原始文件
├── scripts/
│   ├── init_db.py                 # 初始化数据库表结构与默认配置
│   ├── import_links.py            # 从指定文件批量导入链接并去重
│   ├── check_status.py            # 批量检查已收录链接的可用性
│   └── export_site.py             # 生成静态站点数据（HTML / Markdown）
├── tests/
│   ├── test_indexer.py            # 索引模块的单元测试
│   ├── test_validator.py          # URL 校验与去重测试用例
│   └── fixtures/                  # 测试用的模拟数据（样本链接与元数据）
└── docs/
    ├── quickstart.md              # 快速入门指南
    ├── data-spec.md               # 数据格式规范说明
    ├── query.md                   # 检索语法与过滤参数参考
    └── maintenance.md             # 运维、备份与故障恢复文档
```

## 贡献指南

我们欢迎并鼓励社区提交改进建议、扩展功能或修正问题。请遵循以下步骤参与贡献。

首先，在 GitHub 上复刻（Fork）本仓库至个人账户，并将复刻后的仓库克隆到本地开发环境。

其次，新建一个以特性或修复为主题的分支，分支名称应简洁描述所处理的问题，例如 `fix-import-csv-encoding` 或 `add-json-export-option`。

第三，在相应模块中编写或修改代码，并确保所有新增功能包含对应的单元测试（位于 `tests/` 目录下），同时更新受影响的文档文件。

第四，运行完整的测试套件以验证未引入回归问题：在项目根目录执行 `pytest tests/`，并确认所有测试用例通过。

最后，提交包含清晰描述信息的变更记录（commit message），将分支推送至复刻仓库，然后通过 GitHub 界面发起合并请求（Pull Request），请求合并到主仓库的 `main` 分支。合并请求描述中应说明变更动机、实现方式以及可能的副作用。

## 常见问题

问：导入链接时提示“重复条目”，但确认该链接并未在数据库中出现，应如何处理？

答：此情况通常源于数据库中的历史快照文件或导入临时缓存中已存在相同 URL。首先，检查 `data/imports/` 目录下是否有之前未清理的临时文件。其次，可以使用 `scripts/import_links.py` 的 `--force` 参数强制覆盖已有记录。若问题依旧，建议检查 SQLite 数据库中的 `links` 表是否有冗余索引或触发器导致误判，必要时可执行 `scripts/init_db.py --reset` 重置索引（注意此操作会清空所有数据，请提前备份）。

问：检索接口返回的结果数量与实际收录数不符，可能是什么原因？

答：默认检索接口使用了分页机制，每页默认返回 20 条记录。如果希望获取全量结果，需要在请求中指定 `limit` 参数为较大值（如 `limit=1000`）或使用导出功能（`export_site.py`）生成完整清单。另外，请确认检索关键词是否包含特殊字符，部分字符在 SQLite 的 LIKE 查询中需转义，建议使用 `--exact` 参数进行精确匹配测试。

问：如何迁移 LinkArchive Core 到另一台服务器，或在不丢失数据的情况下升级版本？

答：迁移或升级时，只需备份 `data/archive.db` 数据库文件以及 `data/snapshots/` 目录下的所有快照文件。将这两个数据目录完整复制到新环境或新版本的工作目录下，然后重新运行 `scripts/init_db.py --migrate` 执行任何必要的表结构变更脚本。该迁移工具不会删除已有数据，但建议在执行前对原始数据库进行一次完整备份。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
