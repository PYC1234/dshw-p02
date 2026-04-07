## P01：金融数据获取、管理与初步分析

### 股票列表

| 代码 | 名称 | 行业 | 选股理由 |
|------|------|------|---------|
| 000001 | 平安银行 | 银行 | 资产规模大，流动性好，作为银行板块代表 |
| 600036 | 招商银行 | 银行 | 零售银行业龙头，资产质量优异 |
| 600519 | 贵州茅台 | 白酒 | A股白酒龙头，防御性强，业绩稳定 |
| 000858 | 五粮液 | 白酒 | 白酒行业老二，品牌影响力强 |
| 600048 | 保利发展 | 房地产 | 央企背景，财务稳健，行业龙头 |
| 000002 | 万科A | 房地产 | 房地产开发龙头，政策受益标的 |
| 601857 | 中国石油 | 能源 | 能源巨头，油气一体化，周期性明显 |
| 600900 | 长江电力 | 能源 | 水电龙头，业绩稳定，防御性特征 |
| 002594 | 比亚迪 | 汽车 | 新能源汽车龙头，技术领先 |
| 600050 | 中国联通 | 通讯 | 通讯行业代表性标的，5G受益 |

### 行业覆盖

本次选股覆盖 **6个行业**：
- 银行：2只（平安银行、招商银行）
- 白酒：2只（贵州茅台、五粮液）
- 房地产：2只（保利发展、万科A）
- 能源：2只（中国石油、长江电力）
- 汽车：1只（比亚迪）
- 通讯：1只（中国联通）

### 数据来源

- **股票行情**：baostock，`baostock.stock_zh_a_hist()`，后复权，日度
- **市场指数**：
  - 沪深300（000300）：CAPM分析的市场基准
  - 创业板指（399006）：自选指数，代表成长型股票
- **宏观指标**：
  - CPI同比增速：必选指标，来源：baostock `macro_china_cpi_yearly()`
  - M2同比增速：自选指标，反映货币政策松紧，来源：baostock `macro_china_m2()`
  - 选择理由：CPI反映通胀水平，与货币政策和股市流动性密切相关；M2增速反映货币供应，与股市资金面正相关
- **财务数据**：baostock `stock_financial_report()`，提取ROE（净资产收益率）作为公司盈利能力指标

### 存储方式

- **基础：CSV（方式 A）**：所有原始数据以CSV格式存储，便于查看和交换
- **进阶：Parquet（方式 B）**：选择理由——列式存储适合分析场景，读取特定列时更快，文件体积更小
- CSV格式优点：通用性强，无需特殊库即可打开，文本可读
- CSV格式力不从心时：数据量大时读取慢、内存占用高；不支持数据类型契约；嵌套结构支持差

### 在线电子书

**访问地址**：https://PYC1234.github.io/dshw-p01/

本项目同时以 Quarto 电子书形式发布，包含完整的章节导航、图表和代码分析。

### GitHub 仓库

https://github.com/PYC1234/dshw-p01

### 如何运行

1. 安装依赖：`pip install -r requirements.txt`
2. 运行 `01_download.ipynb` 下载原始数据（会自动创建 `data/stock/`、`data/index/`、`data/macro/`、`data/finance/` 目录）
3. 运行 `02_clean.ipynb` 清洗并存储数据（生成 `data/clean/`、`data/combined/`、`fin_data.db`）
4. 运行 `03_regression_analysis.ipynb` 查看分析结果
5. 运行 `04_capm_analysis.ipynb` 查看分析结果
6. 打开 `report.html` 阅读完整报告

### 从头重建（他人克隆后）

```bash
# 1. 克隆仓库
git clone https://github.com/PYC1234/dshw-p01.git
cd dshw-p01

# 2. 安装依赖
pip install -r requirements.txt

# 3. 依次运行 4 个 Notebook
jupyter notebook 01_download.ipynb   # 下载原始数据
jupyter notebook 02_clean.ipynb     # 清洗数据
jupyter notebook 03_regression_analysis.ipynb  # CAPM 分析
jupyter notebook 04_capm_analysis.ipynb        # CAPM + 宏观回归

# 4. 打开 report.html 查看完整报告
```

> **说明**：`data/stock/`、`data/index/`、`data/macro/`、`data/finance/` 不上传 GitHub（体积较大），通过步骤 3 重新下载生成。`*.db` 为 SQLite 中间文件，也不上传。

### .gitignore 说明

以下文件不上传 GitHub：
- `data/stock/`、`data/index/`、`data/macro/`、`data/finance/`：原始数据，通过 `01_download.ipynb` 重新下载
- `*.db`、`fin_data.db`：SQLite 数据库文件，运行 `02_clean.ipynb` 时自动生成
- `.ipynb_checkpoints/`：Jupyter Notebook 执行缓存
- `__pycache__/`、`.DS_Store`：系统/Python 临时文件

### 项目结构

```
dshw-p01/                ← GitHub 仓库根目录
├── README.md
├── report.html          ← 完整分析报告（可直接浏览器打开）
├── requirements.txt
├── .gitignore
├── _quarto.yml          ← Quarto 电子书配置
├── index.qmd            ← 电子书封面
├── 01_data_download.qmd ← 第1章：数据下载
├── 02_data_cleaning.qmd← 第2章：数据清洗
├── 03_data_storage.qmd ← 第3章：数据存储
├── 04_descriptive_analysis.qmd ← 第4章：描述性统计
├── 05_capm_regression.qmd      ← 第5章：CAPM回归
├── 06_cpi_macro_regression.qmd ← 第6章：CPI宏观回归
├── references.qmd        ← 参考文献
├── appendix_data_dict.qmd ← 附录：数据字典
├── .github/workflows/quarto-publish.yml ← GitHub Pages 自动部署
├── 01_download.ipynb    ← Step 1：下载原始数据
├── 02_clean.ipynb       ← Step 2：数据清洗
├── 03_regression_analysis.ipynb ← Step 3：描述性统计 + 可视化
├── 04_capm_analysis.ipynb       ← Step 4：CAPM 回归 + 宏观回归
├── data/
│   ├── clean/           ← 清洗后数据（CSV + Parquet）
│   └── combined/        ← 合并后综合数据
├── output/              ← 图形输出（PNG）+ 结果表格（CSV）
└── download_log.txt   ← 下载日志
```
