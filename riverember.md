# WebIndex Mobile Article Aggregator

WebIndex Mobile Article Aggregator 是一个面向移动端技术内容聚合与导航的开源工具集，专注于从多个内容源自动抓取、解析和归类技术文章。项目主要服务于技术内容运营者、个人知识管理爱好者以及小型团队，帮助其以结构化的方式管理和分发来自不同域名的移动端 H5 文章资源。通过统一的索引机制与轻量级预处理流水线，该项目能够将分散的 URL 资源转化为可检索、可分类、可导出的结构化数据集，适用于构建自定义导航站、垂直领域内容聚合页或内部知识库的初始数据层。

项目采用模块化设计，核心功能包括多源文章列表拉取、HTML 元数据抽取、去重与时效性校验、关键词自动标引以及 JSON/CSV 格式的数据导出。当前版本已适配多个内容源域名，并提供可扩展的适配器接口，方便开发者接入新的数据源。WebIndex 不依赖大型前端框架，运行于 Node.js 或 Deno 环境，亦可编译为轻量级二进制工具，满足低资源服务器或边缘计算节点的部署需求。

## 功能概览

**多源并发抓取**：支持对多个域名下的文章列表页进行并发请求，内置重试机制与超时控制，可配置请求间隔以避免触发源站限流策略。

**元数据自动抽取**：从文章详情页中自动提取标题、发布时间、正文摘要、作者信息及分类标签，抽取规则支持 XPath 与 CSS 选择器双模式配置。

**去重与增量更新**：基于文章 URL 与标题哈希实现增量去重，支持将新抓取的文章与本地缓存进行比对，仅更新变更内容，降低重复处理开销。

**关键词智能标引**：内置中文分词与词频统计模块，自动为每篇文章生成 3-5 个核心关键词，便于后续的分类导航与检索功能构建。

**多格式数据导出**：支持将整理后的文章索引导出为 JSON Lines、CSV 或 SQLite 数据库文件，适配不同的下游应用场景，如静态站点生成、数据分析或全文检索导入。

**可扩展适配器机制**：提供标准化的适配器接口，开发者只需实现 fetchList 与 fetchDetail 两个方法即可接入新的内容源，无需修改核心代码。

**本地 Web 预览服务**：内置基于原生 HTTP 模块的简易预览服务器，可在开发阶段实时查看抓取结果与分类统计，便于调试适配器规则。

## 应用场景

技术博客与资讯每日汇总：内容运营人员可配置定时任务，每日自动从多个技术博客源拉取最新文章，经过自动分类与关键词标引后生成汇总日报，供团队内部浏览或对外发布。

个人知识库文章采集：研究员或开发者可将该项目作为知识管理流水线的上游工具，定期采集关注领域的技术文章，结合后续的全文检索与标签系统，构建个人专属的技术资料库。

垂直领域导航站构建：团队可利用 WebIndex 的多源聚合能力，快速搭建某个技术垂直领域（如云原生、前端框架或人工智能）的导航站点，通过导出的 JSON 数据直接驱动静态页面生成，降低手动维护成本。

内容迁移与备份：在需要将文章数据从一个平台迁移至另一个平台时，可使用 WebIndex 批量导出文章元数据及原始 URL，再通过下游适配脚本完成内容导入，减少人工复制粘贴的工作量。

## 快速开始

以下指令适用于 Linux/macOS/WSL 环境，需提前安装 Node.js 18.x 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/webindex-mobile/webindex-aggregator.git
cd webindex-aggregator

# 安装项目依赖
npm install

# 复制示例配置文件并修改数据源参数
cp config.example.json config.json

# 执行全量抓取任务（默认输出至 ./output 目录）
npm run crawl

