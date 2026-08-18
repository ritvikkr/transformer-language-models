# Bigram Transformer

A small character-level language model implemented using a Transformer
architecture and trained on *The Wonderful Wizard of Oz* by L. Frank
Baum.

This project is an educational implementation designed to demonstrate
how a simple Transformer-based language model learns patterns in text
and generates new sequences.

------------------------------------------------------------------------

## Project Structure

``` text
bigram-transformer/
│
├── bigram_transformer.ipynb
├── wizard_of_oz.txt
└── README.md
```

### Files

  -----------------------------------------------------------------------
  File                                Description
  ----------------------------------- -----------------------------------
  `bigram_transformer.ipynb`          Notebook containing the model
                                      implementation, training process,
                                      evaluation, and text generation

  `wizard_of_oz.txt`                  Text corpus used to train the model

  `README.md`                         Documentation for the project
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Dataset

The model is trained on *The Wonderful Wizard of Oz* by **L. Frank
Baum**.

The text used for training is stored in:

``` text
wizard_of_oz.txt
```

The dataset is used as a character-level corpus for learning patterns
and predicting the next character in a sequence.

The repository should preserve the attribution and licensing information
associated with the copy of the text being used.

------------------------------------------------------------------------

## Model Overview

The project implements a **Bigram Language Model using a
Transformer-style architecture**.

At a high level:

``` text
Input Text
    │
    ▼
Character-level Tokenization
    │
    ▼
Token Embeddings
    +
Positional Embeddings
    │
    ▼
Self-Attention
    │
    ▼
Linear Output Layer
    │
    ▼
Next-Character Prediction
    │
    ▼
Autoregressive Text Generation
```

The model learns the relationship between characters in the training
text and uses those learned patterns to predict subsequent characters.

------------------------------------------------------------------------

## Key Concepts

### Character-Level Tokenization

The text is represented at the character level rather than using words
or subword tokens.

For example:

``` text
"hello"
```

can be represented as:

``` text
h → e → l → l → o
```

Each unique character is mapped to an integer representation that can be
processed by the neural network.

------------------------------------------------------------------------

### Bigram Language Modeling

The model learns to predict the next character based on the preceding
context.

Conceptually:

``` text
Input:
The

Prediction:
space / next character
```

During generation, the predicted character is appended to the existing
sequence and becomes part of the context for the next prediction.

------------------------------------------------------------------------

### Self-Attention

Self-attention allows the model to determine which previous positions in
the sequence are useful when predicting the next character.

The model uses:

-   Query
-   Key
-   Value

representations to calculate attention weights between positions.

------------------------------------------------------------------------

### Causal Masking

The attention mechanism uses causal masking so that a position cannot
look at future characters while making a prediction.

Conceptually:

``` text
Character 1 → can see Character 1
Character 2 → can see Characters 1–2
Character 3 → can see Characters 1–3
Character 4 → can see Characters 1–4
```

This preserves the autoregressive nature of language modeling.

------------------------------------------------------------------------

### Positional Embeddings

Because attention itself does not inherently encode the order of
characters, positional information is added to the token embeddings.

The model therefore receives information about both:

-   What the character is
-   Where the character occurs in the sequence

------------------------------------------------------------------------

## Training

The notebook contains the training process for the model.

The general training workflow is:

``` text
Wizard of Oz Dataset
        │
        ▼
Character Encoding
        │
        ▼
Training / Validation Data
        │
        ▼
Input and Target Sequences
        │
        ▼
Transformer
        │
        ▼
Next-Character Predictions
        │
        ▼
Loss Calculation
        │
        ▼
Backpropagation
        │
        ▼
Parameter Updates
```

The model learns by minimizing the difference between its predicted next
character and the actual next character in the training sequence.

------------------------------------------------------------------------

## Text Generation

After training, the model can generate text autoregressively.

The process can be represented as:

``` text
Starting Prompt
      │
      ▼
Model Prediction
      │
      ▼
Next Character
      │
      ▼
Append Character
      │
      ▼
Use Updated Context
      │
      ▼
Repeat
```

For example:

``` text
Prompt:
Dorothy

Generated:
Dorothy ...
```

The exact output depends on the trained model parameters and sampling
process.

------------------------------------------------------------------------

## Running the Project

### Requirements

Install the dependencies listed in the main repository:

``` bash
pip install -r ../requirements.txt
```

Or, from the repository root:

``` bash
pip install -r requirements.txt
```

### Run the Notebook

Open:

``` text
bigram_transformer.ipynb
```

using Jupyter Notebook or JupyterLab.

For example:

``` bash
jupyter notebook
```

Then open the notebook and run the cells sequentially.

------------------------------------------------------------------------

## Results

The primary results of this project are the text sequences generated by
the trained model.

When documenting an experiment, useful information includes:

-   Training configuration
-   Training/validation loss, if recorded
-   Example prompts
-   Generated text
-   Training hardware
-   Training time

Example format:

``` text
Prompt:
Dorothy

Model Output:
<generated text>
```

Generated text should be evaluated as an experimental result rather than
as a factual or coherent response from a modern conversational LLM.

------------------------------------------------------------------------

## Limitations

This is a small educational language-modeling experiment.

The model is limited by:

-   Small training corpus
-   Character-level representation
-   Model size
-   Training duration
-   Limited context
-   Sampling strategy

It is intended to demonstrate the underlying concepts of Transformer
language modeling rather than serve as a production conversational AI
system.

------------------------------------------------------------------------

## Learning Objectives

This project provides practical exposure to:

-   Character-level tokenization
-   Vocabulary construction
-   Embeddings
-   Positional embeddings
-   Self-attention
-   Causal masking
-   Next-token prediction
-   Loss calculation
-   Training a neural language model
-   Autoregressive text generation
-   Transformer-based language modeling

------------------------------------------------------------------------

## Dataset Attribution

The training corpus is *The Wonderful Wizard of Oz* by **L. Frank
Baum**.

The repository should retain the attribution and licensing information
included with the dataset.

------------------------------------------------------------------------

## Author

**Ritvik Kumar**

This project was created as part of an exploration of:

-   Machine Learning
-   Deep Learning
-   Natural Language Processing
-   Transformers
-   Large Language Models
-   PyTorch
