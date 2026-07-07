# Mobile Article Aggregator Service (MAS)

Mobile Article Aggregator Service 是一个面向移动端内容聚合与分发场景的开源中间件项目。该项目旨在为中小型内容平台、个人站长及移动应用开发者提供一套标准化的外链文章元数据采集、结构化存储与统一检索接口。MAS 不生产内容，而是通过可配置的抓取管道，将分散在移动 Web 端的文章详情页（如 hcbezg.cn、fuvxie.cn、cvsifc.cn 等来源）转化为格式化的 JSON 数据流，供上游推荐系统、搜索引擎或静态站点生成器使用。

项目定位为技术基础设施中的“数据桥接层”，重点关注请求调度、响应解析、去重策略与异常重试机制。目标用户包括具备基本运维能力的独立开发者、从事内容聚合业务的创业团队以及需要批量导入历史文章数据的数据工程师。MAS 的核心价值在于降低多源异构移动页面采集的维护成本，通过统一的配置化抽取规则和内置的防封禁策略，让开发者能够在数小时内搭建起一个日均处理万级文章链接的轻量级聚合服务。

## 功能概览

- **多源并发抓取**：支持对不同域名来源的文章列表页与详情页进行并发请求，可配置单域名最大并发数与请求间隔，避免源站压力过大。

- **可配置内容抽取规则**：基于 XPath 与 CSS 选择器混合模式，针对每个来源域名独立配置标题、正文、发布时间、作者等字段的抽取表达式，规则变更无需重启服务。

- **增量去重存储**：内置基于 URL 哈希与内容指纹的双层去重机制，支持 SQLite、PostgreSQL 两种存储后端，默认保留最近 30 天的抓取记录。

- **失败重试与熔断保护**：对超时、5xx 状态码、解析异常等失败情况自动进行指数退避重试，单个域名连续失败超过阈值时触发熔断，保护下游资源。

- **Webhook 通知**：支持在文章抓取成功后向配置的多个 Webhook 地址推送结构化数据，便于与第三方系统（如 Elasticsearch、CDN 刷新队列）集成。

- **Prometheus 监控指标**：暴露抓取任务总数、成功数、失败数、各阶段耗时分布等 Prometheus 指标，可接入 Grafana 进行可视化监控。

- **管理命令行工具**：提供 CLI 子命令用于手动触发单链接抓取、清空去重缓存、导出全量数据为 CSV 等运维操作。

## 应用场景

**场景一：垂直领域资讯聚合站点**
运营一个专注科技或财经领域的资讯导航站，需要从多个移动端来源自动拉取最新文章标题与摘要，按时间线展示。MAS 可配置为每 10 分钟拉取一次指定栏目页，解析后存入数据库，前端通过 REST API 获取最新列表，实现半自动化的内容更新。

**场景二：历史数据批量入库**
内容迁移或数据分析项目中，需要将数百条已知的文章详情页链接批量解析为结构化记录。MAS 的 `batch-import` 命令支持从文本文件读取 URL 列表，并发执行抓取与解析，并将结果输出为 JSON Lines 格式，便于后续导入数据仓库或训练语料库。

**场景三：移动端轻量级搜索索引构建**
为一个小型移动应用提供站内搜索功能，需要定期抓取合作方文章并更新索引。MAS 的 Webhook 功能可在每篇新文章抓取完成后实时调用搜索服务的索引 API，确保搜索结果接近实时更新，同时通过去重机制避免重复索引。

**场景四：内容合规性巡检**
内容审核团队需要定期抽查外部引用链接的当前页面状态与内容变更情况。MAS 可配置为每周全量扫描一次指定链接列表，记录标题与正文哈希变化，当检测到显著变更时通过邮件或企业微信机器人发出告警。

## 快速开始

以下步骤指导您在 Linux/macOS 环境下从源码编译并启动 MAS 服务。

```bash
# 克隆代码仓库
git clone https://github.com/mas-io/mobile-aggregator.git
cd mobile-aggregator

# 安装项目依赖（使用 Go Modules）
go mod download
go mod verify

# 构建可执行文件
make build
# 或者直接使用 go build -o bin/mas cmd/mas/main.go

# 复制默认配置文件并修改数据库连接
cp configs/config.example.yaml configs/config.yaml
# 编辑 configs/config.yaml，设置 storage.dsn 为您的数据库连接字符串

# 运行服务（默认监听 8080 端口）
./bin/mas server --config configs/config.yaml
```

