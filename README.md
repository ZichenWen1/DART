<div align="center">
  <h1 style="display: inline-block; margin: 0;">🚀Stop Looking for Important Tokens in Multimodal Language Models: Duplication Matters More</h1>
</div>

<h4 align="center"> 

[Zichen Wen](https://scholar.google.com/citations?user=N-aPFvEAAAAJ&hl=zh-CN)<sup>1,2</sup>,
Yifeng Gao<sup>1</sup>,
[Shaobo Wang](https://gszfwsb.github.io/)<sup>1</sup>,
[Junyuan Zhang](https://scholar.google.com/citations?user=uwwqEg8AAAAJ&hl=en)<sup>2</sup>,
Qintong Zhang<sup>2,4</sup>, <br>
[Weijia Li](https://liweijia.github.io/)<sup>3,2</sup>,
[Conghui He](https://conghui.github.io/)<sup>2✉</sup>,
[Linfeng Zhang](http://www.zhanglinfeng.tech/)<sup>1✉</sup>,


<sup>1</sup>Shanghai Jiao Tong University, <sup>2</sup>Shanghai AI Laboratory, <br>
<sup>3</sup>Sun Yat-sen University, <sup>4</sup>Peking University

</h4>

<div align="center">

[![arXiv](https://img.shields.io/badge/Arxiv-2502.11494-AD1C18.svg?logo=arXiv)](https://arxiv.org/pdf/2502.11494)
[![](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FZichenWen1%2FDART&count_bg=%23C25AE6&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=Visitor&edge_flat=false)](https://hits.seeyoufarm.com)
[![GitHub issues](https://img.shields.io/github/issues/ZichenWen1/DART?color=critical&label=Issues)](https://github.com/ZichenWen1/DART/issues)
[![GitHub Stars](https://img.shields.io/github/stars/ZichenWen1/DART?style=social)](https://github.com/ZichenWen1/DART/stargazers)
</div>

## 🔥 News
* **`2025.10.13`** 🤗🤗 We have released our latest work [EPIC](https://zichenwen1.github.io/EPIC/), an efficient framework for progressive consistency distillation in multimodal large language models!
* **`2025.10.10`** 🤗🤗 We've released our latest work, [VTC-Bench](https://arxiv.org/pdf/2510.07143). Come test whether your token compression method really works!
* **`2025.08.30`** 🤗🤗 We have seamlessly integrated DART into [Qwen2.5-VL](https://github.com/ZichenWen1/DART/tree/main/Qwen2_5-VL).
* **`2025.08.21`** 🤗🤗 Our DART is accepted at EMNLP'25 main!
* **`2025.05.15`** 🤗🤗 Our analytical [work](https://aclanthology.org/2025.findings-acl.802.pdf) on token compression has been accepted as ACL'25 Finding!
* **`2025.03.19`** 🤗🤗 The implementation and [evaluation scripts](https://github.com/ZichenWen1/DART/tree/main/scripts/v1_6/eval) for LLaVA-Next are now available
* **`2025.03.18`** 🤗🤗 We have released the implementation of DART for Qwen2-VL, and now you can easily evaluate it using [lmms-eval](https://github.com/EvolvingLMMs-Lab/lmms-eval)!
* **`2025.02.22`** 🤗🤗 We release our latest work [DART](https://arxiv.org/pdf/2502.11494), a plug-and-play, training-free token reduction method that seamlessly integrates with efficient attention operators. [Code](https://github.com/ZichenWen1/DART) is available!

## 👀 Overview
<p align='center'>
<img src='https://github.com/ZichenWen1/DART/blob/main/images/overview.png' alt='mask' width='1000px'>
</p>

> **TLDR:** We propose DART (Duplication-Aware Reduction of Tokens), a training-free method that prunes vision tokens based on duplication, achieving 88.9% token reduction and 1.99
 speed-up while maintaining performance and compatibility with efficient attention operators.

## 🛠 Preparation
### LLaVA
1. Clone this repository.

```bash
git clone https://github.com/ZichenWen1/DART
cd DART
```

2. Environment Setup and Preparation

```Shell
 conda create -n DART python=3.10 -y
 conda activate DART
 pip install -e .
 pip install flash-attn --no-build-isolation
```

3. Download Multimodal Benchmark

Please follow the detailed instruction in [LLaVA-Evaluation](https://github.com/haotian-liu/LLaVA/blob/main/docs/Evaluation.md).

### Qwen2-VL
```bash
 conda create -n DART_Qwen2VL python=3.10 -y
 conda activate DART_Qwen2VL
 cd Qwen2-VL/transformers && pip install -e .
 pip install accelerate qwen-vl-utils[decord]
 pip install flash-attn --no-build-isolation
 cd ../../lmms-eval && pip install -e .
```

### Qwen2.5-VL
```bash
pip install -U transformers==4.55.4
```


## 🎯 Usage
### LLaVA
### 📖 Script Templates
```shell
bash scripts/v1_5/eval/[Benchmark].sh [Reduction_Ratio] [Max_Num_Trunction]
```

### 🐝 Examples
```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/textvqa.sh 0.778 128
```

```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/pope.sh 0.778 128
```

```Shell
CUDA_VISIBLE_DEVICES=0 bash scripts/v1_5/eval/mme.sh 0.778 128
```

### Qwen2-VL
### 🐝 Examples
```bash
cd Qwen2-VL
bash eval_scripts/lmms_eval.sh True [Reduction_Ratio]
```

### Qwen2.5-VL
### 🐝 Examples
```bash
cd Qwen2_5-VL
bash eval_scripts/lmms_eval.sh True [Reduction_Ratio]
```


## 🔑 License

This project is released under the [Apache 2.0 license](LICENSE).

## 📌 Citation

Please consider citing our paper in your publications, if our findings help your research.
```bibtex
@article{wen2025stop,
  title={Stop Looking for Important Tokens in Multimodal Language Models: Duplication Matters More},
  author={Wen, Zichen and Gao, Yifeng and Wang, Shaobo and Zhang, Junyuan and Zhang, Qintong and Li, Weijia and He, Conghui and Zhang, Linfeng},
  journal={arXiv preprint arXiv:2502.11494},
  year={2025}
}

@article{wen2025token,
  title={Token Pruning in Multimodal Large Language Models: Are We Solving the Right Problem?},
  author={Wen, Zichen and Gao, Yifeng and Li, Weijia and He, Conghui and Zhang, Linfeng},
  journal={arXiv preprint arXiv:2502.11501},
  year={2025}
}
```


## 👍 Acknowledgment
We extend our gratitude to the open-source efforts of [LLaVA](https://github.com/haotian-liu/LLaVA), [Qwen2-VL](https://github.com/QwenLM/Qwen2-VL), and [lmms-eval](https://github.com/EvolvingLMMs-Lab/lmms-eval).



## 📩 Contact
For any questions about our paper or code, please email `zichen.wen@outlook.com`.

