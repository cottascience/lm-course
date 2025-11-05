# Language Models Course

A simple, mini hands-on course on language models. Learn by doing.

## Quick Start (Local Setup)
```bash
# Install UV
curl -LsSf https://astral.sh/uv/install.sh | sh
# Clone and setup
git clone https://github.com/yourusername/lm-course.git
cd ttlm
uv sync
# Start learning
uv run python -m scripts.pretrain --experiment=default # (or any other experiment, like default_cpu for cpu only job)
```

## Quick Start (Google Colab)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cottascience/lm-course/blob/master/ttlm/notebook.ipynb)

## A workflow for ssh in Google Colab

(You only need to do 1-3 once)
1. Fork this repository to your own account.
2. Clone it locally to your computer so you can edit as you wish, then push your changes to your fork.
3. Run scripts/launch_colab.sh to set up your ssh config for colab (works only for MacOS with homebrew).
4. Open a new notebook on colab and start a new runtime (GPU or CPU, recommended GPU)
5. Run the following code in a cell (replace {your-username}, {your-name} and {your-email}):
```python
from google.colab import drive
import os
drive.mount('/content/drive')
work_dir = '/content/drive/MyDrive/colab-projects'
os.makedirs(work_dir, exist_ok=True)
os.chdir(work_dir)
if not os.path.exists('lm-course'):
    !git clone https://github.com/cottascience/lm-course.git
!ln -sf /content/drive/MyDrive/colab-projects/lm-course /root/lm-course
os.chdir('lm-course')
!git config --global user.email "your-email@example.com"
!git config --global user.name "Your Name"
!pip install colab-ssh
!chmod +x /content/cloudflared 2>/dev/null || true
!chmod +x ./cloudflared 2>/dev/null || true
!chmod +x ~/.cloudflared 2>/dev/null || true
!find /content -name "cloudflared" -exec chmod +x {} \; 2>/dev/null || true
from colab_ssh import launch_ssh_cloudflared
import getpass
password = getpass.getpass("Enter SSH password: ")
launch_ssh_cloudflared(password=password)
```
6. Now, you can use the SSH connection to run your own code. Edit locally, push to your fork, pull in the machine and run the code.

## Course Structure
```
lm-course/
├── notes/          # Lecturer's notes
└── ttlm/          # Code and utilities
```

## Lectures

A full manuscript with notes is being prepared. For now, you can find some slides that will support our discussion in [notes](notes/ttlm_support.pdf).

## Prerequisites

- Python/torch programming
- Basic linear algebra
- Some familiarity and previous experience with neural networks (helpful)

## Reading List
A (too short and biased) reading list, that can be helpful to get you started:

- Transformers:
  - [Attention is All You Need](https://arxiv.org/abs/1706.03762)
  - [Formal Algorithms for Transformers](https://arxiv.org/abs/2207.09238)
  - [Positional Encodings](https://karlstratos.com/notes/position_emb.pdf)
- Data and Pretraining Pipeline:
  - [DataComp-LM](https://proceedings.neurips.cc/paper_files/paper/2024/hash/19e4ea30dded58259665db375885e412-Abstract-Datasets_and_Benchmarks_Track.html)
  - [LLAMA-3](https://arxiv.org/abs/2407.21783)
- Post-training:
  - [RLHF](https://www.alignmentforum.org/posts/eoHbneGvqDu25Hasc/rl-with-kl-penalties-is-better-seen-as-bayesian-inference)
  - [LoRA](https://arxiv.org/abs/2106.09685)
  - [Inspiration to understand RL](https://proceedings.mlr.press/v15/ross11a)
- Inference and Deployment:
  - [KV cache](https://magazine.sebastianraschka.com/p/coding-the-kv-cache-in-llms)

## Side Quests

- Implement BPE and compare performance with character-level tokenizer;
- Implement KV cache and compare peformance with naive inference;
- Implement a simple RLHF tuning using LLM-generated preference dataset, e.g., make the model speak like a pirate;
- Implement a forward pass with flash attention for the model.

## License

MIT License - use freely!

---
