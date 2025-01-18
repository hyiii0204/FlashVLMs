

## ✒️ Contents
- [News](#news)
- [Contents](#contents)
- [Overview](#overview)
- [Preparation](#preparation)
- [Usage](#usage)
- [Citation](#citation)
- [Acknowledgment](#acknowledgment)

## 👀 Overview

In vision-language models (VLMs), visual tokens usually consume a significant amount of computational overhead, despite their sparser information density compared to text tokens. To address this, existing methods extract more compact image representations by modifying the image encoder or projector. While some recent works further sparsify vision tokens during the decoding, they still ignore the guidance from the language tokens, which **contradicts the multimodality paradigm**. We argue that **visual tokens should be sparsified adaptively based on the question prompt**, as the model might focus on different parts (e.g., foreground or background) when dealing with various questions, as shown in Figure below. Unlike previous methods with text-agnostic visual sparsification (c) e.g., recent FastV, our SparseVLM (b) is guided by question prompts to select relevant visual patches.

<div align=center>
<img width="600" alt="image" src="./assests/moti.png">
</div>

## 👨‍💻 Preparation

1. Clone this repository and navigate to SparseVLMs folder
```bash
git clone https://github.com/hyiii0204/FlashVLMs.git
cd FlashVLMs
```

2. Install necessary package
```Shell
conda create -n FlashVLMs python=3.10 -y
conda activate FlashVLMs
pip install -e .
```

3. Download Multimodal Benchmark

Please follow the detailed instruction in [LLaVA-Evaluation](https://github.com/haotian-liu/LLaVA/blob/main/docs/Evaluation.md).

## 🎯 Usage
Specifically, `--sparse` in script indicates whether to perform sparseness, while `--scale` and `--bias` control the degree of token sparsity.

1. Example for evaluating MME results (192 tokens, scale = 13.5, bias = 0.0):
```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/mme.sh
```

2. Example for evaluating POPE results (128 tokens, scale = 9, bias = 6):
```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/pope.sh
```

3. Example for evaluating TextVQA results (64 tokens, scale = 0.8, bias = 0.0):
```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/textvqa.sh
```

## License

This project is released under the [Apache 2.0 license](LICENSE).

## Acknowledgment

We extend our gratitude to the open-source efforts of [TCFormer](https://github.com/zengwang430521/TCFormer), [LLaVA](https://github.com/haotian-liu/LLaVA), [MiniGemini](https://github.com/dvlab-research/MGM) and [VideoLLaVA](https://github.com/PKU-YuanGroup/Video-LLaVA).
