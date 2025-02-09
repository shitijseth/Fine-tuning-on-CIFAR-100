# Fine-tuning-on-CIFAR-100
Fine-tuning a ResNet-18 using the GPT-2 tokenizer on the CIFAR-100 dataset

The code implements a multimodal fine‑tuning pipeline for a simplified LLaVA‑like model on the CIFAR‑100 dataset. Here’s a summary:

Model Architecture:
A pre‑trained ResNet‑18 is used as a vision encoder, whose output is projected to an embedding space. This is combined with text embeddings (using a GPT‑2 tokenizer) and passed through a small transformer decoder. A language modeling head then generates logits for text tokens.

Data Preparation:
CIFAR‑100 images are resized and normalized for the ResNet encoder. Each sample is formatted with a prompt (e.g., “Please classify the following image:”) and a target answer (e.g., “Answer: cat”). The input tokens are created by concatenating the prompt and target, with labels that ignore the prompt portion during loss computation.

Training & Evaluation:
The model is fine‑tuned with a cross‑entropy loss computed only over the target tokens. After training, the code evaluates the performance by performing greedy decoding on the test set and comparing the generated text against the expected target answers to compute the accuracy.

Saving:
Finally, the trained model and tokenizer are saved for future use.
