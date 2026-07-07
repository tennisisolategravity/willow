# Mobile Resource Aggregator (MRA)

Mobile Resource Aggregator 是一个面向移动端开发人员、技术内容策展人和信息分析师的轻量级外链资源汇总系统。该项目旨在解决移动互联网环境下技术文章、行业报告、开发文档与案例分析分散于多个内容源，缺乏统一索引和快速检索入口的问题。MRA 本身不存储任何正文内容，仅提供结构化的外链索引、分类标签和基础元数据提取服务，适用于构建个人或团队内部的技术阅读清单、垂直领域知识库或自动化内容采集管道的上游入口。

MRA 的设计目标用户包括：需要定期跟踪特定技术站点更新动态的研发工程师、从事移动行业竞品分析的产品经理、以及希望建立自有轻量级内容导航站点的独立开发者。项目采用静态链接聚合模式，无需后端数据库，依赖 Git 版本控制管理链接增删改，支持通过 Markdown 与 YAML Frontmatter 混合编排元数据，可无缝对接静态站点生成器或 CI/CD 自动化检测流程。

## 功能概览

**多源链接统一索引** 提供对多个内容域名下文章链接的扁平化收录，支持按来源域名、文章编号范围、采集批次进行快速筛选。

**元数据自动提取** 对收录的每条外链自动解析 URL 结构，抽取域名、资源类型（Article）、数字标识符，并记录采集批次号与时间戳。

**批次化管理机制** 以 60 批为一个大周期，每批最多容纳 250 个资源链接，便于团队协作时划分任务边界和追踪采集进度。

**Markdown 原生编排** 所有链接清单、分类标签、备注说明均以 Markdown 纯文本格式存储，无需专用编辑器，兼容 Git 差异对比。

**静态站点生成适配** 项目目录结构遵循通用静态站点生成器（如 Hugo、Jekyll、VuePress）的约定，可一键生成为带搜索功能的导航页面。

**外链健康状态检查接口** 提供 Shell 脚本示例，用于批量检测收录链接的 HTTP 状态码，自动标记失效链接便于后续清理。

**权限分级与审阅标记** 支持为每条链接添加状态标签（待审阅/已发布/已归档），适用于多人在线协作维护链接库的场景。

## 应用场景

**移动端技术日报汇编** 团队技术负责人每日从收录的链接池中筛选 5-10 条高质量文章，生成内部技术早报发送给研发组成员，节省重复搜索时间。

**竞品动态监控看板** 产品团队将竞品官方发布站点、行业媒体专栏链接纳入 MRA 管理，每周定期批量检测链接更新情况，快速定位新发布的版本说明或案例研究。

**个人知识库冷存储层** 独立开发者将日常浏览中发现的值得留存的技术问答、代码片段解析链接统一存入 MRA，通过 Git 仓库同步至多台设备，形成可检索的个人阅读清单。

**自动化采集管道入口** 数据工程师将 MRA 中的链接列表作为爬虫任务队列的数据源，按批次调度采集任务，避免爬虫因入口分散而遗漏目标页面。

**开源文档外部参考附录** 开源项目维护者将项目文档中引用的外部参考资料链接迁移至 MRA 统一管理，保持 README 正文简洁，同时确保引用链接的可维护性。

## 快速开始

以下命令演示如何将 MRA 项目克隆至本地、安装基础依赖（仅需 Git 和标准 Unix 工具链）并运行初始链接清单检查脚本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/mobile-resource-aggregator.git
cd mobile-resource-aggregator

# 安装依赖（项目本身无第三方依赖，仅建议安装 link-checker 用于健康检查）
# 以下为可选步骤，使用 Python 3 安装链接检查工具
pip install link-checker

# 运行基础检查脚本，验证当前批次链接格式
./scripts/check-links.sh batches/28_60.txt

