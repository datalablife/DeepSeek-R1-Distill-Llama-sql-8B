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

# About Model 

Fine-tuning is used to convert SQL language into natural language, making it easier for users to understand the business meaning of SQL queries. This fine-tuned model is based on the unsloth framework 和 uses the DeepSeek-R1-Distill-Llama-8B pre-trained model under unsloth.


# DataSet 

[b-mc2/sql-create-context](https://huggingface.co/datasets/b-mc2/sql-create-context)

# Model  train

![](https://github.com/datalablife/DeepSeek-R1-Distill-Llama-sql-8B/blob/main/images/train.png?raw=true)

1. **train/loss**: This chart shows the model's loss during training. As the training steps (global step) increase, the loss value drops sharply 和 then stabilizes, indicating that the model is gradually converging.
2. **train/learning_rate**: This chart shows how the learning rate changes over training steps. From the chart, we can see that the learning rate decreases as training progresses, which is likely part of a learning rate decay strategy to prevent the model from oscillating in the later stages of training.
3. **train/grad_norm**: This chart displays the change in gradient norm over training steps. The decrease in gradient norm suggests that the gradients are stabilizing, reducing instability during training.
4. **train/global_step**: This chart shows the increase in global training steps. As the training progresses, the step count gradually increases, indicating the progress of the training process.
5. **train/epoch**: This chart represents the progress of each training epoch. As the global steps increase, the epoch count also steadily grows.


# Inference results before 和 after model training:

## Prompt
![](https://github.com/datalablife/DeepSeek-R1-Distill-Llama-sql-8B/blob/1b7d2b95c5a1df0a753fa362fc1d7130f828308c/images/train-prompt.jpeg)

## Define SQL query for testing
This is a complex customer analysis query used to test the understanding of the model

query1 = """
```sql
SELECT
    c.customer_id,
    c.name AS customer_name,
    COUNT(o.order_id) AS total_orders,
    SUM(o.total_amount) AS total_spent,
    AVG(o.total_amount) AS avg_order_value,
    MAX(o.order_date) AS last_order_date
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
LEFT JOIN order_items oi ON o.order_id = oi.order_id
WHERE o.order_date >= '2024-01-01'
GROUP BY c.customer_id, c.name
ORDER BY total_spent DESC
LIMIT 10;
```
Explain use case of this query.
"""

## Pre-training inference results:

The SQL query is designed to analyze customer data from the orders placed in January 2024. It aggregates information such as the number of orders, total spending, average order value, and the last order date for each customer. The results are sorted by total spending in descending order, allowing the identification of the top 10 customers based on their spending. This is useful for marketing or sales teams to target high-spending customers for promotions or personalized campaigns. The LEFT JOIN with order_items ensures that all customers, including those with pending or incomplete orders, are included in the results.<｜end▁of▁sentence｜>

## Inference results after training:
Show customer id, customer name, total orders, total spent, average order value，last order date for top 10 customers by total spent.< | end▁of▁sentence｜>


# Model  Download

| **Model**                        | **Base Model**                                               | **下载**                                                 |
| -------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| DeepSeek-R1-Distill-Llama-sql-8B | [Llama-3.1-8B](https://huggingface.co/meta-llama/Llama-3.1-8B) | [🤗 HuggingFace](https://huggingface.co/jackcwf/deepseek_sql_model/blob/main/unsloth.Q8_0.gguf) |


# Usage

If you are unsure how to use GGUF files, refer to one of [TheBloke's READMEs](https://huggingface.co/TheBloke/KafkaLM-70B-German-V0.1-GGUF) for more details, including on how to concatenate multi-part files.


# Uploaded  model

- **Developed by:** jackcwf
- **License:** apache-2.0
- **Finetuned from model :** unsloth/deepseek-r1-distill-llama-8b-unsloth-bnb-4bit



This llama model was trained 2x faster with [Unsloth](https://github.com/unslothai/unsloth) and Huggingface's TRL library.

[<img src="https://raw.githubusercontent.com/unslothai/unsloth/main/images/unsloth%20made%20with%20love.png" width="200"/>](https://github.com/unslothai/unsloth)
