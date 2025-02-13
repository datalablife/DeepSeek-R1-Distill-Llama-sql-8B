---



base_model: unsloth/deepseek-r1-distill-llama-8b-unsloth-bnb-4bit
tags:
- text-generation-inference
- transformers
- unsloth
- llama
- trl
license: apache-2.0
language:
- en
---

# DataSet 

[b-mc2/sql-create-context](https://huggingface.co/datasets/b-mc2/sql-create-context)

# Model  train

![](https://github.com/datalablife/DeepSeek-R1-Distill-Llama-sql-8B/blob/main/images/train.png?raw=true)

1. **train/loss**: This chart shows the model's loss during training. As the training steps (global step) increase, the loss value drops sharply and then stabilizes, indicating that the model is gradually converging.
2. **train/learning_rate**: This chart shows how the learning rate changes over training steps. From the chart, we can see that the learning rate decreases as training progresses, which is likely part of a learning rate decay strategy to prevent the model from oscillating in the later stages of training.
3. **train/grad_norm**: This chart displays the change in gradient norm over training steps. The decrease in gradient norm suggests that the gradients are stabilizing, reducing instability during training.
4. **train/global_step**: This chart shows the increase in global training steps. As the training progresses, the step count gradually increases, indicating the progress of the training process.
5. **train/epoch**: This chart represents the progress of each training epoch. As the global steps increase, the epoch count also steadily grows.


## Usage

If you are unsure how to use GGUF files, refer to one of [TheBloke's READMEs](https://huggingface.co/TheBloke/KafkaLM-70B-German-V0.1-GGUF) for more details, including on how to concatenate multi-part files.

# Uploaded  model

- **Developed by:** jackcwf
- **License:** apache-2.0
- **Finetuned from model :** unsloth/deepseek-r1-distill-llama-8b-unsloth-bnb-4bit

This llama model was trained 2x faster with [Unsloth](https://github.com/unslothai/unsloth) and Huggingface's TRL library.

[<img src="https://raw.githubusercontent.com/unslothai/unsloth/main/images/unsloth%20made%20with%20love.png" width="200"/>](https://github.com/unslothai/unsloth)
