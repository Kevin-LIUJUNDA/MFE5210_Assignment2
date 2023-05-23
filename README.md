# MFE5210_Assignment2
input 的时间跨度为 30 天，每天的 features 为 ['close','open','high','low','amount','volume'] 共 6 个，因此每个 input 为 30×6 的二维向量。

output 为未来 5 日收益 future_return_5（future_return_5>0.2, 取 0.2;future_return_5<-0.2, 取 - 0.2)，为使训练效果更加明显，output=future_return_5×10； features 均经过标准化处理 (在每个样本内每个 feature 标准化处理一次)。

训练数据：沪深 300 2005-01-01 至 2014-12-31 时间段的数据；测试数据：沪深 300 2015-01-01 至 2017-05-01 时间段数据。

模型构建：鉴于数据较少（训练数据约 2500 个，预测数据约 500 个），因此模型构建的相对简单。模型共四层，为一层 LSTM 层 + 三层 Dense 层（图 3）。

回测：得到 LSTM 预测结果后，若 LSTM 预测值小于 0，则记为 - 1，若大于 0，记为 1。
