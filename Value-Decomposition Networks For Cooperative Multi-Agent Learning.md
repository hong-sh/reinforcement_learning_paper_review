## Value-Decomposition Networks For Cooperative Multi-Agent Learning

##### DeepMind, https://arxiv.org/pdf/1706.05296.pdf

### Introduction

- MARL을 풀기위한 방법으로 jointly optimize a single reward 등 활용
- Coordinated MARL 문제는 self-driving vehicles, traffic signals, transportation system, productivity of a factory 와 같은 문제에 적용
- 본 논문에서는 학습 대상 agents 중 특정 agent가 유용한 policy를 학습하고 있을 때, 다른 agents 의 policy를 통한 experiments가 이 agent에 대해서는 안좋은 방향의 explorartion이 될 수 있기 때문에 발생하는 "lazy" 현상에 대한 centralised approach의 비효과적인 policy 학습을 보여줌
- 대안적 접근으로는 independent learners를 학습시키는 방식이 있는데, 이것은 동적인 환경에서 불안정한 문제를 직면할 수 있음
- 본 논문에서는 개인 agents에 대한 additive value-decomposition 학습 방법 제안
- 이 value decomposition network는 team reward signal을 통한 optimal linear value decomposition을 위함

### Background

- 일반적인 Reinforcement Learning에 대한 설명
- Deep Q-Learning에 대한 설명
- Multi-Agent Reinforcement Learning에 대한 설명
  Joint reward를 활용하는 Dec-POMDP에 대한 설명

### A Deep-RL Architecture for Coop-MARL

### Experiments

### Conclusions

