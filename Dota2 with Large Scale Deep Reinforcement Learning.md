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
- human experts에 대항하기 위한 policy를 찾는 것이 목적
- 처음에는 캐릭터 사망, 자원 습득 등에 대한 reward function을 최대화 하는것을 연습하고 zero sum game을 감안해 적 팀의 reward 점수를 빼는 것 적용
- policy는 Proximal Policy Optimization 사용
- optimization으로 Generalized Advantage Estimation 사용
- 학습 네트워크는 중앙에 LSTM을 두고 policy, value로 갈라지게끔 구성 
- ![System Overview](paper_images/Dota2_image2.PNG)
- 학습 시스템은 다음과 같고 Dota2 self-play 3experience를 활용하여 학습 수행
- 중앙의 GPU는 비동기적으로 experience buffer를 저장하고 NCCL2를 통해 동기적으로 parameter gradient update
- total batch size는 1 step 당 300만개이며 Adam Optimizer 활용
- Rollout worker는 self-play game을 real-time 2배 가속으로 구동
- self-play policy 적용 전략은 최신 policy로 전체의 80% 게임을 구동하고 20%는 old policy로 구동
  
#### Continual Transfer via Surgery
- 프로젝트 진행 도중, code 나 environment가 3가지 이유로 지속적으로 변화됨
  1. 학습과 실험 중에 reward structure, observation, policy network 변경 등 학습 process를 변경시킬 일 발생 
  2. 시간이 지남에 따라 agent의 action, observation space를 확장시킬 일이 발생
  3. 시시 각각 Dota 2 game의 영웅, 아이템, 지도 등에 대한 업데이트 발생
- 본 논문에서는 surgery라고 하는 새로운 환경에서 old policy를 통해 다른 크기와 의미를 가진 new policy로 성능이 저하되지 않도록 이식하는 offline operation 제안
- 이는 Net2Net-style의 transformation이며, 본 논문에서 10달 간 학습 동안 성능저하 없이 20번 이상의 surgery 수행
  
### Experiments and Evaluation
#### Human Evaluation
#### Validating Surgery with Rerun
#### Batch Size
#### Data Quality
#### Long term credit assignment

### Related Work

### Conclusion