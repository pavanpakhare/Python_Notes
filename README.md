# Transformers-Notes-

# Transformers in Python: A Step-by-Step Tutorial

This tutorial will guide you through using the Hugging Face Transformers library, which provides state-of-the-art natural language processing models like BERT, GPT-2, and more.

## Prerequisites

Before starting, make sure you have:
- Python 3.6+
- pip installed

## Installation

First, install the transformers library along with PyTorch or TensorFlow:

```bash
pip install transformers
pip install torch  # or tensorflow
```

## Part 1: Using Pre-trained Models

### 1. Text Classification

```python
from transformers import pipeline

# Create a text classification pipeline
classifier = pipeline("text-classification")

# Classify a text
result = classifier("I love using transformers library!")
print(result)
```

### 2. Named Entity Recognition (NER)

```python
ner = pipeline("ner", grouped_entities=True)
result = ner("My name is John and I work at Google in New York.")
print(result)
```

### 3. Question Answering

```python
qa = pipeline("question-answering")
result = qa(
    question="What is the capital of France?",
    context="France is a country in Europe. Its capital is Paris."
)
print(result)
```

### 4. Text Generation

```python
generator = pipeline("text-generation", model="gpt2")
result = generator("In the future, AI will", max_length=50, num_return_sequences=2)
print(result)
```

## Part 2: Working with Models and Tokenizers Directly

### 1. Loading Models and Tokenizers

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model_name = "bert-base-uncased"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name)
```

### 2. Tokenizing Text

```python
text = "Transformers are awesome!"
inputs = tokenizer(text, return_tensors="pt")
print(inputs)
```

### 3. Model Inference

```python
outputs = model(**inputs)
print(outputs)
```

## Part 3: Fine-tuning a Model

### 1. Preparing Data

```python
from datasets import load_dataset

dataset = load_dataset("imdb")
print(dataset["train"][0])
```

### 2. Tokenizing the Dataset

```python
def tokenize_function(examples):
    return tokenizer(examples["text"], padding="max_length", truncation=True)

tokenized_datasets = dataset.map(tokenize_function, batched=True)
```

### 3. Training Setup

```python
from transformers import TrainingArguments, Trainer

training_args = TrainingArguments(
    output_dir="./results",
    evaluation_strategy="epoch",
    learning_rate=2e-5,
    per_device_train_batch_size=8,
    per_device_eval_batch_size=8,
    num_train_epochs=3,
    weight_decay=0.01,
)

trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=tokenized_datasets["train"].select(range(1000)),
    eval_dataset=tokenized_datasets["test"].select(range(1000)),
)
```

### 4. Training the Model

```python
trainer.train()
```

## Part 4: Saving and Loading Models

### 1. Saving a Model

```python
model.save_pretrained("./my_model")
tokenizer.save_pretrained("./my_model")
```

### 2. Loading a Saved Model

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("./my_model")
tokenizer = AutoTokenizer.from_pretrained("./my_model")
```

## Part 5: Advanced Topics

### 1. Custom Model Architectures

```python
from transformers import BertConfig, BertModel

config = BertConfig(
    hidden_size=768,
    num_attention_heads=12,
    num_hidden_layers=6,
)
model = BertModel(config)
```

### 2. Using Different Frameworks

```python
# PyTorch
from transformers import BertModel
model = BertModel.from_pretrained("bert-base-uncased")

# TensorFlow
from transformers import TFBertModel
model = TFBertModel.from_pretrained("bert-base-uncased")
```
