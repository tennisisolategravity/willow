# WapLink Bridge

WapLink Bridge 是一个面向移动端内容聚合与链路分发的基础设施项目，专注于对多源移动站点下的文章资源进行统一索引、结构化映射与访问链路管理。项目定位于为开发者、内容运营者以及数据迁移工程师提供一套可复用的外链资源整合方案，解决在分散域名、多级目录、大量存量文章链接场景下的检索、归类与访问可达性校验问题。

本项目不提供具体内容展示界面，而是围绕 250 个移动端文章链接构建一个规范化的资源描述层与调用示例集合。目标用户包括从事站点迁移、内容资产管理、移动端兼容性测试以及批量链接状态监控的技术人员。通过 WapLink Bridge，用户能够快速获得一个可扩展的资源管理原型，理解如何对非标准化 URL 结构进行工程化处理，并将原始链接清单转化为可维护的项目资产。

## 功能概览

**多源站点资源映射**  
提供对 fuvxie.cn、cvsifc.cn、hcbezg.cn 三个移动域名的文章链接进行统一归类与编号索引的能力，支持按来源域名与文章 ID 进行基础筛选。

**链接状态探测接口示例**  
内置基于 HTTP 头分析的链接可达性检测脚本，可批量验证资源列表中各文章链接的响应状态码与内容类型。

**结构化元数据提取模板**  
提供从 URL 路径中解析文章编号、来源域名、文件扩展名等关键字段的 Python 与 Shell 参考实现，便于下游系统消费。

**批量导入与导出工具**  
支持将资源列表以 CSV 与 JSON 格式导出，便于接入外部监控系统或静态站点生成器。

**可配置的忽略规则引擎**  
允许用户自定义 URL 过滤模式，排除特定域名或文章 ID 范围，适配企业内部内容合规策略。

**日志与统计摘要模块**  
记录每次资源扫描的执行时间、成功数、失败数，并生成简单的域名分布与状态码分布报表。

## 应用场景

**移动站点内容迁移前的资产盘点**  
在将旧版移动站点迁移至新架构前，使用 WapLink Bridge 对现有文章链接进行全量扫描与状态记录，生成迁移前后的 URL 映射对照表，避免死链与内容丢失。

**内容安全与合规性审计**  
安全团队可利用本项目的链接列表与探测工具，定期检查外链资源是否存在异常跳转、被篡改或指向违规内容的风险，并生成审计日志。

**前端开发环境中的 mock 数据生成**  
前端开发者在构建移动端列表页或详情页时，可直接引用 WapLink Bridge 中的真实文章链接作为 mock 数据源，模拟不同域名下的跨域请求与资源加载表现。

**批量链接更新与重定向规则验证**  
当站点域名或目录结构发生变更时，运维人员可使用本项目的导出工具生成旧链接清单，配合重定向规则测试工具进行全量回归验证。

## 快速开始

以下命令演示如何克隆项目、安装基础依赖并执行首次资源扫描。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/waplink-bridge.git
cd waplink-bridge

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 执行资源列表扫描与状态检测
python scripts/scan_links.py --input data/raw_links.txt --output reports/status_report.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心脚本运行环境，用于链接解析与探测 |
| requests | 2.25.0 及以上 | HTTP 请求库，用于发送探测请求与处理响应 |
| click | 8.0.0 及以上 | 命令行参数解析框架，用于脚本交互 |
| pytest | 7.0.0 及以上 | 单元测试框架，用于验证解析逻辑（开发依赖） |
| black | 22.0.0 及以上 | 代码格式化工具（开发依赖） |
| pre-commit | 2.20.0 及以上 | Git 钩子管理工具（开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 入门指南 | docs/getting_started.md | 如何快速配置运行环境并执行首次扫描？ |
| 链接解析规范 | docs/url_parsing.md | URL 路径中各段落的含义是什么？如何自定义解析规则？ |
| 探测引擎配置 | docs/probe_config.md | 如何调整超时时间、重试策略与并发数？ |
| 导出格式说明 | docs/export_formats.md | 支持哪些导出格式？各格式的字段定义是什么？ |

## 资源列表

