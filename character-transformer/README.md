# Character-Level Transformer

A character-level Transformer language model trained on
OpenWebText-derived data using PyTorch.

## Files

``` text
character-transformer/
├── extract.py
├── training.py
├── chatbot.py
│
├── dataset/
│   └── README.md
│
├── data/
│   ├── README.md
│   └── vocab.txt
│
├── checkpoints/
│   ├── README.md
│   └── model-01.pth
│
└── README.md
```

-   `extract.py` --- extracts the compressed dataset, creates the
    training/validation splits, and builds the character vocabulary.
-   `training.py` --- defines, trains, evaluates, and saves the
    Transformer model.
-   `chatbot.py` --- loads the trained model and generates text from a
    prompt.
-   `data/vocab.txt` --- character vocabulary.
-   `checkpoints/model-01.pth` --- trained model checkpoint.

## Model

The current model uses:

  Parameter                         Value
  --------------------- -----------------
  Tokenization            Character-level
  Context length                      256
  Embedding dimension                 384
  Attention heads                       6
  Transformer layers                    6
  Dropout                             0.2
  Learning rate                      3e-4
  Training iterations              10,000
  Optimizer                         AdamW

The architecture consists of token and positional embeddings followed by
causal multi-head self-attention, feed-forward layers, residual
connections, layer normalization, and a language-model output head.

## Dataset

The OpenWebText-derived dataset is **not included** because of its size.

Place the compressed dataset files in the location described in:

``` text
dataset/README.md
```

Then run:

``` bash
python extract.py
```

The script generates the processed training and validation data and the
character vocabulary required by the training script.

## Training

From the `character-transformer` directory:

``` bash
python training.py --batch_size 64
```

Adjust `batch_size` according to available hardware.

The training script evaluates both training and validation loss during
training.

## Text Generation

After training, run:

``` bash
python chatbot.py
```

Enter a prompt to generate a continuation from the trained model.

Example:

``` text
Prompt:
The future of artificial intelligence

Completion:
<generated text>
```

## Results

Useful results to record from an actual training run include:

-   Final training loss
-   Final validation loss
-   Model parameter count
-   Training hardware
-   Training time
-   Sample generated text

## Limitations

This is an educational character-level language model and is not
intended to function as a production conversational LLM.

## Author

**Ritvik Kumar**