# 生成统计报告
./scripts/gen-stats.sh
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Git | 2.20 及以上 | 用于克隆仓库和提交链接变更记录 |
| Bash | 4.0 及以上 | 运行项目提供的辅助 Shell 脚本 |
| Python 3 | 3.6 及以上 | 仅当需要使用 link-checker 或自定义解析脚本时必需 |
| GNU Coreutils | 8.0 及以上 | 提供 sort、uniq、wc 等基础命令用于统计 |
| curl | 7.0 及以上 | 用于外链健康状态检测脚本中的 HTTP 请求 |
| grep | 3.0 及以上 | 用于链接格式校验和域名提取 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/usage.md | 如何收录新链接、如何编辑已有链接元数据、如何生成不同格式的链接清单 |
| 运维指南 | docs/operations.md | 如何配置自动化检查定时任务、如何备份链接库、如何处理失效链接 |
| 贡献规范 | docs/contributing.md | 提交链接的格式标准、批次编号规则、审核流程与合并请求模板 |
| 设计说明 | docs/design.md | 项目目录结构设计缘由、元数据字段定义、静态站点生成适配方案 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/32104.shtml
- http://www.mobile.fuvxie.cn/Article/5640902.shtml
- http://www.mobile.fuvxie.cn/Article/1167128.shtml
- http://www.mobile.hcbezg.cn/Article/588985.shtml
- http://www.mobile.hcbezg.cn/Article/225323.shtml
- http://www.mobile.hcbezg.cn/Article/6124972.shtml
- http://www.mobile.hcbezg.cn/Article/1505.shtml
- http://www.mobile.hcbezg.cn/Article/552297.shtml
- http://www.mobile.cvsifc.cn/Article/1421218.shtml
- http://www.mobile.fuvxie.cn/Article/8989.shtml
- http://www.mobile.cvsifc.cn/Article/803573.shtml
- http://www.mobile.cvsifc.cn/Article/83512.shtml
- http://www.mobile.hcbezg.cn/Article/51233.shtml
- http://www.mobile.fuvxie.cn/Article/349984.shtml
- http://www.mobile.hcbezg.cn/Article/2075.shtml
- http://www.mobile.hcbezg.cn/Article/63383.shtml
- http://www.mobile.hcbezg.cn/Article/372653.shtml
- http://www.mobile.hcbezg.cn/Article/3491.shtml
- http://www.mobile.fuvxie.cn/Article/659939.shtml
- http://www.mobile.cvsifc.cn/Article/70900.shtml
- http://www.mobile.cvsifc.cn/Article/91518.shtml
- http://www.mobile.fuvxie.cn/Article/42856.shtml
- http://www.mobile.hcbezg.cn/Article/674202.shtml
- http://www.mobile.cvsifc.cn/Article/0999.shtml
- http://www.mobile.hcbezg.cn/Article/4528.shtml
- http://www.mobile.fuvxie.cn/Article/40473.shtml
- http://www.mobile.cvsifc.cn/Article/9986.shtml
- http://www.mobile.cvsifc.cn/Article/9962.shtml
- http://www.mobile.fuvxie.cn/Article/024084.shtml
- http://www.mobile.cvsifc.cn/Article/8062899.shtml
- http://www.mobile.hcbezg.cn/Article/9213047.shtml
- http://www.mobile.hcbezg.cn/Article/5641.shtml
- http://www.mobile.cvsifc.cn/Article/8873027.shtml
- http://www.mobile.fuvxie.cn/Article/394605.shtml
- http://www.mobile.fuvxie.cn/Article/3945349.shtml
- http://www.mobile.cvsifc.cn/Article/3066.shtml
- http://www.mobile.hcbezg.cn/Article/738491.shtml
- http://www.mobile.cvsifc.cn/Article/031352.shtml
- http://www.mobile.hcbezg.cn/Article/59420.shtml
- http://www.mobile.cvsifc.cn/Article/8084.shtml
- http://www.mobile.hcbezg.cn/Article/6385.shtml
- http://www.mobile.cvsifc.cn/Article/741398.shtml
- http://www.mobile.fuvxie.cn/Article/39373.shtml
- http://www.mobile.hcbezg.cn/Article/5628263.shtml
- http://www.mobile.hcbezg.cn/Article/34126.shtml
- http://www.mobile.hcbezg.cn/Article/379456.shtml
- http://www.mobile.fuvxie.cn/Article/43562.shtml
- http://www.mobile.fuvxie.cn/Article/2442.shtml
- http://www.mobile.hcbezg.cn/Article/08554.shtml
- http://www.mobile.hcbezg.cn/Article/449426.shtml
- http://www.mobile.fuvxie.cn/Article/5508779.shtml
- http://www.mobile.cvsifc.cn/Article/802973.shtml
- http://www.mobile.fuvxie.cn/Article/01989.shtml
- http://www.mobile.cvsifc.cn/Article/06529.shtml
- http://www.mobile.cvsifc.cn/Article/746327.shtml
- http://www.mobile.fuvxie.cn/Article/4961128.shtml
- http://www.mobile.fuvxie.cn/Article/2050919.shtml
- http://www.mobile.fuvxie.cn/Article/58122.shtml
- http://www.mobile.fuvxie.cn/Article/235865.shtml
- http://www.mobile.hcbezg.cn/Article/3641.shtml
- http://www.mobile.fuvxie.cn/Article/5850183.shtml
- http://www.mobile.hcbezg.cn/Article/92564.shtml
- http://www.mobile.cvsifc.cn/Article/6794683.shtml
- http://www.mobile.cvsifc.cn/Article/5894713.shtml
- http://www.mobile.fuvxie.cn/Article/6884.shtml
- http://www.mobile.cvsifc.cn/Article/3288.shtml
- http://www.mobile.hcbezg.cn/Article/5745.shtml
- http://www.mobile.hcbezg.cn/Article/0353.shtml
- http://www.mobile.hcbezg.cn/Article/4911.shtml
- http://www.mobile.hcbezg.cn/Article/424427.shtml
- http://www.mobile.cvsifc.cn/Article/49854.shtml
- http://www.mobile.hcbezg.cn/Article/767928.shtml
- http://www.mobile.cvsifc.cn/Article/87654.shtml
- http://www.mobile.hcbezg.cn/Article/536530.shtml
- http://www.mobile.cvsifc.cn/Article/9768670.shtml
- http://www.mobile.cvsifc.cn/Article/551735.shtml
- http://www.mobile.hcbezg.cn/Article/7958406.shtml
- http://www.mobile.fuvxie.cn/Article/618566.shtml
- http://www.mobile.fuvxie.cn/Article/6249.shtml
- http://www.mobile.fuvxie.cn/Article/1987.shtml
- http://www.mobile.cvsifc.cn/Article/4555.shtml
- http://www.mobile.fuvxie.cn/Article/1558.shtml
- http://www.mobile.hcbezg.cn/Article/7892.shtml
- http://www.mobile.fuvxie.cn/Article/217771.shtml
- http://www.mobile.fuvxie.cn/Article/1084661.shtml
- http://www.mobile.fuvxie.cn/Article/4015.shtml
- http://www.mobile.hcbezg.cn/Article/1263982.shtml
- http://www.mobile.cvsifc.cn/Article/51545.shtml
- http://www.mobile.cvsifc.cn/Article/84900.shtml
- http://www.mobile.hcbezg.cn/Article/2631.shtml
- http://www.mobile.cvsifc.cn/Article/2521.shtml
- http://www.mobile.hcbezg.cn/Article/489654.shtml
- http://www.mobile.fuvxie.cn/Article/204439.shtml
- http://www.mobile.cvsifc.cn/Article/3135.shtml
- http://www.mobile.cvsifc.cn/Article/2513.shtml
- http://www.mobile.cvsifc.cn/Article/2883.shtml
- http://www.mobile.fuvxie.cn/Article/5829.shtml
- http://www.mobile.hcbezg.cn/Article/5688296.shtml
- http://www.mobile.hcbezg.cn/Article/2344.shtml
- http://www.mobile.fuvxie.cn/Article/5656205.shtml
- http://www.mobile.hcbezg.cn/Article/1997490.shtml
- http://www.mobile.fuvxie.cn/Article/9524.shtml
- http://www.mobile.cvsifc.cn/Article/2752.shtml
- http://www.mobile.hcbezg.cn/Article/92691.shtml
- http://www.mobile.hcbezg.cn/Article/1167515.shtml
- http://www.mobile.cvsifc.cn/Article/76690.shtml
- http://www.mobile.hcbezg.cn/Article/732144.shtml
- http://www.mobile.cvsifc.cn/Article/9446.shtml
- http://www.mobile.cvsifc.cn/Article/75212.shtml
- http://www.mobile.fuvxie.cn/Article/2315476.shtml
- http://www.mobile.fuvxie.cn/Article/336636.shtml
- http://www.mobile.hcbezg.cn/Article/1418.shtml
- http://www.mobile.cvsifc.cn/Article/5767376.shtml
- http://www.mobile.fuvxie.cn/Article/5480.shtml
- http://www.mobile.cvsifc.cn/Article/9174.shtml
- http://www.mobile.fuvxie.cn/Article/579617.shtml
- http://www.mobile.hcbezg.cn/Article/6609966.shtml
- http://www.mobile.cvsifc.cn/Article/975965.shtml
- http://www.mobile.cvsifc.cn/Article/9490.shtml
- http://www.mobile.hcbezg.cn/Article/23595.shtml
- http://www.mobile.cvsifc.cn/Article/679874.shtml
- http://www.mobile.hcbezg.cn/Article/10715.shtml
- http://www.mobile.cvsifc.cn/Article/22126.shtml
- http://www.mobile.cvsifc.cn/Article/941250.shtml
- http://www.mobile.fuvxie.cn/Article/850132.shtml
- http://www.mobile.hcbezg.cn/Article/32819.shtml
- http://www.mobile.hcbezg.cn/Article/6107.shtml
- http://www.mobile.hcbezg.cn/Article/2245999.shtml
- http://www.mobile.fuvxie.cn/Article/6784444.shtml
- http://www.mobile.hcbezg.cn/Article/98595.shtml
- http://www.mobile.fuvxie.cn/Article/4586744.shtml
- http://www.mobile.cvsifc.cn/Article/784357.shtml
- http://www.mobile.hcbezg.cn/Article/817919.shtml
- http://www.mobile.fuvxie.cn/Article/323704.shtml
- http://www.mobile.fuvxie.cn/Article/5741.shtml
- http://www.mobile.fuvxie.cn/Article/6886.shtml
- http://www.mobile.cvsifc.cn/Article/177315.shtml
- http://www.mobile.cvsifc.cn/Article/3836.shtml
- http://www.mobile.hcbezg.cn/Article/5231829.shtml
- http://www.mobile.fuvxie.cn/Article/5335.shtml
- http://www.mobile.fuvxie.cn/Article/826424.shtml
- http://www.mobile.cvsifc.cn/Article/6638175.shtml
- http://www.mobile.hcbezg.cn/Article/41192.shtml
- http://www.mobile.cvsifc.cn/Article/1418.shtml
- http://www.mobile.hcbezg.cn/Article/0840.shtml
- http://www.mobile.fuvxie.cn/Article/624649.shtml
- http://www.mobile.fuvxie.cn/Article/1074.shtml
- http://www.mobile.cvsifc.cn/Article/5170042.shtml
- http://www.mobile.fuvxie.cn/Article/5027.shtml
- http://www.mobile.hcbezg.cn/Article/8785492.shtml
- http://www.mobile.fuvxie.cn/Article/905280.shtml
- http://www.mobile.fuvxie.cn/Article/1720.shtml
- http://www.mobile.cvsifc.cn/Article/1530.shtml
- http://www.mobile.fuvxie.cn/Article/4581.shtml
- http://www.mobile.fuvxie.cn/Article/88611.shtml
- http://www.mobile.cvsifc.cn/Article/8477938.shtml
- http://www.mobile.fuvxie.cn/Article/035910.shtml
- http://www.mobile.hcbezg.cn/Article/099912.shtml
- http://www.mobile.fuvxie.cn/Article/2593.shtml
- http://www.mobile.fuvxie.cn/Article/5995.shtml
- http://www.mobile.cvsifc.cn/Article/0581454.shtml
- http://www.mobile.cvsifc.cn/Article/8827405.shtml
- http://www.mobile.cvsifc.cn/Article/2998843.shtml
- http://www.mobile.fuvxie.cn/Article/65626.shtml
- http://www.mobile.fuvxie.cn/Article/21695.shtml
- http://www.mobile.fuvxie.cn/Article/8191299.shtml
- http://www.mobile.fuvxie.cn/Article/6963649.shtml
- http://www.mobile.cvsifc.cn/Article/5724.shtml
- http://www.mobile.fuvxie.cn/Article/88219.shtml
- http://www.mobile.hcbezg.cn/Article/428483.shtml
- http://www.mobile.hcbezg.cn/Article/489936.shtml
- http://www.mobile.fuvxie.cn/Article/983202.shtml
- http://www.mobile.hcbezg.cn/Article/8770327.shtml
- http://www.mobile.hcbezg.cn/Article/1634.shtml
- http://www.mobile.hcbezg.cn/Article/4045.shtml
- http://www.mobile.cvsifc.cn/Article/0050246.shtml
- http://www.mobile.hcbezg.cn/Article/644399.shtml
- http://www.mobile.fuvxie.cn/Article/0012084.shtml
- http://www.mobile.cvsifc.cn/Article/8956.shtml
- http://www.mobile.hcbezg.cn/Article/9714439.shtml
- http://www.mobile.hcbezg.cn/Article/98973.shtml
- http://www.mobile.cvsifc.cn/Article/1428.shtml
- http://www.mobile.fuvxie.cn/Article/5269224.shtml
- http://www.mobile.cvsifc.cn/Article/84788.shtml
- http://www.mobile.hcbezg.cn/Article/74354.shtml
- http://www.mobile.hcbezg.cn/Article/2370455.shtml
- http://www.mobile.hcbezg.cn/Article/0194.shtml
- http://www.mobile.fuvxie.cn/Article/60925.shtml
- http://www.mobile.fuvxie.cn/Article/6787.shtml
- http://www.mobile.fuvxie.cn/Article/774603.shtml
- http://www.mobile.fuvxie.cn/Article/821155.shtml
- http://www.mobile.hcbezg.cn/Article/77059.shtml
- http://www.mobile.cvsifc.cn/Article/6543.shtml
- http://www.mobile.hcbezg.cn/Article/9742622.shtml
- http://www.mobile.fuvxie.cn/Article/9864.shtml
- http://www.mobile.cvsifc.cn/Article/31932.shtml
- http://www.mobile.hcbezg.cn/Article/615367.shtml
- http://www.mobile.hcbezg.cn/Article/9545917.shtml
- http://www.mobile.hcbezg.cn/Article/6927961.shtml
- http://www.mobile.cvsifc.cn/Article/85936.shtml
- http://www.mobile.cvsifc.cn/Article/3592.shtml
- http://www.mobile.fuvxie.cn/Article/5639533.shtml
- http://www.mobile.fuvxie.cn/Article/376048.shtml
- http://www.mobile.fuvxie.cn/Article/7928890.shtml
- http://www.mobile.hcbezg.cn/Article/8645.shtml
- http://www.mobile.fuvxie.cn/Article/897843.shtml
- http://www.mobile.cvsifc.cn/Article/84486.shtml
- http://www.mobile.fuvxie.cn/Article/7534585.shtml
- http://www.mobile.cvsifc.cn/Article/87192.shtml
- http://www.mobile.cvsifc.cn/Article/215446.shtml
- http://www.mobile.fuvxie.cn/Article/54895.shtml
- http://www.mobile.cvsifc.cn/Article/384385.shtml
- http://www.mobile.hcbezg.cn/Article/0415.shtml
- http://www.mobile.cvsifc.cn/Article/565718.shtml
- http://www.mobile.fuvxie.cn/Article/4692.shtml
- http://www.mobile.cvsifc.cn/Article/65968.shtml
- http://www.mobile.fuvxie.cn/Article/72577.shtml
- http://www.mobile.cvsifc.cn/Article/120844.shtml
- http://www.mobile.cvsifc.cn/Article/280258.shtml
- http://www.mobile.fuvxie.cn/Article/05788.shtml
- http://www.mobile.cvsifc.cn/Article/2397.shtml
- http://www.mobile.cvsifc.cn/Article/1229.shtml
- http://www.mobile.hcbezg.cn/Article/9184.shtml
- http://www.mobile.cvsifc.cn/Article/7382435.shtml
- http://www.mobile.fuvxie.cn/Article/2746756.shtml
- http://www.mobile.hcbezg.cn/Article/791250.shtml
- http://www.mobile.fuvxie.cn/Article/2052135.shtml
- http://www.mobile.cvsifc.cn/Article/4195968.shtml
- http://www.mobile.cvsifc.cn/Article/392943.shtml
- http://www.mobile.fuvxie.cn/Article/137177.shtml
- http://www.mobile.cvsifc.cn/Article/187256.shtml
- http://www.mobile.hcbezg.cn/Article/37600.shtml
- http://www.mobile.fuvxie.cn/Article/608151.shtml
- http://www.mobile.cvsifc.cn/Article/9160.shtml
- http://www.mobile.fuvxie.cn/Article/87067.shtml
- http://www.mobile.hcbezg.cn/Article/7969.shtml
- http://www.mobile.cvsifc.cn/Article/3679.shtml
- http://www.mobile.fuvxie.cn/Article/6874.shtml
- http://www.mobile.fuvxie.cn/Article/6540.shtml
- http://www.mobile.hcbezg.cn/Article/6541914.shtml
- http://www.mobile.fuvxie.cn/Article/134060.shtml
- http://www.mobile.cvsifc.cn/Article/1789.shtml
- http://www.mobile.hcbezg.cn/Article/684730.shtml
- http://www.mobile.fuvxie.cn/Article/11584.shtml
- http://www.mobile.fuvxie.cn/Article/462815.shtml
- http://www.mobile.fuvxie.cn/Article/855355.shtml
- http://www.mobile.fuvxie.cn/Article/820212.shtml
- http://www.mobile.fuvxie.cn/Article/8147271.shtml
- http://www.mobile.cvsifc.cn/Article/5289632.shtml
- http://www.mobile.hcbezg.cn/Article/1308485.shtml

