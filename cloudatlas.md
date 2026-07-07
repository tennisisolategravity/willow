# LinkMap Aggregate

LinkMap Aggregate 是一个面向技术研究人员、数据挖掘工程师和内容聚合开发者的结构化外链资源归集系统。该项目通过对分散在多个内容发布节点上的文章链接进行系统性采集、分类与元数据抽取，提供统一的资源访问入口与批量处理能力。系统以轻量级爬虫与静态索引生成器为核心，适用于需要快速建立外链资源清单、进行站点内容审计或构建自定义导航页面的场景。

本项目不依赖第三方内容管理平台，所有资源链接均以原始形态存储，并支持通过扩展脚本接入自定义解析逻辑。目标用户包括运维工程师、SEO 分析师、学术文献管理者以及个人知识库维护者。

## 功能概览

- 批量链接导入与去重：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别重复条目并生成唯一索引。

- 多级分类标签生成：基于 URL 路径结构、域名特征和文章 ID 模式，自动为每条资源打上分类标签，便于后续过滤与检索。

- 资源状态健康检查：内置 HTTP 头探测与响应时间记录，可定期检测链接可用性，输出异常状态报告。

- 静态索引页面生成：根据资源列表自动生成适配桌面端与移动端的静态 HTML 索引页，无需数据库即可部署。

- 元数据抽取与补全：支持通过配置正则表达式或 XPath 规则，从目标页面抽取标题、发布时间、作者等基础元数据。

- 增量更新与版本记录：支持基于时间戳或内容哈希的增量更新策略，每次变更生成版本日志，便于追溯资源变动历史。

- 导出格式扩展：除标准 Markdown 列表外，支持导出为 JSON、YAML 或 CSV 格式，便于接入其他数据处理流水线。

## 应用场景

1. 技术文档聚合站点维护
   技术团队可将分散在各个内部或外部博客、知识库中的参考文章链接汇总至 LinkMap Aggregate，通过自动生成的索引页面为团队成员提供统一的查阅入口，减少信息检索耗时。

2. 网站内容迁移与审计
   在进行网站改版或域名迁移时，使用本系统批量导入原有站点所有的外链资源，快速生成资源清单并检查链接有效性，确保迁移后所有引用资源均可正常访问。

3. 学术文献参考整理
   研究人员可将各类在线论文、数据集、工具页面的链接导入系统，按研究方向或项目阶段进行分类，并利用元数据抽取功能记录每篇文献的标题与摘要信息，辅助文献综述撰写。

4. 个人知识库外链管理
   个人笔记或知识库维护者可将散落在各笔记文件中的外部链接统一归集至 LinkMap Aggregate，避免链接丢失或遗忘，同时通过索引页面实现快速跳转。

5. 数据标注流水线前端
   数据标注团队可使用本系统作为标注任务的数据源管理工具，将待标注页面链接统一导入并按批次分配至标注人员，配合状态检查功能监控链接稳定性。

## 快速开始

以下操作步骤适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 与 Node.js（建议 v18 及以上版本）。

```bash
# 克隆项目仓库
git clone https://github.com/linkmap/linkmap-aggregate.git
cd linkmap-aggregate

# 安装项目依赖
npm install

# 复制示例配置文件并修改
cp config.example.yaml config.yaml

# 运行资源导入与索引生成
npm run import -- --input ./data/raw_links.txt --output ./dist/index.html

# 启动本地预览服务
npm run serve
```

执行完毕后，可通过浏览器访问 `http://localhost:3000` 查看生成的索引页面。若需更新资源列表，修改 `./data/raw_links.txt` 后重新运行 `npm run import` 即可。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或更高 | 运行时环境，用于执行核心脚本与依赖管理 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖包 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与版本管理 |
| curl | 7.68 或更高 | 用于链接健康检查模块中的 HTTP 探测 |
| yaml | 2.2.x（npm 包） | 配置文件解析依赖，自动通过 npm 安装 |
| cheerio | 1.0.x（npm 包） | 用于元数据抽取中的 HTML 解析 |
| node-fetch | 3.3.x（npm 包） | 用于发送 HTTP 请求进行资源探测 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速部署并生成第一份资源索引页 |
| 配置说明 | docs/configuration.md | 如何配置数据源、分类规则、输出模板等参数 |
| 开发指南 | docs/development.md | 如何扩展自定义元数据抽取器或添加新的导出格式 |
| API 参考 | docs/api-reference.md | 核心模块的函数签名、参数说明与调用示例 |

