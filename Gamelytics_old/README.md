# 移动游戏用户增长与行为洞察分析（Gamelytics_old）

> 旧版探索性分析：4 个独立 Notebook 从留存/A/B、综合分析、流失回归、挑战题解答等不同角度切入同一份 Gamelytics 移动游戏运营数据。

## 项目简介

本子项目是 Gamelytics 题目的**旧版**实现，由 4 个相互独立的 Notebook 组成，分别从不同视角对同一数据集进行分析，是后续重构版（`Gamelytics_new/`）的前置探索。数据与新版一致：100 万注册玩家、960 万登录记录、40.5 万 A/B 测试用户。

| Notebook | 主题 |
|----------|------|
| `an-example-of-analyzing-project-data.ipynb` | 留存率分析、A/B 测试与主题活动评估的示例项目 |
| `faith-hsia-gamelytics-mobile-challenge.ipynb` | Gamelytics 挑战题解答（留存 + A/B 测试） |
| `gamelytics-comprehensive-analysis.ipynb` | 留存率、A/B 测试、玩家行为与机器学习综合分析 |
| `what-brings-players-back.ipynb` | 玩家流失后回归模式的行为分析 |

## 目录结构

```
Gamelytics_old/
├── an-example-of-analyzing-project-data.ipynb
├── faith-hsia-gamelytics-mobile-challenge.ipynb
├── gamelytics-comprehensive-analysis.ipynb
├── what-brings-players-back.ipynb
├── reg_data.csv
├── auth_data.csv
└── ab_test.csv
```

## 数据集说明

数据文件位于本目录根路径（与新版 `data/` 内容一致）：

| 数据集 | 记录数 | 字段 | 说明 |
|--------|--------|------|------|
| `reg_data.csv` | 1,000,000 | `reg_ts`、`uid` | 玩家注册时间 |
| `auth_data.csv` | 9,601,013 | `auth_ts`、`uid` | 玩家登录/认证时间 |
| `ab_test.csv` | 404,770 | `user_id`、`revenue`、`testgroup` | A/B 促销实验 |

## 环境依赖

- Python 3.x
- 核心库：`pandas`、`numpy`、`matplotlib`、`seaborn`、`scipy`
- 机器学习：`scikit-learn`（`gamelytics-comprehensive-analysis.ipynb` 使用）
- 标准库：`os`、`datetime`、`typing`、`warnings`

## 运行方式

1. 安装依赖：`pip install pandas numpy matplotlib seaborn scipy scikit-learn`
2. 使用 Jupyter Notebook 分别打开各 `.ipynb` 文件，按顺序执行单元格。
3. 数据文件（`.csv`）需与 Notebook 位于同一目录（已满足）。

## 结果结论

- **留存**：注册后早期流失严重，首日流失为最大瓶颈，留存曲线呈「小而忠诚」的核心用户群特征。
- **A/B 测试**：测试组促销方案在单付费用户价值（ARPPU）上显著更优，综合效应量评分判定测试组胜出。
- **玩家回归**：玩家参与行为相对结构化而非随机，中等参与度玩家表现出最强的长期留存，行为稳定性是重要的留存信号。
- **机器学习**：流失预测模型（LR/RF/XGBoost）能有效区分早期流失玩家，`lifecycle_days` 与 `total_logins` 为最重要特征。

## 项目章节

### an-example-of-analyzing-project-data.ipynb

1. 项目介绍与目标
2. 阶段 1：数据加载与预处理
3. 阶段 2：通用数据分析（缺失天数、UID 探索）
4. 阶段 3：任务解决——任务 1（新玩家注册趋势 / 留存率）、任务 2（A/B 测试）

### faith-hsia-gamelytics-mobile-challenge.ipynb

以代码为主的挑战题解答，围绕留存率分析与 A/B 测试两大任务展开（40 个代码单元）。

### gamelytics-comprehensive-analysis.ipynb

1. Phase 0 环境配置 → Phase 1 数据加载与预处理
2. Phase 2 EDA → Phase 3 留存率分析（Task 1）
3. Phase 4 A/B 测试（Task 2）→ Phase 5 主题活动评估（Task 3）
4. Phase 6 玩家行为深度分析 → Phase 7 机器学习（流失预测 + 行为聚类）
5. Phase 8 时间序列与收入整合 → Phase 9 实时监控仪表板 → Phase 10 综合结论

### what-brings-players-back.ipynb

1. 引言与业务问题 → 数据准备 → 初步行为探索
2. 识别不活跃与回归行为 → 玩家参与度一致性 → 玩家分层
3. 参与度稳定性 → 生命周期分析 → 早期流失风险分析
4. 最终结论、局限性与未来工作（含 5 个未来项目方向）
