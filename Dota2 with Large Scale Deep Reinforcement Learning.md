## Dota 2 with Large Scale Deep Reinforcement Learning

##### OpenAI, https://arxiv.org/pdf/1912.06680.pdf

### Introduction
- real-world 문제에 대한 도전은 AI 분야의 오랜 목표
- Backgammon, Chess, Atari, Go 등의 게임을 Reinforcement Learning을 통해 해결
- 본 논문에서는 longtime horizon, partially observation, high dimensionality observation and action 환경인 Dota 2를 Reinfocement 를 통해 해결하고자 함
- Dota 2 agent인 OpenAI Five는 Dota 2 world champion 인 OG team에 패배했고, 이후 community에 대전 가능하도록 공개하여 7000 게임에서 99.4% 승률 달성
- OpenAI Five 개발 동안 계속해서 코드와 환경이 변했기 때문에 surgery라고 불리는 최소한의 loss로 훈련을 계속 지속할 수 있는 방식 제안

### Dota 2
#### Long time horizons
- Dota 2는 30Hz로 거의 45분간 진행
- OpenAI Five는 4 frame 마다 action을 선택하기 때문에 20,000 정도의 step 진행 (Chess: 80 step, Go: 150 step)
  
#### Partially-observed state
- 각 팀은 unit이나 건물 근처의 일부만 game state로 볼 수 있음
  
#### High-dimensional action and observation state
- Dota 2는 10 heroes, 12 buildings, 12 non-player units, game features(runes, trees, wards, ...) 들 때문에 최대 16,000개의 observation space 존재
- action space 또한 8,000 ~ 80,000 정도로 Chess의 경우 1,000, Go의 경우 6,000 action space

#### limitations from regular game
- OpenAI Five는 117개 영웅 중 17개 활용
- 

### Training System
#### Playing Dota using AI
#### Optimizing the Policy
#### Continual Transfer via Surgery

### Experiments and Evaluation
#### Human Evaluation
#### Validating Surgery with Rerun
#### Batch Size
#### Data Quality
#### Long term credit assignment

### Related Work

### Conclusion