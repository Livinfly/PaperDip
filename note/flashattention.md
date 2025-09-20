# [FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness](https://arxiv.org/abs/2205.14135)

## 动机

attention kernel 是 memory-bound，最近的工作尝试缓解内存读取 / 降低计算，但是有降低性能 / 效果不明显等缺点。

## 贡献

提出 flash-attention，io-aware

提供了可作为通用基础算子的验证（dense / sparse)

## 方法

tiling，kernel fusion 的基础，让块从 HBM 装入 SRAM 

recompute，虽然增加了 FLOPs，但是减少存储占用。

kernel fusion，把 attention kernel 作为一个单独的 kernel，减少 kernel 启动次数，更重要的是，可以减少数据在 HBM 的搬运。

给出 block sparse flashattn 的实现。


和先前的两种也用了 tiling 的主要区别在于：

1. 优化目标不同主要关注**减少内存访问次数**而非**总占用**，虽然减少内存访问会自然减少内存占用，但内存访问次数才是决定运行时间的关键因素。
2. **增量更新输出**，不需要每个块一份。
3. **简化反向传播**，只需要重算注意力矩阵，而不是 gradient checkpointing 重算注意力矩阵 + 临时输出。

## 不足

当时还只是 CUDA 的算子，不够通用推广，multi-GPU，其他架构都还没有。

tiling 的块大小不是固定就能取到最优，不同硬件、模型也会不同，只能取到较优。
