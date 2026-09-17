# Tamil LLM — 23M Parameters

A Tamil language model built from scratch using a custom BPE tokenizer and a decoder-only Transformer architecture. The project covers data preparation, tokenization, pretraining, and supervised fine-tuning (SFT), implemented using PyTorch and Google Colab.

## Model

| Component               | Configuration            |
| ----------------------- | ------------------------ |
| Architecture            | Decoder-only Transformer |
| Parameters              | 23,033,856 (~23M)        |
| Language                | Tamil                    |
| Vocabulary              | 32,000                   |
| Tokenizer               | Custom BPE               |
| Transformer layers      | 6                        |
| Hidden dimension        | 384                      |
| Attention heads         | 6                        |
| Feed-forward dimension  | 1,536                    |
| Maximum sequence length | 256 tokens               |

## Project Pipeline

1. **Data Preparation** — Collected and cleaned Tamil text.
2. **Tokenization** — Trained a custom 32K BPE tokenizer.
3. **Pretraining** — Trained a custom Transformer using causal language modeling.
4. **Supervised Fine-Tuning** — Fine-tuned the pretrained checkpoint using Tamil conversation examples.
5. **Evaluation** — Tested generated responses and examined model limitations.

## Dataset

The pretraining dataset consisted of approximately:

* 100,000 Tamil documents
* 58 million tokens
* 90% training split
* 10% validation split

The original pretraining corpus is not included in this repository.

## Training Results

### Pretraining

The best completed pretraining checkpoint achieved a validation loss of approximately **5.13**.

The fourth epoch was interrupted by a Google Colab runtime disconnection. The best completed checkpoint was retained.

### Supervised Fine-Tuning

The SFT experiment used 20 Tamil conversation examples over 5 epochs.

| Configuration     | Value |
| ----------------- | ----: |
| Training examples |    20 |
| Batch size        |     4 |
| Learning rate     |  2e-5 |
| Epochs            |     5 |
| Optimizer         | AdamW |

**SFT training loss**

| Epoch |   Loss |
| ----: | -----: |
|     1 | 9.5971 |
|     2 | 7.7903 |
|     3 | 6.1306 |
|     4 | 4.4205 |
|     5 | 2.8685 |

## Model Weights & Tokenizer

The pretrained checkpoint, SFT checkpoint, tokenizer, and model configuration are hosted on Hugging Face.

**[View Tamil LLM on Hugging Face](https://huggingface.co/data-pageup/tamil-llm-23m)**

* `best_model.pt` — Best completed pretrained checkpoint
* `sft_model.pt` — SFT checkpoint
* `tamil_bpe_tokenizer.json` — Custom Tamil BPE tokenizer
* `config.json` — Model configuration

## Current Limitations

The current SFT model produces repetitive and incoherent text during generation. The decrease in training loss did not translate into coherent responses.

The experiment used a small SFT dataset and limited training resources. Further work is needed to improve data coverage, training, and evaluation.

## Future Work

* Expand the Tamil pretraining corpus.
* Increase the diversity and size of the SFT dataset.
* Experiment with additional training steps and model configurations.
* Evaluate generation quality using dedicated Tamil test sets.
* Improve inference and deployment.

## Tech Stack

* Python
* PyTorch
* Hugging Face Tokenizers
* Google Colab



## Disclaimer

This is an experimental learning and research project. The current model is not production-ready and should not be treated as a reliable general-purpose Tamil assistant.

## Author

**Amirtha Ganesh R**

GitHub: [Data-pageup](https://github.com/Data-pageup)

Hugging Face: [data-pageup/tamil-llm-23m](https://huggingface.co/data-pageup/tamil-llm-23m)