- http://wap.mobile.fuvxie.cn/Article/9303.shtml
- http://wap.mobile.cvsifc.cn/Article/8999.shtml
- http://wap.mobile.fuvxie.cn/Article/2522545.shtml
- http://wap.mobile.cvsifc.cn/Article/6504.shtml
- http://wap.mobile.hcbezg.cn/Article/3145759.shtml
- http://wap.mobile.hcbezg.cn/Article/768148.shtml
- http://wap.mobile.cvsifc.cn/Article/49758.shtml
- http://wap.mobile.cvsifc.cn/Article/56320.shtml
- http://wap.mobile.fuvxie.cn/Article/7834.shtml
- http://wap.mobile.hcbezg.cn/Article/40502.shtml
- http://wap.mobile.fuvxie.cn/Article/2011517.shtml
- http://wap.mobile.fuvxie.cn/Article/8263.shtml
- http://wap.mobile.hcbezg.cn/Article/8514.shtml
- http://wap.mobile.cvsifc.cn/Article/7669036.shtml
- http://wap.mobile.hcbezg.cn/Article/99267.shtml
- http://wap.mobile.hcbezg.cn/Article/30794.shtml
- http://wap.mobile.hcbezg.cn/Article/6771395.shtml
- http://wap.mobile.cvsifc.cn/Article/5578.shtml
- http://wap.mobile.hcbezg.cn/Article/0530.shtml
- http://wap.mobile.hcbezg.cn/Article/609978.shtml
- http://wap.mobile.cvsifc.cn/Article/9890869.shtml
- http://wap.mobile.cvsifc.cn/Article/655223.shtml
- http://wap.mobile.fuvxie.cn/Article/5283.shtml
- http://wap.mobile.fuvxie.cn/Article/999035.shtml
- http://wap.mobile.cvsifc.cn/Article/22436.shtml
- http://wap.mobile.cvsifc.cn/Article/5807228.shtml
- http://wap.mobile.hcbezg.cn/Article/01349.shtml
- http://wap.mobile.cvsifc.cn/Article/243221.shtml
- http://wap.mobile.hcbezg.cn/Article/6631697.shtml
- http://wap.mobile.cvsifc.cn/Article/882725.shtml
- http://wap.mobile.hcbezg.cn/Article/859476.shtml
- http://wap.mobile.cvsifc.cn/Article/700701.shtml
- http://wap.mobile.hcbezg.cn/Article/0574503.shtml
- http://wap.mobile.hcbezg.cn/Article/8159297.shtml
- http://wap.mobile.cvsifc.cn/Article/17439.shtml
- http://wap.mobile.cvsifc.cn/Article/89617.shtml
- http://wap.mobile.cvsifc.cn/Article/30639.shtml
- http://wap.mobile.cvsifc.cn/Article/4400.shtml
- http://wap.mobile.cvsifc.cn/Article/6582.shtml
- http://wap.mobile.hcbezg.cn/Article/526939.shtml
- http://wap.mobile.cvsifc.cn/Article/0337226.shtml
- http://wap.mobile.hcbezg.cn/Article/240268.shtml
- http://wap.mobile.hcbezg.cn/Article/045913.shtml
- http://wap.mobile.fuvxie.cn/Article/9692.shtml
- http://wap.mobile.hcbezg.cn/Article/3839620.shtml
- http://wap.mobile.hcbezg.cn/Article/2907652.shtml
- http://wap.mobile.hcbezg.cn/Article/889272.shtml
- http://wap.mobile.cvsifc.cn/Article/685180.shtml
- http://wap.mobile.hcbezg.cn/Article/1525720.shtml
- http://wap.mobile.hcbezg.cn/Article/5980327.shtml
- http://wap.mobile.hcbezg.cn/Article/0647.shtml
- http://wap.mobile.hcbezg.cn/Article/848419.shtml
- http://wap.mobile.fuvxie.cn/Article/0365.shtml
- http://wap.mobile.cvsifc.cn/Article/8446839.shtml
- http://wap.mobile.fuvxie.cn/Article/088876.shtml
- http://wap.mobile.fuvxie.cn/Article/127661.shtml
- http://wap.mobile.hcbezg.cn/Article/725931.shtml
- http://wap.mobile.fuvxie.cn/Article/838591.shtml
- http://wap.mobile.cvsifc.cn/Article/60632.shtml
- http://wap.mobile.fuvxie.cn/Article/4256.shtml
- http://wap.mobile.cvsifc.cn/Article/87792.shtml
- http://wap.mobile.hcbezg.cn/Article/5352.shtml
- http://wap.mobile.hcbezg.cn/Article/358116.shtml
- http://wap.mobile.fuvxie.cn/Article/82511.shtml
- http://wap.mobile.hcbezg.cn/Article/5580352.shtml
- http://wap.mobile.hcbezg.cn/Article/9958160.shtml
- http://wap.mobile.fuvxie.cn/Article/1756.shtml
- http://wap.mobile.cvsifc.cn/Article/973498.shtml
- http://wap.mobile.hcbezg.cn/Article/1705695.shtml
- http://wap.mobile.hcbezg.cn/Article/4630.shtml
- http://wap.mobile.hcbezg.cn/Article/5960.shtml
- http://wap.mobile.hcbezg.cn/Article/2315089.shtml
- http://wap.mobile.hcbezg.cn/Article/0204.shtml
- http://wap.mobile.hcbezg.cn/Article/086881.shtml
- http://wap.mobile.fuvxie.cn/Article/8434497.shtml
- http://wap.mobile.hcbezg.cn/Article/2471300.shtml
- http://wap.mobile.fuvxie.cn/Article/47564.shtml
- http://wap.mobile.cvsifc.cn/Article/295592.shtml
- http://wap.mobile.hcbezg.cn/Article/8000776.shtml
- http://wap.mobile.fuvxie.cn/Article/4132021.shtml
- http://wap.mobile.cvsifc.cn/Article/7620774.shtml
- http://wap.mobile.fuvxie.cn/Article/29522.shtml
- http://wap.mobile.cvsifc.cn/Article/0124979.shtml
- http://wap.mobile.cvsifc.cn/Article/88997.shtml
- http://wap.mobile.hcbezg.cn/Article/388224.shtml
- http://wap.mobile.fuvxie.cn/Article/0152.shtml
- http://wap.mobile.cvsifc.cn/Article/538408.shtml
- http://wap.mobile.hcbezg.cn/Article/004493.shtml
- http://wap.mobile.cvsifc.cn/Article/29007.shtml
- http://wap.mobile.cvsifc.cn/Article/751263.shtml
- http://wap.mobile.cvsifc.cn/Article/6589.shtml
- http://wap.mobile.cvsifc.cn/Article/473423.shtml
- http://wap.mobile.fuvxie.cn/Article/1590.shtml
- http://wap.mobile.hcbezg.cn/Article/2090.shtml
- http://wap.mobile.hcbezg.cn/Article/07457.shtml
- http://wap.mobile.fuvxie.cn/Article/71785.shtml
- http://wap.mobile.cvsifc.cn/Article/4327.shtml
- http://wap.mobile.fuvxie.cn/Article/7222.shtml
- http://wap.mobile.hcbezg.cn/Article/48279.shtml
- http://wap.mobile.cvsifc.cn/Article/0888.shtml
- http://wap.mobile.fuvxie.cn/Article/9440664.shtml
- http://wap.mobile.fuvxie.cn/Article/904930.shtml
- http://wap.mobile.cvsifc.cn/Article/4048479.shtml
- http://wap.mobile.fuvxie.cn/Article/6294.shtml
- http://wap.mobile.cvsifc.cn/Article/0232.shtml
- http://wap.mobile.cvsifc.cn/Article/429472.shtml
- http://wap.mobile.fuvxie.cn/Article/053334.shtml
- http://wap.mobile.cvsifc.cn/Article/3012.shtml
- http://wap.mobile.hcbezg.cn/Article/830758.shtml
- http://wap.mobile.hcbezg.cn/Article/10888.shtml
- http://wap.mobile.cvsifc.cn/Article/096948.shtml
- http://wap.mobile.cvsifc.cn/Article/3882991.shtml
- http://wap.mobile.cvsifc.cn/Article/5314.shtml
- http://wap.mobile.hcbezg.cn/Article/7211.shtml
- http://wap.mobile.cvsifc.cn/Article/5060119.shtml
- http://wap.mobile.fuvxie.cn/Article/432901.shtml
- http://wap.mobile.hcbezg.cn/Article/681379.shtml
- http://wap.mobile.cvsifc.cn/Article/520798.shtml
- http://wap.mobile.hcbezg.cn/Article/29807.shtml
- http://wap.mobile.cvsifc.cn/Article/5128.shtml
- http://wap.mobile.hcbezg.cn/Article/841266.shtml
- http://wap.mobile.hcbezg.cn/Article/17259.shtml
- http://wap.mobile.hcbezg.cn/Article/642759.shtml
- http://wap.mobile.fuvxie.cn/Article/2678.shtml
- http://wap.mobile.hcbezg.cn/Article/477788.shtml
- http://wap.mobile.fuvxie.cn/Article/5242713.shtml
- http://wap.mobile.fuvxie.cn/Article/406545.shtml
- http://wap.mobile.hcbezg.cn/Article/013017.shtml
- http://wap.mobile.hcbezg.cn/Article/7566.shtml
- http://wap.mobile.fuvxie.cn/Article/556513.shtml
- http://wap.mobile.fuvxie.cn/Article/863343.shtml
- http://wap.mobile.fuvxie.cn/Article/6214.shtml
- http://wap.mobile.hcbezg.cn/Article/33788.shtml
- http://wap.mobile.fuvxie.cn/Article/1839468.shtml
- http://wap.mobile.cvsifc.cn/Article/38876.shtml
- http://wap.mobile.cvsifc.cn/Article/24939.shtml
- http://wap.mobile.cvsifc.cn/Article/332976.shtml
- http://wap.mobile.cvsifc.cn/Article/63231.shtml
- http://wap.mobile.hcbezg.cn/Article/3862356.shtml
- http://wap.mobile.hcbezg.cn/Article/0231028.shtml
- http://wap.mobile.cvsifc.cn/Article/0122.shtml
- http://wap.mobile.fuvxie.cn/Article/69387.shtml
- http://wap.mobile.cvsifc.cn/Article/20772.shtml
- http://wap.mobile.cvsifc.cn/Article/5093923.shtml
- http://wap.mobile.cvsifc.cn/Article/8254.shtml
- http://wap.mobile.cvsifc.cn/Article/957877.shtml
- http://wap.mobile.fuvxie.cn/Article/12745.shtml
- http://wap.mobile.hcbezg.cn/Article/93934.shtml
- http://wap.mobile.hcbezg.cn/Article/6683.shtml
- http://wap.mobile.hcbezg.cn/Article/28978.shtml
- http://wap.mobile.fuvxie.cn/Article/99921.shtml
- http://wap.mobile.fuvxie.cn/Article/7681.shtml
- http://wap.mobile.fuvxie.cn/Article/9542650.shtml
- http://wap.mobile.fuvxie.cn/Article/5849.shtml
- http://wap.mobile.hcbezg.cn/Article/6301.shtml
- http://wap.mobile.hcbezg.cn/Article/72744.shtml
- http://wap.mobile.cvsifc.cn/Article/3623357.shtml
- http://wap.mobile.fuvxie.cn/Article/09935.shtml
- http://wap.mobile.hcbezg.cn/Article/273702.shtml
- http://wap.mobile.hcbezg.cn/Article/711951.shtml
- http://wap.mobile.cvsifc.cn/Article/2350.shtml
- http://wap.mobile.cvsifc.cn/Article/884149.shtml
- http://wap.mobile.fuvxie.cn/Article/50829.shtml
- http://wap.mobile.hcbezg.cn/Article/846972.shtml
- http://wap.mobile.cvsifc.cn/Article/2298.shtml
- http://wap.mobile.cvsifc.cn/Article/6588.shtml
- http://wap.mobile.hcbezg.cn/Article/72138.shtml
- http://wap.mobile.hcbezg.cn/Article/345284.shtml
- http://wap.mobile.cvsifc.cn/Article/0965.shtml
- http://wap.mobile.fuvxie.cn/Article/25427.shtml
- http://wap.mobile.cvsifc.cn/Article/56449.shtml
- http://wap.mobile.fuvxie.cn/Article/15725.shtml
- http://wap.mobile.fuvxie.cn/Article/215264.shtml
- http://wap.mobile.hcbezg.cn/Article/22113.shtml
- http://wap.mobile.cvsifc.cn/Article/15890.shtml
- http://wap.mobile.hcbezg.cn/Article/8649559.shtml
- http://wap.mobile.cvsifc.cn/Article/749333.shtml
- http://wap.mobile.fuvxie.cn/Article/3563.shtml
- http://wap.mobile.cvsifc.cn/Article/90200.shtml
- http://wap.mobile.hcbezg.cn/Article/0451.shtml
- http://wap.mobile.hcbezg.cn/Article/4018480.shtml
- http://wap.mobile.fuvxie.cn/Article/99769.shtml
- http://wap.mobile.hcbezg.cn/Article/8460969.shtml
- http://wap.mobile.hcbezg.cn/Article/9070.shtml
- http://wap.mobile.cvsifc.cn/Article/7753629.shtml
- http://wap.mobile.fuvxie.cn/Article/91107.shtml
- http://wap.mobile.hcbezg.cn/Article/72648.shtml
- http://wap.mobile.hcbezg.cn/Article/56905.shtml
- http://wap.mobile.hcbezg.cn/Article/415103.shtml
- http://wap.mobile.fuvxie.cn/Article/380325.shtml
- http://wap.mobile.hcbezg.cn/Article/0056.shtml
- http://wap.mobile.hcbezg.cn/Article/4841.shtml
- http://wap.mobile.hcbezg.cn/Article/3002.shtml
- http://wap.mobile.fuvxie.cn/Article/7126.shtml
- http://wap.mobile.cvsifc.cn/Article/78954.shtml
- http://wap.mobile.hcbezg.cn/Article/83827.shtml
- http://wap.mobile.cvsifc.cn/Article/5920.shtml
- http://wap.mobile.cvsifc.cn/Article/441864.shtml
- http://wap.mobile.fuvxie.cn/Article/5949.shtml
- http://wap.mobile.hcbezg.cn/Article/2104.shtml
- http://wap.mobile.hcbezg.cn/Article/6998.shtml
- http://wap.mobile.fuvxie.cn/Article/2888143.shtml
- http://wap.mobile.fuvxie.cn/Article/0064.shtml
- http://wap.mobile.fuvxie.cn/Article/7862.shtml
- http://wap.mobile.cvsifc.cn/Article/053025.shtml
- http://wap.mobile.hcbezg.cn/Article/4977864.shtml
- http://wap.mobile.fuvxie.cn/Article/27467.shtml
- http://wap.mobile.fuvxie.cn/Article/09398.shtml
- http://wap.mobile.fuvxie.cn/Article/9149449.shtml
- http://wap.mobile.fuvxie.cn/Article/7592.shtml
- http://wap.mobile.cvsifc.cn/Article/60801.shtml
- http://wap.mobile.hcbezg.cn/Article/969277.shtml
- http://wap.mobile.cvsifc.cn/Article/9831.shtml
- http://wap.mobile.cvsifc.cn/Article/69135.shtml
- http://wap.mobile.cvsifc.cn/Article/44736.shtml
- http://wap.mobile.fuvxie.cn/Article/698775.shtml
- http://wap.mobile.hcbezg.cn/Article/42659.shtml
- http://wap.mobile.fuvxie.cn/Article/1746.shtml
- http://wap.mobile.fuvxie.cn/Article/9375362.shtml
- http://wap.mobile.hcbezg.cn/Article/7452775.shtml
- http://wap.mobile.cvsifc.cn/Article/6584590.shtml
- http://wap.mobile.cvsifc.cn/Article/518276.shtml
- http://wap.mobile.hcbezg.cn/Article/38451.shtml
- http://wap.mobile.cvsifc.cn/Article/154096.shtml
- http://wap.mobile.fuvxie.cn/Article/84673.shtml
- http://wap.mobile.fuvxie.cn/Article/65727.shtml
- http://wap.mobile.fuvxie.cn/Article/799280.shtml
- http://wap.mobile.hcbezg.cn/Article/60901.shtml
- http://wap.mobile.fuvxie.cn/Article/6681458.shtml
- http://wap.mobile.fuvxie.cn/Article/563634.shtml
- http://wap.mobile.fuvxie.cn/Article/232555.shtml
- http://wap.mobile.hcbezg.cn/Article/5685385.shtml
- http://wap.mobile.hcbezg.cn/Article/397810.shtml
- http://wap.mobile.fuvxie.cn/Article/4672497.shtml
- http://wap.mobile.cvsifc.cn/Article/04120.shtml
- http://wap.mobile.hcbezg.cn/Article/16710.shtml
- http://wap.mobile.cvsifc.cn/Article/825094.shtml
- http://wap.mobile.cvsifc.cn/Article/5758975.shtml
- http://wap.mobile.fuvxie.cn/Article/5452824.shtml
- http://wap.mobile.hcbezg.cn/Article/215532.shtml
- http://wap.mobile.cvsifc.cn/Article/7506951.shtml
- http://wap.mobile.fuvxie.cn/Article/39549.shtml
- http://wap.mobile.hcbezg.cn/Article/01073.shtml
- http://wap.mobile.cvsifc.cn/Article/859839.shtml
- http://wap.mobile.hcbezg.cn/Article/5110757.shtml
- http://wap.mobile.hcbezg.cn/Article/6584569.shtml
- http://wap.mobile.cvsifc.cn/Article/8136.shtml
- http://wap.mobile.fuvxie.cn/Article/931916.shtml
- http://wap.mobile.cvsifc.cn/Article/700853.shtml
- http://wap.mobile.cvsifc.cn/Article/304800.shtml

