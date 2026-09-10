Create `README.md` in the `Assignment 03` folder with the following content:

````markdown
# Assignment 03

This assignment demonstrates Finite Automata and Finite-State Transducers (FSTs) for basic English word recognition and noun morphology.

## Contents

- `Assignment_03_01.ipynb` — Main Jupyter Notebook
- `brown_nouns.txt` — Brown noun corpus used for validation

## Part 1: DFA Word Validation

A Deterministic Finite Automaton (DFA) is created using `visual_automata`.

### Accepted language

The DFA accepts words containing only lowercase alphabetic characters:

- `cat`
- `dog`
- `zebra`
- `a`

### Rejected examples

- `dog1`
- `1dog`
- `DogHouse`
- `Dog_house`
- ` cats`

The `evaluate_word()` function processes each character and returns either:

- `Accepted`
- `Not Accepted`

## Part 2: Noun Morphology Using an FST

The notebook implements a Finite-State Transducer for singular and plural noun analysis.

### Supported pluralization rules

#### Regular `s` plural

```text
bag  → bags
dog  → dogs
```

Output:

```text
bag+N+PL
```

#### `es` plural

Used for words ending in `s`, `z`, `x`, `ch`, or `sh`.

```text
fox   → foxes
watch → watches
```

Output:

```text
fox+N+PL
watch+N+PL
```

#### `y` to `ies` plural

Used when a consonant precedes the final `y`.

```text
try  → tries
city → cities
```

Output:

```text
try+N+PL
city+N+PL
```

### Singular analysis

Known singular nouns are returned with the following format:

```text
word+N+SG
```

For example:

```text
fox+N+SG
bag+N+SG
```

Invalid or unsupported words return:

```text
Invalid Word
```

## FST Components

The notebook contains:

- A transition table
- Input alphabet definition
- Expanded character-level transitions
- Singular and plural states
- `run_fst()` for rule-based transduction
- `analyze_word()` for corpus-based noun analysis

## Running the Notebook

1. Open the `Assignment_03` folder in Visual Studio Code.
2. Ensure Python and the Jupyter extension are installed.
3. Install the required package:

```bash
pip install visual-automata
```

4. Place `brown_nouns.txt` in the same folder as the notebook.
5. Open `Assignment_03_01.ipynb`.
6. Run the cells from top to bottom.

## Example Test Cases

```text
fox     → fox+N+SG
foxes   → fox+N+PL
watch   → watch+N+SG
watches → watch+N+PL
try     → try+N+SG
tries   → try+N+PL
bag     → bag+N+SG
bags    → bag+N+PL
foxs    → Invalid Word
```

## Objective

The objective of this assignment is to show how:

- DFAs can validate input strings.
- FSTs can model morphological transformations.
- Corpus data can be used to validate noun roots.
- Words can be analyzed using linguistic tags such as `N`, `SG`, and `PL`.
````
