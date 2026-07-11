# 裸模型 Raw Model

**Token List** → **Raw Model** → 下一个Token的**概率分布**

[ 1, 3, … ,2 ]

⇒

{

15: 0.06,

293: 0.1,

}

- Token List 是自然语言换算成数字的结果（分词）
- Context Window 上下文窗口: Token List 的长度

Raw Model 是一个权重矩阵：数字

训练、微调 目的就是为了得到权重矩阵（输入语料）

但是只有权重矩阵无法运行，本质只有了一些数字，想跑起来还得要

[**模型 = 架构代码 + 权重参数 + tokenizer + 推理运行时**](%E8%A3%B8%E6%A8%A1%E5%9E%8B%20Raw%20Model/%E6%A8%A1%E5%9E%8B%20=%20%E6%9E%B6%E6%9E%84%E4%BB%A3%E7%A0%81%20+%20%E6%9D%83%E9%87%8D%E5%8F%82%E6%95%B0%20+%20tokenizer%20+%20%E6%8E%A8%E7%90%86%E8%BF%90%E8%A1%8C%E6%97%B6%203550f8d8d1fd80e4a2a4f0e55cc7ae5d.md)

需要像 transformer架构、tensor架构 等神经网络、深度学习

模型就像一个函数，运算量很大用 GPU 并行计算

计算机是用浮点数的，不满足结合律

0.1+0.2+0.3 ≠ 0.1+(0.2+0.3)

**多模态**：模型不知道自然语言、图片… 只认识数字

本质没有区别

[AI核心](%E8%A3%B8%E6%A8%A1%E5%9E%8B%20Raw%20Model/AI%E6%A0%B8%E5%BF%83%2035c0f8d8d1fd80eba70df6a703e5b9ee.md)

[LoRA、蒸馏、微调、SFT](%E8%A3%B8%E6%A8%A1%E5%9E%8B%20Raw%20Model/LoRA%E3%80%81%E8%92%B8%E9%A6%8F%E3%80%81%E5%BE%AE%E8%B0%83%E3%80%81SFT%2035c0f8d8d1fd80ecbf88f998bff862ba.md)

[HuggingFace, Colab](%E8%A3%B8%E6%A8%A1%E5%9E%8B%20Raw%20Model/HuggingFace,%20Colab%2035c0f8d8d1fd80dc8cc7f6149729f96a.md)