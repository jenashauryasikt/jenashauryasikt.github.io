---
title: 'Reinforcement Learning for Scotland Yard: Strategies and Implementation'
summary: 'Mastering Scotland Yard with Reinforcement Learning: Deep Q-Networks and Monte Carlo Tree Search'
date: 2024-06-10
authors:
  - admin
tags:
  - Projects
image:
  caption:
---

Reinforcement Learning techniques like Deep Q-Networks and Monte Carlo Tree Search can improve the computer agent strategies in the Scotland Yard board game, improving user experience.

{{< toc mobile_only=true is_open=true >}}

### Introduction to Scotland Yard and Reinforcement Learning

Scotland Yard is a classic board game of strategy and deduction, where a group of detectives chase a secretive criminal, Mr. X, across a map of Old England. Using different modes of transportation, players must outsmart each other in this game of hide-and-seek. With the integration of Reinforcement Learning (RL) methods such as Deep Q-Networks (DQN) and Monte Carlo Tree Search (MCTS), we can significantly enhance the gameplay, particularly the strategies employed by Mr. X.

#### Game Rules

##### Setup
- Scotland Yard involves 2-5 detectives and one criminal, Mr. X.
- Players use taxis, buses, and the underground to move across 200 nodes on the map.
- Detectives win by landing on Mr. X’s location, while Mr. X wins by evading capture for 20 turns.

##### Information Asymmetry
- Mr. X’s location is hidden except at specific intervals.
- Detectives know the transportation modes used by Mr. X but not his exact location.

#### Game Design Challenges
- Asymmetry: The game is biased against Mr. X due to the limited turns and collective detective strategy.
- Partial Observability: Detectives operate with incomplete information, making standard RL algorithms less effective without modifications.

### Reinforcement Learning in Gameplay

#### Methodology

The two main policy optimization techniques used are Deep Q-Networks and Monte Carlo Tree Search. Feature vectors are engineered to include the locations of detectives, the modes of transport used by all players, and the nodes on the map to be used as data.

**Method:** Both Mr. X and detective agents are trained adversarially to improve each other’s strategies. This involves simulating games where each side employs its optimal policy, continuously refining through competition.

**Strategy:** Integrating DQN with MCTS combines the strengths of deep learning and tree search, optimizing decision-making processes.

#### Results

##### Baseline

Initial simulations with <mark>random</mark> moves set a baseline win rate for Mr. X at around <mark>9-10%</mark>.

##### Deep Q-Networks

Mr. X’s win rate increased to approximately <mark>50%</mark> after extensive training against <mark>random detective moves</mark>.

##### Monte Carlo Tree Search

MCTS-based strategies yielded a maximum win rate of over <mark>60%</mark> for Mr. X, highlighting its effectiveness in complex decision-making environments.

##### Combined Approach

The hybrid DQN + MCTS model showed promising results set to surpass just MCTS but required extensive training iterations to reach its full potential with smart detective agents trained adversarially.

#### Conclusion

Reinforcement Learning offers a robust framework for enhancing the strategies in Scotland Yard. By leveraging DQN and MCTS, we can develop intelligent agents capable of outperforming traditional human strategies. However, the computational demands and the need for extensive training iterations present challenges that need to be addressed in future work.

### Future Developments

- **Enhanced Computational Resources**, ensuring sufficient computational power to train models to their optimal performance levels.
- **Graph Neural Networks** to model game states more accurately.
- **Asynchronous Actor-Critic Models** for more stable learning.

The project report can be found [here](RL_ScotlandYard.pdf)