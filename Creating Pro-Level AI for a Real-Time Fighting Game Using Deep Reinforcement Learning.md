## Creating Pro-Level AI for a Real-Time Fighting Game Using Deep Reinforcement Learning

### Introduction

강화학습은 Atari와 같은 PVE(player versus environment), Go나 Chess와 같은 PVP(player versus player) 와 같이 다양한 게임 장르로 확장되고 있으며, 최근에는 StarCraft2와 Quake3, Dota2와 같이 복잡한 비디오 게임의 PVP에 포커싱.
본 논문에서는 Blade & Soul(B&S) Arena Battle에서 최신 self-play 기반 강화학습을 통한 pro-level AI agents 개발.

- B&S Arena Battle
  - two player battle 시스템으로 two-player zero sum game
  - time step 별 144 개의 action space [8(avail skills) * 9(8 directional + no move) * 2(facing opponent or moving direction)]
  - skill 간 dependency 존재 (저항기와 no-op, no-op와 상태이상기, 상태이상기와 저항기 간)

### MDP Design

- 각 time step을 0.1초로 결정
- 여러 tick의 Observation을 LSTM 네트워크에 적용
- Observation
  - HP, SP
  - 적과의 거리
  - 벽 까지의 거리
  - 현재 위치
  - 잔여 게임 시간
  - 44 skill에 대한 잔여 cooldown
  - agent 의 상태(스턴, 그로기, 다운 등)
- Action
  - skill action (44 skill + no_op)
  - move or target action (4 move + no_op + 적과 반대방향 이동)
- Reward
  - Win reward + HP reward
  - HP reward = $(HP^{ag}_t + HP^{ag}_{t-1}) - (HP^{op}_t - HP^{op}_{t-1})$

### Self-Play Curriculum with Diverse Styles

- 다른 battle style에 대한 agent를 만들어 서로 대전하게 하는 self-play 기법 적용

- battle style을 aggressive, balanced, defensive로 나누고 해당 battle style에 대해 reward shaping 적용

  - |                  | Aggressive | Balanced | Defensive |
    | ---------------- | ---------- | -------- | --------- |
    | Time penalty     | 0.008      | 0.004    | 0.0       |
    | HP ratio         | 5:5        | 5:5      | 6:4       |
    | Distance Penalty | 0.002      | 0.0002   | 0.0       |

    ​