# Python 学习详细步骤（照着做就行）

> 这是 [Python学习清单](Python学习清单.md) 的**可执行版本**。
> 清单告诉你"学什么"，本文告诉你"**今天打开电脑先干什么**"。
>
> 面向：C# ASP.NET WebForm + SQL Server 背景、Python 入门、每天 2 小时、
> 目标是做 A 股表格数据建模。

- 创建日期：2026-07-24
- 版本：v1.0

---

## 目录

- [每天怎么安排这 2 小时](#每天怎么安排这-2-小时)
- [第 0 天：装环境](#第-0-天装环境)
- [第 1 周：Python 语法（Day 1–7）](#第-1-周python-语法day-17)
- [第 2 周：Python 收尾 + 自测（Day 8–14）](#第-2-周python-收尾--自测day-814)
- [第 3–6 周：Pandas（重心）](#第-36-周pandas重心)
- [第 7–8 周：画图与工具链](#第-78-周画图与工具链)
- [第 9–12 周：A 股数据实战](#第-912-周a-股数据实战)
- [卡住了怎么办](#卡住了怎么办)
- [常见报错速查](#常见报错速查)
- [学习日志模板](#学习日志模板)

---

## 每天怎么安排这 2 小时

| 时段 | 时长 | 做什么 |
|---|---|---|
| 第一段 | **30 分钟** | 看教程 / 读文档，只看今天要用的那一点 |
| 第二段 | **80 分钟** | **敲代码**：照着敲 → 自己改 → 出错调试 |
| 第三段 | **10 分钟** | 写学习日志：今天学了什么、踩了什么坑 |

**三条规则：**

1. 🚨 **看与敲至少 1 : 2。** 判断标准：**今天敲的代码超过 50 行了吗？**
2. 🚨 **不要一天学两个主题。** 每天只推进一个小点，学完就停。
3. 🚨 **报错是正常的，不是失败。** 每个报错都是一次学习机会，别绕过它。

**关于遗忘：** 你会忘。这很正常，不是年龄问题 —— 25 岁的人也会忘。
解决办法不是"记住"，而是**写下来**（学习日志）+ **反复用到**。
所以第三段 10 分钟别省。

---

## 第 0 天：装环境

**目标：能在电脑上跑出第一行 Python。** 这一天不学语法，只搞环境。

### 步骤 1：安装 Anaconda

- 下载 **Anaconda**（个人版），一路下一步安装
- 为什么选它：Python + pandas + numpy + matplotlib + Jupyter **全都自带**，
  不用一个个装，对初学者最省事
- 安装时如果有 "Add to PATH" 选项，勾上

> 也可以用 miniconda（更小）或 uv（更现代），但第一次装 **Anaconda 最省心**。
> 别在这一步纠结，装完能跑就行。

### 步骤 2：验证安装成功

打开 **Anaconda Prompt**（Windows 开始菜单里搜），输入：

```bash
python --version
```

看到类似 `Python 3.12.x` 就成功了。

再输入：

```bash
python -c "import pandas; print(pandas.__version__)"
```

看到版本号（如 `2.2.2`）说明 pandas 也有了。

### 步骤 3：打开 Jupyter Notebook

在 Anaconda Prompt 里输入：

```bash
jupyter notebook
```

浏览器会自动打开一个页面。点 **New → Notebook → Python 3**。

在出现的格子（叫 **单元格 / cell**）里输入：

```python
print("你好，Python")
```

按 **Shift + Enter** 执行。看到输出就成功了。

> **Jupyter 是你未来主要的工作环境。**
> 它的好处是：可以一小块一小块地跑代码、随时看中间结果、随时改。
> 做数据分析比写 .py 文件方便得多。

### 步骤 4：认识三个快捷键（就这三个）

| 快捷键 | 作用 |
|---|---|
| **Shift + Enter** | 运行当前格，光标跳到下一格 |
| **Ctrl + Enter** | 运行当前格，光标留在原地 |
| **Esc 然后按 B** | 在下面插入一个新格 |

### 步骤 5（可选）：装 VS Code

如果你想用编辑器写 `.py` 文件，装 **VS Code** + 官方 **Python 扩展**。
你有 C# 背景，可能已经熟悉 VS Code 了。

> **但前 6 周建议主要用 Jupyter**，因为要不断看中间结果。

### 第 0 天完成标准

- [ ] `python --version` 有输出
- [ ] `import pandas` 不报错
- [ ] Jupyter 能打开，能跑出 `print("你好，Python")`

**做到这三条，今天就结束。不要继续。**

---

## 第 1 周：Python 语法（Day 1–7）

> 目标：能读懂、能写出简单的 Python。**不求精通，够用就走。**

### Day 1：变量、类型、print

**学（30 分钟）**：变量赋值、`int` / `float` / `str` / `bool`、`type()`、f-string

**敲（80 分钟）** —— 在 Jupyter 里一格一格敲，每格都运行看结果：

```python
# 1. 变量：不用声明类型，直接赋值（和 C# 的 var 类似，但更自由）
code = "000001"          # 字符串
price = 12.35            # 浮点数
volume = 1000000         # 整数
is_up = True             # 布尔值

print(code, price, volume, is_up)

# 2. 看类型
print(type(code), type(price), type(volume), type(is_up))

# 3. f-string 格式化（对应 C# 的 string.Format / 插值字符串）
name = "平安银行"
print(f"{name} 收盘价 {price:.2f} 元")        # .2f 保留两位小数
print(f"{name} 涨跌幅 {0.0523:.2%}")          # .2% 显示成百分比

# 4. 动态类型：变量可以换类型（C# 不行，Python 可以）
x = 10
print(type(x))
x = "现在我是字符串了"
print(type(x))
```

**自己改一改（重要）**：把 `price` 改成负数、把 `.2f` 改成 `.4f`、试试 `f"{price:,.2f}"`。

**记（10 分钟）**：今天最意外的一点是什么？

---

### Day 2：list（列表）

**学（30 分钟）**：list 的创建、索引、切片、常用方法

**敲（80 分钟）**：

```python
# list 相当于 C# 的 List<T>，但可以混装不同类型
prices = [10.5, 11.2, 10.8, 12.1, 11.9]

# 1. 索引：从 0 开始
print(prices[0])      # 第一个
print(prices[-1])     # ⭐ 最后一个（Python 特有，很好用）
print(prices[-2])     # 倒数第二个

# 2. 切片 [起始:结束]，⚠️ 不包含结束位置
print(prices[0:3])    # 前三个
print(prices[:3])     # 同上，省略 0
print(prices[2:])     # 从第三个到最后
print(prices[-3:])    # ⭐ 最后三个

# 3. 常用操作
prices.append(13.0)          # 追加
print(len(prices))           # 长度
print(max(prices), min(prices), sum(prices))
print(sum(prices) / len(prices))   # 平均值

# 4. 遍历（对应 C# 的 foreach）
for p in prices:
    print(p)

# 5. 带序号遍历
for i, p in enumerate(prices):
    print(f"第 {i} 天：{p}")
```

**⚠️ 今天最容易搞错的**：切片 `[0:3]` 是 **0、1、2**，**不含 3**。
自己多试几次，直到不会算错。

---

### Day 3：if / for / while

**学（30 分钟）**：条件判断、循环、`range`

**敲（80 分钟）**：

```python
price = 12.5
ma20 = 11.8

# 1. if（注意：用缩进代替大括号，冒号不能少）
if price > ma20:
    print("在 20 日均线上方")
elif price == ma20:
    print("正好在均线上")
else:
    print("跌破 20 日均线")

# 2. range 循环
for i in range(5):        # 0,1,2,3,4
    print(i)

for i in range(1, 6):     # 1,2,3,4,5
    print(i)

# 3. ⭐ 实战：手写计算每日涨跌幅
prices = [10.0, 10.5, 10.2, 11.0, 10.8]
returns = []
for i in range(1, len(prices)):
    r = prices[i] / prices[i-1] - 1
    returns.append(r)

print(returns)
for r in returns:
    print(f"{r:.2%}")

# 4. 统计上涨天数
up_days = 0
for r in returns:
    if r > 0:
        up_days += 1
print(f"上涨 {up_days} 天，共 {len(returns)} 天")
```

**⚠️ 缩进是语法！** 少一个空格就报错。**统一用 4 个空格**，别用 Tab。

---

### Day 4：函数

**学（30 分钟）**：`def`、参数、默认值、返回值

**敲（80 分钟）**：

```python
# 1. 最简单的函数
def say_hello(name):
    print(f"你好，{name}")

say_hello("张三")

# 2. 有返回值
def calc_return(today, yesterday):
    return today / yesterday - 1

r = calc_return(11.0, 10.0)
print(f"{r:.2%}")

# 3. 默认参数
def moving_average(prices, n=5):     # n 默认是 5
    """计算最后 n 个价格的平均值"""
    if len(prices) < n:
        return None                   # 数据不够，返回 None
    return sum(prices[-n:]) / n

prices = [10, 11, 12, 13, 14, 15, 16]
print(moving_average(prices))         # 用默认 n=5
print(moving_average(prices, 3))      # 指定 n=3
print(moving_average(prices, 20))     # 数据不够 → None

# 4. ⭐ 今天的重点练习：手写完整的移动平均序列
def ma_series(prices, n):
    """返回每一天的 n 日移动平均，数据不够的位置放 None"""
    result = []
    for i in range(len(prices)):
        if i + 1 < n:
            result.append(None)
        else:
            window = prices[i-n+1 : i+1]      # 取包含当天的 n 个
            result.append(sum(window) / n)
    return result

print(ma_series([10, 11, 12, 13, 14, 15], 3))
```

> 💡 **今天这个 `ma_series` 很重要。** 用纯 Python 写要 8 行，
> 到 Pandas 阶段一行就够（`df["close"].rolling(3).mean()`）。
> **先手写一遍，你才会真正体会到 Pandas 的价值。**

---

### Day 5：dict（字典）

**学（30 分钟）**：dict 的创建、取值、遍历

**敲（80 分钟）**：

```python
# dict 相当于 C# 的 Dictionary<K,V>
stock = {
    "code": "000001",
    "name": "平安银行",
    "close": 12.35,
    "volume": 1000000
}

# 1. 取值
print(stock["name"])
print(stock.get("pe"))               # 键不存在时返回 None，不报错
print(stock.get("pe", 0))            # 不存在时返回 0

# 2. 修改 / 新增
stock["close"] = 12.50
stock["pe"] = 5.2
print(stock)

# 3. 遍历
for key in stock:
    print(key, "=", stock[key])

for key, value in stock.items():     # ⭐ 更常用
    print(f"{key}: {value}")

# 4. ⭐ 实战：多只股票
stocks = [
    {"code": "000001", "name": "平安银行", "close": 12.35},
    {"code": "600036", "name": "招商银行", "close": 38.20},
    {"code": "601318", "name": "中国平安", "close": 45.60},
]

for s in stocks:
    print(f"{s['code']} {s['name']} {s['close']:.2f}")

# 找出收盘价最高的
highest = stocks[0]
for s in stocks:
    if s["close"] > highest["close"]:
        highest = s
print("最高：", highest["name"])
```

> 💡 **这个 `stocks` 结构（字典的列表），就是 DataFrame 的雏形。**
> 到 Pandas 阶段，`pd.DataFrame(stocks)` 一行就能变成表格。

---

### Day 6：列表推导式 + 异常处理

**学（30 分钟）**：列表推导式、`try / except`

**敲（80 分钟）**：

```python
# 1. 列表推导式：一行完成循环+筛选（Python 最常用的写法之一）
prices = [10, 11, 12, 13, 14, 15]

# 老写法
doubled = []
for p in prices:
    doubled.append(p * 2)

# 推导式写法（等价，但一行）
doubled = [p * 2 for p in prices]
print(doubled)

# 带条件筛选
big = [p for p in prices if p > 12]
print(big)

# ⭐ 实战：算涨跌幅
returns = [prices[i]/prices[i-1] - 1 for i in range(1, len(prices))]
print([f"{r:.2%}" for r in returns])

# 2. try / except：防止程序崩溃
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        print("除数不能为 0")
        return None

print(safe_divide(10, 2))
print(safe_divide(10, 0))

# 3. 实战：处理脏数据
raw = ["12.5", "13.1", "abc", "", "14.2"]
clean = []
for s in raw:
    try:
        clean.append(float(s))
    except ValueError:
        clean.append(None)          # 转不了的记为缺失
print(clean)
```

---

### Day 7：读写文件 + 本周复习

**学（30 分钟）**：`open`、`with`、CSV 的基本结构

**敲（80 分钟）**：

```python
# 1. 写一个 csv 文件
lines = [
    "date,close,volume",
    "2026-07-20,12.35,1000000",
    "2026-07-21,12.50,1200000",
    "2026-07-22,12.10,980000",
]

with open("test.csv", "w", encoding="utf-8") as f:
    for line in lines:
        f.write(line + "\n")

print("写好了")

# 2. 读回来
with open("test.csv", "r", encoding="utf-8") as f:
    content = f.read()
print(content)

# 3. 逐行解析
with open("test.csv", "r", encoding="utf-8") as f:
    header = f.readline().strip().split(",")
    print("表头：", header)
    for line in f:
        parts = line.strip().split(",")
        print(f"日期 {parts[0]}，收盘 {float(parts[1]):.2f}")
```

> ⚠️ **中文文件一定要写 `encoding="utf-8"`**，否则 Windows 上容易乱码。

**本周复习（把 Day 1–6 的代码翻一遍，挑不熟的重敲一次）**

---

## 第 2 周：Python 收尾 + 自测（Day 8–14）

### Day 8–9：模块导入 + 标准库速览

```python
# 1. 导入方式
import math
print(math.sqrt(16))

from math import sqrt, log
print(sqrt(16), log(100))

import datetime as dt              # 起别名（很常用）
print(dt.date.today())

# 2. 日期处理（后面处理交易日会用到）
d = dt.date(2026, 7, 24)
print(d, d.year, d.month, d.weekday())    # weekday: 0=周一

d2 = d + dt.timedelta(days=7)
print("7 天后：", d2)

# 3. 排序（sorted 很常用）
stocks = [
    {"code": "000001", "close": 12.35},
    {"code": "600036", "close": 38.20},
    {"code": "601318", "close": 45.60},
]
by_price = sorted(stocks, key=lambda s: s["close"], reverse=True)
for s in by_price:
    print(s["code"], s["close"])
```

> `lambda s: s["close"]` 是**匿名函数**，相当于 C# 的 `s => s.Close`。
> 只需要会用这一种形式，不用深入。

### Day 10–12：综合练习（不学新东西，只做题）

**练习 1：波动率**
```python
def volatility(prices):
    """计算日收益率的标准差"""
    returns = [prices[i]/prices[i-1] - 1 for i in range(1, len(prices))]
    mean = sum(returns) / len(returns)
    var = sum((r - mean) ** 2 for r in returns) / len(returns)
    return var ** 0.5

print(volatility([10, 10.5, 10.2, 11.0, 10.8, 11.2]))
```

**练习 2：连续上涨天数**
```python
def max_up_streak(prices):
    """返回最长连续上涨天数"""
    best = 0
    current = 0
    for i in range(1, len(prices)):
        if prices[i] > prices[i-1]:
            current += 1
            best = max(best, current)
        else:
            current = 0
    return best

print(max_up_streak([10, 11, 12, 11, 12, 13, 14, 13]))
```

**练习 3：最大回撤**（这个稍难，值得花时间）
```python
def max_drawdown(prices):
    """从历史最高点跌下来的最大幅度"""
    peak = prices[0]
    worst = 0
    for p in prices:
        if p > peak:
            peak = p
        dd = p / peak - 1        # 当前相对峰值的跌幅（负数）
        worst = min(worst, dd)
    return worst

print(f"{max_drawdown([10, 12, 11, 9, 13, 10]):.2%}")
```

### Day 13–14：自测（能独立写出来才算过关）

**不看答案，自己写：**

- [ ] **题 1**：输入价格列表，返回每日涨跌幅列表
- [ ] **题 2**：输入价格列表和窗口 n，返回 n 日移动平均列表（不够的位置放 None）
- [ ] **题 3**：读一个 csv 文件，逐行解析并打印
- [ ] **题 4**：输入价格列表，返回"上涨天数占比"
- [ ] **题 5**：输入两个等长列表，返回它们的相关系数（可以查公式）

> **五题里能独立完成 4 题 → 通过，进入 Pandas 阶段。**
> 不通过就再花 2–3 天，别硬往前赶 —— Pandas 阶段更重要，基础不牢会更痛苦。

---

## 第 3–6 周：Pandas（重心）

> ⚠️ **这 4 周是整个学习计划里最重要的部分。** 后面所有工作都建立在这上面。
> 宁可多花一周，不要赶。

### 第 3 周：Series 与 DataFrame

**Day 15–16：创建与查看**

```python
import pandas as pd

# 1. Series：带索引的一列数据
s = pd.Series([10.5, 11.2, 10.8, 12.1])
print(s)
print(s.values)      # 值
print(s.index)       # 索引

# 2. DataFrame：表格（就是内存里的一张表）
df = pd.DataFrame({
    "date":   ["2026-07-20", "2026-07-21", "2026-07-22", "2026-07-23"],
    "open":   [10.2, 10.6, 10.9, 11.5],
    "high":   [10.8, 11.0, 11.6, 11.8],
    "low":    [10.1, 10.4, 10.7, 11.2],
    "close":  [10.5, 10.9, 11.5, 11.3],
    "volume": [1000, 1200, 1500, 1100],
})
print(df)

# 3. 查看数据（每次拿到新数据，先跑这几行）
print(df.head())       # 前 5 行
print(df.tail())       # 后 5 行
print(df.shape)        # (行数, 列数)
print(df.dtypes)       # 每列的类型
print(df.info())       # 综合信息
print(df.describe())   # 统计摘要
```

**Day 17–18：选取与筛选**

```python
# 1. 取列
print(df["close"])              # 一列 → Series
print(df[["date", "close"]])    # 多列 → DataFrame（注意双层括号）

# 2. loc（按标签）vs iloc（按位置）—— ⚠️ 必须彻底搞清楚
print(df.loc[0])                # 索引标签为 0 的那行
print(df.iloc[0])               # 第 0 行（位置）
print(df.iloc[0:2])             # 前两行
print(df.loc[0, "close"])       # 第 0 行的 close
print(df.iloc[0, 4])            # 第 0 行第 4 列

# 3. 布尔筛选（相当于 SQL 的 WHERE）
print(df[df["close"] > 11])

# ⚠️ 多条件必须加括号，且用 & | 而不是 and or
print(df[(df["close"] > 10.8) & (df["volume"] > 1100)])

# 4. 新增列
df["amplitude"] = df["high"] - df["low"]          # 振幅
df["change"] = df["close"] - df["open"]           # 涨跌额
print(df)
```

**Day 19–21：缺失值 + 本周复习**

```python
import numpy as np

df2 = df.copy()
df2.loc[1, "close"] = np.nan       # 人为造一个缺失

print(df2["close"].isna())          # 哪些是缺失
print(df2["close"].isna().sum())    # 缺失几个
print(df2.dropna())                 # 删掉有缺失的行
print(df2.fillna(0))                # 填 0
print(df2["close"].ffill())         # 用前一个值填充

# ⚠️ 股票数据里，缺失值不能随便填
# 停牌日直接前向填充再算收益率，会得出"涨跌幅 0"的假数据
```

---

### 第 4–5 周：时间序列操作 ⭐⭐⭐ 命脉所在

> **80% 的精力放在这两周。** 这几个函数就是你未来所有特征工程的全部工具。

**Day 22–23：日期索引**

```python
import pandas as pd

df["date"] = pd.to_datetime(df["date"])    # 转成日期类型
df = df.set_index("date")                   # 设为索引
df = df.sort_index()                        # ⚠️ 必须排序
print(df)

# 按日期取数据
print(df.loc["2026-07-21"])
print(df.loc["2026-07-21":"2026-07-23"])
print(df.loc["2026-07"])                    # 整个 7 月
```

**Day 24–26：四大金刚 —— shift / rolling / diff / pct_change**

```python
# 造一份长一点的数据练手
import numpy as np
np.random.seed(42)
n = 200
dates = pd.bdate_range("2025-01-01", periods=n)      # 工作日
close = 10 + np.cumsum(np.random.randn(n) * 0.2)     # 模拟随机走势
d = pd.DataFrame({"close": close}, index=dates)

# ⭐ 1. shift —— 平移，防泄漏的核心武器
d["close_prev"] = d["close"].shift(1)        # 昨天的收盘价
d["close_prev5"] = d["close"].shift(5)       # 5 天前
print(d.head(8))

# ⭐ 2. pct_change —— 变化率
d["ret1"] = d["close"].pct_change(1)         # 日收益率
d["ret5"] = d["close"].pct_change(5)         # 5 日收益率

# ⭐ 3. rolling —— 滚动窗口
d["ma5"]  = d["close"].rolling(5).mean()     # 5 日均线
d["ma20"] = d["close"].rolling(20).mean()
d["std20"] = d["close"].pct_change().rolling(20).std()   # 20 日波动率
d["max20"] = d["close"].rolling(20).max()
d["min20"] = d["close"].rolling(20).min()

# ⭐ 4. diff —— 差分
d["ma5_diff"] = d["ma5"].diff(1)             # 均线的变化（斜率）

# ⭐⭐ 5. 二阶变化：本项目的核心思想
d["ret5_chg"] = d["ret5"].diff(5)            # 5日收益的变化 = 动量的变化

print(d.tail(10))
```

> 💡 **最后一行 `ret5_chg` 就是"涨得越来越慢"的数学表达。**
> 理解它，你就理解了整个项目的核心思想。

**Day 27–28：防泄漏的标准写法 + 滚动百分位**

```python
# ⭐ 防泄漏标准写法：所有特征算完后统一 shift(1)
feature_cols = ["ma5", "ma20", "std20", "ret1", "ret5", "ret5_chg"]
for col in feature_cols:
    d[col + "_lag"] = d[col].shift(1)

# ⭐ 滚动百分位（我们讨论定下来的归一化方式）
d["ma5_pct"] = d["ma5"].rolling(60).rank(pct=True)     # 在过去60天中的分位
print(d[["ma5", "ma5_pct"]].tail(10))

# ⭐ 泄漏自检：写断言
# 断言"lag 特征在第 t 行的值，等于原特征在第 t-1 行的值"
assert d["ma5_lag"].iloc[10] == d["ma5"].iloc[9], "shift 出错了！"
print("自检通过")
```

**⚠️ 本阶段必须理解的三件事：**

1. `rolling(5).mean()` 用的是**包含当天**的 5 天 → 本身不含未来，但**含今天**
2. 若决策时点在当天，**必须再 `shift(1)`**，否则用到了当天数据
3. 不要为了消掉 `NaN` 而设 `min_periods=1` —— 那会用不足的窗口算，引入偏差

---

### 第 6 周：groupby / merge（你的 SQL 优势）

**Day 29–31**

```python
# SQL 与 Pandas 对照
# GROUP BY   → groupby()
# JOIN       → merge()
# UNION ALL  → concat()
# 行转列     → pivot()

panel = pd.DataFrame({
    "date":  ["2026-07-20","2026-07-20","2026-07-21","2026-07-21"],
    "code":  ["000001","600036","000001","600036"],
    "close": [12.35, 38.20, 12.50, 38.60],
})
panel["date"] = pd.to_datetime(panel["date"])

# 1. groupby
print(panel.groupby("code")["close"].mean())
print(panel.groupby("date")["close"].agg(["mean", "max", "count"]))

# 2. ⭐ 多股票时序运算：必须先分组，绝不可跨股票串味
panel = panel.sort_values(["code", "date"])
panel["ret"] = panel.groupby("code")["close"].pct_change()
print(panel)

# 3. merge（相当于 JOIN）
info = pd.DataFrame({
    "code": ["000001", "600036"],
    "name": ["平安银行", "招商银行"],
})
merged = panel.merge(info, on="code", how="left")
print(merged)

# 4. pivot（行转列）
wide = panel.pivot(index="date", columns="code", values="close")
print(wide)
```

> 🚨 **第 2 条最重要。** 多股票数据如果不先 `groupby("code")` 就直接
> `pct_change()`，会把上一只股票的最后一天和下一只股票的第一天算成一次涨跌 ——
> 这是面板数据最常见的错误。

**Day 32–35：Pandas 五个坑 + 综合复习**

```python
# 坑 1：SettingWithCopyWarning
# ❌ df[df["close"] > 11]["close"] = 0        # 无效！
# ✅
df.loc[df["close"] > 11, "close"] = 0

# 坑 2：链式索引行为不确定 → 统一用 .loc
# 坑 3：inplace=True 已不推荐 → 统一用赋值
df = df.dropna()

# 坑 4：索引自动对齐
a = pd.Series([1, 2, 3], index=[0, 1, 2])
b = pd.Series([10, 20, 30], index=[1, 2, 3])
print(a + b)         # 会出现 NaN —— 因为索引不完全重合

# 坑 5：rolling 的 min_periods
s = pd.Series([1, 2, 3, 4, 5])
print(s.rolling(3).mean())                    # 前两个是 NaN（正确）
print(s.rolling(3, min_periods=1).mean())     # ⚠️ 前两个用不足窗口算，有偏差
```

---

## 第 7–8 周：画图与工具链

### 第 7 周：Matplotlib

**Day 36–38：基础图**

```python
import matplotlib.pyplot as plt

# 中文显示（Windows）
plt.rcParams["font.sans-serif"] = ["SimHei"]     # 或 "Microsoft YaHei"
plt.rcParams["axes.unicode_minus"] = False        # 负号正常显示

fig, ax = plt.subplots(figsize=(14, 6))
ax.plot(d.index, d["close"], label="收盘价", linewidth=1)
ax.plot(d.index, d["ma5"],  label="MA5")
ax.plot(d.index, d["ma20"], label="MA20")
ax.legend()
ax.set_title("价格与均线")
ax.grid(alpha=0.3)
plt.show()
```

**Day 39–40：多子图 + 标注**

```python
fig, axes = plt.subplots(3, 1, figsize=(14, 10), sharex=True)

axes[0].plot(d.index, d["close"]);  axes[0].set_ylabel("收盘价")
axes[1].plot(d.index, d["ret5"]);   axes[1].axhline(0, color="gray", lw=0.8)
axes[1].set_ylabel("5日收益")
axes[2].plot(d.index, d["std20"]);  axes[2].set_ylabel("20日波动率")

# ⭐ 标注特定日期（用来标转折点）
mark = d.index[100]
for ax in axes:
    ax.axvline(mark, color="red", linestyle="--", alpha=0.6)

plt.tight_layout()
plt.show()
```

> 💡 **画图是最重要的调试手段。** 把模型标出的转折点画在价格图上，
> 一眼就能看出是"真发现了规律"还是"在瞎标"。比任何指标都直观。

**Day 41–42：热力图 + 山脊图（对应我们的可视化方案）**

```python
import numpy as np

# 1. 气泡矩阵（大小=强度，颜色=方向）
n_ind, n_day = 20, 60
mat = np.random.randn(n_ind, n_day)
X, Y = np.meshgrid(range(n_day), range(n_ind))

fig, ax = plt.subplots(figsize=(14, 6))
sc = ax.scatter(X, Y, s=np.abs(mat)*40, c=mat, cmap="RdBu_r", alpha=0.8)
plt.colorbar(sc); ax.set_xlabel("交易日"); ax.set_ylabel("指标族")
ax.set_title("气泡矩阵（大小=强度，颜色=方向）")
plt.show()

# 2. 山脊图（3D 瀑布图的 2D 版本）
fig, ax = plt.subplots(figsize=(14, 8))
for i in range(n_ind):
    ax.plot(mat[i] + i * 3, color="steelblue", lw=1)     # 每条向上偏移
    ax.axhline(i * 3, color="gray", lw=0.3, alpha=0.4)
ax.set_title("山脊图（每行一个指标族）")
plt.show()
```

### 第 8 周：Git 与工作习惯

**Day 43–45：Git 基础**

```bash
git status                    # 看当前状态
git add 文件名                 # 暂存
git commit -m "说明"           # 提交
git log --oneline             # 看历史
```

> 本仓库已经建好，可以直接拿来练手。改一改 `docs/` 里的文件，
> 试着 commit 一次。改坏了也不怕 —— 这就是版本控制的意义。

**Day 46–49：把前 7 周的代码整理成可复用的函数文件**

```python
# 存成 myutils.py
import pandas as pd

def add_basic_features(df, price_col="close"):
    """给 DataFrame 加上一组基础特征（全部因果，不含未来）"""
    out = df.copy()
    p = out[price_col]

    for n in [1, 5, 10, 20]:
        out[f"ret{n}"] = p.pct_change(n)
    for n in [5, 20, 60]:
        out[f"ma{n}"] = p.rolling(n).mean()
        out[f"dev_ma{n}"] = p / out[f"ma{n}"] - 1
    out["std20"] = p.pct_change().rolling(20).std()
    out["ret5_chg"] = out["ret5"].diff(5)          # ⭐ 二阶变化

    return out
```

在 Jupyter 里用：

```python
from myutils import add_basic_features
d2 = add_basic_features(d)
print(d2.tail())
```

> **能把代码整理成函数并复用，说明你已经从"抄代码"进入"写代码"了。**

---

## 第 9–12 周：A 股数据实战

> 这一阶段开始碰真实数据，也是学习动力的来源。

### 第 9 周：取数

**Day 50–52：安装并试用 akshare**

```bash
pip install akshare --upgrade
```

```python
import akshare as ak

# 沪深300 指数历史行情（接口名可能变动，以官方文档为准）
df = ak.index_zh_a_hist(symbol="000300", period="daily",
                        start_date="20060101", end_date="20261231")
print(df.shape)
print(df.head())
print(df.tail())
```

**Day 53–56：搞清复权 + 数据核对**

任务清单：

- [ ] 查清 akshare 里哪个参数控制**复权方式**
- [ ] 明确自己用的是**后复权**（我们讨论过：前复权本身是未来函数）
- [ ] 把列名统一成英文：`date / open / high / low / close / volume`
- [ ] `date` 转 `datetime`，设为索引，排序
- [ ] **检查数据质量**：
  - 有没有重复日期？`df.index.duplicated().sum()`
  - 有没有 0 或负价格？
  - 日收益率有没有超过 ±20% 的异常值？
- [ ] **画出 20 年走势图，和行情软件对照，确认数据正确** ⭐ 这一步不能省

### 第 10 周：特征与画图

- [ ] 用 `add_basic_features()` 生成特征
- [ ] 加上滚动百分位：`x.rolling(250).rank(pct=True)`
- [ ] 画三轨道图：价格 / 5日收益 / 20日波动率
- [ ] **手动标出你自己认为的几个历史转折点，画在图上**

> 💡 最后一条极有价值：会让你亲身体会到"转折点"这个定义本身有多模糊 ——
> 而这正是整个项目最难的地方。

### 第 11 周：泄漏自检 + 归档脚本

- [ ] 所有特征统一 `shift(1)`
- [ ] 写 `assert` 断言验证 shift 正确
- [ ] **写每日自动下载并归档的脚本**（日 K 线 + 分钟线）
      —— 真实盘中快照无法事后补齐，越早开始攒越好

```python
# 归档脚本骨架
import akshare as ak, pandas as pd, datetime as dt, os

def download_and_save(symbol="000300", folder="data"):
    os.makedirs(folder, exist_ok=True)
    df = ak.index_zh_a_hist(symbol=symbol, period="daily",
                            start_date="20060101",
                            end_date=dt.date.today().strftime("%Y%m%d"))
    path = f"{folder}/{symbol}_daily.csv"
    df.to_csv(path, index=False, encoding="utf-8-sig")
    print(f"已保存 {len(df)} 行到 {path}")

download_and_save()
```

### 第 12 周：验收

- [ ] 一份干净、可复现、**经过和行情软件核对**的沪深300 日线数据
- [ ] 一套因果的、带断言自检的特征生成函数
- [ ] 一个能每天运行的归档脚本
- [ ] 能画出价格 + 均线 + 标注图

### 12 周后的验收标准

能独立完成以下事项，即可进入建模阶段：

- [ ] 看到 Pandas 报错，知道大致往哪查
- [ ] 能用一行代码算出任意窗口的滚动统计量
- [ ] 能解释 `shift(1)` 为什么是防泄漏的关键
- [ ] 能说出 `df.loc` 和 `df.iloc` 的区别
- [ ] 能画出带均线的价格图并标注特定日期
- [ ] 有一份核对过的真实数据

---

## 卡住了怎么办

### 三步自救法

1. **读报错的最后一行**。Python 的报错信息很长，但**最后一行才是原因**。
2. **把最后一行粘到搜索引擎**（去掉自己的文件路径和变量名）。
3. **`print()` 大法**：在出错的前一行加 `print(type(x), x)`，看看变量到底是什么。

### 向 Kiro 提问的正确方式

**❌ 不好的提问**："我的代码报错了怎么办"

**✅ 好的提问**：
```
我想做：给 DataFrame 加一列 5 日均线
我写的代码：
    df["ma5"] = df.rolling(5).mean()
报错信息（最后一行）：
    TypeError: ...
我预期的结果：多出一列 ma5
```

**四要素：想做什么 + 代码 + 报错最后一行 + 预期结果。**

**其他有用的提问方式：**
- "这行代码为什么这么写?逐行给我解释一下"
- "我这么理解对不对：`shift(1)` 是把整列往下移一行,所以第 t 行拿到的是第 t-1 行的值"
- "帮我检查这段代码有没有用到未来数据"

> 💡 最后一种最有价值。**养成习惯：写完特征代码，让我帮你查一遍泄漏。**

---

## 常见报错速查

| 报错 | 原因 | 怎么办 |
|---|---|---|
| `IndentationError` | 缩进不对 | 统一用 4 个空格，别混 Tab |
| `NameError: name 'x' is not defined` | 变量没定义 / 拼错 | 检查拼写；Jupyter 里可能是那一格没运行 |
| `KeyError: 'close'` | 列名不存在 | `print(df.columns)` 看真实列名 |
| `TypeError: unsupported operand type(s)` | 类型不匹配（字符串 + 数字） | `print(df.dtypes)`，用 `astype(float)` 转 |
| `ValueError: could not convert string to float` | 数据里有非数字 | 用 `pd.to_numeric(x, errors="coerce")` |
| `SettingWithCopyWarning` | 链式赋值 | 改用 `df.loc[条件, "列"] = 值` |
| `ModuleNotFoundError` | 包没装 | `pip install 包名` |
| 中文显示成方块 | 字体没设 | 设 `plt.rcParams["font.sans-serif"] = ["SimHei"]` |
| CSV 打开乱码 | 编码问题 | 存的时候用 `encoding="utf-8-sig"` |

---

## 学习日志模板

每天最后 10 分钟填一次。建议存成 `docs/学习日志.md`，或者纸笔记也行。

```markdown
## 2026-XX-XX（第 N 天）

**今天学了**：（一句话）

**敲了多少行代码**：约 XX 行

**卡住的地方**：
-

**踩的坑 / 学到的教训**：
-

**明天要做**：
```

> 💡 **一个月后回看这个日志，你会明显看到自己的进步。**
> 而且卡过的坑写下来，第二次遇到能立刻想起来 —— 这比"记住"有效得多。

---

## 三条贯穿全程的原则

1. **看与敲至少 1 : 2** —— 判断标准：今天敲的代码超过 50 行了吗？
2. **每天只推进一个小点** —— 学完就停，不要贪。宁可 14 周走完，不要 8 周半途而废。
3. **报错是进度，不是失败** —— 一个报错解决了，就是一个知识点掌握了。

---

## 附：C# → Python 速查

| C# | Python | 备注 |
|---|---|---|
| `{ }` 代码块 | **缩进** | 🚨 缩进即语法，统一 4 空格 |
| 语句末 `;` | 不需要 | |
| `//` 注释 | `#` | |
| `List<T>` | `list` | 可混装不同类型 |
| `Dictionary<K,V>` | `dict` | |
| `var` / 强类型 | 动态类型 | 变量可随时换类型 |
| `null` | `None` | |
| `for(int i=0;i<n;i++)` | `for i in range(n)` | |
| `foreach (var x in c)` | `for x in c` | |
| `string.Format` / 插值 | f-string | `f"{name} 收盘 {price:.2f}"` |
| `s => s.Close` | `lambda s: s["close"]` | 匿名函数 |
| `x.ToString()` | `str(x)` | |
| `int.Parse(s)` | `int(s)` | |
| `arr.Length` | `len(arr)` | |
| `try/catch` | `try/except` | |
| `&&` `||` | `and` `or`（Pandas 里用 `&` `|`） | ⚠️ Pandas 筛选必须加括号 |