## 项目结构

```
waplink-bridge/
├── data/
│   ├── raw_links.txt          # 原始资源链接清单（250条）
│   └── domains.json           # 域名与站点别名映射配置
├── scripts/
│   ├── scan_links.py          # 主扫描脚本，执行链接探测与状态输出
│   ├── parse_url.py           # URL 解析模块，提取域名、ID、扩展名
│   └── export_csv.py          # 导出为 CSV 格式的工具脚本
├── tests/
│   ├── test_parse.py          # 单元测试：URL 解析逻辑覆盖
│   └── test_scan.py           # 单元测试：扫描流程与异常处理
├── reports/
│   └── .gitkeep               # 用于存放扫描报告的输出目录
├── docs/
│   ├── getting_started.md     # 快速入门指南
│   ├── url_parsing.md         # URL 结构解析规范说明
│   └── probe_config.md        # 探测引擎参数调优文档
├── config/
│   ├── ignore_patterns.yaml   # 忽略规则配置（域名/ID 黑名单）
│   └── probe_settings.yaml    # 超时、重试、并发等探测参数
├── requirements.txt           # Python 生产依赖列表
├── requirements-dev.txt       # Python 开发依赖列表
├── .pre-commit-config.yaml    # Git 提交前检查钩子配置
└── README.md                  # 项目说明文档（本文件）
```

