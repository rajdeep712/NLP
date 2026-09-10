Create `README.md` in the `Assignment 01` folder:

````markdown
# Assignment 01

This assignment collects, cleans, tokenizes, and analyzes Hindi text from the IndicCorpV2 dataset.

## Files

- `Assignment_01.ipynb` — Main Jupyter Notebook
- `hindi_texts_raw.parquet` — Cleaned Hindi text
- `hindi_texts_tokenized.parquet` — Sentence-level tokenized dataset

## Dataset

The notebook uses the Hindi Devanagari split of AI4Bharat's IndicCorpV2 dataset:

```text
ai4bharat/IndicCorpV2
```

The dataset is loaded in streaming mode to reduce memory usage:

```text
Split: hin_Deva
Maximum records: 2,100,000
```

## Data Cleaning

The notebook:

- Removes duplicate texts.
- Removes missing values.
- Removes empty strings.
- Resets the DataFrame index.
- Saves the cleaned data as a compressed Parquet file.

Output file:

```text
hindi_texts_raw.parquet
```

## Sentence Tokenization

Hindi sentences are split using Devanagari and common punctuation marks:

```text
।  !  ?  ॥
```

The sentence tokenizer returns a list of cleaned sentences.

## Word Tokenization

The notebook uses a regular expression tokenizer that recognizes:

- Hindi words
- English words and characters
- Integers
- Decimal numbers
- Dates
- Email addresses
- URLs
- Punctuation
- Special symbols

Each sentence is converted into a list of tokens.

## Dataset Columns

The final tokenized dataset contains:

| Column        | Description                      |
| ------------- | -------------------------------- |
| `sentence`    | Original sentence text           |
| `words`       | List of tokens                   |
| `words_count` | Number of tokens in the sentence |

Output file:

```text
hindi_texts_tokenized.parquet
```

## Corpus Statistics

The notebook calculates:

- Total number of sentences
- Total number of words
- Total number of characters
- Average sentence length
- Average word length
- Total number of tokens
- Number of unique tokens
- Type-Token Ratio (TTR)

The Type-Token Ratio is calculated as:

```text
TTR = Number of unique tokens / Total number of tokens
```

## Workflow

```text
Load IndicCorpV2 Hindi dataset
        ↓
Collect up to 2,100,000 records
        ↓
Remove duplicates and empty values
        ↓
Save cleaned raw text
        ↓
Split text into sentences
        ↓
Tokenize sentences into words
        ↓
Calculate token counts
        ↓
Save tokenized dataset
        ↓
Generate corpus statistics
```

## Requirements

Install the required Python packages:

```bash
pip install datasets pandas tqdm pyarrow
```

## Running the Notebook

1. Open the `Assignment 01` folder in Visual Studio Code.
2. Install the required dependencies.
3. Open `Assignment_01.ipynb`.
4. Run the cells from top to bottom.
5. Wait for the dataset streaming and preprocessing to complete.
6. Review the generated Parquet files and corpus statistics.

## Notes

- The notebook requires an internet connection to download IndicCorpV2.
- Streaming mode avoids downloading the complete dataset at once.
- The generated `hindi_texts_tokenized.parquet` file is used by later assignments for language-model training and evaluation.
````
