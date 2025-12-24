# (1) Play the Game

https://www.kaggle.com/code/alexisbcook/play-the-game

## 1. Introduction
- Connect Four is a two-player game where players alternate dropping colored discs into a vertical grid
- the goal is to be the first to connect four discs in a row
- in this course, you build intelligent agents to play Connect Four, progressing from simple agents to advanced reinforcement learning–based strategies

## 2. Join the Competition
- you can test your agents against others by joining the Kaggle ConnectX competition
- to participate, you must join the competition and accept the rules, which define submission limits and other constraints

## 3. Getting Started
- the Kaggle ConnectX environment includes built-in agents such as:
    - **random**: selects a valid move uniformly at random
    - **negamax**: a stronger, traditional AI agent
- you create the environment using `make("connectx")` and can run games with `env.run()` and visualize them with `env.render()`

## 4. Defining Agents
- agents are Python functions that take `obs` and `config` as inputs and return a column index (0–6).
    - **obs** includes:
        - `obs.board`: the game board as a list (0 = empty, 1/2 = player discs)
        - `obs.mark`: the agent’s player number (1 or 2)
    - **config** includes:
        - `columns`, `rows`, and `inarow`
- example agents include:
    - a random valid-move agent
    - an agent that always chooses the middle column (can lose by making invalid moves)
    - an agent that chooses the leftmost valid column
- invalid moves immediately lose the game.

## 5. Evaluating Agents
- single games are unreliable, so agents are evaluated over many rounds using `evaluate()`
- each agent goes first about half the time
- results show:
    - the **leftmost valid column agent** performs better than the random agent
    - the **middle-column agent** often loses due to invalid moves
    - avoiding invalid actions is critical for good performance

**Key takeaway**: Even very simple, valid strategies can significantly outperform random play