## 贡献指南

1. 克隆项目并在本地安装开发依赖，运行 `pre-commit install` 激活 Git 钩子，确保代码风格与提交规范一致。
2. 在 `data/raw_links.txt` 中追加或修改资源链接后，必须执行 `python scripts/scan_links.py --validate` 验证链接格式是否符合解析要求。
3. 新增解析规则或探测参数时，需同步更新 `docs/` 下对应的说明文档，并补充单元测试到 `tests/` 目录。
4. 提交前执行 `pytest tests/` 确保全部测试用例通过，且覆盖率不低于 90%。
5. 发起 Pull Request 时，请在描述中注明变更类型（新增链接、修复解析、优化探测等），并附上 `reports/` 中的测试报告摘要。

## 常见问题

**Q：扫描脚本返回超时错误如何解决？**  
A：可编辑 `config/probe_settings.yaml` 中的 `timeout` 字段增加单次请求等待时间，或调整 `max_retries` 参数增加重试次数。若批量扫描触发源站限流，建议调低 `concurrency` 并发数。

**Q：如何只扫描特定域名下的链接？**  
A：在命令行使用 `--domain` 参数指定，例如 `python scripts/scan_links.py --domain hcbezg.cn`。也可在 `config/ignore_patterns.yaml` 中配置反向过滤规则。

**Q：项目是否支持 HTTPS 链接的探测？**  
A：脚本底层基于 requests 库，默认遵循 HTTP 到 HTTPS 的重定向，但不会自动升级协议。若需强制使用 HTTPS，可在 `config/probe_settings.yaml` 中启用 `force_https` 选项，脚本将在请求前将 URL 协议替换为 https。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