## 资源列表

- http://map.mobile.hcbezg.cn/Article/397632.shtml
- http://map.mobile.cvsifc.cn/Article/5574172.shtml
- http://map.mobile.cvsifc.cn/Article/1862.shtml
- http://map.mobile.cvsifc.cn/Article/069021.shtml
- http://map.mobile.fuvxie.cn/Article/15587.shtml
- http://map.mobile.cvsifc.cn/Article/002716.shtml
- http://map.mobile.hcbezg.cn/Article/542631.shtml
- http://map.mobile.hcbezg.cn/Article/808134.shtml
- http://map.mobile.fuvxie.cn/Article/027831.shtml
- http://map.mobile.cvsifc.cn/Article/1277370.shtml
- http://map.mobile.fuvxie.cn/Article/6299.shtml
- http://map.mobile.cvsifc.cn/Article/617721.shtml
- http://map.mobile.hcbezg.cn/Article/6404.shtml
- http://map.mobile.cvsifc.cn/Article/52736.shtml
- http://map.mobile.hcbezg.cn/Article/7505.shtml
- http://map.mobile.fuvxie.cn/Article/7659.shtml
- http://map.mobile.fuvxie.cn/Article/6126.shtml
- http://map.mobile.cvsifc.cn/Article/6384.shtml
- http://map.mobile.cvsifc.cn/Article/8191488.shtml
- http://map.mobile.fuvxie.cn/Article/3448.shtml
- http://map.mobile.hcbezg.cn/Article/911483.shtml
- http://map.mobile.hcbezg.cn/Article/1133.shtml
- http://map.mobile.fuvxie.cn/Article/471889.shtml
- http://map.mobile.cvsifc.cn/Article/210261.shtml
- http://map.mobile.hcbezg.cn/Article/177630.shtml
- http://map.mobile.hcbezg.cn/Article/8071.shtml
- http://map.mobile.fuvxie.cn/Article/684321.shtml
- http://map.mobile.fuvxie.cn/Article/303014.shtml
- http://map.mobile.cvsifc.cn/Article/0601137.shtml
- http://map.mobile.cvsifc.cn/Article/7266588.shtml
- http://map.mobile.cvsifc.cn/Article/4656712.shtml
- http://map.mobile.fuvxie.cn/Article/8982.shtml
- http://map.mobile.fuvxie.cn/Article/643097.shtml
- http://map.mobile.cvsifc.cn/Article/0957474.shtml
- http://map.mobile.hcbezg.cn/Article/39094.shtml
- http://map.mobile.fuvxie.cn/Article/542285.shtml
- http://map.mobile.hcbezg.cn/Article/5912039.shtml
- http://map.mobile.hcbezg.cn/Article/4773.shtml
- http://map.mobile.fuvxie.cn/Article/288166.shtml
- http://map.mobile.cvsifc.cn/Article/60361.shtml
- http://map.mobile.hcbezg.cn/Article/82829.shtml
- http://map.mobile.hcbezg.cn/Article/0672.shtml
- http://map.mobile.cvsifc.cn/Article/816150.shtml
- http://map.mobile.cvsifc.cn/Article/9166.shtml
- http://map.mobile.hcbezg.cn/Article/16699.shtml
- http://map.mobile.hcbezg.cn/Article/8699.shtml
- http://map.mobile.cvsifc.cn/Article/1437595.shtml
- http://map.mobile.cvsifc.cn/Article/7782.shtml
- http://map.mobile.cvsifc.cn/Article/263152.shtml
- http://map.mobile.cvsifc.cn/Article/0667.shtml
- http://map.mobile.fuvxie.cn/Article/461516.shtml
- http://map.mobile.cvsifc.cn/Article/05937.shtml
- http://map.mobile.fuvxie.cn/Article/9908235.shtml
- http://map.mobile.hcbezg.cn/Article/53800.shtml
- http://map.mobile.hcbezg.cn/Article/91474.shtml
- http://map.mobile.cvsifc.cn/Article/83972.shtml
- http://map.mobile.cvsifc.cn/Article/8947417.shtml
- http://map.mobile.fuvxie.cn/Article/9702482.shtml
- http://map.mobile.cvsifc.cn/Article/8509.shtml
- http://map.mobile.fuvxie.cn/Article/0454.shtml
- http://map.mobile.cvsifc.cn/Article/5013.shtml
- http://map.mobile.cvsifc.cn/Article/29427.shtml
- http://map.mobile.fuvxie.cn/Article/8946.shtml
- http://map.mobile.fuvxie.cn/Article/33673.shtml
- http://map.mobile.hcbezg.cn/Article/4291232.shtml
- http://map.mobile.fuvxie.cn/Article/132265.shtml
- http://map.mobile.fuvxie.cn/Article/9621.shtml
- http://map.mobile.hcbezg.cn/Article/960785.shtml
- http://map.mobile.hcbezg.cn/Article/679924.shtml
- http://map.mobile.fuvxie.cn/Article/10408.shtml
- http://map.mobile.fuvxie.cn/Article/474654.shtml
- http://map.mobile.fuvxie.cn/Article/7837.shtml
- http://map.mobile.fuvxie.cn/Article/5235144.shtml
- http://map.mobile.hcbezg.cn/Article/84713.shtml
- http://map.mobile.hcbezg.cn/Article/176384.shtml
- http://map.mobile.hcbezg.cn/Article/14851.shtml
- http://map.mobile.hcbezg.cn/Article/9832.shtml
- http://map.mobile.cvsifc.cn/Article/3783.shtml
- http://map.mobile.hcbezg.cn/Article/9136.shtml
- http://map.mobile.fuvxie.cn/Article/105590.shtml
- http://map.mobile.cvsifc.cn/Article/861125.shtml
- http://map.mobile.cvsifc.cn/Article/6468.shtml
- http://map.mobile.fuvxie.cn/Article/9735531.shtml
- http://map.mobile.cvsifc.cn/Article/94870.shtml
- http://map.mobile.hcbezg.cn/Article/22017.shtml
- http://map.mobile.cvsifc.cn/Article/06789.shtml
- http://map.mobile.cvsifc.cn/Article/098568.shtml
- http://map.mobile.cvsifc.cn/Article/251230.shtml
- http://map.mobile.cvsifc.cn/Article/44166.shtml
- http://map.mobile.fuvxie.cn/Article/261512.shtml
- http://map.mobile.cvsifc.cn/Article/83362.shtml
- http://map.mobile.cvsifc.cn/Article/1420618.shtml
- http://map.mobile.fuvxie.cn/Article/412198.shtml
- http://map.mobile.fuvxie.cn/Article/62453.shtml
- http://map.mobile.hcbezg.cn/Article/7871354.shtml
- http://map.mobile.cvsifc.cn/Article/0361112.shtml
- http://map.mobile.cvsifc.cn/Article/0939.shtml
- http://map.mobile.hcbezg.cn/Article/2004942.shtml
- http://map.mobile.cvsifc.cn/Article/9946639.shtml
- http://map.mobile.cvsifc.cn/Article/62430.shtml
- http://map.mobile.hcbezg.cn/Article/0971093.shtml
- http://map.mobile.cvsifc.cn/Article/41776.shtml
- http://map.mobile.hcbezg.cn/Article/1235.shtml
- http://map.mobile.hcbezg.cn/Article/4509.shtml
- http://map.mobile.fuvxie.cn/Article/7287495.shtml
- http://map.mobile.cvsifc.cn/Article/6964966.shtml
- http://map.mobile.fuvxie.cn/Article/58488.shtml
- http://map.mobile.fuvxie.cn/Article/6817210.shtml
- http://map.mobile.cvsifc.cn/Article/76490.shtml
- http://map.mobile.hcbezg.cn/Article/74677.shtml
- http://map.mobile.fuvxie.cn/Article/2732.shtml
- http://map.mobile.hcbezg.cn/Article/92019.shtml
- http://map.mobile.cvsifc.cn/Article/0180.shtml
- http://map.mobile.fuvxie.cn/Article/368634.shtml
- http://map.mobile.fuvxie.cn/Article/05714.shtml
- http://map.mobile.fuvxie.cn/Article/825542.shtml
- http://map.mobile.fuvxie.cn/Article/1373.shtml
- http://map.mobile.fuvxie.cn/Article/1167.shtml
- http://map.mobile.cvsifc.cn/Article/977876.shtml
- http://map.mobile.cvsifc.cn/Article/7816.shtml
- http://map.mobile.cvsifc.cn/Article/8831633.shtml
- http://map.mobile.hcbezg.cn/Article/17925.shtml
- http://map.mobile.fuvxie.cn/Article/198762.shtml
- http://map.mobile.fuvxie.cn/Article/8744447.shtml
- http://map.mobile.hcbezg.cn/Article/997415.shtml
- http://map.mobile.cvsifc.cn/Article/943982.shtml
- http://map.mobile.fuvxie.cn/Article/21444.shtml
- http://map.mobile.hcbezg.cn/Article/728966.shtml
- http://map.mobile.cvsifc.cn/Article/6311.shtml
- http://map.mobile.cvsifc.cn/Article/38495.shtml
- http://map.mobile.cvsifc.cn/Article/5732.shtml
- http://map.mobile.fuvxie.cn/Article/7983.shtml
- http://map.mobile.hcbezg.cn/Article/82002.shtml
- http://map.mobile.cvsifc.cn/Article/25212.shtml
- http://map.mobile.hcbezg.cn/Article/25277.shtml
- http://map.mobile.fuvxie.cn/Article/623399.shtml
- http://map.mobile.cvsifc.cn/Article/272460.shtml
- http://map.mobile.cvsifc.cn/Article/7236392.shtml
- http://map.mobile.hcbezg.cn/Article/867569.shtml
- http://map.mobile.cvsifc.cn/Article/078860.shtml
- http://map.mobile.hcbezg.cn/Article/654235.shtml
- http://map.mobile.fuvxie.cn/Article/024121.shtml
- http://map.mobile.fuvxie.cn/Article/31789.shtml
- http://map.mobile.fuvxie.cn/Article/9485834.shtml
- http://map.mobile.hcbezg.cn/Article/1015181.shtml
- http://map.mobile.cvsifc.cn/Article/3721171.shtml
- http://map.mobile.hcbezg.cn/Article/9148.shtml
- http://map.mobile.hcbezg.cn/Article/82308.shtml
- http://map.mobile.cvsifc.cn/Article/6587010.shtml
- http://map.mobile.cvsifc.cn/Article/79098.shtml
- http://map.mobile.fuvxie.cn/Article/61206.shtml
- http://map.mobile.cvsifc.cn/Article/6744.shtml
- http://map.mobile.cvsifc.cn/Article/3010974.shtml
- http://map.mobile.fuvxie.cn/Article/53968.shtml
- http://map.mobile.cvsifc.cn/Article/835066.shtml
- http://map.mobile.hcbezg.cn/Article/1829707.shtml
- http://map.mobile.cvsifc.cn/Article/22937.shtml
- http://map.mobile.fuvxie.cn/Article/7331.shtml
- http://map.mobile.fuvxie.cn/Article/90704.shtml
- http://map.mobile.cvsifc.cn/Article/5607.shtml
- http://map.mobile.fuvxie.cn/Article/97835.shtml
- http://map.mobile.fuvxie.cn/Article/1033757.shtml
- http://map.mobile.cvsifc.cn/Article/4168.shtml
- http://map.mobile.hcbezg.cn/Article/9615567.shtml
- http://map.mobile.fuvxie.cn/Article/3118338.shtml
- http://map.mobile.fuvxie.cn/Article/519486.shtml
- http://map.mobile.hcbezg.cn/Article/2178939.shtml
- http://map.mobile.fuvxie.cn/Article/6304567.shtml
- http://map.mobile.cvsifc.cn/Article/3591025.shtml
- http://map.mobile.hcbezg.cn/Article/12769.shtml
- http://map.mobile.cvsifc.cn/Article/2997387.shtml
- http://map.mobile.cvsifc.cn/Article/683346.shtml
- http://map.mobile.hcbezg.cn/Article/821657.shtml
- http://map.mobile.cvsifc.cn/Article/218640.shtml
- http://map.mobile.hcbezg.cn/Article/3190.shtml
- http://map.mobile.hcbezg.cn/Article/010414.shtml
- http://map.mobile.fuvxie.cn/Article/1153028.shtml
- http://map.mobile.cvsifc.cn/Article/28480.shtml
- http://map.mobile.hcbezg.cn/Article/2296040.shtml
- http://map.mobile.cvsifc.cn/Article/6625034.shtml
- http://map.mobile.hcbezg.cn/Article/798627.shtml
- http://map.mobile.fuvxie.cn/Article/3889.shtml
- http://map.mobile.hcbezg.cn/Article/080678.shtml
- http://map.mobile.hcbezg.cn/Article/7059.shtml
- http://map.mobile.hcbezg.cn/Article/3102953.shtml
- http://map.mobile.hcbezg.cn/Article/999325.shtml
- http://map.mobile.fuvxie.cn/Article/897944.shtml
- http://map.mobile.fuvxie.cn/Article/313787.shtml
- http://map.mobile.fuvxie.cn/Article/845359.shtml
- http://map.mobile.fuvxie.cn/Article/312251.shtml
- http://map.mobile.fuvxie.cn/Article/73744.shtml
- http://map.mobile.hcbezg.cn/Article/4067.shtml
- http://map.mobile.fuvxie.cn/Article/1684.shtml
- http://map.mobile.fuvxie.cn/Article/5940.shtml
- http://map.mobile.hcbezg.cn/Article/8641.shtml
- http://map.mobile.cvsifc.cn/Article/8360429.shtml
- http://map.mobile.cvsifc.cn/Article/91700.shtml
- http://map.mobile.fuvxie.cn/Article/284542.shtml
- http://map.mobile.hcbezg.cn/Article/9718.shtml
- http://map.mobile.hcbezg.cn/Article/305306.shtml
- http://map.mobile.fuvxie.cn/Article/0225.shtml
- http://map.mobile.hcbezg.cn/Article/53012.shtml
- http://map.mobile.hcbezg.cn/Article/1463.shtml
- http://map.mobile.fuvxie.cn/Article/18186.shtml
- http://map.mobile.hcbezg.cn/Article/1671736.shtml
- http://map.mobile.fuvxie.cn/Article/07983.shtml
- http://map.mobile.hcbezg.cn/Article/5663679.shtml
- http://map.mobile.fuvxie.cn/Article/1686.shtml
- http://map.mobile.cvsifc.cn/Article/241345.shtml
- http://map.mobile.fuvxie.cn/Article/82744.shtml
- http://map.mobile.fuvxie.cn/Article/5286.shtml
- http://map.mobile.fuvxie.cn/Article/162532.shtml
- http://map.mobile.cvsifc.cn/Article/905311.shtml
- http://map.mobile.fuvxie.cn/Article/6772415.shtml
- http://map.mobile.hcbezg.cn/Article/230058.shtml
- http://map.mobile.hcbezg.cn/Article/5123741.shtml
- http://map.mobile.fuvxie.cn/Article/51452.shtml
- http://map.mobile.fuvxie.cn/Article/505019.shtml
- http://map.mobile.fuvxie.cn/Article/582291.shtml
- http://map.mobile.hcbezg.cn/Article/5189098.shtml
- http://map.mobile.hcbezg.cn/Article/60244.shtml
- http://map.mobile.cvsifc.cn/Article/011909.shtml
- http://map.mobile.fuvxie.cn/Article/9920.shtml
- http://map.mobile.hcbezg.cn/Article/78252.shtml
- http://map.mobile.cvsifc.cn/Article/02777.shtml
- http://map.mobile.cvsifc.cn/Article/7681.shtml
- http://map.mobile.cvsifc.cn/Article/494791.shtml
- http://map.mobile.cvsifc.cn/Article/1388.shtml
- http://map.mobile.fuvxie.cn/Article/704216.shtml
- http://map.mobile.fuvxie.cn/Article/049377.shtml
- http://map.mobile.fuvxie.cn/Article/5504746.shtml
- http://map.mobile.fuvxie.cn/Article/114958.shtml
- http://map.mobile.fuvxie.cn/Article/1007119.shtml
- http://map.mobile.cvsifc.cn/Article/14583.shtml
- http://map.mobile.hcbezg.cn/Article/695082.shtml
- http://map.mobile.hcbezg.cn/Article/240838.shtml
- http://map.mobile.cvsifc.cn/Article/306303.shtml
- http://map.mobile.hcbezg.cn/Article/8698.shtml
- http://map.mobile.hcbezg.cn/Article/9694.shtml
- http://map.mobile.fuvxie.cn/Article/9581365.shtml
- http://map.mobile.hcbezg.cn/Article/45001.shtml
- http://map.mobile.hcbezg.cn/Article/2479836.shtml
- http://map.mobile.cvsifc.cn/Article/3800.shtml
- http://map.mobile.hcbezg.cn/Article/1877219.shtml
- http://map.mobile.fuvxie.cn/Article/94134.shtml
- http://map.mobile.cvsifc.cn/Article/88475.shtml
- http://map.mobile.fuvxie.cn/Article/5543118.shtml
- http://map.mobile.hcbezg.cn/Article/0155.shtml
- http://map.mobile.cvsifc.cn/Article/6712.shtml
- http://map.mobile.hcbezg.cn/Article/6753720.shtml