## 安装要求

MAS 采用 Go 语言开发，编译为静态二进制文件，运行时依赖较少。正式部署建议使用以下环境配置：

| 依赖项 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Go 编译器 | 1.21.0 或更高 | 构建时依赖，生产环境若使用预编译二进制则不要求 |
| SQLite / PostgreSQL | SQLite 3.35+ 或 PostgreSQL 12+ | 存储抓取记录与去重缓存，二选一 |
| Linux 内核 / macOS | Linux kernel 4.0+ 或 macOS 10.15+ | 支持 epoll/kqueue 的网络轮询器 |
| 可用内存 | 最低 256 MB，推荐 1 GB 以上 | 内存影响并发连接数与缓存命中率 |
| 可用磁盘 | 最低 1 GB | 存储日志文件与 SQLite 数据文件（若使用） |
| 网络 | 出方向可访问目标域名（如 hcbezg.cn 等） | 需允许 HTTP/HTTPS 流量，建议配置 DNS 缓存 |

## 文档导航

MAS 提供完整的技术文档覆盖从部署到二次开发的各个环节，下表为关键文档入口：

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | `docs/user/configuration.md` | 如何编写来源域名的抽取规则？配置文件中的 timeout、retry、concurrency 参数如何调整？ |
| 用户手册 | `docs/user/api.md` | 服务启动后有哪些 REST API 端点？如何提交单链接抓取任务？如何查询抓取状态？ |
| 开发者指南 | `docs/developer/architecture.md` | 项目的分层架构是怎样的？Pipeline 各阶段（Fetcher、Parser、Deduplicator、Storage）如何协作？ |
| 开发者指南 | `docs/developer/extension.md` | 如何新增一个自定义解析器用于处理新的内容来源？如何替换默认的存储实现？ |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/20920.shtml
- http://m.mobile.fuvxie.cn/Article/470595.shtml
- http://m.mobile.hcbezg.cn/Article/216047.shtml
- http://m.mobile.cvsifc.cn/Article/1477842.shtml
- http://m.mobile.cvsifc.cn/Article/9762.shtml
- http://m.mobile.cvsifc.cn/Article/492188.shtml
- http://m.mobile.fuvxie.cn/Article/67167.shtml
- http://m.mobile.fuvxie.cn/Article/5816.shtml
- http://m.mobile.cvsifc.cn/Article/774795.shtml
- http://m.mobile.fuvxie.cn/Article/028945.shtml
- http://m.mobile.fuvxie.cn/Article/636253.shtml
- http://m.mobile.fuvxie.cn/Article/904838.shtml
- http://m.mobile.hcbezg.cn/Article/742873.shtml
- http://m.mobile.fuvxie.cn/Article/2668.shtml
- http://m.mobile.fuvxie.cn/Article/6179391.shtml
- http://m.mobile.fuvxie.cn/Article/0061588.shtml
- http://m.mobile.cvsifc.cn/Article/8285393.shtml
- http://m.mobile.hcbezg.cn/Article/459914.shtml
- http://m.mobile.fuvxie.cn/Article/21899.shtml
- http://m.mobile.hcbezg.cn/Article/0955.shtml
- http://m.mobile.hcbezg.cn/Article/650208.shtml
- http://m.mobile.fuvxie.cn/Article/07566.shtml
- http://m.mobile.cvsifc.cn/Article/79657.shtml
- http://m.mobile.cvsifc.cn/Article/0752467.shtml
- http://m.mobile.cvsifc.cn/Article/8122.shtml
- http://m.mobile.hcbezg.cn/Article/882242.shtml
- http://m.mobile.cvsifc.cn/Article/0407.shtml
- http://m.mobile.fuvxie.cn/Article/13849.shtml
- http://m.mobile.cvsifc.cn/Article/04201.shtml
- http://m.mobile.cvsifc.cn/Article/0787.shtml
- http://m.mobile.fuvxie.cn/Article/9676206.shtml
- http://m.mobile.hcbezg.cn/Article/564552.shtml
- http://m.mobile.hcbezg.cn/Article/6302160.shtml
- http://m.mobile.cvsifc.cn/Article/86067.shtml
- http://m.mobile.cvsifc.cn/Article/2927448.shtml
- http://m.mobile.cvsifc.cn/Article/906234.shtml
- http://m.mobile.fuvxie.cn/Article/776123.shtml
- http://m.mobile.fuvxie.cn/Article/927591.shtml
- http://m.mobile.cvsifc.cn/Article/7230.shtml
- http://m.mobile.cvsifc.cn/Article/1875972.shtml
- http://m.mobile.cvsifc.cn/Article/706336.shtml
- http://m.mobile.hcbezg.cn/Article/922995.shtml
- http://m.mobile.hcbezg.cn/Article/1537326.shtml
- http://m.mobile.hcbezg.cn/Article/316906.shtml
- http://m.mobile.hcbezg.cn/Article/4562.shtml
- http://m.mobile.cvsifc.cn/Article/69032.shtml
- http://m.mobile.fuvxie.cn/Article/397298.shtml
- http://m.mobile.hcbezg.cn/Article/6421.shtml
- http://m.mobile.cvsifc.cn/Article/4104936.shtml
- http://m.mobile.cvsifc.cn/Article/1383.shtml
- http://m.mobile.hcbezg.cn/Article/39605.shtml
- http://m.mobile.cvsifc.cn/Article/1458.shtml
- http://m.mobile.fuvxie.cn/Article/23608.shtml
- http://m.mobile.cvsifc.cn/Article/1987.shtml
- http://m.mobile.hcbezg.cn/Article/78022.shtml
- http://m.mobile.cvsifc.cn/Article/2794.shtml
- http://m.mobile.hcbezg.cn/Article/0035.shtml
- http://m.mobile.hcbezg.cn/Article/38866.shtml
- http://m.mobile.hcbezg.cn/Article/3069.shtml
- http://m.mobile.fuvxie.cn/Article/492113.shtml
- http://m.mobile.fuvxie.cn/Article/4541.shtml
- http://m.mobile.fuvxie.cn/Article/5147965.shtml
- http://m.mobile.hcbezg.cn/Article/7281.shtml
- http://m.mobile.cvsifc.cn/Article/3524.shtml
- http://m.mobile.cvsifc.cn/Article/4163439.shtml
- http://m.mobile.hcbezg.cn/Article/2967.shtml
- http://m.mobile.cvsifc.cn/Article/37108.shtml
- http://m.mobile.fuvxie.cn/Article/5896.shtml
- http://m.mobile.hcbezg.cn/Article/23483.shtml
- http://m.mobile.cvsifc.cn/Article/7471.shtml
- http://m.mobile.hcbezg.cn/Article/43695.shtml
- http://m.mobile.fuvxie.cn/Article/0371.shtml
- http://m.mobile.fuvxie.cn/Article/022412.shtml
- http://m.mobile.fuvxie.cn/Article/7773708.shtml
- http://m.mobile.fuvxie.cn/Article/64380.shtml
- http://m.mobile.fuvxie.cn/Article/402024.shtml
- http://m.mobile.cvsifc.cn/Article/2448.shtml
- http://m.mobile.hcbezg.cn/Article/7632245.shtml
- http://m.mobile.hcbezg.cn/Article/120507.shtml
- http://m.mobile.fuvxie.cn/Article/408845.shtml
- http://m.mobile.hcbezg.cn/Article/75510.shtml
- http://m.mobile.cvsifc.cn/Article/602311.shtml
- http://m.mobile.hcbezg.cn/Article/40456.shtml
- http://m.mobile.cvsifc.cn/Article/5286477.shtml
- http://m.mobile.hcbezg.cn/Article/34590.shtml
- http://m.mobile.fuvxie.cn/Article/5310.shtml
- http://m.mobile.hcbezg.cn/Article/9781916.shtml
- http://m.mobile.hcbezg.cn/Article/4131339.shtml
- http://m.mobile.cvsifc.cn/Article/2229.shtml
- http://m.mobile.fuvxie.cn/Article/869281.shtml
- http://m.mobile.cvsifc.cn/Article/3831129.shtml
- http://m.mobile.cvsifc.cn/Article/04855.shtml
- http://m.mobile.fuvxie.cn/Article/5419.shtml
- http://m.mobile.fuvxie.cn/Article/63616.shtml
- http://m.mobile.fuvxie.cn/Article/2699.shtml
- http://m.mobile.hcbezg.cn/Article/13274.shtml
- http://m.mobile.hcbezg.cn/Article/5638.shtml
- http://m.mobile.cvsifc.cn/Article/9409.shtml
- http://m.mobile.cvsifc.cn/Article/7879080.shtml
- http://m.mobile.fuvxie.cn/Article/6867.shtml
- http://m.mobile.fuvxie.cn/Article/358760.shtml
- http://m.mobile.fuvxie.cn/Article/7923.shtml
- http://m.mobile.fuvxie.cn/Article/2422.shtml
- http://m.mobile.fuvxie.cn/Article/734777.shtml
- http://m.mobile.fuvxie.cn/Article/1872609.shtml
- http://m.mobile.fuvxie.cn/Article/049077.shtml
- http://m.mobile.hcbezg.cn/Article/73759.shtml
- http://m.mobile.hcbezg.cn/Article/9944306.shtml
- http://m.mobile.hcbezg.cn/Article/1341666.shtml
- http://m.mobile.cvsifc.cn/Article/051407.shtml
- http://m.mobile.fuvxie.cn/Article/49693.shtml
- http://m.mobile.cvsifc.cn/Article/6118.shtml
- http://m.mobile.hcbezg.cn/Article/4365304.shtml
- http://m.mobile.hcbezg.cn/Article/455872.shtml
- http://m.mobile.cvsifc.cn/Article/636613.shtml
- http://m.mobile.hcbezg.cn/Article/425925.shtml
- http://m.mobile.hcbezg.cn/Article/60701.shtml
- http://m.mobile.cvsifc.cn/Article/113663.shtml
- http://m.mobile.hcbezg.cn/Article/1426.shtml
- http://m.mobile.cvsifc.cn/Article/52138.shtml
- http://m.mobile.fuvxie.cn/Article/777864.shtml
- http://m.mobile.cvsifc.cn/Article/8760.shtml
- http://m.mobile.hcbezg.cn/Article/31075.shtml
- http://m.mobile.fuvxie.cn/Article/562209.shtml
- http://m.mobile.cvsifc.cn/Article/85548.shtml
- http://m.mobile.fuvxie.cn/Article/22061.shtml
- http://m.mobile.hcbezg.cn/Article/38526.shtml
- http://m.mobile.fuvxie.cn/Article/507812.shtml
- http://m.mobile.cvsifc.cn/Article/3658.shtml
- http://m.mobile.fuvxie.cn/Article/4451940.shtml
- http://m.mobile.fuvxie.cn/Article/1437.shtml
- http://m.mobile.cvsifc.cn/Article/1663357.shtml
- http://m.mobile.hcbezg.cn/Article/2638429.shtml
- http://m.mobile.cvsifc.cn/Article/2061.shtml
- http://m.mobile.cvsifc.cn/Article/8137739.shtml
- http://m.mobile.fuvxie.cn/Article/2979805.shtml
- http://m.mobile.hcbezg.cn/Article/2962289.shtml
- http://m.mobile.fuvxie.cn/Article/797682.shtml
- http://m.mobile.hcbezg.cn/Article/6685192.shtml
- http://m.mobile.cvsifc.cn/Article/096797.shtml
- http://m.mobile.hcbezg.cn/Article/55147.shtml
- http://m.mobile.cvsifc.cn/Article/11807.shtml
- http://m.mobile.hcbezg.cn/Article/6203796.shtml
- http://m.mobile.cvsifc.cn/Article/5999005.shtml
- http://m.mobile.fuvxie.cn/Article/0755.shtml
- http://m.mobile.fuvxie.cn/Article/6611.shtml
- http://m.mobile.fuvxie.cn/Article/3907.shtml
- http://m.mobile.hcbezg.cn/Article/14977.shtml
- http://m.mobile.cvsifc.cn/Article/44323.shtml
- http://m.mobile.cvsifc.cn/Article/2902.shtml
- http://m.mobile.cvsifc.cn/Article/611003.shtml
- http://m.mobile.fuvxie.cn/Article/12253.shtml
- http://m.mobile.hcbezg.cn/Article/861287.shtml
- http://m.mobile.cvsifc.cn/Article/85746.shtml
- http://m.mobile.cvsifc.cn/Article/3603.shtml
- http://m.mobile.hcbezg.cn/Article/6428686.shtml
- http://m.mobile.cvsifc.cn/Article/0675.shtml
- http://m.mobile.fuvxie.cn/Article/0737.shtml
- http://m.mobile.hcbezg.cn/Article/370311.shtml
- http://m.mobile.fuvxie.cn/Article/25563.shtml
- http://m.mobile.fuvxie.cn/Article/64175.shtml
- http://m.mobile.cvsifc.cn/Article/485799.shtml
- http://m.mobile.cvsifc.cn/Article/8070.shtml
- http://m.mobile.cvsifc.cn/Article/6265.shtml
- http://m.mobile.fuvxie.cn/Article/28037.shtml
- http://m.mobile.hcbezg.cn/Article/487177.shtml
- http://m.mobile.hcbezg.cn/Article/60568.shtml
- http://m.mobile.cvsifc.cn/Article/12195.shtml
- http://m.mobile.fuvxie.cn/Article/1914.shtml
- http://m.mobile.cvsifc.cn/Article/6217.shtml
- http://m.mobile.cvsifc.cn/Article/8673960.shtml
- http://m.mobile.hcbezg.cn/Article/5686332.shtml
- http://m.mobile.hcbezg.cn/Article/9519999.shtml
- http://m.mobile.cvsifc.cn/Article/739643.shtml
- http://m.mobile.fuvxie.cn/Article/3099795.shtml
- http://m.mobile.hcbezg.cn/Article/64928.shtml
- http://m.mobile.fuvxie.cn/Article/092522.shtml
- http://m.mobile.hcbezg.cn/Article/6154313.shtml
- http://m.mobile.hcbezg.cn/Article/1816281.shtml
- http://m.mobile.cvsifc.cn/Article/857350.shtml
- http://m.mobile.fuvxie.cn/Article/18237.shtml
- http://m.mobile.fuvxie.cn/Article/3453.shtml
- http://m.mobile.fuvxie.cn/Article/54524.shtml
- http://m.mobile.hcbezg.cn/Article/5749.shtml
- http://m.mobile.cvsifc.cn/Article/96979.shtml
- http://m.mobile.cvsifc.cn/Article/493068.shtml
- http://m.mobile.cvsifc.cn/Article/61387.shtml
- http://m.mobile.hcbezg.cn/Article/5577821.shtml
- http://m.mobile.fuvxie.cn/Article/6703117.shtml
- http://m.mobile.hcbezg.cn/Article/457979.shtml
- http://m.mobile.cvsifc.cn/Article/4859.shtml
- http://m.mobile.cvsifc.cn/Article/6374.shtml
- http://m.mobile.hcbezg.cn/Article/9726940.shtml
- http://m.mobile.cvsifc.cn/Article/68808.shtml
- http://m.mobile.fuvxie.cn/Article/464615.shtml
- http://m.mobile.hcbezg.cn/Article/8075.shtml
- http://m.mobile.hcbezg.cn/Article/6494.shtml
- http://m.mobile.fuvxie.cn/Article/961223.shtml
- http://m.mobile.hcbezg.cn/Article/2653129.shtml
- http://m.mobile.hcbezg.cn/Article/3784.shtml
- http://m.mobile.fuvxie.cn/Article/0501.shtml
- http://m.mobile.fuvxie.cn/Article/303829.shtml
- http://m.mobile.fuvxie.cn/Article/7652631.shtml
- http://m.mobile.hcbezg.cn/Article/3358.shtml
- http://m.mobile.fuvxie.cn/Article/78767.shtml
- http://m.mobile.fuvxie.cn/Article/23629.shtml
- http://m.mobile.cvsifc.cn/Article/1042374.shtml
- http://m.mobile.hcbezg.cn/Article/73504.shtml
- http://m.mobile.hcbezg.cn/Article/400717.shtml
- http://m.mobile.hcbezg.cn/Article/7625.shtml
- http://m.mobile.cvsifc.cn/Article/170311.shtml
- http://m.mobile.fuvxie.cn/Article/2975.shtml
- http://m.mobile.hcbezg.cn/Article/84556.shtml
- http://m.mobile.fuvxie.cn/Article/1315900.shtml
- http://m.mobile.hcbezg.cn/Article/8446.shtml
- http://m.mobile.hcbezg.cn/Article/47467.shtml
- http://m.mobile.cvsifc.cn/Article/349221.shtml
- http://m.mobile.hcbezg.cn/Article/43531.shtml
- http://m.mobile.hcbezg.cn/Article/8276349.shtml
- http://m.mobile.fuvxie.cn/Article/044213.shtml
- http://m.mobile.fuvxie.cn/Article/044064.shtml
- http://m.mobile.fuvxie.cn/Article/67667.shtml
- http://m.mobile.cvsifc.cn/Article/967238.shtml
- http://m.mobile.cvsifc.cn/Article/70597.shtml
- http://m.mobile.cvsifc.cn/Article/7126.shtml
- http://m.mobile.fuvxie.cn/Article/6904337.shtml
- http://m.mobile.fuvxie.cn/Article/23431.shtml
- http://m.mobile.cvsifc.cn/Article/7102.shtml
- http://m.mobile.hcbezg.cn/Article/3407178.shtml
- http://m.mobile.cvsifc.cn/Article/45669.shtml
- http://m.mobile.fuvxie.cn/Article/2840343.shtml
- http://m.mobile.fuvxie.cn/Article/7061.shtml
- http://m.mobile.fuvxie.cn/Article/1166321.shtml
- http://m.mobile.cvsifc.cn/Article/99703.shtml
- http://m.mobile.cvsifc.cn/Article/9786.shtml
- http://m.mobile.fuvxie.cn/Article/51180.shtml
- http://m.mobile.fuvxie.cn/Article/9197126.shtml
- http://m.mobile.cvsifc.cn/Article/9645.shtml
- http://m.mobile.hcbezg.cn/Article/86726.shtml
- http://m.mobile.hcbezg.cn/Article/72914.shtml
- http://m.mobile.fuvxie.cn/Article/82284.shtml
- http://m.mobile.cvsifc.cn/Article/146471.shtml
- http://m.mobile.hcbezg.cn/Article/8739051.shtml
- http://m.mobile.cvsifc.cn/Article/8819.shtml
- http://m.mobile.cvsifc.cn/Article/332276.shtml
- http://m.mobile.fuvxie.cn/Article/3750050.shtml
- http://m.mobile.fuvxie.cn/Article/2628938.shtml
- http://m.mobile.fuvxie.cn/Article/06379.shtml
- http://m.mobile.cvsifc.cn/Article/00126.shtml
- http://m.mobile.cvsifc.cn/Article/5022301.shtml

