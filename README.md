<div align="center">

<h1> SparseVLM: Visual Token Sparsification for Efficient Vision-Language Model Inference </h1>

<h5 align="center"> 

[Yuan Zhang](https://gumpest.github.io/)<sup>1</sup>,
[Chun-Kai Fan](https://scholar.google.com/citations?user=TxeAbWkAAAAJ&hl=en&oi=ao)<sup>1</sup>,
[Junpeng Ma]()<sup>2</sup>,
[Wenzhao Zheng](https://wzzheng.net/)<sup>3</sup>,
[Tao Huang](https://taohuang.info/)<sup>4</sup>,
[Kuan Cheng](https://cfcs.pku.edu.cn/people/faculty/kuancheng/index.htm)<sup>1</sup>,

[Denis Gudovskiy]()<sup>5</sup>,
[Tomoyuki Okuno]()<sup>5</sup>,
[Yohei Nakata]()<sup>5</sup>,
[Kurt Keutzer](http://people.eecs.berkeley.edu/~keutzer/)<sup>3</sup>,
[Shanghang Zhang](https://idm.pku.edu.cn/info/1017/1598.htm)<sup>1*✉️</sup>

<sup>1</sup>School of Computer Science, Peking University, <sup>2</sup>Fudan University,

<sup>3</sup>UC Berkeley, <sup>4</sup>The University of Sydney, <sup>5</sup>Panasonic Holdings Corporation

</h5>
</div>

## 📜 News 
🔥 **[2024/10/15]** We relased **SparseVLM**! The code is now open source!


<p align='center'>
<img src='./assests/archi.png' alt='mask' width='700px'>
</p>

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
git clone https://github.com/Gumpest/SparseVLMs.git
cd SparseVLMs
```

2. Install necessary package
```Shell
conda create -n SparseVLMs python=3.10 -y
conda activate SparseVLMs
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

## Citation

If you use SparseVLM in your research, please cite our work by using the following BibTeX entry:
```bibtex
@article{zhang2024sparse,
  title={SparseVLM: Visual Token Sparsification for Efficient Vision-Language Model Inference},
  author={Zhang, Yuan and Fan, Chun-Kai and and Ma, Junpeng and Huang, Tao and Cheng, Kuan and Zhang, Shanghang},
  journal={arXiv preprint arXiv:24010.08156},
  year={2024}
}

```
## Acknowledgment

We extend our gratitude to the open-source efforts of [LLaVA](https://github.com/haotian-liu/LLaVA), [MiniGemini](https://github.com/dvlab-research/MGM) and [VideoLLaVA](https://github.com/PKU-YuanGroup/Video-LLaVA).