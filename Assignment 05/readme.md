Create `README.md` in the `Assignment 05` folder:

````markdown
# Assignment 05

This assignment evaluates previously trained Hindi N-gram language models using Add-K smoothing.

## Files

- `Assignment_05.ipynb` — Main Jupyter Notebook
- Hugging Face models — `rajdeeppa53/hindi-ngram-language-models`
- Input dataset — `../Assignment 01/hindi_texts_tokenized.parquet`

## Objectives

- Download trained N-gram models from Hugging Face.
- Load compressed vocabulary and count files.
- Apply Add-K smoothing.
- Evaluate unigram, bigram, trigram, and quadrigram models.
- Compare development and test perplexity.

## Models Used

The notebook loads four count-based language models:

- Unigram
- Bigram
- Trigram
- Quadrigram

The following files are downloaded:

```text
vocab.pkl.gz
unigram_counts.pkl.gz
bigram_counts.pkl.gz
bigram_context_counts.pkl.gz
trigram_counts.pkl.gz
trigram_context_counts.pkl.gz
quadrigram_counts.pkl.gz
quadrigram_context_counts.pkl.gz
metadata.json
```

## Add-K Smoothing

The smoothing parameter is:

```text
K = 0.3
```

The general smoothed probability is:

```text
P = (count + K) / (context_count + K × vocabulary_size)
```

For unigram probabilities:

```text
P(w) = (C(w) + K) / (N + K × V)
```

Smoothing assigns non-zero probabilities to unseen n-grams.

## Data Processing

The notebook:

1. Downloads the trained models from Hugging Face.
2. Loads the Hindi tokenized dataset.
3. Uses random seed `42`.
4. Creates development and test sets of 1,000 sentences each.
5. Replaces out-of-vocabulary words with `<UNK>`.
6. Adds `<s>` and `</s>` sentence-boundary tokens.
7. Calculates model probabilities using Add-K smoothing.

## Evaluation

Each model is evaluated using perplexity on:

- Development data
- Test data

Lower perplexity indicates better predictive performance.

The final results table contains:

- Model name
- Development perplexity
- Test perplexity
- Smoothing parameter `K`

## Hugging Face Repository

The models are downloaded from:

```text
https://huggingface.co/rajdeeppa53/hindi-ngram-language-models
```

The notebook uses `hf_hub_download()` to retrieve individual model files.

## Requirements

Install the required packages:

```bash
pip install pandas numpy pyarrow huggingface_hub
```

## Running the Notebook

1. Open the `Assignment 05` folder in Visual Studio Code.
2. Ensure the dataset exists at:

   ```text
   ../Assignment 01/hindi_texts_tokenized.parquet
   ```

3. Open `Assignment_05.ipynb`.
4. Run the cells from top to bottom.
5. Allow the notebook to download the models from Hugging Face.
6. Review the final perplexity comparison table.

## Workflow

```text
Download models from Hugging Face
        ↓
Load vocabulary and n-gram counts
        ↓
Load Hindi tokenized dataset
        ↓
Create development and test sets
        ↓
Replace unknown words
        ↓
Add sentence-boundary tokens
        ↓
Apply Add-K smoothing
        ↓
Calculate perplexity
        ↓
Compare model performance
```

## Related Assignment

Assignment 05 extends Assignment 04 by replacing Add-One/Laplace smoothing with Add-K smoothing and evaluating the effect of:

```text
K = 0.3
```
````
