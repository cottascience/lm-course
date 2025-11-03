# Language Models Course

A simple, hands-on course on language models. Learn by doing.

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

## A workflow for Google Colab

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
    !git clone https://github.com/{your-username}/lm-course.git
os.chdir('lm-course')
!git config --global user.email "{your-email}@example.com"
!git config --global user.name "{your-name}"
!pip install colab-ssh
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

## License

MIT License - use freely!

---
