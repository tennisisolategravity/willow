# WebArchive Link Aggregator

WebArchive Link Aggregator 是一个面向技术文档研究者、历史数据归档工程师和内容溯源分析人员的结构化外链资源归集系统。该项目针对移动端碎片化技术文章散落于多个次级域名、缺乏统一索引和可检索元数据的现状，提供了一套基于域名来源与文章编号的轻量级资源映射方案。

项目本身不托管任何原始内容，而是以高完整度的外链清单为核心资产，配合自动化分类脚本，帮助用户快速定位特定来源站点（cvsifc.cn、fuvxie.cn、hcbezg.cn）下的技术文章入口。目标用户包括爬虫策略工程师、竞品分析专员、学术文献补充材料整理者以及个人知识库构建者。

## 功能概览

- 按来源域名分组索引：自动识别 cvsifc.cn、fuvxie.cn、hcbezg.cn 三大移动端内容源，并生成独立的映射视图。

- 文章编号快速检索：支持通过 Article/ 后的数字编号进行精确匹配，便于与外部日志或数据库记录关联。

- 原始链接完整性校验：内置链接格式检查器，可识别裸域名与带协议前缀的混合条目，确保输出符合下游系统的导入规范。

- 批量导出多格式清单：支持将资源列表导出为纯文本、JSON 数组或 CSV 表格，适配不同脚本语言的批量请求构造。

- 去重与变更检测：对同一文章编号在不同域名下的重复出现进行标记，并记录首次与末次抓取时间戳。

- 定时同步钩子：提供 cron 表达式接口，可定期重新拉取列表并更新本地缓存，适用于长期监控场景。

- 访问状态快照记录：每条链接可附加 HTTP 状态码与响应时长元数据，辅助判断资源可用性变化趋势。

## 应用场景

技术文档历史版本追溯：当某篇技术博客或产品公告被下线或迁移时，通过该资源列表中的历史链接入口，结合第三方缓存服务（如 Wayback Machine）进行内容复原比对。

移动端 SEO 外链审计：SEO 分析师可利用本清单快速获取指定二级域名下的全部文章入口，配合外链分析工具批量检查页面标题、关键词密度及内链分布。

爬虫任务队列构建：数据采集工程师可将本列表作为起始种子 URL，通过 Article 编号规律构造增量爬取计划，减少对站点地图的依赖。

内部知识库引用规范化：企业知识管理团队将项目中的链接作为外部参考条目的标准格式模板，统一团队对外部资料的引用方式与来源标注。

## 快速开始

以下命令演示了从代码仓库克隆、安装基础依赖到启动本地索引服务的完整流程。

