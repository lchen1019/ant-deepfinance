<div align="center">

# AntDT-DeepFinance-300K

<div>
A Large-Scale Financial Dataset via Systematic Chain-of-Thought Synthesis Optimization
</div>

</div>


<div align="center">

[![Data](https://img.shields.io/badge/Data-4d5eff?style=for-the-badge&logo=huggingface&logoColor=ffffff&labelColor)](https://huggingface.co/datasets/zwhe99/DeepMath-103K)
[![Model](https://img.shields.io/badge/Model-4d5eff?style=for-the-badge&logo=huggingface&logoColor=ffffff&labelColor)](https://huggingface.co/collections/zwhe99/deepmath-6816e139b7f467f21a459a9a)
[![Github](https://img.shields.io/badge/Code-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/zwhe99/DeepMath)
[![GitHub Stars](https://img.shields.io/github/stars/zwhe99/DeepMath?style=for-the-badge&logo=github&logoColor=white&label=Stars&color=000000)](https://github.com/zwhe99/DeepMath)
[![arXiv](https://img.shields.io/badge/arXiv-2504.11456-b31b1b.svg?style=for-the-badge)](https://arxiv.org/abs/2504.11456)
</div>

中文 ｜ 英文

## :fire: ​最新动态

- **2025.7.11** AntDT-DeepFinance-300K的技术报告《AntDT-DeepFinance-300K: A Large-Scale Financial Dataset via
  Systematic Chain-of-Thought Synthesis Optimization》已发布。
- **2025.7.11**  AntDT-DeepFinance-300K的数据已经开源，其中15K的安全合规数据因存在风险无法开源。

## :book: 简介

![简介](assets/intro.png)

从通用的推理模型中提炼高质量金融思维链 (CoT) ，为构建金融推理模型提供了一条高效且可行的途径。然而，现有的 CoT 合成方法只是进行简单的浅层采样，导致如何构建一个高质量的金融推理知识空间尚未得到深入研究。为了构建高质量推理数据，我们进行了系统性的CoT合成优化，从三个角度对上述问题进行解决：

**（1）全面的 CoT 合成框架**：我们的流程引入多视角知识提取 (MKE) 和自反思重写 (SCR) ，以生成详尽而深入的金融推理轨迹。

**（2）“CoT Cube”系统性研究**：旨在分析影响 CoT 有效性的关键因素，例如必要性、长度和合成器，从而为构建高质量的金融 CoT 提供指导。

**（3）来源于真实世界的查询：**为了填补与真实世界用户交互的差距，我们还系统地整理了大量内部专有金融查询。这些查询经过了隐私保护转换，并由领域专家进行注释，以反映真实世界中需要的金融能力。

基于上面的合成优化，我们公开发布 AntDT-DeepFinance，以推动金融推理模型研究。

## :rocket: 全面的CoT合成框架

![全面的CoT合成流程](assets/framework.png)

**1. 多方面知识提取：**该方法旨在实现详尽而全面的金融推理知识建模，

- `Q2A (Direct Curation)`直接从种子语料库中获取结构良好的问答对
- `A2Q (Counterfactual Augmentation)` 通过反事实扰动增强关键知识点的因果连通性
- `T2Q (CoT Knowledge Mining)` 挖掘思维链中隐含的推理依赖

**2. 自反思改写：**为确保数据集的整体准确性，现有方法中的一种常见做法是丢弃缺乏正确采样答案的 QA 对。然而，这些被丢弃的 QA 对通常涉及复杂的推理过程，可以作为提升模型能力的宝贵资源。自反思改写则是将有缺陷的推理轨迹通过适当的纠正机制转化为正确的训练语料。

## 🛠️ “CoT Cube”系统性研究

**CoT必要性实验**：无论任务类型和难度如何，加入 CoT 都能持续提高模型性能，特别是在复杂的推理任务和难题中。

![不同任务类型是否需要CoT](https://intranetproxy.alipay.com/skylark/lark/0/2025/png/167556596/1752132190863-d775c9fb-83dc-4006-b3bd-13d613a8ead1.png)

![不同难度题目是否需要CoT](https://intranetproxy.alipay.com/skylark/lark/0/2025/png/167556596/1752132199619-ba645846-3b8e-4f50-903c-4d1d3485187a.png)

**CoT合成器实验**：推理模型作为 CoT 合成器的有效性并不总是与其内在的推理性能相一致。在我们的实验中，蒸馏QwQ-Plus获得的CoT质量超过蒸馏DeepSeek-R1的。

![CoT合成器实验](https://intranetproxy.alipay.com/skylark/lark/0/2025/png/167556596/1752132297916-0000e9bb-ac8d-4543-84a3-8ae17ef9cfa2.png)

**CoT长度实验**：提炼精简的CoT 可以让训练模型输出更简洁的响应，但也会损害推理能力。金融推理模型需要长 CoT。

![CoT长度实验](https://intranetproxy.alipay.com/skylark/lark/0/2025/png/167556596/1752132438448-9d2fbf1b-c886-4ed3-bc2f-26172c844df5.png)

## 🙏 致谢

This work can not be done without the help of the following works:

- **[verl](https://github.com/volcengine/verl)**: A very fast reinforcement learning framework.
- **[Vivacem/MMIQC](https://huggingface.co/datasets/Vivacem/MMIQC)**: A mixture of question-response pairs extracted from Mathematics Stack Exchange pages.
- **[TIGER-Lab/WebInstructSub](https://huggingface.co/datasets/TIGER-Lab/WebInstructSub)**: Instruction data from MathStackExchange and ScienceStackExchange.
- **[AI-MO/NuminaMath-CoT](https://huggingface.co/datasets/AI-MO/NuminaMath-CoT)**: Approximately 860k math problems.

## 📚 引用

```
@article{deepmath,
  title={DeepMath-103K: A Large-Scale, Challenging, Decontaminated, and  Verifiable Mathematical Dataset for Advancing Reasoning},
  author={He, Zhiwei and Liang, Tian and Xu, Jiahao and Liu, Qiuzhi and Chen, Xingyu and Wang, Yue and Song, Linfeng and Yu, Dian and Liang, Zhenwen and Wang, Wenxuan and Zhang, Zhuosheng and Wang, Rui and Tu, Zhaopeng and Mi, Haitao and Yu, Dong},
  year={2025},
  eprint={2504.11456},
  archivePrefix={arXiv},
  primaryClass={cs.CL},
  url={https://arxiv.org/abs/2504.11456}, 
}
```

## 🤝 联系我们

非常感谢您对通义点金系列的关注！如果您有兴趣向我们的研究团队或产品团队留言，欢迎通过我们的官方邮箱或者扫码加入钉群与我们联系：[CFLUE@alibabacloud.com](mailto:CFLUE@alibabacloud.com)。我们的团队将竭诚为您提供帮助和支持。

