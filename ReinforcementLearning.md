# Reinforcement Learning - Multi-Agent Decision Making

## **1. Learning Agents**

**Agents operate in initially unknown environments** and improve their competence through learning.

- Components:
  - **Performance Element**: Maps perceptions to actions.
  - **Learning Element**: Improves the performance element.
  - **Critic**: Evaluates agent performance.
  - **Problem Generator**: Suggests exploratory actions for new experiences.



## **2. What is Reinforcement Learning?**

- RL is about **learning from interaction** with an **environment**.
- The agent **chooses actions** to maximize a **numerical reward signal**.

**Key challenges**:

- The **agent is not told which actions to take**.
- **Actions affect future states** and rewards.

### **Examples of RL Applications**

| Task | Rewards |
|------|---------|
| Flying stunt maneuvers | + for correct trajectory, - for crashing |
| Playing Atari games | + for higher scores, - for losing |
| Controlling a power station | + for stable power, - for exceeding safety limits |
| Walking humanoid robots | + for forward motion, - for falling |

## **3. RL vs Supervised & Unsupervised Learning**

| Type | Definition |
|------|------------|
| **Supervised Learning** | Agent learns from labeled examples (direct feedback). |
| **Unsupervised Learning** | Agent finds hidden structures in unlabeled data. |
| **Reinforcement Learning** | Agent **interacts** with an **environment**, aiming to **maximize rewards**. |

## **4. Key Elements of RL**

1. **Policy ($\pi$)**: Determines how the agent behaves.
2. **Reward Signal ($r$)**: Defines the **goal** of learning.
3. **Value Function ($v$)**: Represents **long-term reward expectations**.
4. **Model of the Environment** (optional): Used in **model-based** approaches.

## **5. Exploration vs Exploitation**

**Exploitation**: Choosing the **best known action** to maximize rewards.

**Exploration**: Trying **new actions** to discover better strategies.

**Tradeoff**: **Neither pure exploration nor exploitation is optimal**.

### **Examples of Exploration-Exploitation Dilemma**

| Scenario | Exploitation | Exploration |
|----------|-------------|-------------|
| Restaurant selection | Go to your favorite restaurant | Try a new restaurant |
| Online ads | Show the best ad | Try a different ad |
| Game playing | Choose the best move | Try a new move |

## **6. Multi-Armed Bandit Problems**

**Simple setting**: Single state, multiple actions.

- **$K$-armed bandit problem**:
  - $K$ actions, each with **unknown expected reward**.
  - Goal: **Estimate action values** to maximize cumulative reward.

### **Action Selection Methods**

1. **Greedy**: Always selects the best-known action.
2. **$\epsilon$-Greedy**: Explores randomly **with probability $\epsilon$**.
3. **Softmax (Boltzmann)**: Chooses actions **based on probability distribution**.

## **7. Markov Decision Processes (MDPs)**

**MDPs** formalize **sequential decision making**:

