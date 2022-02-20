## Dota 2 with Large Scale Deep Reinforcement Learning

##### OpenAI, https://arxiv.org/pdf/1912.06680.pdf

### Introduction
- real-world 문제에 대한 도전은 AI 분야의 오랜 목표
- Backgammon, Chess, Atari, Go 등의 게임을 Reinforcement Learning을 통해 해결
- 본 논문에서는 longtime horizon, partially observation, high dimensionality observation and action 환경인 Dota 2를 Reinfocement 를 통해 해결하고자 함
- Dota 2 agent인 OpenAI Five는 Dota 2 world champion 인 OG team에 패배했고, 이후 community에 대전 가능하도록 공개하여 7000 게임에서 99.4% 승률 달성
- OpenAI Five 개발 동안 계속해서 코드와 환경이 변했기 때문에 surgery라고 불리는 최소한의 loss로 훈련을 계속 지속할 수 있는 방식 제안

### Dota 2
- Long time horizons
  - Dota 2는 30Hz로 거의 45분간 진행
  - OpenAI Five는 4 frame 마다 action을 선택하기 때문에 20,000 정도의 step 진행 (Chess: 80 step, Go: 150 step)
  
- Partially-observed state
  - 각 팀은 unit이나 건물 근처의 일부만 game state로 볼 수 있음
  
- High-dimensional action and observation state
  - Dota 2는 10 heroes, 12 buildings, 12 non-player units, game features(runes, trees, wards, ...) 들 때문에 최대 16,000개의 observation space 존재
  - action space 또한 8,000 ~ 80,000 정도로 Chess의 경우 1,000, Go의 경우 6,000 action space

- limitations from regular game
  - OpenAI Five는 117개 영웅 중 17개 활용
  - player가 일시적으로 동시에 multiple unit을 컨트롤하는 아이템 제외

### Training System
#### Playing Dota using AI
- OpenAI Five는 4 frame 마다 movement, attack 등으로 embedding 된 discrete action 결정
- item이나 ability 구매, courier unit 컨트롤과 같은 부분은 hand-script logic으로 처리
- policy는 action probability distribution을 결정하도록 설계하고 4096-unit LSTM을 활용해서 총 159 million parameter 학습
- ![Simplified OpenAI Five Model Architecture](paper_images/Dota2_image1.PNG)
- pixel on the screen을 observation으로 활용하는 대신 set of data arrays를 활용
- 이렇게 하는 이유는 두 가지 이유가 있는데
  - 첫 번째로 visual processing 에 집중하는 대신 strategic planning and high-level decision making에 대한 연구에 집중하기 위함
  - 두 번째로 모든 training game에서 각 frame을 rendering 하는 것이 불가능에 가까움
  
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