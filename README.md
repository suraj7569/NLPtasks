
# NLP Text Processing

This project utilizes the Hugging Face Transformers library to perform various Natural Language Processing (NLP) tasks, including sentiment analysis, zero-shot classification, text generation, summarization, and translation.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Sentiment Analysis](#sentiment-analysis)
  - [Zero-Shot Classification](#zero-shot-classification)
  - [Text Generation](#text-generation)
  - [Text Summarization](#text-summarization)
  - [Text Translation](#text-translation)
- [License](#license)

## Installation

To install the required libraries, run the following command:

```bash
pip install transformers
```

## Usage

### Sentiment Analysis

The sentiment analysis pipeline uses the `distilbert-base-uncased-finetuned-sst-2-english` model to classify the sentiment of given texts.

```python
from transformers import pipeline

classifier = pipeline("sentiment-analysis", model='distilbert-base-uncased-finetuned-sst-2-english')
result = classifier("This is by far the best product I have ever used; it exceeded all my expectations.")
print(result)
```

**Example Output:**
```json
[{'label': 'POSITIVE', 'score': 0.9998}]
```

### Zero-Shot Classification

This pipeline allows for classifying texts into predefined categories without needing a training dataset.

```python
classifier = pipeline("zero-shot-classification")
classifier("Photosynthesis is the process by which green plants use sunlight to synthesize nutrients from carbon dioxide and water.", candidate_labels=["education", "science", "business"])
```

### Text Generation

The text generation pipeline uses the `distilgpt2` model to generate text based on a given prompt.

```python
generator = pipeline("text-generation", model="distilgpt2")
generator("I love her but can't able to say", max_length=1000, num_return_sequences=2)
```

### Text Summarization

This pipeline summarizes long texts into shorter versions.

```python
summarizer = pipeline("summarization")
text = """
San Francisco, officially the City and County of San Francisco, is a commercial and cultural center in the northern region of the U.S. state of California. San Francisco is the fourth most populous city in California and the 17th most populous in the United States, with 808,437 residents as of 2022.
"""
summary = summarizer(text, max_length=50, min_length=25, do_sample=False)
print(summary)
```

**Example Output:**
```json
[{'summary_text': 'San Francisco is a commercial and cultural center in California.'}]
```

### Text Translation

The translation pipeline translates text from French to English using the `Helsinki-NLP/opus-mt-fr-en` model.

```python
translator = pipeline("translation", model="Helsinki-NLP/opus-mt-fr-en")
translation = translator("L'engagement de l'entreprise envers l'innovation et l'excellence est véritablement inspirant.")
print(translation)
```

**Example Output:**
```json
[{'translation_text': "The company's commitment to innovation and excellence is truly inspiring."}]
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to modify any sections as needed!



