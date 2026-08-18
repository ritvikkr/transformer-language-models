# Data

This directory contains the small processed data artifact required by
the Character-Level Transformer.

## Contents

``` text
data/
├── README.md
└── vocab.txt
```

### `vocab.txt`

`vocab.txt` contains the character vocabulary used by the model.

The training script reads this file to construct the
character-to-integer and integer-to-character mappings used during
training and text generation.

## Generated Data

The complete processed training and validation datasets are
intentionally **not included** in this directory because of their size.

After running:

``` bash
python extract.py
```

the preprocessing pipeline generates:

``` text
train_split.txt
val_split.txt
vocab.txt
```

The large training and validation files should remain local and are
excluded from the GitHub repository.

## Usage

The data in this directory is consumed by:

``` text
training.py
    │
    ▼
vocab.txt
    │
    ▼
Character Encoding
    │
    ▼
Model Training
```

No manual modification of `vocab.txt` is required for normal training.
