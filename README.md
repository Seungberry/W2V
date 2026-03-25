# Word2Vec


[](https://www.python.org/downloads/)
[](https://pytorch.org/)

## 项目简介

本项目是基于 PyTorch 实现的经典自然语言处理模型 **Word2Vec**。Word2Vec 是一种用于生成词向量（Word Embeddings）的高效预测模型，能够将复杂的文本信息映射到低维连续向量空间中，从而捕获词汇之间的语义和语法关系。

本项目重点实现了以下核心架构：

  * **Skip-gram 模型**：通过中心词预测周围的上下文词。
  * **负采样 (Negative Sampling)**：为了提高训练效率，引入负采样机制，将多分类问题转化为二分类问题，极大降低了计算开销。

该项目旨在提供一个简洁、易读的代码实现，方便研究人员和开发者理解词向量的底层训练逻辑，并支持在自定义数据集上进行快速训练。

## 核心特性

  * **高效的数据预处理**：包含文本清洗、分词、构建词汇表以及子采样（Subsampling）高频词。
  * **灵活的模型配置**：支持自定义词向量维度、窗口大小（Window Size）和负采样样本数。
  * **可视化支持**：内置 TSNE 降维工具，可将高维词向量可视化，直观观察词汇间的语义聚类效果。
  * **参数调优**：支持调整词频过滤阈值和学习率等核心超参数。

## 安装指南

1.  **克隆仓库**：

    ```bash
    git clone https://github.com/Seungberry/W2V.git
    cd W2V
    ```

2.  **环境配置**：
    建议使用 Conda 或虚拟环境：

    ```bash
    pip install -r requirements.txt
    ```

    主要依赖：PyTorch, NumPy, Scikit-learn, Matplotlib*

## 使用说明

### 1\. 训练模型

运行主训练脚本，你可以通过命令行参数指定数据集路径：

```bash
python train.py --data ./data/corpus.txt --epochs 10 --batch_size 512
```

### 2\. 模型推理

使用训练好的权重查找相似词：

```python
from model import Word2VecExecutor

model = Word2VecExecutor(model_path='checkpoint.pth')
print(model.get_similar_words("king", top_k=5))
```
