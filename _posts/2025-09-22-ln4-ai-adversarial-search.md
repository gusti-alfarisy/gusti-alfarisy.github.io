---
title: "Lecture Notes 4: Adversarial Search and Games"
date: 2025-09-22
background: "https://news.northeastern.edu/wp-content/uploads/2024/10/Game-AI-1400x933-1.jpg"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Artificial Intelligence, Agent, Adversarial Search]
comments: true
toc: true
---

When two or more agents pursue conflicting goals, a problem known as adversarial search arises. In this lecture, we will explore how agents operate in competitive environments, where each agent must reason about and respond to the actions of others to achieve its objective.

## Two-player zero-sum games

zero-sum games means that there is unlikely to have multiple winners which means that what is good for one entitiy is bad for the others. 

For agent in games the synonym for action and state are move and position respectively.

* $$S_0$$ is the initial state, the starting condition of a game
* TO-MOVE(s): player whose turn it is to move in state s
* ACTIONS(s): the set of legal moves in state s
* RESULT(s, a) is a transition model that defines the state resulting from taking action a in state s
* IS-TERMINAL(s) is a terminal test which is true when the game is over and false otherwise
* UTILITY(s, p) is a utility function (can be considered as objective function). This provide numerical value to player p when in terminate state s (the game ends). In case of chess the outcomes are win (1), loss (0), or draw (0.5)


## MINIMAX Search Algorithm

![A (partial) game tree for the game of tic-tac-toe](/assets/theme/images/posts/tictactoe_search.png)

![A two-ply game tree](/assets/theme/images/posts/two_ply_tree.png)

$$
\text{MINIMAX}(s) =
\begin{cases}
\text{UTILITY}(s, \text{MAX}), & \text{if IS-TERMINAL(s)} \\[6pt]
\max\limits_{a \in \text{ACTIONS}(s)} \text{MINIMAX}(\text{RESULT}(s,a)), & \text{if TO-MOVE}(s) = \text{MAX} \\[6pt]
\min\limits_{a \in \text{ACTIONS}(s)} \text{MINIMAX}(\text{RESULT}(s,a)), & \text{if TO-MOVE}(s) = \text{MIN}
\end{cases}
$$

The algorithm:

```
function MINIMAX-SEARCH(game, state) returns an action
    player ← game.T O -M OVE(state)
    value, move ← M AX -VALUE(game, state)
    return move

function MAX-VALUE(game, state) returns a (utility, move) pair
    if game.IS-TERMINAL(state) then return game.UTILITY(state, player), null
    v, move ← −∞
    for each a in game.ACTIONS(state) do
        v2, a2 ← MIN-VALUE(game, game.RESULT(state, a))
        if v2 > v then
            v, move ← v2, a
    return v, move

function MIN-VALUE(game, state) returns a (utility, move) pair
    if game.I S -T ERMINAL(state) then return game.U TILITY(state, player), null
    v, move ← +∞
    for each a in game.ACTIONS(state) do
        v2, a2 ← MAX-VALUE(game, game.RESULT(state, a))
        if v2 < v then
            v, move ← v2, a
    return v, move
```

If there is $$b$$ legal move with the maximum depth of a tree $$m$$, then the time complexity is $$\mathcal{O}(b^m)$$

"The space complexity is $$\mathcal{O}(bm)$$ for an algorithm that generates all actions at once"