## 项目结构

```
mobile-aggregator/
├── cmd/                                # 可执行程序入口目录
│   └── mas/                            # 主服务入口
│       └── main.go                     # 初始化配置、日志、启动 server 或 cli 子命令
├── internal/                           # 内部实现包（不对外暴露）
│   ├── fetcher/                        # 抓取层：管理 HTTP 客户端、代理、请求头策略
│   │   ├── client.go                   # 带连接池和超时控制的 http.Client 封装
│   │   └── dispatcher.go               # 并发调度器，控制单域名请求速率和最大并发
│   ├── parser/                         # 解析层：针对不同来源的规则引擎
│   │   ├── rule.go                     # 定义抽取规则结构体（XPath + CSS 选择器混合）
│   │   ├── compiler.go                 # 预编译规则供重用
│   │   └── extractor.go                # 执行 HTML 解析与字段提取
│   ├── dedup/                          # 去重层：URL 哈希与内容指纹双重去重
│   │   ├── bloom.go                    # 布隆过滤器实现（可选内存去重）
│   │   └── store.go                    # 持久化去重记录接口（SQL 实现）
│   ├── storage/                        # 存储层：数据库连接与 CRUD 操作
│   │   ├── sqlite.go                   # SQLite 驱动适配器
│   │   └── postgres.go                 # PostgreSQL 驱动适配器
│   ├── pipeline/                       # 编排层：串联抓取-解析-去重-存储流程
│   │   ├── orchestrator.go             # 主流程控制，处理重试与熔断
│   │   └── webhook.go                  # 成功记录后触发 Webhook 通知
│   └── metrics/                        # 监控层：Prometheus 指标注册与更新
│       └── prometheus.go               # 定义 Counter、Histogram 等指标
├── pkg/                                # 可对外暴露的公共库代码
│   ├── config/                         # 配置文件解析与校验
│   │   └── config.go                   # YAML 结构体映射与默认值填充
│   └── logger/                         # 结构化日志封装（基于 zap）
│       └── logger.go                   # 日志级别、输出格式、文件轮转配置
├── configs/                            # 配置文件目录
│   ├── config.example.yaml             # 示例配置文件（含所有必填字段注释）
│   └── sources/                        # 来源域名规则子目录，每个域名一个 yaml 文件
│       ├── hcbezg.yaml                 # 针对 hcbezg.cn 的抽取规则
│       ├── fuvxie.yaml                 # 针对 fuvxie.cn 的抽取规则
│       └── cvsifc.yaml                 # 针对 cvsifc.cn 的抽取规则
├── scripts/                            # 运维辅助脚本
│   ├── migrate_db.sh                   # 数据库 schema 迁移脚本
│   └── health_check.sh                 # 服务健康状态探测脚本
├── testdata/                           # 测试数据目录
│   └── sample.html                     # 用于单元测试的静态 HTML 样本
├── docs/                               # 文档目录（结构与导航部分一致）
│   ├── user/                           # 用户手册
│   └── developer/                      # 开发者手册
├── Makefile                            # 构建、测试、打包的统一入口
├── go.mod                              # Go 模块依赖定义
├── go.sum                              # 依赖哈希锁定
└── README.md                           # 本文件
```

