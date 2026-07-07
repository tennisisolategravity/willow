# WebIndex Mobile Resource Aggregator

WebIndex Mobile Resource Aggregator 是一个面向移动端技术内容聚合与分发的基础设施项目，旨在解决移动端 Web 页面、WAP 站点及轻应用场景下技术文档、教程、案例和参考资料分散难以检索的问题。本项目不提供内容创作，而是作为结构化外链索引引擎，对特定领域的技术文章进行规范化收录、分类和版本标注，便于开发者、技术作者和内容运营人员快速定位高质量信息来源。

项目面向三类目标用户：其一是移动端开发工程师，需要查阅具体技术实现细节；其二是技术博客作者，需要引用外部资料作为参考文献；其三是企业内容运营团队，需要批量采集和审核外部技术内容以支撑内部知识库建设。本项目以纯静态 Markdown 文档形式发布，所有收录链接均保持原始出处，不做任何二次跳转或代理转发，确保来源可追溯。

## 功能概览

**按域名自动归类**：系统根据来源域名对收录链接执行自动分组，当前支持 cvsifc.cn、hcbezg.cn、fuvxie.cn 三个主域，便于按站点维度检索内容。

**按文章 ID 排序与过滤**：每条链接均提取文章数字 ID 作为唯一主键，支持基于 ID 范围的批量导出和去重过滤。

**移动端 URL 格式标准化**：所有收录链接均保留 wap.mobile 子域名结构，确保移动端设备直接访问时获得最优渲染视图。

**批量链接健康检查**：提供内置链接可达性检测脚本，可对全部收录链接执行 HTTP 状态码验证，自动标记失效链接。

**Markdown 原生呈现**：整个资源列表以纯 Markdown 格式输出，无 JavaScript 依赖，无需数据库，可直接托管于任何静态 Web 服务器或代码托管平台。

**外链引用追踪**：每条链接均保留完整的 Article 路径和 .shtml 后缀，支持第三方统计工具进行引用来源分析。

**批次管理**：当前版本为第 46/60 批收录批次，总计收录 250 个资源链接，支持按批次号进行增量更新和历史回溯。

**多维度筛选导出**：支持按域名、ID 范围、批次号等维度对链接列表进行筛选和导出，便于下游系统集成。

## 应用场景

移动端技术资料库构建：技术团队可将本项目作为数据源，通过脚本定期拉取链接列表，结合爬虫工具对文章标题、摘要、发布时间进行二次抽取，构建内部技术资料检索系统。

外链引用合规审查：内容审核人员使用本项目的结构化链接列表，逐条核对来源域名的备案信息、内容安全性和版权声明，确保企业对外发布的内容符合引用规范。

技术文章参考文献补全：技术博主在撰写移动端开发教程时，可通过本项目的域名分组快速查找相关领域的参考文章，补充文章末尾的参考资料章节。

批量链接迁移与备份：运维人员利用本项目的纯文本链接列表，配合 wget 或 curl 批量工具，对指定批次的所有文章执行静态化备份，防止源站内容下线造成信息丢失。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex-mobile/resource-aggregator.git

# 进入项目目录
cd resource-aggregator

# 安装依赖（Python 3.8+ 环境）
pip install -r requirements.txt

# 执行链接健康检查（可选）
python scripts/check_links.py --batch 46

