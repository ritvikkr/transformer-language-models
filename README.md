# Transformer Language Models from Scratch

A collection of Transformer-based language models implemented and
trained from scratch using PyTorch.

This repository documents my progression from a small **Bigram
Transformer** trained on *The Wonderful Wizard of Oz* to a larger
**character-level Transformer** trained on OpenWebText-derived data.

The primary goal of this project is educational: to understand the
fundamentals of Transformer language modeling by implementing the model
architecture, data preparation, training pipeline, checkpointing, and
autoregressive text generation directly in PyTorch.

------------------------------------------------------------------------

## Repository Structure

``` text
transformer-language-models/
│
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
│
├── bigram-transformer/
│   ├── bigram_transformer.ipynb
│   ├── wizard_of_oz.txt
│   └── README.md
│
└── character-transformer/
    ├── README.md
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
    └── checkpoints/
        ├── README.md
        └── model-01.pth
```

Large OpenWebText-derived files are intentionally **not included** in
this repository.

------------------------------------------------------------------------

# Projects

## 1. Bigram Transformer

A small Transformer language-modeling experiment trained on *The
Wonderful Wizard of Oz*.

**Location:** `bigram-transformer/`

**Main file:** `bigram_transformer.ipynb`

The project provides an introductory implementation for exploring the
fundamentals of language modeling and Transformer-based next-token
prediction.

### Concepts explored

-   Character-level tokenization
-   Vocabulary creation
-   Embeddings
-   Positional information
-   Self-attention
-   Transformer blocks
-   Next-token prediction
-   Autoregressive text generation

------------------------------------------------------------------------

## 2. Character-Level Transformer

A larger character-level Transformer trained on OpenWebText-derived
data.

**Location:** `character-transformer/`

The project contains a complete pipeline for:

1.  Preparing the dataset
2.  Building a character vocabulary
3.  Training the Transformer
4.  Saving the trained model
5.  Loading the trained model
6.  Generating text from prompts

### Main files

  File                         Purpose
  ---------------------------- ------------------------------------------------
  `extract.py`                 Extracts and prepares the OpenWebText data
  `training.py`                Defines, trains, and evaluates the Transformer
  `chatbot.py`                 Loads the trained model and generates text
  `data/vocab.txt`             Character vocabulary used by the model
  `checkpoints/model-01.pth`   Trained model checkpoint

------------------------------------------------------------------------

# Character-Level Transformer Architecture

The model follows this general pipeline:

``` text
Input Characters
       │
       ▼
Character Embeddings
       │
       +
       │
Positional Embeddings
       │
       ▼
Transformer Blocks
       │
       ├── Causal Multi-Head Self-Attention
       ├── Feed-Forward Network
       ├── Residual Connections
       └── Layer Normalization
       │
       ▼
Final Layer Normalization
       │
       ▼
Language Model Head
       │
       ▼
Character Probabilities
       │
       ▼
Autoregressive Generation
```

The attention mechanism is causal, meaning that during next-character
prediction the model cannot use future characters as context.

------------------------------------------------------------------------

# Model Configuration

The current Character-Level Transformer uses the following
configuration:

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

These are the parameters used in the current training implementation.
Future experiments may use different configurations.

------------------------------------------------------------------------

# Data Pipeline

The Character-Level Transformer uses OpenWebText-derived data.

``` text
OpenWebText .xz files
          │
          ▼
      extract.py
          │
          ├───────────────┐
          ▼               ▼
   Training Data     Validation Data
          │               │
          └───────┬───────┘
                  ▼
             vocab.txt
                  │
                  ▼
             training.py
                  │
                  ▼
             Transformer
                  │
                  ▼
          Model Checkpoint
                  │
                  ▼
             chatbot.py
                  │
                  ▼
           Text Generation
```

The large processed training and validation files are not included in
the repository.

Instead, `extract.py` provides the data-preparation step required to
generate them locally.

------------------------------------------------------------------------

# Dataset Setup

OpenWebText-derived data is not included because of its size.

Before running the Character-Level Transformer, follow the instructions
in:

``` text
character-transformer/dataset/README.md
```

The expected dataset directory should contain the OpenWebText compressed
files.

After placing the dataset in the expected location, run:

``` bash
cd character-transformer
python extract.py
```

This generates the processed data and vocabulary required for training.

The generated large files should remain excluded through `.gitignore`.

------------------------------------------------------------------------

# Installation

## 1. Clone the repository

``` bash
git clone https://github.com/YOUR_USERNAME/transformer-language-models.git
cd transformer-language-models
```

Replace `YOUR_USERNAME` with your GitHub username.

## 2. Create a virtual environment

### Windows

``` powershell
python -m venv .venv
.venv\Scriptsctivate
```