## 项目结构

项目采用按批次和功能模块分层组织的目录结构，便于扩展和维护。

```
mobile-resource-aggregator/
├── batches/                         # 批次链接原始数据存放目录
│   ├── 28_60.txt                    # 第28批完整链接清单（当前批次）
│   ├── 28_60_metadata.yaml          # 第28批元数据（采集时间、标签、备注）
│   └── archive/                     # 历史批次归档目录
│       ├── 01_60.txt
│       ├── 02_60.txt
│       └── ...
├── scripts/                         # 辅助运维脚本集合
│   ├── check-links.sh               # 检查链接格式与域名合规性
│   ├── gen-stats.sh                 # 生成批次统计报告（总数、域名分布）
│   ├── health-check.py              # 批量检测外链HTTP状态码（Python）
│   └── deduplicate.sh               # 检测并移除跨批次重复链接
├── docs/                            # 项目文档
│   ├── usage.md                     # 用户使用手册
│   ├── operations.md                # 运维与自动化配置指南
│   ├── contributing.md              # 贡献者提交规范
│   └── design.md                    # 设计决策与架构说明
├── output/                          # 静态站点生成输出目录（自动生成）
│   ├── index.html                   # 首页链接清单
│   ├── search.json                  # 前端搜索索引数据
│   └── tags/                        # 按标签聚合的页面
├── templates/                       # 静态页面模板
│   ├── base.html                    # 基础HTML骨架
│   └── list.html                    # 链接列表渲染模板
├── config.yaml                      # 项目全局配置文件（站点标题、域名白名单）
├── Makefile                         # 常用任务快捷命令（make check、make build）
└── README.md                        # 项目介绍与快速入门（本文件）
```

