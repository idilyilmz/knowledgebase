# (2) One-Step Lookahead

https://www.kaggle.com/code/alexisbcook/one-step-lookahead

## 1. Introduction
- human players use intuition and foresight when playing Connect Four
- this tutorial shows how to encode that intuition into an agent using a heuristic, allowing the agent to make smarter decisions than random play

## 2. Game trees
- players mentally forecast future moves by considering how the opponent might respond
- this process can be represented as a **game tree**, which shows all possible move sequences
- because the full Connect Four game tree is enormous (over 4 trillion board states), agents only explore a small portion of it when choosing a move

## 3. Heuristics
- a **heuristic** is a function that assigns a score to a game board, estimating how favorable it is for the agent.
- example heuristic rules:
    - +1,000,000 points if the agent has four in a row (win)
    - +1 point if the agent has three in a row with one empty space
    - −100 points if the opponent has three in a row with one empty space

The agent:
1. simulates each valid move
2. scores the resulting board using the heuristic
3. chooses the move with the highest score

heuristics are imperfect but effective, and can be improved by testing and adjusting them when the agent makes poor moves

## 4. Code
- the **one-step lookahead agent**:
    - examines only the next move (not deeper levels of the game tree)
    - uses helper functions to simulate dropping a piece and scoring the board
    - counts winning patterns (“windows” of four) horizontally, vertically, and diagonally
    - selects randomly among moves with the highest heuristic score
- this agent dramatically outperforms a random agent, winning about **96% of games**, showing that even shallow lookahead combined with a good heuristic is very powerful