# 生成当前批次 Markdown 文档
python scripts/generate_readme.py --batch 46 --output README.md
```

## 安装要求

| 依赖 | 必需 | 说明 |
|------|------|------|
| Python 3.8 及以上 | 是 | 运行链接检查、批量导出和 Markdown 生成脚本的运行时环境 |
| pip 21.0 及以上 | 是 | 安装 requests、beautifulsoup4 等依赖包所需的包管理工具 |
| Git 2.25 及以上 | 是 | 克隆仓库、提交更新和管理版本历史 |
| requests 库 2.25 及以上 | 是 | 执行 HTTP 链接状态检测和响应头分析 |
| beautifulsoup4 4.9 及以上 | 否 | 解析文章 HTML 标题和元数据（仅用于增强功能） |
| curl 7.68 及以上 | 否 | 批量下载文章静态备份的备选工具链 |
| make 3.81 及以上 | 否 | 执行 Makefile 中定义的批量任务（如全量检测） |
| Docker 20.10 及以上 | 否 | 容器化部署和隔离运行环境（仅用于生产发布） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何使用本项目的链接列表进行检索、筛选和导出？ |
| 运维手册 | docs/operations.md | 如何执行链接健康检查、更新批次和清理失效链接？ |
| 开发指南 | docs/development.md | 如何扩展新的来源域名、修改分类规则和提交补丁？ |
| 批次规范 | docs/batch-spec.md | 每个批次的收录标准、数量上限和 ID 分配规则是什么？ |
| 对外接口 | docs/api-export.md | 如何通过脚本或命令行工具批量获取结构化链接数据？ |

## 资源列表

- http://wap.mobile.cvsifc.cn/Article/8336.shtml
- http://wap.mobile.cvsifc.cn/Article/74109.shtml
- http://wap.mobile.hcbezg.cn/Article/6053.shtml
- http://wap.mobile.hcbezg.cn/Article/5602.shtml
- http://wap.mobile.hcbezg.cn/Article/0937.shtml
- http://wap.mobile.cvsifc.cn/Article/3025723.shtml
- http://wap.mobile.fuvxie.cn/Article/4582812.shtml
- http://wap.mobile.cvsifc.cn/Article/067789.shtml
- http://wap.mobile.hcbezg.cn/Article/1589979.shtml
- http://wap.mobile.hcbezg.cn/Article/7160908.shtml
- http://wap.mobile.fuvxie.cn/Article/6903.shtml
- http://wap.mobile.hcbezg.cn/Article/9927.shtml
- http://wap.mobile.fuvxie.cn/Article/1016359.shtml
- http://wap.mobile.hcbezg.cn/Article/06335.shtml
- http://wap.mobile.hcbezg.cn/Article/7426.shtml
- http://wap.mobile.fuvxie.cn/Article/9386692.shtml
- http://wap.mobile.hcbezg.cn/Article/429501.shtml
- http://wap.mobile.hcbezg.cn/Article/1247085.shtml
- http://wap.mobile.hcbezg.cn/Article/491066.shtml
- http://wap.mobile.cvsifc.cn/Article/564986.shtml
- http://wap.mobile.fuvxie.cn/Article/2711.shtml
- http://wap.mobile.hcbezg.cn/Article/595155.shtml
- http://wap.mobile.cvsifc.cn/Article/55215.shtml
- http://wap.mobile.hcbezg.cn/Article/9831211.shtml
- http://wap.mobile.cvsifc.cn/Article/4117.shtml
- http://wap.mobile.hcbezg.cn/Article/703554.shtml
- http://wap.mobile.hcbezg.cn/Article/0980792.shtml
- http://wap.mobile.fuvxie.cn/Article/0367.shtml
- http://wap.mobile.fuvxie.cn/Article/77795.shtml
- http://wap.mobile.cvsifc.cn/Article/2326.shtml
- http://wap.mobile.cvsifc.cn/Article/2236849.shtml
- http://wap.mobile.fuvxie.cn/Article/44080.shtml
- http://wap.mobile.hcbezg.cn/Article/5547.shtml
- http://wap.mobile.hcbezg.cn/Article/579248.shtml
- http://wap.mobile.hcbezg.cn/Article/6328.shtml
- http://wap.mobile.cvsifc.cn/Article/383660.shtml
- http://wap.mobile.cvsifc.cn/Article/4059.shtml
- http://wap.mobile.hcbezg.cn/Article/2436.shtml
- http://wap.mobile.fuvxie.cn/Article/09754.shtml
- http://wap.mobile.hcbezg.cn/Article/7541528.shtml
- http://wap.mobile.fuvxie.cn/Article/9130041.shtml
- http://wap.mobile.hcbezg.cn/Article/4106.shtml
- http://wap.mobile.fuvxie.cn/Article/4949299.shtml
- http://wap.mobile.fuvxie.cn/Article/963899.shtml
- http://wap.mobile.cvsifc.cn/Article/262392.shtml
- http://wap.mobile.cvsifc.cn/Article/9226172.shtml
- http://wap.mobile.hcbezg.cn/Article/6443.shtml
- http://wap.mobile.cvsifc.cn/Article/8370.shtml
- http://wap.mobile.hcbezg.cn/Article/0069.shtml
- http://wap.mobile.fuvxie.cn/Article/01809.shtml
- http://wap.mobile.fuvxie.cn/Article/024786.shtml
- http://wap.mobile.hcbezg.cn/Article/74541.shtml
- http://wap.mobile.cvsifc.cn/Article/813010.shtml
- http://wap.mobile.fuvxie.cn/Article/3172.shtml
- http://wap.mobile.hcbezg.cn/Article/11771.shtml
- http://wap.mobile.fuvxie.cn/Article/2046046.shtml
- http://wap.mobile.fuvxie.cn/Article/722656.shtml
- http://wap.mobile.hcbezg.cn/Article/2785.shtml
- http://wap.mobile.hcbezg.cn/Article/143625.shtml
- http://wap.mobile.fuvxie.cn/Article/473204.shtml
- http://wap.mobile.fuvxie.cn/Article/57692.shtml
- http://wap.mobile.fuvxie.cn/Article/038743.shtml
- http://wap.mobile.cvsifc.cn/Article/19150.shtml
- http://wap.mobile.cvsifc.cn/Article/1606997.shtml
- http://wap.mobile.hcbezg.cn/Article/1112.shtml
- http://wap.mobile.hcbezg.cn/Article/9527766.shtml
- http://wap.mobile.fuvxie.cn/Article/72600.shtml
- http://wap.mobile.fuvxie.cn/Article/6335.shtml
- http://wap.mobile.hcbezg.cn/Article/30529.shtml
- http://wap.mobile.fuvxie.cn/Article/7409968.shtml
- http://wap.mobile.hcbezg.cn/Article/41391.shtml
- http://wap.mobile.hcbezg.cn/Article/8241.shtml
- http://wap.mobile.hcbezg.cn/Article/9705.shtml
- http://wap.mobile.cvsifc.cn/Article/7403.shtml
- http://wap.mobile.hcbezg.cn/Article/8151.shtml
- http://wap.mobile.cvsifc.cn/Article/786136.shtml
- http://wap.mobile.fuvxie.cn/Article/0485.shtml
- http://wap.mobile.fuvxie.cn/Article/700970.shtml
- http://wap.mobile.hcbezg.cn/Article/194676.shtml
- http://wap.mobile.hcbezg.cn/Article/7337.shtml
- http://wap.mobile.fuvxie.cn/Article/6689.shtml
- http://wap.mobile.fuvxie.cn/Article/288852.shtml
- http://wap.mobile.cvsifc.cn/Article/9375134.shtml
- http://wap.mobile.cvsifc.cn/Article/1025182.shtml
- http://wap.mobile.fuvxie.cn/Article/9470334.shtml
- http://wap.mobile.hcbezg.cn/Article/28088.shtml
- http://wap.mobile.hcbezg.cn/Article/8280.shtml
- http://wap.mobile.hcbezg.cn/Article/474337.shtml
- http://wap.mobile.fuvxie.cn/Article/5489.shtml
- http://wap.mobile.cvsifc.cn/Article/00985.shtml
- http://wap.mobile.hcbezg.cn/Article/4576.shtml
- http://wap.mobile.fuvxie.cn/Article/6490325.shtml
- http://wap.mobile.hcbezg.cn/Article/6724.shtml
- http://wap.mobile.fuvxie.cn/Article/4626134.shtml
- http://wap.mobile.hcbezg.cn/Article/9452.shtml
- http://wap.mobile.fuvxie.cn/Article/5403890.shtml
- http://wap.mobile.cvsifc.cn/Article/468952.shtml
- http://wap.mobile.fuvxie.cn/Article/6583.shtml
- http://wap.mobile.hcbezg.cn/Article/29817.shtml
- http://wap.mobile.cvsifc.cn/Article/5525755.shtml
- http://wap.mobile.cvsifc.cn/Article/4404605.shtml
- http://wap.mobile.fuvxie.cn/Article/2598.shtml
- http://wap.mobile.hcbezg.cn/Article/9097795.shtml
- http://wap.mobile.cvsifc.cn/Article/6067.shtml
- http://wap.mobile.fuvxie.cn/Article/3690042.shtml
- http://wap.mobile.fuvxie.cn/Article/33953.shtml
- http://wap.mobile.cvsifc.cn/Article/1892.shtml
- http://wap.mobile.cvsifc.cn/Article/537349.shtml
- http://wap.mobile.fuvxie.cn/Article/40821.shtml
- http://wap.mobile.fuvxie.cn/Article/88575.shtml
- http://wap.mobile.cvsifc.cn/Article/207569.shtml
- http://wap.mobile.hcbezg.cn/Article/1331056.shtml
- http://wap.mobile.fuvxie.cn/Article/5618.shtml
- http://wap.mobile.cvsifc.cn/Article/0838933.shtml
- http://wap.mobile.cvsifc.cn/Article/6293939.shtml
- http://wap.mobile.cvsifc.cn/Article/7639.shtml
- http://wap.mobile.hcbezg.cn/Article/06179.shtml
- http://wap.mobile.cvsifc.cn/Article/4673.shtml
- http://wap.mobile.fuvxie.cn/Article/918698.shtml
- http://wap.mobile.hcbezg.cn/Article/5339.shtml
- http://wap.mobile.hcbezg.cn/Article/52262.shtml
- http://wap.mobile.hcbezg.cn/Article/7041.shtml
- http://wap.mobile.cvsifc.cn/Article/22713.shtml
- http://wap.mobile.fuvxie.cn/Article/701214.shtml
- http://wap.mobile.cvsifc.cn/Article/6566045.shtml
- http://wap.mobile.hcbezg.cn/Article/71555.shtml
- http://wap.mobile.fuvxie.cn/Article/579070.shtml
- http://wap.mobile.cvsifc.cn/Article/5478.shtml
- http://wap.mobile.fuvxie.cn/Article/96358.shtml
- http://wap.mobile.fuvxie.cn/Article/06934.shtml
- http://wap.mobile.hcbezg.cn/Article/785976.shtml
- http://wap.mobile.cvsifc.cn/Article/210274.shtml
- http://wap.mobile.hcbezg.cn/Article/9820544.shtml
- http://wap.mobile.hcbezg.cn/Article/620298.shtml
- http://wap.mobile.fuvxie.cn/Article/051020.shtml
- http://wap.mobile.hcbezg.cn/Article/958768.shtml
- http://wap.mobile.cvsifc.cn/Article/8387669.shtml
- http://wap.mobile.fuvxie.cn/Article/4917.shtml
- http://wap.mobile.cvsifc.cn/Article/943752.shtml
- http://wap.mobile.hcbezg.cn/Article/46415.shtml
- http://wap.mobile.hcbezg.cn/Article/0146718.shtml
- http://wap.mobile.fuvxie.cn/Article/85554.shtml
- http://wap.mobile.fuvxie.cn/Article/9541025.shtml
- http://wap.mobile.fuvxie.cn/Article/817549.shtml
- http://wap.mobile.cvsifc.cn/Article/97395.shtml
- http://wap.mobile.fuvxie.cn/Article/039460.shtml
- http://wap.mobile.cvsifc.cn/Article/268382.shtml
- http://wap.mobile.hcbezg.cn/Article/7772185.shtml
- http://wap.mobile.fuvxie.cn/Article/187477.shtml
- http://wap.mobile.cvsifc.cn/Article/37800.shtml
- http://wap.mobile.hcbezg.cn/Article/5400.shtml
- http://wap.mobile.hcbezg.cn/Article/0839.shtml
- http://wap.mobile.cvsifc.cn/Article/8134281.shtml
- http://wap.mobile.fuvxie.cn/Article/914632.shtml
- http://wap.mobile.cvsifc.cn/Article/264648.shtml
- http://wap.mobile.hcbezg.cn/Article/16485.shtml
- http://wap.mobile.cvsifc.cn/Article/95067.shtml
- http://wap.mobile.hcbezg.cn/Article/05760.shtml
- http://wap.mobile.cvsifc.cn/Article/765978.shtml
- http://wap.mobile.hcbezg.cn/Article/3011.shtml
- http://wap.mobile.fuvxie.cn/Article/02315.shtml
- http://wap.mobile.fuvxie.cn/Article/3324564.shtml
- http://wap.mobile.cvsifc.cn/Article/0617090.shtml
- http://wap.mobile.cvsifc.cn/Article/1454.shtml
- http://wap.mobile.hcbezg.cn/Article/310956.shtml
- http://wap.mobile.cvsifc.cn/Article/1414.shtml
- http://wap.mobile.fuvxie.cn/Article/886001.shtml
- http://wap.mobile.cvsifc.cn/Article/8272.shtml
- http://wap.mobile.fuvxie.cn/Article/74867.shtml
- http://wap.mobile.hcbezg.cn/Article/0020.shtml
- http://wap.mobile.cvsifc.cn/Article/70725.shtml
- http://wap.mobile.fuvxie.cn/Article/351182.shtml
- http://wap.mobile.fuvxie.cn/Article/6104134.shtml
- http://wap.mobile.cvsifc.cn/Article/6343.shtml
- http://wap.mobile.hcbezg.cn/Article/5286266.shtml
- http://wap.mobile.hcbezg.cn/Article/85693.shtml
- http://wap.mobile.hcbezg.cn/Article/1721661.shtml
- http://wap.mobile.fuvxie.cn/Article/16491.shtml
- http://wap.mobile.cvsifc.cn/Article/922512.shtml
- http://wap.mobile.cvsifc.cn/Article/687852.shtml
- http://wap.mobile.fuvxie.cn/Article/193348.shtml
- http://wap.mobile.cvsifc.cn/Article/06725.shtml
- http://wap.mobile.fuvxie.cn/Article/428039.shtml
- http://wap.mobile.hcbezg.cn/Article/572195.shtml
- http://wap.mobile.fuvxie.cn/Article/36181.shtml
- http://wap.mobile.hcbezg.cn/Article/2069.shtml
- http://wap.mobile.cvsifc.cn/Article/568485.shtml
- http://wap.mobile.fuvxie.cn/Article/033867.shtml
- http://wap.mobile.fuvxie.cn/Article/2650.shtml
- http://wap.mobile.fuvxie.cn/Article/39832.shtml
- http://wap.mobile.fuvxie.cn/Article/879563.shtml
- http://wap.mobile.hcbezg.cn/Article/6586.shtml
- http://wap.mobile.cvsifc.cn/Article/5864.shtml
- http://wap.mobile.cvsifc.cn/Article/9421711.shtml
- http://wap.mobile.cvsifc.cn/Article/3732.shtml
- http://wap.mobile.cvsifc.cn/Article/232303.shtml
- http://wap.mobile.hcbezg.cn/Article/4681499.shtml
- http://wap.mobile.hcbezg.cn/Article/7261885.shtml
- http://wap.mobile.hcbezg.cn/Article/57574.shtml
- http://wap.mobile.hcbezg.cn/Article/33941.shtml
- http://wap.mobile.hcbezg.cn/Article/972263.shtml
- http://wap.mobile.cvsifc.cn/Article/416177.shtml
- http://wap.mobile.fuvxie.cn/Article/3820136.shtml
- http://wap.mobile.hcbezg.cn/Article/7310.shtml
- http://wap.mobile.hcbezg.cn/Article/1715.shtml
- http://wap.mobile.fuvxie.cn/Article/42679.shtml
- http://wap.mobile.cvsifc.cn/Article/2131567.shtml
- http://wap.mobile.cvsifc.cn/Article/47677.shtml
- http://wap.mobile.fuvxie.cn/Article/8025.shtml
- http://wap.mobile.cvsifc.cn/Article/722886.shtml
- http://wap.mobile.fuvxie.cn/Article/091946.shtml
- http://wap.mobile.fuvxie.cn/Article/31511.shtml
- http://wap.mobile.hcbezg.cn/Article/6645070.shtml
- http://wap.mobile.cvsifc.cn/Article/09107.shtml
- http://wap.mobile.fuvxie.cn/Article/1919.shtml
- http://wap.mobile.fuvxie.cn/Article/184606.shtml
- http://wap.mobile.fuvxie.cn/Article/1573694.shtml
- http://wap.mobile.hcbezg.cn/Article/7539775.shtml
- http://wap.mobile.cvsifc.cn/Article/9958849.shtml
- http://wap.mobile.hcbezg.cn/Article/5253.shtml
- http://wap.mobile.fuvxie.cn/Article/4895.shtml
- http://wap.mobile.cvsifc.cn/Article/3909.shtml
- http://wap.mobile.cvsifc.cn/Article/06582.shtml
- http://wap.mobile.hcbezg.cn/Article/6989.shtml
- http://wap.mobile.cvsifc.cn/Article/833229.shtml
- http://wap.mobile.cvsifc.cn/Article/848865.shtml
- http://wap.mobile.fuvxie.cn/Article/3973.shtml
- http://wap.mobile.hcbezg.cn/Article/43981.shtml
- http://wap.mobile.hcbezg.cn/Article/0458174.shtml
- http://wap.mobile.cvsifc.cn/Article/058359.shtml
- http://wap.mobile.fuvxie.cn/Article/59897.shtml
- http://wap.mobile.cvsifc.cn/Article/9420.shtml
- http://wap.mobile.hcbezg.cn/Article/2314493.shtml
- http://wap.mobile.fuvxie.cn/Article/38368.shtml
- http://wap.mobile.hcbezg.cn/Article/9626947.shtml
- http://wap.mobile.fuvxie.cn/Article/1520138.shtml
- http://wap.mobile.fuvxie.cn/Article/040127.shtml
- http://wap.mobile.hcbezg.cn/Article/132085.shtml
- http://wap.mobile.cvsifc.cn/Article/741243.shtml
- http://wap.mobile.hcbezg.cn/Article/776526.shtml
- http://wap.mobile.hcbezg.cn/Article/2020.shtml
- http://wap.mobile.fuvxie.cn/Article/8279031.shtml
- http://wap.mobile.fuvxie.cn/Article/8568169.shtml
- http://wap.mobile.cvsifc.cn/Article/66182.shtml
- http://wap.mobile.hcbezg.cn/Article/1314930.shtml
- http://wap.mobile.cvsifc.cn/Article/667330.shtml
- http://wap.mobile.cvsifc.cn/Article/790560.shtml
- http://wap.mobile.fuvxie.cn/Article/661558.shtml
- http://wap.mobile.fuvxie.cn/Article/6328765.shtml
- http://wap.mobile.fuvxie.cn/Article/6964577.shtml

## 项目结构

```
webindex-mobile-aggregator/
├── README.md                         # 项目主文档，包含批次说明和资源列表
├── LICENSE                           # MIT 许可证文件
├── requirements.txt                  # Python 依赖清单
├── Makefile                          # 批量任务自动化入口
├── config/
│   ├── domains.yaml                  # 来源域名配置及分类映射规则
│   └── batch.toml                    # 当前批次号、收录数量和 ID 范围配置
├── scripts/
│   ├── check_links.py                # 批量链接健康状态检测脚本
│   ├── generate_readme.py            # 从数据源生成 README.md 的渲染脚本
│   ├── export_csv.py                 # 将链接列表导出为 CSV 格式
│   └── deduplicate.py                # 基于文章 ID 的去重过滤脚本
├── data/
│   ├── batch_46.json                 # 第 46 批次原始链接数据（JSON 格式）
│   ├── batch_46.csv                  # 第 46 批次链接数据（CSV 格式，便于 Excel 查看）
│   └── archives/                     # 历史批次数据归档目录
├── docs/
│   ├── user-guide.md                 # 用户使用手册
│   ├── operations.md                 # 运维操作手册
│   ├── development.md                # 开发贡献指南
│   └── batch-spec.md                 # 批次规范文档
├── tests/
│   ├── test_checker.py               # 链接检测模块的单元测试
│   └── test_export.py                # 导出模块的单元测试
└── .github/
    └── workflows/
        └── ci.yml                    # GitHub Actions 持续集成配置文件
