# 环境监测数据分析系统
[![Git](https://img.shields.io/badge/Git-2.43.0+-blue.svg)](https://git-scm.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-green.svg)](https://www.python.org/)
[![Dependencies](https://img.shields.io/badge/Dependencies-Pandas%20%7C%20NumPy%20%7C%20Matplotlib-orange.svg)](./requirements.txt)

## 项目简介
本项目是一套基于 Python 开发的环境监测数据分析系统，针对温度、湿度、PM2.5 等环境传感器数据，实现**数据加载预处理、多维度统计分析、可视化报告生成**三大核心功能。
项目适配 Git 团队协作流程，可作为小型数据分析项目的实战案例，涵盖版本控制、模块开发、冲突解决等全流程。

## 环境准备
### 1. 基础依赖安装
#### 步骤1：克隆仓库（本地/远程）
```bash
# 克隆远程仓库（替换为你的 GitHub 仓库地址）
git clone https://github.com/AlexFu0520/env_monitor_system.git
cd env_monitor_system

# 若为本地初始化仓库，直接进入项目目录
# cd env_monitor_system
步骤 2：安装 Python 依赖
bash
运行
# 升级 pip（可选，避免依赖安装失败）
pip install --upgrade pip

# 安装项目依赖
pip install -r requirements.txt
步骤 3：Git 环境配置（首次使用）
bash
运行
# 配置用户名和邮箱（与 GitHub 账号一致）
git config --global user.name "AlexFu0520"
git config --global user.email "你的GitHub注册邮箱@xxx.com"
2. 环境要求
操作系统：Windows/macOS/Linux
Python 版本：3.8 及以上
Git 版本：2.0 及以上
核心依赖：
pandas==2.0.0（数据处理）
numpy==1.24.0（数值计算）
matplotlib==3.7.0（可视化）
seaborn==0.12.0（热图绘制）
快速开始
1. 生成模拟传感器数据
bash
运行
# 运行数据生成脚本，生成 data/sensor_data.csv
python data/generate_data.py
生成的数据包含 30 天的环境监测记录，涵盖「站点 A / 站点 B」两个监测点的温度、湿度、PM2.5 指标。
2. 运行主程序
bash
运行
# 执行核心分析流程
python src/main.py
运行后会自动完成：
数据加载与验证
基础统计 / 站点对比 / 空气质量评估
生成可视化图表（保存至 docs/ 目录）
3. 查看输出结果
控制台输出：数据分析的文本结果（统计值、空气质量比例等）
可视化文件：
docs/timeseries.png：时间序列趋势图（温度 / 湿度 / PM2.5 变化）
docs/distribution.png：数据分布图（指标分布 + 站点对比）
docs/correlation.png：相关性热图（环境指标关联分析）
项目结构
plaintext
env_monitor_system/
├── README.md              # 项目说明文档
├── requirements.txt       # Python 依赖列表
├── data/                  # 数据目录
│   ├── generate_data.py   # 模拟数据生成脚本
│   └── sensor_data.csv    # 传感器数据文件（生成后出现）
├── src/                   # 核心源代码
│   ├── data_loader.py     # 数据加载模块（读取/验证/预处理）
│   ├── data_analysis.py   # 数据分析模块（统计/评估/趋势分析）
│   ├── visualization.py   # 可视化模块（图表生成/保存）
│   └── main.py            # 主程序（整合所有模块）
└── docs/                  # 文档/可视化输出目录
    ├── report.md          # 项目分析报告
    └── *.png              # 可视化图表（运行后生成）
核心功能
模块	功能说明
数据加载模块	读取 CSV 数据、日期格式转换、数据完整性验证、输出数据摘要
数据分析模块	基础统计（均值 / 中位数 / 标准差）、站点对比、空气质量分级、温度极值分析
可视化模块	时间序列趋势图、指标分布直方图、站点对比柱状图、相关性热图
团队协作流程
1. 分支管理规范
bash
运行
# 创建功能分支（示例：开发可视化模块）
git checkout -b feature-visualization

# 提交分支代码
git add src/visualization.py
git commit -m "可视化模块：新增相关性热图功能"
git push origin feature-visualization

# 合并分支（主分支）
git checkout main
git pull origin main
git merge feature-visualization
git push origin main
2. 冲突解决
若多人修改同一文件导致合并冲突：
执行 git merge <分支名> 触发冲突提示
打开冲突文件，删除 <<<<<<< HEAD/=======/>>>>>>> 分支名 标记，保留正确代码
重新提交：git add . && git commit -m "解决合并冲突"
常见问题
1. Git 推送认证失败
问题：Password authentication is not supported
解决：改用 GitHub 个人访问令牌（PAT）或 SSH 协议，参考 GitHub 认证指南
2. 中文显示乱码（可视化图表）
解决：修改 src/visualization.py 中的字体配置：
python
运行
# Windows
plt.rcParams['font.sans-serif'] = ['SimHei']
# macOS
# plt.rcParams['font.sans-serif'] = ['PingFang SC']
# Linux
# plt.rcParams['font.sans-serif'] = ['DejaVu Sans']
plt.rcParams['axes.unicode_minus'] = False
3. 数据文件找不到
确认运行目录为项目根目录（env_monitor_system/）
先执行 python data/generate_data.py 生成 sensor_data.csv
许可证
本项目为学习用实战案例，无商业用途，可自由修改和分发。
维护者
用户名：AlexFu0520
邮箱：你的邮箱地址（可选）