```bash
git clone https://github.com/webarchive/link-aggregator.git
cd link-aggregator
pip install -r requirements.txt
python scripts/build_index.py --input data/raw_urls.txt --output data/index.json
python server.py --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心解析与索引生成脚本运行环境 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装依赖库 |
| requests | 2.28.0 及以上 | 发送 HTTP 请求以校验链接可达性 |
| pytest | 7.2.0 及以上 | 单元测试框架，用于验证索引构建逻辑 |
| Git | 2.30.0 及以上 | 克隆仓库及版本控制 |
| curl | 7.68.0 及以上 | 用于外部链接快速调试与单条测试 |
| jq | 1.6 及以上 | JSON 数据流处理，辅助查看索引文件 |
| make | 3.81 及以上 | 自动化任务执行器，用于批量操作组合 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何导入自定义链接列表、如何按域名过滤、如何导出不同格式的索引文件 |
| 运维指南 | docs/operations.md | 如何配置定时同步任务、如何备份索引快照、如何监控链接状态变更 |
| 开发者文档 | docs/development.md | 索引构建流程的类图、新增解析器的方法、单元测试编写规范 |
| 架构概述 | docs/architecture.md | 系统采用的分层模型、数据流走向、各模块间的接口契约定义 |
| 变更日志 | CHANGELOG.md | 每个版本的迭代历史、已修复缺陷、不兼容变更说明与升级路径 |

## 资源列表

- http://wap.mobile.cvsifc.cn/Article/9965.shtml
- http://wap.mobile.fuvxie.cn/Article/1246.shtml
- http://wap.mobile.cvsifc.cn/Article/8972.shtml
- http://wap.mobile.fuvxie.cn/Article/6471465.shtml
- http://wap.mobile.hcbezg.cn/Article/2088.shtml
- http://wap.mobile.cvsifc.cn/Article/1188067.shtml
- http://wap.mobile.hcbezg.cn/Article/6291.shtml
- http://wap.mobile.hcbezg.cn/Article/854915.shtml
- http://wap.mobile.cvsifc.cn/Article/6297418.shtml
- http://wap.mobile.fuvxie.cn/Article/51329.shtml
- http://wap.mobile.cvsifc.cn/Article/5218347.shtml
- http://wap.mobile.hcbezg.cn/Article/027887.shtml
- http://wap.mobile.fuvxie.cn/Article/9889723.shtml
- http://wap.mobile.fuvxie.cn/Article/13763.shtml
- http://wap.mobile.fuvxie.cn/Article/8558854.shtml
- http://wap.mobile.fuvxie.cn/Article/070989.shtml
- http://wap.mobile.fuvxie.cn/Article/7058201.shtml
- http://wap.mobile.hcbezg.cn/Article/63364.shtml
- http://wap.mobile.hcbezg.cn/Article/7910.shtml
- http://wap.mobile.cvsifc.cn/Article/0537.shtml
- http://wap.mobile.fuvxie.cn/Article/7494903.shtml
- http://wap.mobile.fuvxie.cn/Article/396566.shtml
- http://wap.mobile.fuvxie.cn/Article/6275.shtml
- http://wap.mobile.fuvxie.cn/Article/157006.shtml
- http://wap.mobile.cvsifc.cn/Article/70854.shtml
- http://wap.mobile.hcbezg.cn/Article/09716.shtml
- http://wap.mobile.fuvxie.cn/Article/232968.shtml
- http://wap.mobile.fuvxie.cn/Article/227719.shtml
- http://wap.mobile.cvsifc.cn/Article/94450.shtml
- http://wap.mobile.cvsifc.cn/Article/1060.shtml
- http://wap.mobile.hcbezg.cn/Article/6419.shtml
- http://wap.mobile.fuvxie.cn/Article/240208.shtml
- http://wap.mobile.fuvxie.cn/Article/62561.shtml
- http://wap.mobile.fuvxie.cn/Article/966985.shtml
- http://wap.mobile.fuvxie.cn/Article/727457.shtml
- http://wap.mobile.cvsifc.cn/Article/955525.shtml
- http://wap.mobile.cvsifc.cn/Article/3219602.shtml
- http://wap.mobile.cvsifc.cn/Article/7471201.shtml
- http://wap.mobile.hcbezg.cn/Article/8571606.shtml
- http://wap.mobile.hcbezg.cn/Article/2704776.shtml
- http://wap.mobile.fuvxie.cn/Article/71104.shtml
- http://wap.mobile.fuvxie.cn/Article/79181.shtml
- http://wap.mobile.fuvxie.cn/Article/22165.shtml
- http://wap.mobile.cvsifc.cn/Article/3959452.shtml
- http://wap.mobile.cvsifc.cn/Article/0311.shtml
- http://wap.mobile.fuvxie.cn/Article/513046.shtml
- http://wap.mobile.hcbezg.cn/Article/00014.shtml
- http://wap.mobile.hcbezg.cn/Article/3115.shtml
- http://wap.mobile.cvsifc.cn/Article/30643.shtml
- http://wap.mobile.cvsifc.cn/Article/66599.shtml
- http://wap.mobile.cvsifc.cn/Article/473633.shtml
- http://wap.mobile.fuvxie.cn/Article/0946.shtml
- http://wap.mobile.hcbezg.cn/Article/2518.shtml
- http://wap.mobile.fuvxie.cn/Article/41372.shtml
- http://wap.mobile.cvsifc.cn/Article/8766.shtml
- http://wap.mobile.hcbezg.cn/Article/6263.shtml
- http://wap.mobile.hcbezg.cn/Article/78541.shtml
- http://wap.mobile.hcbezg.cn/Article/912081.shtml
- http://wap.mobile.fuvxie.cn/Article/6346021.shtml
- http://wap.mobile.cvsifc.cn/Article/6848190.shtml
- http://wap.mobile.cvsifc.cn/Article/6497.shtml
- http://wap.mobile.cvsifc.cn/Article/3019.shtml
- http://wap.mobile.fuvxie.cn/Article/49052.shtml
- http://wap.mobile.cvsifc.cn/Article/1058.shtml
- http://wap.mobile.cvsifc.cn/Article/933736.shtml
- http://wap.mobile.cvsifc.cn/Article/051878.shtml
- http://wap.mobile.cvsifc.cn/Article/4065836.shtml
- http://wap.mobile.cvsifc.cn/Article/69528.shtml
- http://wap.mobile.hcbezg.cn/Article/262173.shtml
- http://wap.mobile.fuvxie.cn/Article/48878.shtml
- http://wap.mobile.cvsifc.cn/Article/1430.shtml
- http://wap.mobile.cvsifc.cn/Article/510781.shtml
- http://wap.mobile.hcbezg.cn/Article/5640510.shtml
- http://wap.mobile.hcbezg.cn/Article/467326.shtml
- http://wap.mobile.cvsifc.cn/Article/0165.shtml
- http://wap.mobile.hcbezg.cn/Article/2274411.shtml
- http://wap.mobile.cvsifc.cn/Article/86763.shtml
- http://wap.mobile.fuvxie.cn/Article/2164.shtml
- http://wap.mobile.cvsifc.cn/Article/71658.shtml
- http://wap.mobile.cvsifc.cn/Article/4474.shtml
- http://wap.mobile.cvsifc.cn/Article/986709.shtml
- http://wap.mobile.cvsifc.cn/Article/499818.shtml
- http://wap.mobile.cvsifc.cn/Article/298398.shtml
- http://wap.mobile.fuvxie.cn/Article/0707.shtml
- http://wap.mobile.cvsifc.cn/Article/94162.shtml
- http://wap.mobile.hcbezg.cn/Article/869792.shtml
- http://wap.mobile.cvsifc.cn/Article/1837.shtml
- http://wap.mobile.fuvxie.cn/Article/8780222.shtml
- http://wap.mobile.fuvxie.cn/Article/5876.shtml
- http://wap.mobile.fuvxie.cn/Article/147540.shtml
- http://wap.mobile.hcbezg.cn/Article/0975.shtml
- http://wap.mobile.hcbezg.cn/Article/394521.shtml
- http://wap.mobile.fuvxie.cn/Article/2278114.shtml
- http://wap.mobile.fuvxie.cn/Article/39469.shtml
- http://wap.mobile.fuvxie.cn/Article/8731.shtml
- http://wap.mobile.fuvxie.cn/Article/7081.shtml
- http://wap.mobile.fuvxie.cn/Article/1009.shtml
- http://wap.mobile.cvsifc.cn/Article/83713.shtml
- http://wap.mobile.hcbezg.cn/Article/098873.shtml
- http://wap.mobile.hcbezg.cn/Article/016834.shtml
- http://wap.mobile.hcbezg.cn/Article/505944.shtml
- http://wap.mobile.cvsifc.cn/Article/9234.shtml
- http://wap.mobile.cvsifc.cn/Article/9780.shtml
- http://wap.mobile.cvsifc.cn/Article/2176.shtml
- http://wap.mobile.fuvxie.cn/Article/5717009.shtml
- http://wap.mobile.fuvxie.cn/Article/8745.shtml
- http://wap.mobile.cvsifc.cn/Article/56083.shtml
- http://wap.mobile.hcbezg.cn/Article/88255.shtml
- http://wap.mobile.cvsifc.cn/Article/7840.shtml
- http://wap.mobile.hcbezg.cn/Article/305164.shtml
- http://wap.mobile.cvsifc.cn/Article/42444.shtml
- http://wap.mobile.fuvxie.cn/Article/457264.shtml
- http://wap.mobile.hcbezg.cn/Article/43699.shtml
- http://wap.mobile.hcbezg.cn/Article/69504.shtml
- http://wap.mobile.cvsifc.cn/Article/327368.shtml
- http://wap.mobile.fuvxie.cn/Article/08826.shtml
- http://wap.mobile.cvsifc.cn/Article/56541.shtml
- http://wap.mobile.fuvxie.cn/Article/205064.shtml
- http://wap.mobile.fuvxie.cn/Article/31765.shtml
- http://wap.mobile.fuvxie.cn/Article/909189.shtml
- http://wap.mobile.cvsifc.cn/Article/088911.shtml
- http://wap.mobile.fuvxie.cn/Article/510103.shtml
- http://wap.mobile.cvsifc.cn/Article/4420.shtml
- http://wap.mobile.fuvxie.cn/Article/264469.shtml
- http://wap.mobile.fuvxie.cn/Article/36756.shtml
- http://wap.mobile.fuvxie.cn/Article/2392007.shtml
- http://wap.mobile.cvsifc.cn/Article/5876269.shtml
- http://wap.mobile.cvsifc.cn/Article/4471.shtml
- http://wap.mobile.cvsifc.cn/Article/2264056.shtml
- http://wap.mobile.fuvxie.cn/Article/3294.shtml
- http://wap.mobile.cvsifc.cn/Article/032367.shtml
- http://wap.mobile.fuvxie.cn/Article/0302.shtml
- http://wap.mobile.cvsifc.cn/Article/341320.shtml
- http://wap.mobile.fuvxie.cn/Article/9386.shtml
- http://wap.mobile.cvsifc.cn/Article/8899184.shtml
- http://wap.mobile.cvsifc.cn/Article/4542.shtml
- http://wap.mobile.cvsifc.cn/Article/6709062.shtml
- http://wap.mobile.fuvxie.cn/Article/9438722.shtml
- http://wap.mobile.hcbezg.cn/Article/83709.shtml
- http://wap.mobile.cvsifc.cn/Article/8229.shtml
- http://wap.mobile.hcbezg.cn/Article/0550.shtml
- http://wap.mobile.cvsifc.cn/Article/167904.shtml
- http://wap.mobile.fuvxie.cn/Article/4081257.shtml
- http://wap.mobile.fuvxie.cn/Article/65615.shtml
- http://wap.mobile.cvsifc.cn/Article/2081657.shtml
- http://wap.mobile.cvsifc.cn/Article/434831.shtml
- http://wap.mobile.cvsifc.cn/Article/3091956.shtml
- http://wap.mobile.cvsifc.cn/Article/800287.shtml
- http://wap.mobile.cvsifc.cn/Article/4306.shtml
- http://wap.mobile.hcbezg.cn/Article/024957.shtml
- http://wap.mobile.cvsifc.cn/Article/8471677.shtml
- http://wap.mobile.fuvxie.cn/Article/4910.shtml
- http://wap.mobile.hcbezg.cn/Article/801206.shtml
- http://wap.mobile.hcbezg.cn/Article/76237.shtml
- http://wap.mobile.fuvxie.cn/Article/5756190.shtml
- http://wap.mobile.fuvxie.cn/Article/3715.shtml
- http://wap.mobile.cvsifc.cn/Article/9828907.shtml
- http://wap.mobile.fuvxie.cn/Article/8282.shtml
- http://wap.mobile.hcbezg.cn/Article/9253946.shtml
- http://wap.mobile.cvsifc.cn/Article/2902538.shtml
- http://wap.mobile.cvsifc.cn/Article/5268.shtml
- http://wap.mobile.hcbezg.cn/Article/69291.shtml
- http://wap.mobile.cvsifc.cn/Article/80872.shtml
- http://wap.mobile.hcbezg.cn/Article/7542565.shtml
- http://wap.mobile.hcbezg.cn/Article/2839.shtml
- http://wap.mobile.fuvxie.cn/Article/70554.shtml
- http://wap.mobile.cvsifc.cn/Article/068119.shtml
- http://wap.mobile.fuvxie.cn/Article/7662.shtml
- http://wap.mobile.hcbezg.cn/Article/03703.shtml
- http://wap.mobile.hcbezg.cn/Article/0881583.shtml
- http://wap.mobile.cvsifc.cn/Article/98660.shtml
- http://wap.mobile.cvsifc.cn/Article/51776.shtml
- http://wap.mobile.fuvxie.cn/Article/34951.shtml
- http://wap.mobile.hcbezg.cn/Article/2394883.shtml
- http://wap.mobile.cvsifc.cn/Article/465926.shtml
- http://wap.mobile.fuvxie.cn/Article/9028.shtml
- http://wap.mobile.hcbezg.cn/Article/5220.shtml
- http://wap.mobile.cvsifc.cn/Article/934567.shtml
- http://wap.mobile.fuvxie.cn/Article/39966.shtml
- http://wap.mobile.fuvxie.cn/Article/093894.shtml
- http://wap.mobile.cvsifc.cn/Article/6840.shtml
- http://wap.mobile.fuvxie.cn/Article/167563.shtml
- http://wap.mobile.cvsifc.cn/Article/5860506.shtml
- http://wap.mobile.cvsifc.cn/Article/56832.shtml
- http://wap.mobile.hcbezg.cn/Article/080019.shtml
- http://wap.mobile.hcbezg.cn/Article/967908.shtml
- http://wap.mobile.fuvxie.cn/Article/31200.shtml
- http://wap.mobile.cvsifc.cn/Article/4762757.shtml
- http://wap.mobile.hcbezg.cn/Article/9128.shtml
- http://wap.mobile.fuvxie.cn/Article/7600.shtml
- http://wap.mobile.fuvxie.cn/Article/177699.shtml
- http://wap.mobile.cvsifc.cn/Article/650107.shtml
- http://wap.mobile.cvsifc.cn/Article/0529.shtml
- http://wap.mobile.hcbezg.cn/Article/582721.shtml
- http://wap.mobile.hcbezg.cn/Article/6056.shtml
- http://wap.mobile.hcbezg.cn/Article/960600.shtml
- http://wap.mobile.cvsifc.cn/Article/550786.shtml
- http://wap.mobile.cvsifc.cn/Article/2842.shtml
- http://wap.mobile.fuvxie.cn/Article/068894.shtml
- http://wap.mobile.hcbezg.cn/Article/54102.shtml
- http://wap.mobile.cvsifc.cn/Article/5963882.shtml
- http://wap.mobile.fuvxie.cn/Article/5227923.shtml
- http://wap.mobile.cvsifc.cn/Article/9125723.shtml
- http://wap.mobile.cvsifc.cn/Article/3227624.shtml
- http://wap.mobile.cvsifc.cn/Article/1716840.shtml
- http://wap.mobile.hcbezg.cn/Article/8126709.shtml
- http://wap.mobile.hcbezg.cn/Article/1763802.shtml
- http://wap.mobile.fuvxie.cn/Article/9646.shtml
- http://wap.mobile.cvsifc.cn/Article/1827.shtml
- http://wap.mobile.cvsifc.cn/Article/7640308.shtml
- http://wap.mobile.cvsifc.cn/Article/54894.shtml
- http://wap.mobile.cvsifc.cn/Article/8194.shtml
- http://wap.mobile.cvsifc.cn/Article/62132.shtml
- http://wap.mobile.fuvxie.cn/Article/268272.shtml
- http://wap.mobile.fuvxie.cn/Article/66276.shtml
- http://wap.mobile.cvsifc.cn/Article/47335.shtml
- http://wap.mobile.cvsifc.cn/Article/9799943.shtml
- http://wap.mobile.cvsifc.cn/Article/0086.shtml
- http://wap.mobile.fuvxie.cn/Article/86260.shtml
- http://wap.mobile.fuvxie.cn/Article/01599.shtml
- http://wap.mobile.cvsifc.cn/Article/475476.shtml
- http://wap.mobile.hcbezg.cn/Article/2703.shtml
- http://wap.mobile.cvsifc.cn/Article/02694.shtml
- http://wap.mobile.fuvxie.cn/Article/96685.shtml
- http://wap.mobile.fuvxie.cn/Article/8904894.shtml
- http://wap.mobile.fuvxie.cn/Article/4682.shtml
- http://wap.mobile.hcbezg.cn/Article/322334.shtml
- http://wap.mobile.hcbezg.cn/Article/465267.shtml
- http://wap.mobile.fuvxie.cn/Article/8412464.shtml
- http://wap.mobile.hcbezg.cn/Article/7706.shtml
- http://wap.mobile.cvsifc.cn/Article/1535380.shtml
- http://wap.mobile.hcbezg.cn/Article/3269.shtml
- http://wap.mobile.fuvxie.cn/Article/1187734.shtml
- http://wap.mobile.cvsifc.cn/Article/56505.shtml
- http://wap.mobile.cvsifc.cn/Article/31236.shtml
- http://wap.mobile.fuvxie.cn/Article/3583.shtml
- http://wap.mobile.cvsifc.cn/Article/99126.shtml
- http://wap.mobile.hcbezg.cn/Article/0788367.shtml
- http://wap.mobile.cvsifc.cn/Article/79044.shtml
- http://wap.mobile.hcbezg.cn/Article/018522.shtml
- http://wap.mobile.cvsifc.cn/Article/843696.shtml
- http://wap.mobile.cvsifc.cn/Article/243672.shtml
- http://wap.mobile.cvsifc.cn/Article/555065.shtml
- http://wap.mobile.hcbezg.cn/Article/4032.shtml
- http://wap.mobile.hcbezg.cn/Article/202237.shtml
- http://wap.mobile.cvsifc.cn/Article/901593.shtml
- http://wap.mobile.hcbezg.cn/Article/703704.shtml
- http://wap.mobile.cvsifc.cn/Article/2311637.shtml
- http://wap.mobile.fuvxie.cn/Article/01512.shtml
- http://wap.mobile.fuvxie.cn/Article/9544.shtml

## 项目结构

```
link-aggregator/
├── README.md                        # 项目总览与使用入口
├── CHANGELOG.md                     # 版本迭代记录与发布说明
├── LICENSE                          # MIT 许可证全文
├── Makefile                         # 自动化任务集合（格式检查、测试、构建）
├── requirements.txt                 # Python 运行时依赖清单
├── data/
│   ├── raw_urls.txt                 # 原始链接列表，每行一条，未经处理
│   ├── index.json                   # 构建后的索引主文件，包含域名分组与元数据
│   └── snapshots/                   # 历史快照目录，按日期归档旧索引
│       └── 2026-07-08.json
├── scripts/
│   ├── build_index.py               # 核心构建脚本：读取 raw_urls.txt，输出 index.json
│   ├── check_duplicates.py          # 去重检测工具，报告重复文章编号
│   ├── export_formats.py            # 格式转换器：支持 json、csv、txt 导出
│   └── validate_links.py            # 链接可用性校验器，附带重试机制与超时配置
├── tests/
│   ├── test_builder.py              # 构建器单元测试，覆盖空输入与畸形链接场景
│   ├── test_validator.py            # 校验器功能测试，模拟各类 HTTP 响应码
│   └── fixtures/                    # 测试用固定数据样本
│       └── sample_urls.txt
├── docs/
│   ├── user_guide.md                # 面向最终用户的操作指引
│   ├── operations.md                # 面向运维人员的部署与监控手册
│   ├── development.md               # 面向开发者的代码贡献与二次开发说明
│   └── architecture.md              # 系统设计文档，包含组件关系图与数据字典
└── server.py                        # 简易 HTTP 服务，用于本地预览索引内容
```

## 贡献指南

1. 从 GitHub Issues 中认领未被指派的待办任务，或提出新的功能建议与缺陷报告。建议先搜索已有议题，避免重复提交。

2. Fork 本仓库到个人账户，并基于 main 分支创建以 feature/ 或 fix/ 为前缀的命名分支，例如 feature/support-json-stream-export。

3. 编写代码或文档变更时，请遵循项目配置的 PEP 8 代码风格，并为新增函数或类添加 docstring 说明。若为功能性修改，需在 tests/ 目录下补充对应的测试用例。

4. 提交前运行 make test 确保所有现有测试通过，并执行 make lint 检查代码格式问题。新提交的 commit message 请采用约定式提交规范（类型: 简短描述）。

5. 向原仓库发起 Pull Request，并在描述中关联对应的 Issue 编号，同时附上测试结果截图或日志片段，以便维护者快速审阅。

## 常见问题

Q: 资源列表中的某些链接返回 404 或超时，项目是否会自动处理这些无效条目？

A: 项目核心定位是外链归集与索引，不强制要求每条链接的实时可用性。但脚本 scripts/validate_links.py 提供了独立的校验工具，可定期运行并将状态码记录到索引的元数据字段中。用户可根据校验结果手动筛选或过滤无效条目。

Q: 如何将本项目部署到生产环境用于定时任务？

A: 推荐使用 cron 或 systemd timer 定期执行 scripts/build_index.py，并结合 scripts/export_formats.py 生成最新的 JSON 索引文件。若需要提供外部访问接口，可使用 server.py 启动轻量级 HTTP 服务，或通过反向代理（如 Nginx）将其挂载到既有域名下。

Q: 不同域名（cvsifc.cn、fuvxie.cn、hcbezg.cn）之间的文章编号是否存在冲突或重复？

A: 编号本身在不同域名间相互独立，但实际数据中可能出现跨域重复。项目在构建索引时会自动检测重复编号，并在 index.json 的 each article entry 下添加 duplicate_of 字段指向首次出现的条目。用户可以依据此字段进行合并或去重操作。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
