# 移动游戏用户增长与行为洞察分析（Gamelytics）

> 基于 100 万注册玩家、960 万登录记录与 40.5 万 A/B 测试用户，构建覆盖「用户增长 → 留存 → 商业化 → 玩家画像 → 流失预测 → 实时运营监控」的全链路移动游戏运营数据分析项目。

## 项目简介

本项目以一款真实移动游戏的运营数据为蓝本，系统回答三个业务问题：**留存**（每日留存率与群组留存曲线、早期流失定位）、**商业化**（两套促销方案 A/B 测试的优劣量化）、**画像与运营**（玩家行为原型、流失风险与前置干预）。

本目录包含同一题目的两个版本实现：

| 子项目 | 定位 | 内容 |
|--------|------|------|
| `Gamelytics_old/` | 旧版探索性分析 | 4 个独立 Notebook，从不同角度切入（留存/A/B、综合分析、流失回归、挑战题解答） |
| `Gamelytics_new/` | 重构后的全链路分析 | 单一 Notebook 打通完整分析链路，含标准化的数据目录与可视化图表 |

## 目录结构

```
01/
├── Gamelytics_old/                              # 旧版：多 Notebook 探索性分析
│   ├── an-example-of-analyzing-project-data.ipynb
│   ├── faith-hsia-gamelytics-mobile-challenge.ipynb
│   ├── gamelytics-comprehensive-analysis.ipynb
│   ├── what-brings-players-back.ipynb
│   ├── reg_data.csv / auth_data.csv / ab_test.csv
│   └── README.md
└── Gamelytics_new/                              # 新版：全链路标准化分析
    ├── 移动游戏用户增长与行为洞察分析.ipynb
    ├── 可视化分析报告.md
    ├── data/          # ab_test.csv / auth_data.csv / reg_data.csv
    ├── figures/       # 20 张分析图表（*.png）
    └── README.md
```

## 数据集说明

数据时间跨度 1998—2020 年，无缺失值，数据质量良好。

| 数据集 | 记录数 | 字段 | 说明 |
|--------|--------|------|------|
| `reg_data.csv` | 1,000,000 | `reg_ts`（Unix 时间戳）、`uid` | 玩家注册时间 |
| `auth_data.csv` | 9,601,013 | `auth_ts`（Unix 时间戳）、`uid` | 玩家登录/认证时间 |
| `ab_test.csv` | 404,770 | `user_id`、`revenue`、`testgroup`（a/b） | A/B 促销实验结果 |

## 环境依赖

- Python 3.x
- 核心库：`pandas`、`numpy`、`matplotlib`、`seaborn`、`scipy`
- 机器学习：`scikit-learn`、`xgboost`
- 标准库：`os`、`sys`、`datetime`、`typing`、`warnings`

## 运行方式

1. 安装依赖：`pip install pandas numpy matplotlib seaborn scipy scikit-learn xgboost`
2. 使用 Jupyter Notebook 打开对应 `.ipynb` 文件，按顺序执行单元格。
3. 新版脚本会自动将图表输出到 `figures/` 目录；数据文件需与 Notebook 位于同一目录（新版位于 `data/` 子目录）。

## 结果结论

- **留存**：首月留存率 15.4%~18.9%，注册后前 5 天为关键干预窗口；79.4% 的玩家在注册后 7 天内流失。
- **商业化**：测试组促销方案 ARPPU 显著提升 **12.75%**（CR 仅微降 0.06pp），建议采纳。
- **画像**：消费-留存呈倒 U 型，低消费层玩家最活跃、高消费鲸鱼登录次数最低，支撑「普惠转化 + 差异化运营」策略。
- **预测与运营**：随机森林/XGBoost 可有效识别早期流失玩家，配合动态风险评分实现流失预警闭环。