- **States ($S$)**
- **Actions ($A$)**
- **Transition probabilities ($P(s' | s, a)$)**
- **Rewards ($R$)**

If the **state fully determines future states**, the system has the **Markov property**.

### **Example: Recycling Robot**

- Actions: **Search**, **Wait**, **Recharge**.
- States: **High energy, Low energy**.
- **Reward-based decisions** ensure energy efficiency.

## **8. Temporal-Difference (TD) Learning**

**Model-free method** that **updates value estimates** using observed transitions.

**TD Update Rule**:
  $$
  V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]
  $$

### **Comparison with Monte Carlo (MC)**

| Feature | Monte Carlo (MC) | Temporal Difference (TD) |
|---------|-----------------|-------------------------|
| **Learning** | At episode end | At each time step |
| **Model Required?** | No | No |
| **Updates** | Full return | Bootstrapped |


## **9. Q-Learning (Off-Policy TD Control)**

**Off-policy RL method** that estimates the **optimal action-value function**.

- **Update Rule**:
  $$
  Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
  $$

### **Example: Cliff Walking**

**Q-learning finds the optimal shortest path** but may fall off the cliff due to exploration.

## **10. Deep Q-Networks (DQN)**

**Deep Reinforcement Learning** uses **neural networks** to approximate Q-values.

- **Experience Replay**:
  - Stores past experiences and samples them to **break correlation** in training.
- **Target Networks**:
  - Stabilizes learning by maintaining a **fixed target Q-network**.

### **Example: Atari Games**

- **DQN learned to play Atari games better than humans** using only pixel input.

## **11. Policy Gradient Methods**

Instead of learning a **value function**, **policy gradient methods** learn a **policy directly**.

**REINFORCE Algorithm**:

- Updates policy parameters $\theta$ based on rewards:
    $$
    \theta_{t+1} = \theta_t + \alpha G_t \nabla \log \pi(A_t | S_t, \theta)
    $$

### **Actor-Critic Methods**

- **Actor**: Updates the policy.
- **Critic**: Evaluates the current policy and helps reduce variance.

## **12. Reinforcement Learning in Games**

- **TD-Gammon**: RL agent learned to play Backgammon at world-champion level.
- **AlphaGo**: Used **policy gradients & Monte Carlo Tree Search** to defeat human Go champions.
- **Poker AI (DeepStack, Libratus)**: RL used for **game-theoretic strategies**.

## **13. Open-Source RL Libraries**

- **OpenAI Gym**: RL benchmarking environments.
- **Stable Baselines 3**: High-quality RL algorithm implementations.
- **Unity ML-Agents**: RL for **3D environments and simulations**.

## **14. Example: Toothpick Game**

**Game Rules**:

- 10 toothpicks.
- Players take **1, 2, or 3** toothpicks per turn.
- The player who takes the last toothpick **loses**.

**Using Q-Learning with $\alpha = 0.5, \gamma = 0.9$, we update $Q(s, a)$**:

- After three rounds, the **optimal strategy emerges**.
- **Greedy policy ensures the opponent is forced into losing states**.



## Exercises for Practicing Q-Learning Calculations

**In each exercise:**

**State ($s$)** represents the current situation.

**Actions ($a$)** determine the possible moves.

**Rewards ($r$)** are given for reaching the goal or making certain moves.

**Learning rate ($\alpha$)** and discount factor ($\gamma$) define the Q-learning updates.

Formula for Q-Learning Update:
￼
$$Q(s_t, a_t) \leftarrow Q(s_t, a_t) + \alpha \left[ r_t + \gamma \max_{a} Q(s_{t+1}, a) - Q(s_t, a_t) \right]$$


---

### 1. **Coin Collection Game**

Game Rules:

- There are 5 states ($S_0$ to $S_4$).
- The agent starts at $S_0$ and must reach $S_4$ to collect a coin (+10 reward).
- Moving forward (right) is the best move.
- Moving backward (left) gives no reward.
- If the agent reaches $S_4$, the episode ends.

State-Action Table

| State	| Action (Left)	| Action (Right) | Reward |
|-------|---------------|----------------|--------|
| $S_0$	| Stay at $S_0$	| Move to $S_1$	| 0      |
| $S_1$	| Move to $S_0$	| Move to $S_2$	| 0      |
| $S_2$	| Move to $S_1$	| Move to $S_3$	| 0      |
| $S_3$	| Move to $S_2$	| Move to $S_4$	| +10    |
| $S_4$	| -	            | -	            | Terminal State |


#### **Task:**

1. Given: $\alpha = 0.5$, $\gamma = 0.9$, and an initial Q-table of zeros.
2. Calculate the Q-values for the first two episodes if the agent takes the actions:

  - Episode 1: $S_0 \to S_1 \to S_2 \to S_3 \to S_4$ (Always move right)
  - Episode 2: $S_0 \to S_1 \to S_2 \to S_1 \to S_2 \to S_3 \to S_4$ (One mistake: moving left at $S_2$)

3. Find the optimal Q-values for each state.

--- 

### 2. **The Candy Jar Game**

**Game Rules:**

- There is a jar with 6 candies.
- Two players take turns picking 1 or 2 candies.
- The player who takes the last candy loses.
- Rewards:
  - If the agent forces the opponent to take the last candy → +5 reward.
  - If the agent loses → -5 reward.


**State-Action Table:**

| Candies Left | Action: Take 1 | Action: Take 2 | Winner |
|--------------|----------------|----------------|--------|
| 6            | 5 left         | 4 left         | -      |
| 5            | 4 left         | 3 left         | -      |
| 4            | 3 left         | 2 left         | -      |
| 3            | 2 left         | 1 left         | -      |
| 2            | 1 left         | Lose (-5)      | Opponent wins |
| 1            | Lose (-5)      | -              | Opponent wins |

#### **Task:**

- Given: $\alpha = 0.3$, $\gamma = 0.9$, and an initial Q-table of zeros.
- Calculate Q-values for two training episodes:
  - Episode 1: Agent picks random moves.
  - Episode 2: Agent starts to learn from experience.
- Find the optimal Q-values to make the agent always win the game.

---

### 3. **The Escape Room Game**

**Game Rules:**

- The agent is trapped in a 3-room environment and must find the exit.
- Each room has two doors leading to other rooms.
- The agent receives +10 reward for exiting and -1 for each move.

**Room Layout:**

(Room 1) ---- (Room 2) ---- (Exit)

**State** = {Room 1, Room 2, Exit}

**Actions** = {Left, Right}

**Rewards:**

- Moving Left: -1.
- Moving Right: -1 (except when reaching Exit: +10).

**State-Action Table**

| Room   | Action: Left      | Action: Right     | Reward |
|--------|-------------------|-------------------|--------|
| Room 1 | Stay at Room 1    | Move to Room 2    | -1     |
| Room 2 | Move to Room 1    | Move to Exit      | +10    |
| Exit   | -                 | -                 | Terminal State |

#### **Task**

1. Given: $\alpha = 0.7$, $\gamma = 0.8$, and an initial Q-table of zeros.
2. Simulate the Q-learning updates for three training episodes:

  - Episode 1: Agent moves randomly.
  - Episode 2: Agent starts preferring the exit.
  - Episode 3: Agent converges to the optimal policy.

3. Find the best Q-values so the agent escapes in the shortest time.

---

### **How to Solve These Exercises**

#### **Step-by-Step Q-Learning Calculation**

1. Initialize the Q-table with all zeros.
2. Simulate an episode:
   - Choose an action.
   - Observe the next state and reward.
   - Apply the Q-learning update formula:
   $$
   Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
   $$
3. Repeat the process for multiple episodes.
4. Check if Q-values converge to an optimal policy.
