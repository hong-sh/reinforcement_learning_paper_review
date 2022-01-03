## Multi-Agent Actor-Ciritic for Mixed Cooperative-Competitive Environments (MADDPG)

##### OpenAI, https://arxiv.org/pdf/1706.02275.pdf

### Introduction

현재 강화학습은 game playing to robotics, data center와 같은 large scale systems 등 single agents 환경에서 성공을 거둠
하지만 multi-robot control, multiplayer games, discovery of communication and language 등의 multiple agent 간 interaction을 포함한 환경에 대한 강화학습 도입이 중요
본 논문에서는 범용 목적을 가진 multi-agent 강화학습 알고리즘 제안

- 실행 단계에서 오직 local information을 활용한 policy 학습 진행
- agent 간 통신을 위한 동적이거나 특정 구조를 가정하지 않는 모델
- cooperative interaction 뿐만 아니라 competitive 혹은 mixed interaction 까지 적용한 알고리즘
- Centralized training with decentralized execution(CTDE)를 차용
- 기본적으로 actor-critic 구조인데 critic의 경우 다른 agents 들의 policies 정보를 추가로 사용하고 actor의 경우 오직 local information 만 활용
- ensemble of policies를 통해 안정적으로 multi-agent의 policies에 대한 improve 방법 제시

### Related Work

- 

### Background

- Markov Games (MDP) 설명
- Q-Learning and Deep Q-Networks (DQN) 설명
- Policy Gradient (PG) Algorithms 설명
- Deterministic Policy Gradient (DPG) Algorithms 설명

### Methods

#### Multi-Agent Actor Critic

![Overview of our multi-agent decentralized actor, centralized critic approach](paper_images/MADDPG_image1.png)

- centralized training with decentralized execution의 구조를 가지고 있기 때문에 training 단계에서 policies를 학습 할 때 extra information 활용 가능
- Q-learning에서 training 과 test 단계에 다른 추가 information을 포함하는 것이 적절하지 않기 때문에 다른 agents의 policies information을 critic에 추가하여 actor-critic 구조를 간단하게 확장

![Object function](paper_images/MADDPG_image2.png)

- 목적함수는 다음과 같은 구조를 가짐
- $Q_i^\pi(x, a_1, ..., a_N)$ 은 모든 agents의 actions과 state x(x = o_1, ..., o_N)을 입력으로 가지는 centralized action-value function

![Object function](paper_images/MADDPG_image3.png)

- 이를 continuous 환경의 deterministic policy로 변환하면 다음과 같은 목적함수가 됨

#### Inferring Policies of Other Agents



### Experiments

- $\pi_{skill} , \pi_{move, target}, Q_{skill}, Q_{move, target}$ 을 학습하는 LSTM-based network 구성
- ACER(Actor-Critic with Experience Replay) 알고리즘 활용 
  - A3C(Asynchronous Advantage Actor-Critic)의 off-policy 버전
  - off-policy가 가능하기 위해 Importance sampling 기법 적용

### Conclusions and Future Work

- 인간과의 공정함을 위해 action 마다 평균 230ms의 delay를 줌
- Destroyer class 간 대전만 진행하고 skill set을 인간이 정한 것으로 맞추게끔 함

- 