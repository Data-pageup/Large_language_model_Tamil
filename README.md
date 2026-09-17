# Tamil LLM — 23M Parameters
**[View Tamil LLM on Hugging Face](https://huggingface.co/AG-dataScientist/tamil-llm-23m)**



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

The current model produces repetitive and incoherent text during generation. Although training loss decreased, this did not translate into coherent Tamil responses.

The model was trained on approximately 58 million tokens, with a limited pretraining duration, and fine-tuned using only 20 conversation examples over 5 epochs.

Further training and improvements to the dataset are required to improve generation quality.

## Future Work

* Expand the Tamil pretraining corpus with more high-quality text.
* Extend pretraining to **at least 20 epochs**.
* Increase the size and diversity of the Tamil SFT dataset.
* Experiment with additional SFT training and hyperparameter configurations.
* Evaluate generation quality using dedicated Tamil test sets.
* Improve inference and deployment.

## Disclaimer

This is an experimental Tamil language-model project. The current checkpoint is not production-ready and should not be considered a reliable general-purpose Tamil assistant. Further pretraining, expanded SFT data, and evaluation are planned.


## Author

**Amirtha Ganesh R**

GitHub: [Data-pageup](https://github.com/Data-pageup)

Hugging Face: [data-pageup/tamil-llm-23m](https://huggingface.co/data-pageup/tamil-llm-23m)

