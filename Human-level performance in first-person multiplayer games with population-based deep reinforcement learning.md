## Human-level performance in first-person multiplayer games with population-based deep reinforcement learning

#### DeepMind, https://arxiv.org/pdf/1807.01281&hl=en&sa=X&d=15122523080710664267&scisig=AAGBfm3w_xBhB1LUjM_5wJ--G5MJuW5YSQ&nossl=1&oi=scholaralrt

### Introduction
- reinforcement learning은 복잡한 single-agent environment에서 좋은 성과를 거뒀지만, multiple agents가 포함 된 real-world에서는 도전적으로 남음
- 본 논문에서는 human-level의 3D multi player video game인 Quake 3 Area Capture the Flag에서 오직 pixel input만으로 RL 도입
- 실험 결과는 지능형 에이전트의 능력이 human-level intelligence에 확연히 가까워 졌음을 나타냄
- 본 논문은 복잡한 multi-agent 환경에서 새로운 agent의 지능적 행위 창발이 어떻게 일어나는지를 보임
![CTF task and computational training framework](paper_images/CTF_image1.PNG)
- 본 논문의 실험 환경은 modify 된 Quake 3 Area 환경인 Capture the Flag mode에서 진행
- partially observable한 multi-agent environments에서 다양한 agent population이 학습하기 때문에 학습 과정의 안정성 때문에 meta-optimisation 제안
- 이는 win/loss signal의 sparse한 delayed reward를 internal reward signal로 해결
- feature에 대해 multi-scale representation으로 long-term temporal reasoning 이 가능한 구조 제안

### Background

### Method

### Experiments

### Conclusions