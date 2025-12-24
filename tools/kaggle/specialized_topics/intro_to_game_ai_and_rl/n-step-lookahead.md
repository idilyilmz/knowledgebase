# (3) N-Step Lookahead

https://www.kaggle.com/code/alexisbcook/n-step-lookahead

## 1. Introduction
- one-step lookahead agents can still make bad moves because they only consider the immediate next turn
- some moves look good short-term but allow the opponent to win on their next move
- to fix this, the **minimax algorithm** lets the agent look several moves ahead and avoid dangerous choices

## 2. Minimax
- minimax explores the game tree deeper by alternating between:
    - agent moves (trying to maximize the score)
    - opponent moves (trying to minimize the agent’s score)
- the agent assumes the opponent plays optimally
- instead of choosing the move with the highest possible outcome, the agent chooses the move with the best worst-case outcome, reducing risk and avoiding traps
- with a depth of 3, the agent considers:
1. its current move
2. the opponent’s response
3. its next move

## 3. Heuristic
- the heuristic is extended to account for opponent wins:
    - +1,000,000 if the agent has four in a row (win)
    - +1 if the agent has three in a row with one empty space
    - −100 if the opponent has three in a row with one empty space
    - −10,000 if the opponent has four in a row (loss)
- this allows minimax to penalize moves that lead to immediate defeat.

## 4. Code
- the minimax agent:
    - simulates future moves recursively using the minimax function
    - stops searching when a terminal state (win, loss, draw) or depth limit is reached
    - uses the heuristic to evaluate board states
    - chooses the move that maximizes the minimum possible score
- the search depth is controlled by N_STEPS (higher values improve play but increase computation time)

## 5. Performance
- when tested against a random agent, the minimax agent:
    - wins **100% of games**
    - makes no invalid moves
- **key takeaway**: Looking multiple steps ahead and assuming an optimal opponent leads to dramatically stronger gameplay than one-step lookahead.
