# Dataset

This directory is used for the **OpenWebText-derived dataset** required
by the Character-Level Transformer.

The raw dataset is **not included in this repository** because of its
size. It must be obtained separately and placed in the expected
directory before running the data-extraction script.

## Expected Structure

Place the compressed OpenWebText files (`.xz`) inside:

``` text
dataset/
└── OpenWebText/
    ├── file1.xz
    ├── file2.xz
    ├── file3.xz
    └── ...
```

The exact filenames are not important as long as the files use the `.xz`
format.

## Data Preparation

From the `character-transformer` directory, run:

``` bash
python extract.py
```

The extraction script:

1.  Finds the `.xz` files in the dataset directory.
2.  Uses approximately **90% of the files for training** and **10% for
    validation**.
3.  Extracts the text from the compressed files.
4.  Creates the training and validation text files.
5.  Builds the character-level vocabulary.

The generated files are used by `training.py` and are intentionally
excluded from GitHub because of their size.

## Generated Data

After running `extract.py`, the processed data should be available to
the training pipeline as:

``` text
train_split.txt
val_split.txt
vocab.txt
```

`vocab.txt` contains the unique characters used by the character-level
tokenizer.

## Important

Do not commit the raw `.xz` dataset or the generated training and
validation files to this repository.

The dataset should remain local, while `extract.py` provides the
reproducible preprocessing step required to prepare it for training.
