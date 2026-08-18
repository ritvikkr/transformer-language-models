# Checkpoints

This directory contains trained model checkpoints for the
Character-Level Transformer.

## Contents

``` text
checkpoints/
├── README.md
└── model-01.pth
```

### `model-01.pth`

`model-01.pth` is the saved checkpoint of the trained Character-Level
Transformer.

It can be used by `chatbot.py` to load the trained model and generate
text without retraining the model.

## Usage

The checkpoint is loaded during inference by:

``` bash
python chatbot.py
```

Make sure the checkpoint is located in the expected path before running
the chatbot.

## Training a New Checkpoint

To create or replace a checkpoint, train the model using:

``` bash
python training.py --batch_size 64
```

The resulting checkpoint can then be used for text generation.

## Notes

Model checkpoints can be large binary files. If the checkpoint exceeds
GitHub's regular file-size limits, it should be distributed using Git
LFS or a GitHub Release rather than committed directly to the
repository.

Do not commit temporary or intermediate checkpoints unless they are
intentionally being preserved as part of an experiment.