## 项目结构

```
linkmap-aggregate/
├── src/                              # 核心源代码目录
│   ├── core/                         # 核心逻辑模块
│   │   ├── importer.js               # 链接导入与去重处理
│   │   ├── classifier.js             # 基于路径与域名的分类标签生成
│   │   └── exporter.js               # 多格式导出（HTML/JSON/CSV）
│   ├── checker/                      # 链接健康检查模块
│   │   ├── http_probe.js             # HTTP 头探测与响应记录
│   │   └── reporter.js               # 异常状态报告生成
│   ├── parser/                       # 元数据抽取模块
│   │   ├── rule_engine.js            # 正则与 XPath 规则引擎
│   │   └── extractor.js              # 标题/时间/作者抽取实现
│   ├── generator/                    # 静态页面生成模块
│   │   ├── template.js               # 索引页模板渲染
│   │   └── asset_builder.js          # CSS/JS 资源打包
│   └── cli/                          # 命令行入口
│       ├── index.js                  # CLI 主入口
│       └── commands/                 # 子命令实现（import/serve/check）
├── config/                           # 配置文件目录
│   ├── default.yaml                  # 默认配置参数
│   └── schema.json                   # 配置项 JSON Schema 校验
├── data/                             # 数据存储目录
│   ├── raw_links.txt                 # 原始链接列表（用户输入）
│   ├── indexed.json                  # 去重后索引数据
│   └── version.log                   # 增量更新版本记录
├── dist/                             # 构建输出目录
│   ├── index.html                    # 生成的静态索引页面
│   └── assets/                       # 打包后的静态资源
├── tests/                            # 单元测试与集成测试
│   ├── unit/                         # 模块级测试用例
│   └── fixtures/                     # 测试固定数据
├── docs/                             # 文档目录
│   ├── getting-started.md            # 入门指南
│   ├── configuration.md              # 配置说明
│   └── development.md                # 开发指南
├── .github/                          # GitHub 工作流配置
│   └── workflows/                    # CI/CD 流水线定义
├── package.json                      # npm 项目清单
├── package-lock.json                 # 依赖版本锁定
├── config.example.yaml               # 配置示例文件
├── .eslintrc.js                      # ESLint 代码规范配置
└── README.md                         # 项目说明文档
```

