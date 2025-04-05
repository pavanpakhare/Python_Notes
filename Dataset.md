# Datasets Library Tutorial

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Loading Datasets](#loading-datasets)
4. [Exploring Datasets](#exploring-datasets)
5. [Dataset Processing](#dataset-processing)
6. [Custom Datasets](#custom-datasets)
7. [Advanced Features](#advanced-features)
8. [Conclusion](#conclusion)

## Introduction
The Hugging Face `datasets` library provides easy access to thousands of datasets for NLP, computer vision, and audio tasks. It features:
- Efficient memory usage (memory-mapping)
- Built-in versioning
- Easy preprocessing
- Integration with Transformers

## Installation
```bash
pip install datasets
```

For additional features:
```bash
pip install datasets[audio]  # for audio datasets
pip install datasets[vision]  # for image datasets
pip install datasets[arrow]   # for faster processing
```

## Loading Datasets

### Standard Datasets
```python
from datasets import load_dataset

# Load a dataset
dataset = load_dataset("imdb")

# Load specific splits
train_dataset = load_dataset("imdb", split="train")
test_dataset = load_dataset("imdb", split="test")
```

### Dataset Configurations
```python
# Load a specific configuration
dataset = load_dataset("glue", "mrpc")  # MRPC task from GLUE benchmark
```

### Remote Datasets
```python
# Load from a GitHub URL
dataset = load_dataset("json", data_files="https://url/to/dataset.json")
```

### Local Files
```python
# Load local files
dataset = load_dataset("csv", data_files="path/to/file.csv")

# Multiple files
dataset = load_dataset("csv", data_files=["file1.csv", "file2.csv"])
```

## Exploring Datasets

### Basic Inspection
```python
# See dataset structure
print(dataset)

# Check splits
print(dataset.keys())

# First example
print(dataset["train"][0])

# Features
print(dataset["train"].features)
```

### Dataset Statistics
```python
# Length
print(len(dataset["train"]))

# Column names
print(dataset["train"].column_names)

# Unique values
print(dataset["train"].unique("label"))
```

### Visualization
```python
import pandas as pd
import matplotlib.pyplot as plt

# Convert to pandas
df = dataset["train"].to_pandas()

# Plot label distribution
df["label"].value_counts().plot(kind="bar")
plt.show()
```

## Dataset Processing

### Shuffling and Splitting
```python
# Shuffle
shuffled_dataset = dataset["train"].shuffle(seed=42)

# Train-test split
split_dataset = dataset["train"].train_test_split(test_size=0.1)
```

### Mapping Functions
```python
# Simple processing
def process_text(example):
    example["text_length"] = len(example["text"])
    return example

processed_dataset = dataset.map(process_text)

# Batched processing
def batch_process(examples):
    examples["text_length"] = [len(text) for text in examples["text"]]
    return examples

batch_processed = dataset.map(batch_process, batched=True)
```

### Filtering
```python
# Filter examples
filtered_dataset = dataset.filter(lambda example: len(example["text"]) > 100)

# Filter with multiple conditions
filtered_dataset = dataset.filter(
    lambda example: len(example["text"]) > 100 and example["label"] == 1
)
```

### Renaming and Removing Columns
```python
# Rename column
renamed_dataset = dataset.rename_column("text", "sentence")

# Remove columns
cleaned_dataset = dataset.remove_columns(["unnecessary_column"])
```

## Custom Datasets

### From Local Files
```python
# From CSV/JSON/Text
dataset = load_dataset("csv", data_files="my_data.csv")

# From dictionary
from datasets import Dataset
data_dict = {"text": ["sample1", "sample2"], "label": [0, 1]}
custom_dataset = Dataset.from_dict(data_dict)
```

### From Pandas
```python
import pandas as pd
from datasets import Dataset

df = pd.DataFrame({"text": ["sample1", "sample2"], "label": [0, 1]})
dataset = Dataset.from_pandas(df)
```

### From Generator
```python
def data_generator():
    for i in range(10):
        yield {"text": f"sample {i}", "label": i % 2}

dataset = Dataset.from_generator(data_generator)
```

## Advanced Features

### Memory Mapping
```python
# Save to disk (memory-mapped)
dataset.save_to_disk("my_dataset")

# Load from disk
loaded_dataset = load_from_disk("my_dataset")
```

### Push to Hub
```python
# Login first
from huggingface_hub import notebook_login
notebook_login()

# Push dataset
dataset.push_to_hub("my-username/my-dataset-name")
```

### Metrics
```python
# Load metric
from datasets import load_metric

metric = load_metric("glue", "mrpc")
predictions = [0, 1]
references = [0, 1]
print(metric.compute(predictions=predictions, references=references))
```

### Audio and Image Datasets
```python
# Audio dataset
audio_dataset = load_dataset("common_voice", "en")

# Image dataset
image_dataset = load_dataset("cifar10")
```

## Conclusion
The `datasets` library provides powerful tools for:
- Efficient dataset loading and processing
- Memory optimization
- Easy dataset sharing
- Seamless integration with Transformers

### Next Steps
- Explore the [dataset hub](https://huggingface.co/datasets)
- Learn about [dataset streaming](https://huggingface.co/docs/datasets/stream.html)
- Check out [advanced processing](https://huggingface.co/docs/datasets/process.html)

### Example Workflow
```python
from datasets import load_dataset

# Load and process dataset
dataset = load_dataset("imdb")
dataset = dataset.shuffle().map(lambda x: {"length": len(x["text"])})

# Filter and split
dataset = dataset.filter(lambda x: x["length"] > 100)
dataset = dataset["train"].train_test_split(test_size=0.2)

# Use with Transformers
from transformers import AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

def tokenize_function(examples):
    return tokenizer(examples["text"], padding="max_length", truncation=True)

tokenized_dataset = dataset.map(tokenize_function, batched=True)
```