```

## 贡献指南

第一，克隆项目仓库并在本地环境中安装所有开发依赖，确保 Python 3.8 及以上版本可用。执行 `make install` 可一键完成依赖安装和环境检查。

第二，新增或修改链接数据时，请遵循 `data/batch_*.json` 的 JSON 格式规范，每条链接必须包含 `url`、`domain` 和 `article_id` 三个字段。提交前运行 `python scripts/deduplicate.py --batch 46` 进行去重校验。

第三，如需调整域名分类规则或批次参数，请编辑 `config/domains.yaml` 或 `config/batch.toml` 文件，并在提交信息中详细说明变更原因和影响范围。

第四，所有代码和文档变更须通过单元测试和链接健康检查。执行 `make test` 运行全部测试用例，执行 `make check` 对当前批次执行链接可达性检测。测试未通过时不得提交合并请求。

第五，提交合并请求时，请附上清晰的变更描述，包括本次变更解决的问题、影响的批次范围以及测试结果截图或日志。项目维护者将在 5 个工作日内完成审核。

## 常见问题

问：部分收录链接返回 404 或 502 状态码，应该如何处理？

答：链接失效属于正常现象，源站可能对旧文章进行了迁移或删除。项目维护者每季度执行一次全量链接健康检查，对连续两次检测均失效的链接，将在下一批次中标记为 `[DEPRECATED]` 并移出活跃列表，但保留在历史归档中供追溯。

问：如何查找特定主题或关键词的相关文章？

答：本项目作为外链索引，仅提供 URL 列表而不存储文章全文。建议将本项目的链接列表导出为 CSV 后，结合第三方爬虫工具（如 Scrapy 或 Puppeteer）批量抓取文章的标题和正文，再在本地进行关键词检索。项目文档 `docs/user-guide.md` 中提供了参考实现脚本。

问：是否可以申请将新的来源域名加入收录范围？

答：可以。请在 GitHub Issues 中提交新增域名申请，需提供该域名的备案信息、内容主题说明和至少 10 个示例文章链接。项目维护者将根据内容质量、域名信誉和与现有批次的主题契合度进行综合评估，评估通过后会在后续批次中纳入。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
