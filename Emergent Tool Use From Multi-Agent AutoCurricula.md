## Emergent Tool Use From Multi-Agent Autocurricula

##### OpenAI, https://arxiv.org/pdf/1909.07528.pdf

### Introduction
- 물리세계에서 인간처럼 물체와 상호작용할 수 있는 에이전트를 만드는 하나의 접근 방법으로 강화학습이 있음
- 하지만, reward function을 명세하거나 trajectories를 모으는 비용이 비쌈
- 이를 해결하기 위해 비지도적인 exploration을 종용하는 intrinsic motivation 방법이 있음
- 하지만 이는 인간의 진화과정과 다름
- 본 논문에서는 hide-and-seek 게임을 하는 경쟁, 적대적 환경 소개 
- 에이전트는 오직 visibility-based reward function만 가지고 경쟁하며 에이전트의 의도에 따라 적합한 tool 사용 방법을 학습함
- 예를들어 hider는 seeker를 피해 여러개의 forts를 활용하여 바리케이트를 구성하고 seeker는 이에 따라 사다리를 이용해 바리케이트 안으로 점프함
- 이는 intrinsic motivation 방법보다 더 인간적으로 해석할 수 있는 행위 도출
- ![Emergent Skill PRogression From Multi-Agent Autocurricula](paper_images/hide-and-seek_image1.PNG)
- 본 논문의 메인 contribution은 다음과 같음
  1. 다양한 에이전트 전략 상황에서 multi-agent self-play가 autocurricula 창발
  2. 물리 기반 환경에서 multi-agent autocurricula는 tool 활용과 같은 인간적인 전략 유도
  3. 개방형 환경 뿐만 아니라 도메인에 적합한 타겟 지능 테스트를 위한 transfer 제안
  4. multi-agent autocurricula 학습을 위한 오픈 소스 기반 환경 배포

### Related Work
- multi-agent self-play에 대한 설명
- intrinsic motivation 방법에 대한 설명
  - count-based exploration : visit count를 세 안가본 곳으로 exploration
  - transition-based method : transition에 대한 예측 error를 통해 exploration
  - RL을 활용한 tool use 연구 설명
  
### Hide And Seek

### Policy Optimization

### Auto-Curricula And Emergent Behavior

### Evaluation

### Discussion and Future work