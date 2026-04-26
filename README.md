# 房贷违约预测与信用风险建模

本项目基于美国抵押贷款资产池数据，构建违约预测模型，并比较不同机器学习与深度学习方法在信用风险识别中的表现。

## 项目背景

目标是预测贷款是否违约，并在类别极度不平衡（违约率约 4.7%）的情况下，评估模型在风险识别与误判控制之间的权衡能力。

数据采用：

- 训练集：2000 年贷款
- 测试集：2001 年贷款（out-of-sample）
- 样本量：约 100 万条

## 数据处理

主要处理步骤包括：

- 缺失值处理（如 LAST_VAL）
- 类别变量 One-Hot 编码
- 偏态变量 log 变换
- 数值特征标准化
- 按年份划分训练集与测试集
- 不平衡问题处理

核心特征包括：

- 贷款金额、期限
- 借款人数量
- 收入与负债比（DTI）
- 房产类型
- FICO 分数
- LTV 比率等

## 模型方法

实现了多种机器学习与深度学习模型：

- Random Forest（RF）
- Support Vector Machine（SVM）
- Gradient Boosting（GBM）
- XGBoost
- Multilayer Perceptron（MLP）
- RNN
- LSTM
- GRU

并通过：

- Grid Search / Random Search
- K 折交叉验证

进行超参数调优。

## 评估指标

模型评估采用：

- Accuracy
- Precision
- Recall
- Specificity
- F1 Score

重点关注：

> Recall（违约识别能力） vs Precision（误判成本）

## 核心结果

LSTM 模型在测试集上表现最佳：

- Accuracy ≈ 98.42%
- Precision ≈ 76.94%
- Recall ≈ 70.38%
- Specificity ≈ 99.32%
- F1 ≈ 0.735

RF 和 SVM 在低阈值下可实现 Recall ≈ 95%+，但 Precision 较低（约 10%–20%），体现风险覆盖与误判成本之间的权衡。

## 关键结论

- 类别不平衡是核心挑战
- 单一 Accuracy 指标不适用于信用风险问题
- 阈值调整可以灵活适配不同风控策略
- 高 Recall 模型适用于贷前筛查
- 高 Precision 模型适用于审批决策

## 文件说明

- RF.py：随机森林模型
- SVM.py：支持向量机模型
- GBM.py：梯度提升模型
- xbm_mln_rnn.ipynb：XGBoost、MLP、RNN
- lstm_gru.ipynb：LSTM、GRU
- subset_train_40000.csv：调参子集
- 项目PPT.pdf：展示文件

## 说明

原始数据量较大未上传，仓库提供子集用于复现与演示。
