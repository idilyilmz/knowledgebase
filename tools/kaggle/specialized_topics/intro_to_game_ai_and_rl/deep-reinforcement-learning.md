# (4) Deep Reinforcement Learning

https://www.kaggle.com/code/alexisbcook/deep-reinforcement-learning

## 1. Introduction
- previous agents relied on hand-designed heuristics
- in this tutorial, heuristics are removed entirely and replaced with **reinforcement learning (RL)**, where the agent learns how to play by repeatedly playing games and improving based on experience

## 2. Neural Networks
- instead of scoring board states with a heuristic, the agent uses **a neural network**:

Input: the current Connect Four board

Output: a probability distribution over possible moves (columns)

The agent samples moves from these probabilities. Learning consists of adjusting the network’s weights so better moves become more likely over time.

## 3. Setup
- after each move, the agent receives a reward:
    - +1 for winning the game
    - −10 for playing an invalid move
    - −1 if the opponent wins on their next move
    - +1/42 for any other valid move
- the agent’s goal is to maximize **cumulative reward** over a game
- this reward structure encourages winning, avoiding losses, and provides small intermediate feedback to help learning converge

## 4. Reinforcement Learning (RL)
- reinforcement learning algorithms (e.g., PPO, DQN, A2C):
    - start with random neural network weights
    - play many games and experiment with different actions
    - adjust weights based on observed rewards
    - gradually improve the policy (move-selection strategy)
- this tutorial uses **Proximal Policy Optimization (PPO)**, an actor-critic algorithm

## 5. Code 
- key implementation steps:
    - wrap Connect Four as an **OpenAI Gym environment**
    - customize rewards to match the designed reward system
    - use a **convolutional neural network (CNN)** to process the board
    - train the agent with PPO using Stable-Baselines3
    - export the trained model as a competition-ready agent
- the agent is trained specifically against a **random opponent**

## 6. Performance and Limitations
- after training:
    - the RL agent wins about **68% of games** against a random agent
    - it makes no invalid moves
- however, performance is limited because the agent only trained against one type of opponent. To improve further, techniques like **self-play** are needed.

## 7. Key Takeaway
- reinforcement learning allows agents to learn strategies automatically from experience, without handcrafted heuristics, but requires extensive training and diverse opponents to reach strong performance