## 贡献指南

我们欢迎并鼓励社区贡献者参与链接收录与项目改进。请遵循以下步骤提交您的贡献。

1.  **Fork 仓库并创建功能分支**：从主仓库 Fork 至个人账户，然后基于 `main` 分支创建以 `feat/batch-<编号>` 或 `fix/<简述>` 命名的分支。
2.  **按照规范编辑链接清单**：在 `batches/` 目录下找到对应批次文件，新增链接需确保每行一个完整 URL，且符合项目约定的域名白名单与格式要求。
3.  **更新元数据文件**：对于新增或修改的链接，同步更新同批次下的 YAML 元数据文件，填写采集日期、初步分类标签（如 `android`, `ios`, `performance`）和简要备注。
4.  **运行本地检查脚本**：在提交 Pull Request 前，务必在项目根目录执行 `make check` 或 `./scripts/check-links.sh`，确保所有链接格式正确且无重复。
5.  **提交 Pull Request 并等待审阅**：推送分支至远程仓库后，向主仓库的 `main` 分支发起 Pull Request，在描述中清晰说明本次变更的批次编号和链接数量。项目维护者将在 48 小时内进行审阅与合并。

## 常见问题

**问：项目是否存储文章正文或图片等静态资源？**

答：MRA 项目只存储外链 URL 及其基础元数据（如采集时间、来源域名、自定义标签），不缓存、不代理、不存储任何第三方文章正文内容、图片或附件。所有资源均以原始链接形式存在，用户访问时直接跳转至源站点。

**问：如何避免不同批次之间出现重复链接？**

答：项目提供了 `./scripts/deduplicate.sh` 脚本，该脚本会扫描所有批次文件，提取 URL 核心标识符（去除查询参数后）进行去重检测，并输出重复链接列表供人工处理。建议在每次新增批次后运行该脚本，或在 CI 流程中集成自动检测。

**问：如果源站点链接失效或域名变更怎么办？**

答：MRA 不负责维护第三方链接的可用性。但项目提供了 `./scripts/health-check.py` 脚本，可定期对全部收录链接发起 HEAD 请求检测状态码。建议运维人员设置每周定时任务运行该脚本，并手动移除或标记连续多次返回 4xx/5xx 状态的链接。失效链接的清理记录应同步更新至元数据文件的 `status` 字段。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
