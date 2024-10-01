Used optimizations technique:  
1. 4-bit Quantization : Applied 4-bit quantization to reduce the memory footprint using bnb_config
2. LoRA (Low-Rank Adaptation) for Efficient Fine-tuning: Applied LoRA (Low-Rank Adaptation) to fine-tune the model efficiently by only training a small number of parameters, which reduces the memory footprint and training complexity.
3. Memory-Efficient Attention Mechanism: Eager attention is used to optimize for fast computation and lower memory consumption during training and inference. 
4. Gradient Accumulation and Batch Size Optimization
5. FP16 Mixed Precision Training
6. Paged AdamW 8-bit Optimizer
7. Memory Management During Training: Trained the model in small batches by sequentially passing each tokenized dataset, processing batches one at a time to minimize the peak memory usage
8. Tokenization and Sequence Length Adjustments

Performance after tuning: 
GPU = Tesla T4. Max memory = 14.748 GB.
7.797 GB of memory reserved.

N.B: While going through Flash-Attention official github repository[https://github.com/Dao-AILab/flash-attention], I found that "FlashAttention-3 is optimized for Hopper GPUs (e.g. H100)." 
So I did not use it rather used Eager attention.  I also tried using FlashAttention-2. but AutoModelForCausalLM model which I am using does not support Flash Attention 2.0 yet.