## 贡献指南

MAS 项目遵循 Go 社区的标准协作流程，欢迎各类形式的贡献，包括但不限于新增解析规则、优化并发模型、修复边界条件 bug 和改进文档。

1. 查阅 issue 列表与项目看板，选择未被指派的 issue 或提交新 issue 描述您希望解决的问题。对于较大规模的功能新增（如新增存储后端），建议先通过 issue 与维护者沟通设计思路。

2. 从 main 分支检出新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 的格式。确保本地开发环境已安装 golangci-lint 和 go test 工具。

3. 编写代码时请遵循项目根目录下的 `.golangci.yml` 静态检查规则，并为新增的导出函数、类型、常量补充完整的文档注释。单元测试文件需与源文件同目录，以 `_test.go` 结尾，且测试覆盖率不低于 60%。

4. 提交前执行 `make test` 和 `make lint` 确保所有测试通过且无 lint 警告。提交信息使用英文，首行简要概括改动内容（不超过 72 字符），正文描述改动原因与影响范围。

5. 推送到远程仓库后，通过 GitHub 界面发起 Pull Request 到 main 分支。PR 描述中需关联对应的 issue 编号，并勾选自测清单。维护者将在 3 个工作日内进行 Review，必要时会提出修改意见。

## 常见问题

**Q：MAS 是否支持抓取需要登录或带有反爬机制的页面？**
不支持。MAS 目前仅针对公开可访问的移动端文章详情页进行抓取，不提供 Cookie 会话管理、验证码识别或动态渲染（如执行 JavaScript）的能力。对于需要登录或强反爬的源站，建议在上游使用独立的代理服务或 Headless Browser 方案预处理后再接入 MAS。

**Q：如何调整单个域名的最大并发数以避免被源站封禁？**
在配置文件 `config.yaml` 的 `sources` 段中，为每个域名单独设置 `max_concurrent` 和 `interval_ms` 参数。例如将 `max_concurrent` 设为 2、`interval_ms` 设为 500，表示每 500 毫秒最多发起 2 个请求。项目默认全局并发为 5，单域名并发为 2，建议根据源站响应速度与错误率逐步调整。

**Q：服务运行一段时间后出现 "too many open files" 错误，如何解决？**
该错误通常由于系统文件描述符上限不足或 HTTP 连接未正确释放导致。请先检查系统级 `ulimit -n` 设置，建议至少设为 65535。若问题依旧，请在配置文件中减小 `fetcher.max_idle_connections` 和 `fetcher.max_connections_per_host` 的值，同时缩短 `fetcher.idle_timeout_seconds` 到 30 秒以下，以加速空闲连接的回收。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
