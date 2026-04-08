## P01：金融数据获取、管理与初步分析

### 在线电子书

**访问地址**：https://PYC1234.github.io/dshw-p02/

本项目以 Quarto 电子书形式发布，包含完整的章节导航、图表和代码分析。

同时包含完整版report.html 和 简要版report_summary.html。

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

- **股票行情**：baostock，后复权，日度
- **市场指数**：沪深300（CAPM基准）、创业板指
- **宏观指标**：CPI同比增速、M2同比增速
- **财务数据**：ROE（净资产收益率）

### 电子书章节

| 章节 | 文件 | 内容 |
|------|------|------|
| 封面 | `index.qmd` | 封面与项目介绍 |
| 第1章 | `01_download.ipynb` | 数据下载 |
| 第2章 | `02_clean.ipynb` | 数据清洗 |
| 第3章 | `03_regression_analysis.ipynb` | 描述性统计与可视化 |
| 第4章 | `04_capm_analysis.ipynb` | CAPM回归与CPI宏观回归 |

### 如何运行

1. 安装依赖：`pip install -r requirements.txt`
2. 运行 `01_download.ipynb` 下载原始数据
3. 运行 `02_clean.ipynb` 清洗并存储数据
4. 运行 `03_regression_analysis.ipynb` 查看分析结果
5. 运行 `04_capm_analysis.ipynb` 查看CAPM回归结果

### 从头重建

```bash
git clone https://github.com/PYC1234/dshw-p02.git
cd dshw-p02
pip install -r requirements.txt
jupyter notebook 01_download.ipynb
jupyter notebook 02_clean.ipynb
jupyter notebook 03_regression_analysis.ipynb
jupyter notebook 04_capm_analysis.ipynb
```

> **说明**：`data/stock/`、`data/index/`、`data/macro/`、`data/finance/` 不上传 GitHub，通过 `01_download.ipynb` 重新下载。

### .gitignore 说明

以下文件不上传 GitHub：
- `data/stock/`、`data/index/`、`data/macro/`、`data/finance/`：原始数据
- `*.db`、`fin_data.db`：SQLite 数据库文件
- `.ipynb_checkpoints/`：Jupyter 执行缓存
- `_book/`：Quarto 渲染输出（由 GitHub Actions 自动生成）
- `.jupyter_cache/`：Jupyter 缓存

### GitHub 仓库

https://github.com/PYC1234/dshw-p02