# 启动本地预览服务
npm run serve
```

首次执行时，程序会依次请求配置文件中定义的所有文章列表 URL，对每个详情页进行元数据抽取，最终在 output 目录下生成 articles.json 与 summary.csv 两个文件。若需要调整抓取并发数或请求超时时间，可在 config.json 的 crawler 字段中进行设置。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 可选（使用 SQLite 导出时需要） | 系统级 SQLite 库，用于生成 .db 文件 |
| 内存 | 最低 512MB，推荐 1GB | 同时处理 50 个并发请求时的内存占用 |
| 存储空间 | 最低 100MB | 用于存放缓存索引及导出文件，建议保留 500MB |
| 网络 | 稳定外网连接 | 需能够访问配置中的各内容源域名 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速配置数据源并完成第一次抓取任务 |
| 配置参考 | docs/configuration.md | config.json 中每个字段的含义与可选值说明 |
| 适配器开发 | docs/adapter-development.md | 如何为新的内容源编写自定义适配器 |
| 数据导出与集成 | docs/export-integration.md | 导出格式的详细字段说明及与第三方工具集成示例 |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/9965.shtml
- http://h5.mobile.fuvxie.cn/Article/1246.shtml
- http://h5.mobile.cvsifc.cn/Article/8972.shtml
- http://h5.mobile.fuvxie.cn/Article/6471465.shtml
- http://h5.mobile.hcbezg.cn/Article/2088.shtml
- http://h5.mobile.cvsifc.cn/Article/1188067.shtml
- http://h5.mobile.hcbezg.cn/Article/6291.shtml
- http://h5.mobile.hcbezg.cn/Article/854915.shtml
- http://h5.mobile.cvsifc.cn/Article/6297418.shtml
- http://h5.mobile.fuvxie.cn/Article/51329.shtml
- http://h5.mobile.cvsifc.cn/Article/5218347.shtml
- http://h5.mobile.hcbezg.cn/Article/027887.shtml
- http://h5.mobile.fuvxie.cn/Article/9889723.shtml
- http://h5.mobile.fuvxie.cn/Article/13763.shtml
- http://h5.mobile.fuvxie.cn/Article/8558854.shtml
- http://h5.mobile.fuvxie.cn/Article/070989.shtml
- http://h5.mobile.fuvxie.cn/Article/7058201.shtml
- http://h5.mobile.hcbezg.cn/Article/63364.shtml
- http://h5.mobile.hcbezg.cn/Article/7910.shtml
- http://h5.mobile.cvsifc.cn/Article/0537.shtml
- http://h5.mobile.fuvxie.cn/Article/7494903.shtml
- http://h5.mobile.fuvxie.cn/Article/396566.shtml
- http://h5.mobile.fuvxie.cn/Article/6275.shtml
- http://h5.mobile.fuvxie.cn/Article/157006.shtml
- http://h5.mobile.cvsifc.cn/Article/70854.shtml
- http://h5.mobile.hcbezg.cn/Article/09716.shtml
- http://h5.mobile.fuvxie.cn/Article/232968.shtml
- http://h5.mobile.fuvxie.cn/Article/227719.shtml
- http://h5.mobile.cvsifc.cn/Article/94450.shtml
- http://h5.mobile.cvsifc.cn/Article/1060.shtml
- http://h5.mobile.hcbezg.cn/Article/6419.shtml
- http://h5.mobile.fuvxie.cn/Article/240208.shtml
- http://h5.mobile.fuvxie.cn/Article/62561.shtml
- http://h5.mobile.fuvxie.cn/Article/966985.shtml
- http://h5.mobile.fuvxie.cn/Article/727457.shtml
- http://h5.mobile.cvsifc.cn/Article/955525.shtml
- http://h5.mobile.cvsifc.cn/Article/3219602.shtml
- http://h5.mobile.cvsifc.cn/Article/7471201.shtml
- http://h5.mobile.hcbezg.cn/Article/8571606.shtml
- http://h5.mobile.hcbezg.cn/Article/2704776.shtml
- http://h5.mobile.fuvxie.cn/Article/71104.shtml
- http://h5.mobile.fuvxie.cn/Article/79181.shtml
- http://h5.mobile.fuvxie.cn/Article/22165.shtml
- http://h5.mobile.cvsifc.cn/Article/3959452.shtml
- http://h5.mobile.cvsifc.cn/Article/0311.shtml
- http://h5.mobile.fuvxie.cn/Article/513046.shtml
- http://h5.mobile.hcbezg.cn/Article/00014.shtml
- http://h5.mobile.hcbezg.cn/Article/3115.shtml
- http://h5.mobile.cvsifc.cn/Article/30643.shtml
- http://h5.mobile.cvsifc.cn/Article/66599.shtml
- http://h5.mobile.cvsifc.cn/Article/473633.shtml
- http://h5.mobile.fuvxie.cn/Article/0946.shtml
- http://h5.mobile.hcbezg.cn/Article/2518.shtml
- http://h5.mobile.fuvxie.cn/Article/41372.shtml
- http://h5.mobile.cvsifc.cn/Article/8766.shtml
- http://h5.mobile.hcbezg.cn/Article/6263.shtml
- http://h5.mobile.hcbezg.cn/Article/78541.shtml
- http://h5.mobile.hcbezg.cn/Article/912081.shtml
- http://h5.mobile.fuvxie.cn/Article/6346021.shtml
- http://h5.mobile.cvsifc.cn/Article/6848190.shtml
- http://h5.mobile.cvsifc.cn/Article/6497.shtml
- http://h5.mobile.cvsifc.cn/Article/3019.shtml
- http://h5.mobile.fuvxie.cn/Article/49052.shtml
- http://h5.mobile.cvsifc.cn/Article/1058.shtml
- http://h5.mobile.cvsifc.cn/Article/933736.shtml
- http://h5.mobile.cvsifc.cn/Article/051878.shtml
- http://h5.mobile.cvsifc.cn/Article/4065836.shtml
- http://h5.mobile.cvsifc.cn/Article/69528.shtml
- http://h5.mobile.hcbezg.cn/Article/262173.shtml
- http://h5.mobile.fuvxie.cn/Article/48878.shtml
- http://h5.mobile.cvsifc.cn/Article/1430.shtml
- http://h5.mobile.cvsifc.cn/Article/510781.shtml
- http://h5.mobile.hcbezg.cn/Article/5640510.shtml
- http://h5.mobile.hcbezg.cn/Article/467326.shtml
- http://h5.mobile.cvsifc.cn/Article/0165.shtml
- http://h5.mobile.hcbezg.cn/Article/2274411.shtml
- http://h5.mobile.cvsifc.cn/Article/86763.shtml
- http://h5.mobile.fuvxie.cn/Article/2164.shtml
- http://h5.mobile.cvsifc.cn/Article/71658.shtml
- http://h5.mobile.cvsifc.cn/Article/4474.shtml
- http://h5.mobile.cvsifc.cn/Article/986709.shtml
- http://h5.mobile.cvsifc.cn/Article/499818.shtml
- http://h5.mobile.cvsifc.cn/Article/298398.shtml
- http://h5.mobile.fuvxie.cn/Article/0707.shtml
- http://h5.mobile.cvsifc.cn/Article/94162.shtml
- http://h5.mobile.hcbezg.cn/Article/869792.shtml
- http://h5.mobile.cvsifc.cn/Article/1837.shtml
- http://h5.mobile.fuvxie.cn/Article/8780222.shtml
- http://h5.mobile.fuvxie.cn/Article/5876.shtml
- http://h5.mobile.fuvxie.cn/Article/147540.shtml
- http://h5.mobile.hcbezg.cn/Article/0975.shtml
- http://h5.mobile.hcbezg.cn/Article/394521.shtml
- http://h5.mobile.fuvxie.cn/Article/2278114.shtml
- http://h5.mobile.fuvxie.cn/Article/39469.shtml
- http://h5.mobile.fuvxie.cn/Article/8731.shtml
- http://h5.mobile.fuvxie.cn/Article/7081.shtml
- http://h5.mobile.fuvxie.cn/Article/1009.shtml
- http://h5.mobile.cvsifc.cn/Article/83713.shtml
- http://h5.mobile.hcbezg.cn/Article/098873.shtml
- http://h5.mobile.hcbezg.cn/Article/016834.shtml
- http://h5.mobile.hcbezg.cn/Article/505944.shtml
- http://h5.mobile.cvsifc.cn/Article/9234.shtml
- http://h5.mobile.cvsifc.cn/Article/9780.shtml
- http://h5.mobile.cvsifc.cn/Article/2176.shtml
- http://h5.mobile.fuvxie.cn/Article/5717009.shtml
- http://h5.mobile.fuvxie.cn/Article/8745.shtml
- http://h5.mobile.cvsifc.cn/Article/56083.shtml
- http://h5.mobile.hcbezg.cn/Article/88255.shtml
- http://h5.mobile.cvsifc.cn/Article/7840.shtml
- http://h5.mobile.hcbezg.cn/Article/305164.shtml
- http://h5.mobile.cvsifc.cn/Article/42444.shtml
- http://h5.mobile.fuvxie.cn/Article/457264.shtml
- http://h5.mobile.hcbezg.cn/Article/43699.shtml
- http://h5.mobile.hcbezg.cn/Article/69504.shtml
- http://h5.mobile.cvsifc.cn/Article/327368.shtml
- http://h5.mobile.fuvxie.cn/Article/08826.shtml
- http://h5.mobile.cvsifc.cn/Article/56541.shtml
- http://h5.mobile.fuvxie.cn/Article/205064.shtml
- http://h5.mobile.fuvxie.cn/Article/31765.shtml
- http://h5.mobile.fuvxie.cn/Article/909189.shtml
- http://h5.mobile.cvsifc.cn/Article/088911.shtml
- http://h5.mobile.fuvxie.cn/Article/510103.shtml
- http://h5.mobile.cvsifc.cn/Article/4420.shtml
- http://h5.mobile.fuvxie.cn/Article/264469.shtml
- http://h5.mobile.fuvxie.cn/Article/36756.shtml
- http://h5.mobile.fuvxie.cn/Article/2392007.shtml
- http://h5.mobile.cvsifc.cn/Article/5876269.shtml
- http://h5.mobile.cvsifc.cn/Article/4471.shtml
- http://h5.mobile.cvsifc.cn/Article/2264056.shtml
- http://h5.mobile.fuvxie.cn/Article/3294.shtml
- http://h5.mobile.cvsifc.cn/Article/032367.shtml
- http://h5.mobile.fuvxie.cn/Article/0302.shtml
- http://h5.mobile.cvsifc.cn/Article/341320.shtml
- http://h5.mobile.fuvxie.cn/Article/9386.shtml
- http://h5.mobile.cvsifc.cn/Article/8899184.shtml
- http://h5.mobile.cvsifc.cn/Article/4542.shtml
- http://h5.mobile.cvsifc.cn/Article/6709062.shtml
- http://h5.mobile.fuvxie.cn/Article/9438722.shtml
- http://h5.mobile.hcbezg.cn/Article/83709.shtml
- http://h5.mobile.cvsifc.cn/Article/8229.shtml
- http://h5.mobile.hcbezg.cn/Article/0550.shtml
- http://h5.mobile.cvsifc.cn/Article/167904.shtml
- http://h5.mobile.fuvxie.cn/Article/4081257.shtml
- http://h5.mobile.fuvxie.cn/Article/65615.shtml
- http://h5.mobile.cvsifc.cn/Article/2081657.shtml
- http://h5.mobile.cvsifc.cn/Article/434831.shtml
- http://h5.mobile.cvsifc.cn/Article/3091956.shtml
- http://h5.mobile.cvsifc.cn/Article/800287.shtml
- http://h5.mobile.cvsifc.cn/Article/4306.shtml
- http://h5.mobile.hcbezg.cn/Article/024957.shtml
- http://h5.mobile.cvsifc.cn/Article/8471677.shtml
- http://h5.mobile.fuvxie.cn/Article/4910.shtml
- http://h5.mobile.hcbezg.cn/Article/801206.shtml
- http://h5.mobile.hcbezg.cn/Article/76237.shtml
- http://h5.mobile.fuvxie.cn/Article/5756190.shtml
- http://h5.mobile.fuvxie.cn/Article/3715.shtml
- http://h5.mobile.cvsifc.cn/Article/9828907.shtml
- http://h5.mobile.fuvxie.cn/Article/8282.shtml
- http://h5.mobile.hcbezg.cn/Article/9253946.shtml
- http://h5.mobile.cvsifc.cn/Article/2902538.shtml
- http://h5.mobile.cvsifc.cn/Article/5268.shtml
- http://h5.mobile.hcbezg.cn/Article/69291.shtml
- http://h5.mobile.cvsifc.cn/Article/80872.shtml
- http://h5.mobile.hcbezg.cn/Article/7542565.shtml
- http://h5.mobile.hcbezg.cn/Article/2839.shtml
- http://h5.mobile.fuvxie.cn/Article/70554.shtml
- http://h5.mobile.cvsifc.cn/Article/068119.shtml
- http://h5.mobile.fuvxie.cn/Article/7662.shtml
- http://h5.mobile.hcbezg.cn/Article/03703.shtml
- http://h5.mobile.hcbezg.cn/Article/0881583.shtml
- http://h5.mobile.cvsifc.cn/Article/98660.shtml
- http://h5.mobile.cvsifc.cn/Article/51776.shtml
- http://h5.mobile.fuvxie.cn/Article/34951.shtml
- http://h5.mobile.hcbezg.cn/Article/2394883.shtml
- http://h5.mobile.cvsifc.cn/Article/465926.shtml
- http://h5.mobile.fuvxie.cn/Article/9028.shtml
- http://h5.mobile.hcbezg.cn/Article/5220.shtml
- http://h5.mobile.cvsifc.cn/Article/934567.shtml
- http://h5.mobile.fuvxie.cn/Article/39966.shtml
- http://h5.mobile.fuvxie.cn/Article/093894.shtml
- http://h5.mobile.cvsifc.cn/Article/6840.shtml
- http://h5.mobile.fuvxie.cn/Article/167563.shtml
- http://h5.mobile.cvsifc.cn/Article/5860506.shtml
- http://h5.mobile.cvsifc.cn/Article/56832.shtml
- http://h5.mobile.hcbezg.cn/Article/080019.shtml
- http://h5.mobile.hcbezg.cn/Article/967908.shtml
- http://h5.mobile.fuvxie.cn/Article/31200.shtml
- http://h5.mobile.cvsifc.cn/Article/4762757.shtml
- http://h5.mobile.hcbezg.cn/Article/9128.shtml
- http://h5.mobile.fuvxie.cn/Article/7600.shtml
- http://h5.mobile.fuvxie.cn/Article/177699.shtml
- http://h5.mobile.cvsifc.cn/Article/650107.shtml
- http://h5.mobile.cvsifc.cn/Article/0529.shtml
- http://h5.mobile.hcbezg.cn/Article/582721.shtml
- http://h5.mobile.hcbezg.cn/Article/6056.shtml
- http://h5.mobile.hcbezg.cn/Article/960600.shtml
- http://h5.mobile.cvsifc.cn/Article/550786.shtml
- http://h5.mobile.cvsifc.cn/Article/2842.shtml
- http://h5.mobile.fuvxie.cn/Article/068894.shtml
- http://h5.mobile.hcbezg.cn/Article/54102.shtml
- http://h5.mobile.cvsifc.cn/Article/5963882.shtml
- http://h5.mobile.fuvxie.cn/Article/5227923.shtml
- http://h5.mobile.cvsifc.cn/Article/9125723.shtml
- http://h5.mobile.cvsifc.cn/Article/3227624.shtml
- http://h5.mobile.cvsifc.cn/Article/1716840.shtml
- http://h5.mobile.hcbezg.cn/Article/8126709.shtml
- http://h5.mobile.hcbezg.cn/Article/1763802.shtml
- http://h5.mobile.fuvxie.cn/Article/9646.shtml
- http://h5.mobile.cvsifc.cn/Article/1827.shtml
- http://h5.mobile.cvsifc.cn/Article/7640308.shtml
- http://h5.mobile.cvsifc.cn/Article/54894.shtml
- http://h5.mobile.cvsifc.cn/Article/8194.shtml
- http://h5.mobile.cvsifc.cn/Article/62132.shtml
- http://h5.mobile.fuvxie.cn/Article/268272.shtml
- http://h5.mobile.fuvxie.cn/Article/66276.shtml
- http://h5.mobile.cvsifc.cn/Article/47335.shtml
- http://h5.mobile.cvsifc.cn/Article/9799943.shtml
- http://h5.mobile.cvsifc.cn/Article/0086.shtml
- http://h5.mobile.fuvxie.cn/Article/86260.shtml
- http://h5.mobile.fuvxie.cn/Article/01599.shtml
- http://h5.mobile.cvsifc.cn/Article/475476.shtml
- http://h5.mobile.hcbezg.cn/Article/2703.shtml
- http://h5.mobile.cvsifc.cn/Article/02694.shtml
- http://h5.mobile.fuvxie.cn/Article/96685.shtml
- http://h5.mobile.fuvxie.cn/Article/8904894.shtml
- http://h5.mobile.fuvxie.cn/Article/4682.shtml
- http://h5.mobile.hcbezg.cn/Article/322334.shtml
- http://h5.mobile.hcbezg.cn/Article/465267.shtml
- http://h5.mobile.fuvxie.cn/Article/8412464.shtml
- http://h5.mobile.hcbezg.cn/Article/7706.shtml
- http://h5.mobile.cvsifc.cn/Article/1535380.shtml
- http://h5.mobile.hcbezg.cn/Article/3269.shtml
- http://h5.mobile.fuvxie.cn/Article/1187734.shtml
- http://h5.mobile.cvsifc.cn/Article/56505.shtml
- http://h5.mobile.cvsifc.cn/Article/31236.shtml
- http://h5.mobile.fuvxie.cn/Article/3583.shtml
- http://h5.mobile.cvsifc.cn/Article/99126.shtml
- http://h5.mobile.hcbezg.cn/Article/0788367.shtml
- http://h5.mobile.cvsifc.cn/Article/79044.shtml
- http://h5.mobile.hcbezg.cn/Article/018522.shtml
- http://h5.mobile.cvsifc.cn/Article/843696.shtml
- http://h5.mobile.cvsifc.cn/Article/243672.shtml
- http://h5.mobile.cvsifc.cn/Article/555065.shtml
- http://h5.mobile.hcbezg.cn/Article/4032.shtml
- http://h5.mobile.hcbezg.cn/Article/202237.shtml
- http://h5.mobile.cvsifc.cn/Article/901593.shtml
- http://h5.mobile.hcbezg.cn/Article/703704.shtml
- http://h5.mobile.cvsifc.cn/Article/2311637.shtml
- http://h5.mobile.fuvxie.cn/Article/01512.shtml
- http://h5.mobile.fuvxie.cn/Article/9544.shtml

## 项目结构

```
webindex-aggregator/
├── src/                                 # 核心源码目录
│   ├── crawler/                         # 爬虫调度与请求控制模块
│   │   ├── index.js                     # 爬虫主入口，负责并发调度与任务队列管理
│   │   └── request-handler.js           # HTTP 请求封装，含重试、超时与 user-agent 轮换
│   ├── parser/                          # 内容解析模块
│   │   ├── html-extractor.js            # 基于 cheerio 的 HTML 元数据抽取核心
│   │   └── rule-engine.js               # 选择器规则引擎，支持 XPath 与 CSS 选择器
│   ├── adapter/                         # 数据源适配器目录
│   │   ├── base.js                      # 适配器基类与接口定义
│   │   ├── cvsifc.js                    # 针对 h5.mobile.cvsifc.cn 的适配器实现
│   │   ├── fuvxie.js                    # 针对 h5.mobile.fuvxie.cn 的适配器实现
│   │   └── hcbezg.js                    # 针对 h5.mobile.hcbezg.cn 的适配器实现
│   ├── pipeline/                        # 数据处理管道
│   │   ├── deduplicator.js              # 基于标题与 URL 哈希的去重模块
│   │   ├── keyword-tagger.js            # 中文分词与关键词权重计算
│   │   └── exporter.js                  # 多格式导出器（JSON/CSV/SQLite）
│   ├── cache/                           # 本地缓存管理
│   │   ├── index.js                     # 缓存读写接口，基于 LevelDB 实现
│   │   └── ttl-manager.js               # 缓存过期策略与定期清理
│   └── server/                          # 本地预览服务
│       ├── app.js                       # 基于 node:http 的静态与 API 路由
│       └── template/                    # 预览页面的 HTML 模板文件
├── config/                              # 配置文件目录
│   ├── default.json                     # 默认配置，包含爬虫参数与输出路径
│   └── sources.json                     # 数据源列表及对应的适配器映射
├── tests/                               # 单元测试与集成测试
│   ├── crawler.test.js                  # 爬虫模块的模拟请求测试
│   ├── parser.test.js                   # 解析规则覆盖率测试
│   └── fixtures/                        # 测试用的 HTML 样本文件
├── scripts/                             # 运维与辅助脚本
│   ├── daily-cron.sh                    # 每日定时任务的 shell 包装脚本
│   └── migrate-db.js                    # 缓存数据库版本迁移工具
├── docs/                                # 完整项目文档
│   ├── getting-started.md               # 入门指南
│   ├── configuration.md                 # 配置项详解
│   ├── adapter-development.md           # 适配器开发教程
│   └── export-integration.md            # 导出数据与第三方工具集成说明
├── output/                              # 默认导出目录（gitignore）
│   ├── articles.json                    # 全量文章索引 JSON 文件
│   └── summary.csv                      # 摘要信息 CSV 表格
├── package.json                         # npm 项目清单，含依赖与脚本命令
├── .eslintrc.js                         # ESLint 代码规范配置
├── .gitignore                           # Git 忽略规则
└── README.md                            # 本文件
```

## 贡献指南

首先在 GitHub 上 fork 本仓库，并将 fork 后的仓库克隆至本地。建议在 dev 分支上进行开发，所有新功能或修复均通过 Pull Request 提交至主仓库的 main 分支。

提交代码前请运行 npm run lint 与 npm run test 确保代码风格符合 ESLint 规范且所有单元测试通过。若新增适配器，需在 tests/fixtures 中补充对应的模拟 HTML 样本，并在 tests/parser.test.js 中添加覆盖测试。

更新文档时请同步修改 docs 目录下的对应文件。若新增配置项，务必在 config/default.json 中提供默认值，并在 docs/configuration.md 中添加说明。提交信息请遵循 Conventional Commits 格式，使用 feat:、fix:、docs:、refactor: 等前缀。

在 Pull Request 描述中请清晰说明变更目的、影响范围以及测试结果。若修复了已知问题，请关联对应的 issue 编号。项目维护者会在 48 小时内进行初步审核，并可能提出修改意见。

## 常见问题

执行 npm run crawl 时出现 ECONNRESET 或 ETIMEDOUT 错误应如何处理？

此类错误通常由网络不稳定或目标源站限流引起。可尝试在 config.json 中降低 crawler.concurrency 的值（如从 10 降至 3），并适当增加 crawler.timeout 与 crawler.retryDelay 的数值。同时检查运行环境是否能够稳定访问所列出的内容源域名，必要时配置代理或更换网络出口。

输出目录中的 articles.json 文件内容为空或仅包含极少数条目，如何排查？

首先确认 config/sources.json 中的 enabled 字段均为 true。其次检查适配器中的选择器规则是否与目标页面当前 DOM 结构匹配，尤其当源站改版后可能导致抽取失败。可开启 config.json 中的 debug 日志模式（将 logLevel 设为 debug），查看控制台输出的抽取失败详情。若某适配器长期失效，可参考适配器开发文档自行调整选择器规则。

如何定期自动执行抓取任务并生成最新的数据文件？

项目提供了 scripts/daily-cron.sh 脚本，可配合系统 crontab 实现定时执行。将该脚本中的 NODE_PATH 与 PROJECT_DIR 变量修改为实际路径，然后添加 crontab 条目，例如 0 2 * * * /path/to/daily-cron.sh 表示每日凌晨 2 点执行全量更新。脚本内部会自动执行 git pull 拉取最新代码（若使用仓库部署），然后运行 npm run crawl 并备份前一日输出文件。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
