
## Sub-Policy Adaptation for Hierarchical Reinforcement Learning

##### UC Berkeley, https://arxiv.org/pdf/1706.05296.pdf

### Introduction
- Reinforcement Learning 분야는 Go나 Pong과 같은 game, automating robotic locomotion, dexterous manipulation 등 다양한 분야에 적용
- Hierarchical reinforcement learning은 Reinforcement Learning에서 모듈 간 추상화와 재사용 등에 대한 한계를 극복하기 위한 하나의 방법
- 본 논문에서는 temporal hierarchies에 지속적으로 적용 가능한 framework 제시 및 효과적인 hierarchical policy gradient 근사 식 유도
- manager와 sub-policy 간 decoupling 을 보여주고 sub-policy의 특정 baseline 제시하며 stable gradient 식인 HiPPO(Hierarchical Proximal Policy Optimization) 알고리즘 제시

### Preliminaries
- 본 논문에서 discrete-time finite-horizon discounted Markov decision process 제안
- tuple은 다음과 같이 구성 ![HiPPO MDP](paper_images/HIPPO_image1.png)
- S는 state set, A는 action set, P : S X A X S -> R+ 인 transition probability distribution
- 감마는 discount factor, H는 horizon
- ![Temporal hierarchy studied in this paper](paper_images/HIPPO_image2.png)
- zt는 manager policy에 대한 pi_theta(zt | st) sample
- p라는 정적 시간 구간을 정하고 kp 부터 (k+1)p - 1 까지 구간에서 zkp에 따른 sub-policy pi_theta(at | st, zkp)를 통한 at sampling
- 본 논문에서는 hierarchical policy를 학습하고 얼마나 효율적으로 모든 레벨에서 이를 적용할 수 있는지 연구
- high-level policy(manager)와 low-level policy(sub-policy)가 존재하고 n sub-policy에 대해 선택할 수 있는 z = Zn에 중점을 둠

### Related Work
- 전통적인 HRL에 대한 설명과 최근에 continuous space 문제에 접근한 내용 언급
- Option framework에 대한 설명과 최근에 continuous space 문제에 접근한 내용 언급

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