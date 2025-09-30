# Paper Dip

总之是一个记录性质的仓库。

可能的来源：

- [The Hall of Fame Award – ACM SIGOPS](https://www.sigops.org/awards/hof/)
- [ADSL Reading Group](https://adsl-rg.github.io/)

## MLSys

### Kernel

- [ ] [Attention Survey](https://attention-survey.github.io/files/Attention_Survey.pdf)
  [note](./note/attention_survey.md)
- [X] [[2205.14135] FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness](https://arxiv.org/abs/2205.14135)
  Flash Attention, [note](flashattention.md)
- [ ] [[2307.08691] FlashAttention-2: Faster Attention with Better Parallelism and Work Partitioning](https://arxiv.org/abs/2307.08691)
  Flash Attention 2
- [ ] [[2407.08608] FlashAttention-3: Fast and Accurate Attention with Asynchrony and Low-precision](https://arxiv.org/abs/2407.08608)
  Flash Attention 3

### Prefill & Decoding

- [X] [[2308.16369] SARATHI: Efficient LLM Inference by Piggybacking Decodes with Chunked Prefills](https://arxiv.org/abs/2308.16369)

  Chunked Prefills, piggyback, [note](note/STRATHI_chunked_prefill.md)

### Spec Decode

- [X] [[2401.10774] Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads](https://arxiv.org/abs/2401.10774)

  medusa, multiple decoding head, tree-attention, [note](note/Medusa.md)
- [ ] [[2305.10427] Accelerating Transformer Inference for Translation via Parallel Decoding](https://arxiv.org/abs/2305.10427)

  Jacobi Decoding, Parallel Decoding，对不使用 draft model 的尝试，变成使用自回归的过程变成迭代求解非线性方程组。
- [ ] [[2402.02057] Break the Sequential Dependency of LLM Inference Using Lookahead Decoding](https://arxiv.org/abs/2402.02057)

  Lookahead Decoding，将自回归解码视为求解非线性系统，通过固定点迭代（fixed-point iteration），生成轨迹 Jacobi trajectory 可以再利用，之前的推测放入 n-gram pool 中作为候选，重新利用。
- [ ] [[2401.15077] EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty](https://arxiv.org/abs/2401.15077)
- [ ] [[2406.16858] EAGLE-2: Faster Inference of Language Models with Dynamic Draft Trees](https://arxiv.org/abs/2406.16858)
- [ ] [[2503.01840] EAGLE-3: Scaling up Inference Acceleration of Large Language Models via Training-Time Test](https://arxiv.org/abs/2503.01840)

### Serving system

## Other
