# When Do Visual Tokens Become Dispensable?

### A Symmetric Causal Analysis of Visual Information Absorption in Vision-Language Models

[![Status](https://img.shields.io/badge/Status-Under%20Review-lightgrey)](#news)
![Visitors](https://visitor-badge.laobi.icu/badge?page_id=Kai-Liu001.TokenAbsorption)
![Stars](https://img.shields.io/github/stars/Kai-Liu001/TokenAbsorption?style=social)

[project](https://kai-liu001.github.io/TokenAbsorption/) |
[arXiv](#) 
<!-- [supplementary material](#) | -->

**Authors:** [Kai Liu](https://kai-liu.cn/), [Anqi Li](https://github.com/starrywiki), [Ziqing Zhang](https://github.com/sjtuzzq), Zhixin Wang, Zhikai Chen, Renjing Pei, [Yulun Zhang](https://yulunzhang.com/)  


### 🔥🔥🔥 News

- **2026-05-09:** The report is released.

### Abstract
> Vision-Language Models (VLMs) process hundreds of visual tokens alongside text, yet it remains unclear *when* these tokens stop contributing useful information during the forward pass. We introduce a **symmetric interventional framework** of matched visual- and text-side zero-out, complemented by activation patching and a controlled projector swap as strict causal tests, to measure visual information absorption: the migration of visual content from visual tokens into the text residual stream. Across **seven VLMs** (linear, MLP, pixel-shuffle, and cross-attention projectors) and five benchmarks, we find that (i) visual information accumulates in text hidden states with absorption depth $\sim50\%$ on concept tasks and $\sim75\%$ on OCR and open-ended captioning, (ii) text-side zero-out recovers 2-8 layers *later* than visual-side, revealing layered absorption, (iii) projector design modulates spatial heterogeneity: tiled/pixel-shuffle projectors leave $75\%$ of visual tokens dispensable from layer 0, while simpler MLP/linear projectors smear content uniformly, and (iv) absorption depth scales monotonically with the compression ratio. A within-family Bunny projector swap further establishes that absorption is itself a design choice: the $S^2$-Wrapper variant matches task accuracy by routing visual content through attention read-out at the answer position rather than the text residual. The symmetric design exposes dynamics that single-sided ablations miss.
## 💡 Highlights
![Figure 1: Teaser](assets/fig1_teaser.png)
> TLDR: Visual information in InternVL-8B is progressively absorbed from visual tokens into text residual states. Text-to-vision attention collapses after early layers, while text-probe accuracy saturates near the final layers, indicating a transition from **reading** to **digesting** and finally to **absorbed**, where many visual tokens become dispensable.

## 📖 Methodology
![Figure 2: Methodology](assets/fig2_method.png)
> TLDR: TokenAbsorption measures when and where visual information is stored by applying matched visual- and text-side probes/interventions across LLM layers. The pipeline feeds image-text inputs through the vision encoder, projector, and LLM decoder, then uses layer-wise attention ranking, text/visual probes, and visual-state replacement to estimate absorption depth and test causal dependence.

## Key Findings

- **Finding 1**: Visual information concentrates in text residual
- **Finding 2**: Absorption depth is task-dependent
- **Finding 3**: Asymmetric recovery reveals layered absorption
- **Finding 4**: Projector complexity modulates spatial absorption heterogeneity
- **Finding 5**: Compression ratio scales monotonically with absorption depth

## 📎 Citation

If you find this work useful, please cite:

```bibtex
@article{liu2026tokenabsorption,
  title     = {When Do Visual Tokens Become Dispensable? A Symmetric Causal Analysis of Visual Information Absorption in Vision-Language Models},
  author    = {Liu, Kai and Li, Anqi and Zhang, Ziqing and Wang, Zhixin and Chen, Zhikai and  Pei, Renjing and Zhang, Yulun},
  journal = {arxiv},
  year      = {2026}
}
```

## 🔑 License

This project is released under the [Apache License 2.0](LICENSE).

## 👍 Acknowledgements
We thank the open-source VLM community, especially InternVL, LLaVA, Qwen2.5-VL, Phi-3.5-Vision, SmolVLM2, and Bunny, for accessible model releases. We also thank the maintainers of ScienceQA, POPE, TextVQA, MMBench, and SEED-Bench, which make systematic visual information absorption analysis possible.
