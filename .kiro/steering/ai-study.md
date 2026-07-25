---
inclusion: always
---

# AI_Study 仓库上下文规则

本仓库是学习者的 AI 学习记录。在本仓库中回答问题、写代码、给建议时，一律遵循以下前提。

## 学习者档案（不可忽略的约束）

- 55 岁，长期做企业开发：C# ASP.NET WebForm + SQL Server，SQL 与业务理解扎实
- Python 入门水平；大学数学已基本遗忘
- 定位：**应用开发**，不做算法研究、不发论文
- 每天最多可投入 **2 小时**

## 核心目标

用机器学习对**表格化数据**做趋势预测；更重要的是**判断当下是否为趋势的转折点**
（change point detection / regime shift detection）。

## 技术栈（只用这些）

- 数据处理：Pandas + NumPy，重点 `DatetimeIndex`、`resample`、`rolling`、`shift`、`diff`、`pct_change`
- 主力模型：LightGBM（`LGBMClassifier` / `LGBMRegressor`）+ `early_stopping`
  - 参数只聚焦 `num_leaves`、`learning_rate`、`n_estimators`、`min_child_samples`
- 验证：`TimeSeriesSplit` / walk-forward；**严禁** `train_test_split(shuffle=True)`
- 转折点检测：`ruptures`、CUSUM、HMM、`scipy.signal.argrelextrema`
- 解释性：SHAP
- 调参：Optuna
- 不平衡：`scale_pos_weight` / `is_unbalance` / 调整判定阈值
- 可视化与交付：Matplotlib，可选 Streamlit
- 部署形态：Python 训练并暴露 HTTP API，由既有 C#/.NET 系统调用

## 明确不引入

深度学习框架（PyTorch / TensorFlow）、CNN / RNN / LSTM / Transformer 建模、
数学公式推导、LLM 微调、NLP / 图像 / 语音、复杂 ARIMA 统计理论。

理由：表格与中小规模时序场景下 LightGBM 通常更优，且在 2h/天预算下性价比过低。

## 数学边界

只使用：均值、标准差、百分比变化 / 差分、相关性、概率直觉。
不要引入线性代数、微积分、损失函数推导。

## 写代码时必须遵守

1. **禁止未来函数**：任何特征只能用当前时点及之前的数据；用 `.rolling()` 而非全局统计，注意 `shift(1)`
2. **禁止随机划分**：时间序列必须按时间切分
3. **必须给基线对比**：随机漫步（明天=今天）、趋势延续、移动平均交叉
4. **必须留最终测试集**：一段从未参与调参的数据，只在最后评估一次
5. **必须记录确认延迟**：信号发出时距真实转折过了几期
6. 代码需带中文注释，变量名清晰，优先可读性而非炫技

## 建模思路优先级

- A 回归：预测未来 N 期变化率（先验证流程）
- B 三分类：上升 / 下降 / 盘整（带阈值，推荐正式起点）
- C 转折点标注：`argrelextrema` 标历史拐点 → 极不平衡分类；**看精确率 / 召回率，不看准确率**

关键洞察：**转折信号藏在二阶变化里**（涨得越来越慢），斜率变化、动量衰减、
波动率突变比原始值更重要。

## 期望管理

转折点检测达到 60% 精确率、提前 2–3 期给信号即非常有价值。
号称 90% 准的基本是数据泄漏，必须主动排查。
模型定位为**报警器 / 辅助信号**，与学习者业务经验结合，而非全自动决策者。

## 文档维护约定

- 方向或计划有调整时，同步更新 `docs/AI学习路线图.md`（并递增版本号与"最近更新"日期）
- 每次实质性讨论后，在 `docs/讨论记录.md` 追加一条：日期 · 版本 · 讨论内容 · 调整内容 · 调整原因
- 进度变化时同步更新路线图第 10 节与 `README.md` 的进度表

## 语言

一律使用中文回答。