### Linux/macOS

``` bash
python -m venv .venv
source .venv/bin/activate
```

## 3. Install dependencies

``` bash
pip install -r requirements.txt
```

If you use `uv`:

``` bash
uv pip install -r requirements.txt
```

------------------------------------------------------------------------

# Running the Bigram Transformer

Navigate to:

``` bash
cd bigram-transformer
```

Open:

``` text
bigram_transformer.ipynb
```

Run the notebook cells sequentially to train the model and generate
text.

------------------------------------------------------------------------

# Running the Character-Level Transformer

## Step 1 --- Prepare the dataset

Place the OpenWebText `.xz` files in the directory described in:

``` text
character-transformer/dataset/README.md
```

Then run:

``` bash
cd character-transformer
python extract.py
```

This prepares the training data, validation data, and character
vocabulary.

## Step 2 --- Train the model

Run:

``` bash
python training.py --batch_size 64
```

Choose a batch size according to the available GPU/CPU memory.

The training process evaluates both training and validation loss during
training.

## Step 3 --- Generate text

After training, run:

``` bash
python chatbot.py
```

Enter a prompt when requested and the model will generate a
continuation.

------------------------------------------------------------------------

# Model Checkpoint

The trained Character-Level Transformer checkpoint is stored under:

``` text
character-transformer/checkpoints/
```

The checkpoint is intended to allow the trained model to be loaded
without retraining from scratch.

If the checkpoint is distributed separately because of its file size,
the download instructions should be added to
`character-transformer/checkpoints/README.md`.

------------------------------------------------------------------------

# Results

Results are intentionally kept lightweight and are not stored in a
dedicated `results/` directory.

The project documentation should report results such as:

-   Training loss
-   Validation loss
-   Model parameter count
-   Training configuration
-   Training hardware
-   Approximate training time
-   Sample generated text

For generated text, include the **prompt together with the model
output** so that the result can be evaluated in context.

Example:

``` text
Prompt:
The future of artificial intelligence

Model Output:
<generated text>
```

Results should be based on actual training runs rather than estimated
values.

------------------------------------------------------------------------

# Bigram Transformer vs Character-Level Transformer

  -----------------------------------------------------------------------
  Feature                 Bigram Transformer      Character-Level
                                                  Transformer
  ----------------------- ----------------------- -----------------------
  Dataset                 The Wonderful Wizard of OpenWebText-derived
                          Oz                      data

  Scale                   Small                   Larger

  Tokenization            Character-level         Character-level

  Primary purpose         Introductory experiment Larger language-model
                                                  experiment

  Context                 Model-specific          256

  Attention               Transformer attention   Causal multi-head
                                                  attention

  Generation              Autoregressive          Autoregressive
  -----------------------------------------------------------------------

The two projects demonstrate the progression from a smaller
language-modeling experiment to a larger Transformer trained on a more
diverse corpus.

------------------------------------------------------------------------

# Limitations

This repository is an educational implementation and is not intended to
compete with modern production LLMs.

The models are limited by:

-   Dataset scale
-   Model size
-   Training compute
-   Context length
-   Character-level tokenization
-   Training duration
-   Sampling strategy

The Character-Level Transformer should therefore be considered a
learning and experimentation project rather than a production
conversational AI system.

------------------------------------------------------------------------

# Learning Objectives

This repository is intended to build practical understanding of:

-   Character-level tokenization
-   Vocabulary construction
-   Embeddings
-   Positional embeddings
-   Causal self-attention
-   Multi-head attention
-   Transformer blocks
-   Feed-forward networks
-   Residual connections
-   Layer normalization
-   Next-token prediction
-   Cross-entropy loss
-   AdamW optimization
-   Training and validation evaluation
-   Autoregressive generation
-   Model checkpointing
-   GPU-based training with PyTorch

------------------------------------------------------------------------

# Dataset and Attribution

## The Wonderful Wizard of Oz

The Bigram Transformer uses *The Wonderful Wizard of Oz* by L. Frank
Baum.

The repository should preserve the attribution and licensing information
associated with the copy of the text being used.

## OpenWebText

The Character-Level Transformer uses OpenWebText-derived data.

The full dataset and processed training/validation files are not
included in this repository because of their size. Users should obtain
the dataset through an appropriate source and follow its applicable
terms.

------------------------------------------------------------------------

# Author

**Ritvik Kumar**

This project was created as part of an exploration of:

-   Machine Learning
-   Deep Learning
-   Natural Language Processing
-   Transformers
-   Large Language Models
-   PyTorch

------------------------------------------------------------------------

# License

The source code in this repository is intended to be released under the
MIT License.

Dataset files and other third-party materials remain subject to their
respective licenses and terms.
