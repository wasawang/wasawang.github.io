虽然大语言模型从chatGPT时刻开始流行， 相关的技术其实有经过长期的积累， 在这个过程， google公司贡献巨大， 有不少关键节点上都有创造性的贡献。

总体来说， 发展过程可以分为以下几个步骤：

1. 早期的基于词汇统计的模型， 包括早期的N-gram 模型。 这个时期的模型主要通过统计词汇的出现在一起的数据在预测下面的词汇。 这种模型相对比较简单，但是功能有限， 没有什么创造性， 甚至很难保证文法的正确性。

2. 神经网络时期： 词汇的向量化在这个阶段开始出现，相对的词汇之间的关系能够转换成数学的计算。 embedding模型在今天也很重要， 并且是今天大模型的基础。RNN作为一种seq2seq的模型开始应用与翻译等应用， 但是对于长序列的效果不佳， 主要是因为前面的向量对后面的影响会逐层降低， LSTM 和attention机制开始被用来解决这个问题， 有明显的效果但是相对效果还达不到目标， 并且计算效率也是一个大问题。

3. Transformer时期： google的研究者发现 仅仅只用attention就对seq2seq的问题有非常好的效果， 这个对RNN来讲模型简单很多， 也共容易进行并发计算的优化。 基于此， 各种不同的基于transformer模型都有被研究， google的Bert是这个时期的王者， 这是一个encoder only的模型， 对文字的理解非常好。 训练方法相当于做完型填空。

4. LLM 时期： openAI的研究者创建的decoder only的模型真正体现了大力出奇迹。 随者训练数据/模型参数的增加，  模型的能力大幅提升， 并且不限于语言的理解能力。

LLM相关的技术

1. Scaling Law

Scaling law在这个阶段被提出： 更多的数据， 更多的参数， 以及更多的算力能够做出更好的模型。 每个不同的公司都有基于自己模型的scaling law, 也是他们用来预估下一个迭代模型参数的起点。 目前来说比较困难的是能用的文本文本数据已经基本都用了， 在不增加数据的情况下增加参数只会有overfitting的风险， 现在的方向是找到更有效的模型或者使用其他形态的输入。

2. Data Engineering

对于数据的处理也是模型训练中很重要的一步， 这包括怎样得到更多更全面的数据，数据清洗（ 更干净的数据对减少模型的偏差很有用）， 以及怎样有效率的将数据提供给模型训练。

3. Pre-training step

预训练主要基于没有标签的数据进行训练， 主要的难点是如何高效的进行计算。

4. Post-training step

该步骤主要是指令微调， 让模型不止能干预测下个字， 而且可以和人类进行有效的交流。 强化学习也可以用来增强思维能力。

5. Alignment

该步骤主要是为了确保模型与人类的偏好一致， 比如少输出政治不正确的内容等等， 基于用户反馈强化学习是常用的一个思路，但是太贵了。 基于同样数据的微调(DPO)能够达到类似的效果

6. Tooling & Agent

利用Agent来更好的使用模型， 提供更多的实施反馈， 并且像模型基于反馈生成更好的内容。 在大模型里面的Agent和RL里面很不一样， 因为大模型的输入是更灵活的文本， 所以与RL提供奖励函数不同， 这里的Agent可以直接将输出的详细信息提供给模型。