## 贡献指南

1. 查阅 issue 列表或提交新 issue 描述你希望修复的问题或新增的功能，等待维护者确认后再开始编码，避免重复劳动。

2. Fork 本仓库并在本地 clone 你的 fork 副本，创建以 `feature/` 或 `fix/` 为前缀的新分支进行开发。

3. 编写代码时遵循项目已配置的 ESLint 规则，并为新增功能补充对应的单元测试文件，确保所有现有测试用例通过。

4. 提交代码前运行 `npm run lint` 和 `npm run test` 进行本地校验，确认无错误后推送到你的远程分支。

5. 向本仓库的 `main` 分支发起 Pull Request，并在描述中清晰说明改动内容、测试结果以及相关 issue 编号。

## 常见问题

Q: 导入大量链接后，索引生成速度变慢，如何优化？

A: 建议将原始链接文件按每 5000 条拆分为多个文件，通过 `--batch` 参数分批导入。此外，可在配置文件中调整 `checker.concurrency` 参数控制健康检查的并发数，避免网络 IO 阻塞。

Q: 生成的索引页面可以在没有网络的环境下使用吗？

A: 可以。`dist/index.html` 包含所有内联样式和静态资源引用，无需加载外部 CDN 资源即可正常显示。但链接健康检查功能需要网络环境才能探测目标链接状态。

Q: 如何自定义元数据抽取规则以适配不同的目标站点？

A: 在配置文件的 `parser.rules` 节点下，可按域名或路径前缀添加多条规则，每条规则包含 `title`、`publishDate`、`author` 等字段的正则表达式或 XPath 表达式。修改后重新运行 `npm run import` 即可应用新规则。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
