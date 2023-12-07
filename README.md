# Fine-Tuning-BERT-for-text-classification-with-LoRA

* Fine-tuning is a widely employed technique that enables the customization of pre-trained language models for particular tasks.

* In recent times, various research papers have presented different techniques to fine-tune LLMs in a shorter amount of time and with reduced computational demands. One of the most prominent techniques that has yielded state-of-the-art results is **Low Rank Adaptation (LORA)**. This research was conducted by Meta’s AI team. 

* In this tutorial, I will demonstrate how to fine-tune BERT using the **LORA** approach.

### How LoRa works ?

LORA emerged as a solution when we realized that fine-tuning a large language model (LLM) from scratch requires significantly more parameters than when fine-tuning from a pre-trained model. LORA has demonstrated that, to fine-tune a pre-trained model, there’s no need to modify every single weight in each layer. Instead, it introduces a method to learn a lower-dimensional, task-specific representation of the layer’s weights.

* Let’s break down LORA step by step. Consider a fully connected layer with $‘m’$ input units and $’n’$ output units. The weight matrix for this layer has dimensions $‘m x n’$. When we provide an input $‘X’$, the output of this layer is calculated using the formula $Y = W X$.

* During fine-tuning with LORA, we keep $‘W’$ fixed and introduce two matrices, $‘A’$ and $‘B’$, into the equation. The new equation becomes $Y = W X + A*B X$. Now, imagine if ‘m’ is 800 and ’n’ is 3200, making the shape of ‘W’ 800 x 3200, resulting in 2,560,000 weights.

* Here’s where LORA’s innovation comes into play. Matrix A has a shape of $800 x r$, and matrix B has a shape of $r x 3200$. The key is that you can adjust the value of $r$. If we set r to 1, the number of weights in this layer becomes:

$(800 x 1) + (1 x 3200) = 4000.$

* 
LoRa makes fine-tuning large language models quicker and less demanding on computing resources. It uses far fewer adjustments - significantly less than the 2,560,000 weights typically needed in full fine-tuning.

Reference:

	1. original paper: LoRA: Low-Rank Adaptation of Large Language Models (https://arxiv.org/abs/2106.09685)

	2. https://medium.com/@karkar.nizar/fine-tuning-bert-for-text-classification-with-lora-f12af7fa95e4

