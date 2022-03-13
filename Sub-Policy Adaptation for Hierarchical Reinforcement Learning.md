
## Sub-Policy Adaptation for Hierarchical Reinforcement Learning

##### UC Berkeley, https://arxiv.org/pdf/1706.05296.pdf

### Introduction
- Reinforcement Learning 분야는 Go나 Pong과 같은 game, automating robotic locomotion, dexterous manipulation 등 다양한 분야에 적용
- Hierarchical reinforcement learning은 Reinforcement Learning에서 모듈 간 추상화와 재사용 등에 대한 한계를 극복하기 위한 하나의 방법
- 본 논문에서는 temporal hierarchies에 지속적으로 적용 가능한 framework 제시 및 효과적인 hierarchical policy gradient 근사 식 유도
- manager와 sub-policy 간 decoupling 을 보여주고 sub-policy의 특정 baseline 제시하며 stable gradient 식인 HiPPO(Hierarchical Proximal Policy Optimization) 알고리즘 제시

### Preliminaries

### Related Work

### Efficient Hierarchical Policy Gradients
#### Approximate Hierarchical Policy Gradient
#### Unbiased Sub-Policy Baseline
#### Hierarchical Proximal Policy Optimization
#### Varying Time-Commitment

### Experiments
#### Tasks
#### Learning From Scratch and Time-Commitment
#### Comparison to Other Methods
#### Robustness to Dynamics Perturbations
#### Skill Diversity Assumption

### Conclusions and Future work