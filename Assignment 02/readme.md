Create `README.md` in the `Assignment 02` folder:

````markdown
# Assignment 02

This assignment implements and evaluates word segmentation algorithms for text without spaces.

## Files

- `Assignment_02.ipynb` — Main Jupyter Notebook
- `text_segmentation_dataset.json` — Word-frequency data and test cases

## Objectives

- Segment continuous text into words.
- Compare greedy and dynamic programming approaches.
- Use word frequencies to calculate segmentation probabilities.
- Evaluate predictions using accuracy and edit distance.

## Dataset

The notebook loads `text_segmentation_dataset.json`, which contains:

- `word_counts` — Word-frequency dictionary
- `test_cases` — Input strings and their ground-truth segmentations
- `metadata.total_corpus_words` — Total number of words in the corpus

## Greedy Segmentation

The greedy algorithm scans the input from left to right and selects the longest vocabulary word matching the current position.

If no vocabulary word is found, the current character is treated as an unknown token.

```python
greedy_segment(text, vocab)
```

## Dynamic Programming Segmentation

The dynamic programming algorithm considers all possible word boundaries and selects the segmentation with the highest probability.

Word probabilities are calculated from corpus frequencies:

```text
P(word) = count(word) / total_corpus_words
```

Log probabilities are used to avoid numerical underflow:

```text
log(P(word))
```

The algorithm uses backpointers to reconstruct the best word sequence.

```python
dp_segment(text, word_counts)
```

## Evaluation Metrics

### Word Accuracy

Accuracy is calculated by comparing predicted words with the corresponding ground-truth words:

```text
Accuracy = Correctly matched words / Number of actual words
```

### Edit Distance

Edit distance measures the minimum number of word-level operations needed to transform the predicted segmentation into the correct segmentation.

Supported operations:

- Insertion
- Deletion
- Substitution

Lower edit distance indicates better performance.

## Evaluation

Both segmentation methods are evaluated on every test case.

The notebook reports:

- Average word accuracy
- Average edit distance

The results are displayed separately for:

- Greedy segmentation
- Dynamic programming segmentation

## Workflow

```text
Load JSON dataset
    ↓
Extract vocabulary and word counts
    ↓
Run greedy segmentation
    ↓
Calculate word probabilities
    ↓
Run dynamic programming segmentation
    ↓
Compare predictions with ground truth
    ↓
Calculate accuracy and edit distance
```

## Running the Notebook

1. Open the `Assignment 02` folder in Visual Studio Code.
2. Ensure `text_segmentation_dataset.json` is in the same folder.
3. Open `Assignment_02.ipynb`.
4. Run the cells from top to bottom.
5. Compare the evaluation results for both algorithms.

## Requirements

No external packages are required. The notebook uses Python standard-library modules:

```python
import json
import math
```

## Conclusion

The assignment demonstrates that greedy segmentation is simple and fast but may select locally optimal words. Dynamic programming considers multiple possible segmentations and uses word frequencies to find a more probable global solution.
````
