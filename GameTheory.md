# Game theory: strategic interactions among rational agents

Game theory is the mathematical study of strategic decision making among independent, self-interested agents.

- Given the rules of the game, game theory studies strategic behavior of the
agents in the form of a strategy.
- The tools and techniques of game theory have found many applications in
computational multi-agent systems research.

Types of games:

- Cooperative/non-cooperative
- Symmetric/asymmetric
- Zero-sum/win-win,
- Simultaneous/sequential
- Perfect/imperfect information

## **Utility and Preferences**

- **Utility function**: Maps world states to numerical values.

- **Preference ordering**:
  - **Strict preference**: $u_i(\omega_1) > u_i(\omega_2)$
  - **Weak preference**: $u_i(\omega_1) \geq u_i(\omega_2)$

- Properties:
  - **Reflexivity**
  - **Transitivity**
  - **Comparability**


## **Multi-Agent Encounters**

- Agents choose actions simultaneously.
- **Outcomes** depend on combined choices.
- Example of action choices: **Cooperate (C) vs. Defect (D)**.



## **Normal-Form Games**

A **normal-form game** consists of:

- **\( N \)**: Finite set of players.
- **\( A \)**: Action sets.
- **\( u \)**: Payoff functions.
- Represented using **payoff matrices**.

---

## **Examples of Game Theory in Action**

### **Prisoner’s Dilemma**

|     | D (Defect) | C (Cooperate) |
| --- | --- | --- |
| **D** | (2,2) | (0,5) |
| **C** | (5,0) | (3,3) |

- **Defecting is the dominant strategy**.
- Leads to **suboptimal cooperation**.


## **Key Strategic Concepts**

### **Dominant Strategy**

- A strategy is **dominant** if it is the best response **regardless of what others do**.

---

### **Nash Equilibrium**

- A **strategy profile** where no agent benefits from changing their strategy unilaterally.
- **Not all games have pure-strategy Nash equilibria**.
- Some games have **multiple Nash equilibria**.

Two strategies $s_j$ and $s_j$  are in (pure-strategy) Nash equilibrium if:

- Assuming that agent $i$ plays $s_i$, agent $j$ can do no better than play $s_j$, and
- Assuming that agent $j$ plays $s_j$, agent $i$ can do no better than play $s_i$.

![Nash Equilibrium](/figs/nashequi.png)

---

### **Mixed Strategies**

- A pure strategy determines the exact action to play
- A mixed strategy is an assignment of a probability to each pure strategy

---

#### **Mixed-Strategy Nash Equilibrium**

- Assigns **probabilities** to different actions. A mixed strategy for player $i$ is a probability distribution.
- Example: **Rock-Paper-Scissors** has **mixed-strategy Nash equilibrium**.

Best strategy: play an action at random – a mixed strategy:

$p_i(rock) = 1/3, p_i(paper) = 1/3, p_i(scissors) = 1/3$


> Every game in which every player has a finite set of possible strategies has
a Nash equilibrium in mixed strategies.

*In general, it is tricky (and computationally expensive) to compute a
game’s mixed-strategy Nash equilibria*

## **Pareto Optimality**

- **Pareto-optimal** strategies improve at least one player’s utility without harming others.
- **Zero-sum games** always have Pareto-efficient strategies.

---

Strategy profile $s$ Pareto dominates strategy profile $s´$ if for all $i \in N$, $u_i(s) \ge u_i(s´)$, and there exists some $s \in N$ for which $u_j(s) > u_j(s´)$.

- In a Pareto-dominated strategy profile some player can be made better off
without making any other player worse off
- Strategy profile $s$ is Pareto optimal (or Pareto efficient) if there does not
exist another strategy profile $s´$ that Pareto dominates $s$
- There is no other outcome that improves one player’s utility without making
someone worse off
- A Pareto inefficient strategy profile ‘wastes’ some utility

![Pareto Optimality](/figs/pareto.png)

---

- Every game must have at least one Pareto optimum, and at least one in which all players adopt pure strategies
- Some games will have multiple optima
- In *zero-sum games*, all strategy profiles are strictly Pareto efficient
- In common-payoff games, all Pareto optimal strategy profiles have the
same payoffs.

## **Social Welfare Maximization**

> Social Wellfare = Total Utility

- Measures **total utility** in a game.
- Relevant in **common-payoff games**.
– The utility of the outcome is divided among the players.

## **Extensive-Form Games**

While normal-form games assumes simultaneous decision-making, extensive-form games are used for sequential decision-making.

- Used for **sequential decision-making**.
- Represented as **game trees**.

Each node represents a choice point of one of the players. Edges represent actions. Leaves represent final outcomes over which each player has a utility function.

- Solved (finding the payoff) using **Minimax**  when its a two-player, zero-sum game with **alpha-beta pruning**.

![Extensive-Form vs Normal-Form Games](/figs/extvsnorm.png)


## **Uncertainty in Games**

- **Imperfect-information games**:
  - Partially observable environment.
  - Agents **do not know all past actions**.
  - Requires **reasoning under uncertainty**.

- An imperfect-information game is an extensive-form game in which each
agent’s choice nodes are partitioned into information sets.
  - An information set = {all the nodes you might be at}
  - The nodes in an information set are indistinguishable to the agent
  - The set of actions in those nodes is also the same

--- 

- **Incomplete-information games**:
  - Unknown environment.
  - Players **lack knowledge about the environment**.
  - Often rely on **probabilistic reasoning**.



## **Repeated Games**

> In a repeated game, the game is played multiple times by the same set of
players.

- Strategy space
  - Stationary strategy: adopt the same strategy in each stage game
  - Non-stationary strategy: make action depend on the history of play thus far

---

- **Finitely Repeated Games**:
  - Defection is the dominant strategy due to **backward induction**.

---

- **Infinitely Repeated Games**:
  - Strategies like **Tit-for-Tat** and **Trigger Strategy** promote cooperation.

**Tit-for-Tat strategy:** start by cooperating and then choose whatever action was chosen by the other player in the previous round.

**Trigger strategy:** start by cooperating, but if ever the other player defects, then defect forever.

## **Cooperative Game Theory**

- **Allows binding agreements**, unlike non-cooperative games.
- **Utility** is assigned to **groups** rather than individuals.
- Used in scenarios where **collaboration is necessary**.

In **Non-cooperative game theory** the basic modeling unit is the individual.

In **Cooperative game theory** the basic modeling unit is the group.

