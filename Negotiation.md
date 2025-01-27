# Negotiation: finding mutually beneficial deals in the presence of conflicting objectives

The purpose of negotiation is to reach an agreement on matters of common interest, in the presence of conflicting goals and preferences.

## **What is Negotiation?**

- Auctions focus on **allocation of goods**, while **negotiation** aims at **mutual agreement**.
- **Negotiation components**:
  - **Negotiation set**: Possible proposals agents can make.
  - **Protocol**: Defines legal proposals based on history.
  - **Strategies**: Private tactics for making proposals.
  - **Deal rule**: Determines when an agreement is reached.

Negotiation proceeds in a series of rounds, in which legal proposals from the negotiation set are made, as determined by the strategies used.

## **Types of Negotiation**

### **Single-Issue Negotiation**

Example: **Price negotiations**.

- **Straightforward** concessions (e.g., buyer increases offer, seller lowers price).

### **Multi-Issue Negotiation**

Example: **Car purchase** (price, warranty, extras).

- **More complex** because attributes may be **interdependent**.
- **Exponential growth** in possible deals: $m^n$, where $n$ attributes have $m$ values.

## **Negotiation Scenarios**

**One-to-One**: Two agents negotiate directly (e.g., buying a car).

**One-to-Many / Many-to-One**: A single agent negotiates with multiple others (e.g., procurement, auctions, ContractNet protocol).

**Many-to-Many**: Multiple agents negotiate simultaneously (e.g., **two-sided auctions**).

## **Rubinstein’s Alternating Offers Protocol**

**One-to-one negotiation** over a sequence of rounds.

- **Assumptions**:
  - **Disagreement is the worst outcome**.
  - **Agents maximize utility**.
  - **Agents have different patience levels**.

![Rubinstein's Protocol](/figs/Rubenstein.png)

## **Time in Negotiation**

**Time is valuable**: Agents prefer agreements **sooner rather than later**.

- **Patience modeled by a discount factor** $ \gamma_i \in (0,1) $:
  - Larger $ \gamma_i $ → **More patient**.
  - Smaller $ \gamma_i $ → **Less patient**.

## **Behavior in Negotiation**

We can take the negotiation opponent’s previous attitude into account.

### **Tit-for-Tat Strategy**

**Reciprocity-based behavior** (equivalent retaliation).

### **Behavior-Dependent Tactics**

- **Relative Tit-for-Tat**: Adjust offer by the **same percentage** as the opponent.
  - E.g., buyer increases offer in 10%, seller decreases asked price in 10%.
- **Random Absolute Tit-for-Tat**: Adjust offer by **fixed amounts with randomness**.
  - E.g., buyer increases offer in 10€, seller decreases asked price in €10+-$\epsilon$.
- **Averaged Tit-for-Tat**: Uses a **history window** to adjust offers.
  - If window size is 1, we have *relative Tit-For-Tat*.

## **Task Allocation in Negotiation**

A **Task-Oriented Domain (TOD)** is a triple: $<T, Ag, c>$.

1. **Tasks ($T$)** to be allocated.
2. **Agents ($Ag$)** performing the tasks.
3. **Cost function ($c$)**: Cost of executing subsets of tasks.

An encounter is a collection of subsets of tasks $<T_1, \dots,T_n>$, where $T_i \subseteq T$
the set of tasks assigned to agent $i$.

**Encounters**: Agents may **reallocate tasks** to improve efficiency.

## **Deals and Utilities**

Given an *encounter* $<T_1, \dots,T_n>$, a pure deal can be defined as: $$ \delta = <D_1, \dots,D_n> $$

**Deal ($\delta$)**: Reallocation of tasks among agents.

**Utility ($u_i(\delta)$)**: Cost difference before and after reallocation: $$ u_i(\delta) = c(T_i) - c(D_i) $$
    - The utility represents how much the agent gains with the deal.
    - If **negative**, the agent is **worse off**.

> If agents fail to reach agreement, they fall back to the conflict deal, which is the worst outcome. 

## **Dominance in Deals**

**Pareto Optimality**: No better alternative exists without **making someone worse off**.

**Individually Rational Deal**: No agent prefers the **conflict deal** over the new deal.

- **Dominance Condition**:
  - **Strictly dominates**: $ \delta_1 \succ \delta_2 $ if at least **one agent benefits** and **no one is worse off**.
  - **Weakly dominates**: $ \delta_1 \succeq \delta_2 $ if **no one is worse off**.

## **Example: School Drop-Off Negotiation**

**Abe & Ben** have **children attending different schools**. Instead of **separately driving each child**, they negotiate to **share** drop-offs.

- **Negotiation outcomes**:
  - **Individually rational deals**: No parent should have a **higher cost** than before.
  - **Pareto optimal deals**: No better solution exists without making someone worse off.

![School Drop-Off](/figs/kidstoschoolex.png)


**Step 1: Compute Conflict Deal Costs**

If no deal is made, each parent drives their own kids to school:

| Parent  | Route                              | Cost  |
|---------|------------------------------------|------ |
| **Abe** | $A_1 \to S_1$, $A_2 \to S_2$, $A_3 \to S_3$ | **5 + 12 + 7 = 24** |
| **Ben** | $B_1 \to S_1$, $B_2 \to S_2$ | **8 + 8 = 16** |

Thus, the **conflict deal** costs:

- **Abe: 24**
- **Ben: 16**

---

**Step 2: Identify Possible Carpool Deals**

Possible deals for sharing school drop-offs:

1. **Deal 1**: Abe takes **all** kids ($A_1, A_2, A_3, B_1, B_2$).
2. **Deal 2**: Ben takes **all** kids.
3. **Deal 3**: **Split based on school locations**:
   - **Abe takes** $A_1$ and $B_1$ (kids going to $S_1$).
   - **Ben takes** $A_2$, $A_3$, and $B_2$ (kids going to $S_2, S_3$).

| Deal | Abe's Cost | Ben's Cost |
|------|-----------|-----------|
| **Conflict** (no deal) | **24** | **16** |
| **Deal 1: Abe takes all kids** | **30** | **0** |
| **Deal 2: Ben takes all kids** | **0** | **28** |
| **Deal 3: Split by schools** | **10** | **14** |

---

**Step 3: Check Individual Rationality**

A deal is **individually rational** if **no agent is worse off** compared to the conflict deal.

- **Deal 1**: Abe's cost **increases from 24 to 30** → **NOT individually rational**.
- **Deal 2**: Ben's cost **increases from 16 to 28** → **NOT individually rational**.
- **Deal 3**: Abe's cost **decreases from 24 to 10**, Ben's cost **decreases from 16 to 14** → **Individually Rational**.

---

**Step 4: Check Pareto Optimality**

A deal is **Pareto optimal** if **no other deal improves one agent’s utility without making the other worse off**.

- **Deal 1 and Deal 2 are not considered** since they are **not individually rational**.
- **Deal 3 is Pareto optimal** because:
  - It **reduces costs** for both agents compared to the conflict deal.
  - **No better deal exists** that makes one agent better off without harming the other.

---

**Final Answer**

- **Conflict deal cost**: (Abe: **24**, Ben: **16**).
- **Best deal**: **Split by schools** (Abe: **10**, Ben: **14**).
- **Final allocation**:
  - **Abe takes kids to $S_1$** ($A_1, B_1$).
  - **Ben takes kids to $S_2, S_3$** ($A_2, A_3, B_2$).
- **This deal is Individually Rational and Pareto Optimal**.

## **Negotiation Sets**

**Negotiation sets** consists of deals that are *individually rational* and *Pareto optimal*. Individually rational means that here is no purpose in proposing a deal that is worse than the conflict deal for some agent. Pareto optimal means that there is no point in making a proposal for which there is a better alternative for some agent at nobody’s expense.

![Negotiation Sets](/figs/negset.png)

Deals to the left of line B-D are not individually rational for agent $j$. Deals below line A-C are not individually rational for agent $i$. The negotiation set consists of deals in the shaded area B-C-E. But only those that lie on the line B-C are Pareto optimal! This is the negotiation set. Typically, agent $i$ starts by proposing the deal at point B, and agent $j$ starts by proposing the deal at point C.

## **Monotonic Concession Protocol**

**Negotiation rounds**:

Negotiation proceeds in a series of rounds.

1. Both agents simultaneously **propose a deal**.
2. Agreement if one **accepts** the other's offer.
    - Proposal received is at least as good as own proposal
    - Such proposal is the agreement deal.
3. Otherwise, proceed to the **next round** with improved proposals.
    - A proposal cannot be less preferred by the other agent than the previous one.
4. If no agreement is reached, negotiation **ends in conflict**.

## **Zeuthen Strategy**

Determines **who should concede** and **by how much**.

What should be an agent’s first proposal?

- Its most preferred deal


**Risk calculation**:
  $$ \text{risk}_i^t = \frac{\text{utility lost by conceding}}{\text{utility lost in conflict}} $$

- **Higher risk**: Agent prefers **conflict over concession**.
- **Lower risk**: Agent prefers **concession over conflict**.
- If $ \text{risk}_i^t = 1 $, agent is **fully willing to risk conflict**.

The agent least willing to risk conflict is the one that should concede: the one for which the difference
between its current proposal and the conflict deal is highest.

### Pizza Delivery Example

**Problem Setup**

- Two pizza deliverers, **P1** and **P2**, must **coordinate deliveries**.
- Each starts at **origin (O)** and has **two deliveries**:
  - **P1**: Deliver to **A** and **C**.
  - **P2**: Deliver to **B** and **D**.

The goal is to determine an **individually rational** and **Pareto optimal** negotiation deal.

---

**Step 1: Compute Conflict Deal Costs**

If no deal is made, each pizza deliverer handles their own orders:

| Deliverer | Route | Cost |
|-----------|-------|------|
| **P1** | $O \to A \to C$ | **3 + 1 = 4** |
| **P2** | $O \to B \to D$ | **3 + 3 = 6** |

Thus, the **conflict deal** costs:
- **P1: 4**
- **P2: 6**

---

**Step 2: Identify Possible Delivery Deals**

Possible reassignments of deliveries:

1. **Deal 1**: P1 takes **all** deliveries ($A, B, C, D$).
2. **Deal 2**: P2 takes **all** deliveries.
3. **Deal 3**: **Reassign deliveries** based on location proximity:
   - **P1 delivers to A and B**.
   - **P2 delivers to C and D**.

| Deal | P1's Cost | P2's Cost |
|------|----------|----------|
| **Conflict** (no deal) | **4** | **6** |
| **Deal 1: P1 delivers all** | **10** | **0** |
| **Deal 2: P2 delivers all** | **0** | **12** |
| **Deal 3: Split deliveries (A, B) and (C, D)** | **5** | **5** |

---

**Step 3: Check Individual Rationality**

A deal is **individually rational** if **no agent is worse off** compared to the conflict deal.

- **Deal 1**: P1's cost **increases from 4 to 10** → **NOT individually rational**.
- **Deal 2**: P2's cost **increases from 6 to 12** → **NOT individually rational**.
- **Deal 3**: P1’s cost **increases slightly from 4 to 5**, P2’s cost **decreases from 6 to 5** → **Individually Rational ✅**.

---

**Step 4: Check Pareto Optimality**

A deal is **Pareto optimal** if **no alternative deal makes one agent better off without making another worse off**.

- **Deal 1 and Deal 2 are not considered** since they are **not individually rational**.
- **Deal 3 is Pareto optimal** because:
  - **P1's cost only increases by 1 unit** while **P2's cost decreases by 1 unit**.
  - **No better solution exists** that improves one agent’s cost without making the other worse off.

---

**Step 5: Apply Zeuthen Strategy**

- **First proposal**: 
  - **P1 proposes Deal 3 (A, B) for P1 and (C, D) for P2).**
- **Who should concede?**
  - The agent with the **least willingness to risk conflict** should concede.
  - **P2 benefits more from the deal** than P1 (since their cost reduces), so **P1 may need to concede slightly**.
- **Final outcome**:
  - **P1 agrees to take a slightly higher cost (5 instead of 4)**.
  - **P2 accepts since their cost reduces (from 6 to 5)**.

---

**Final Answer**

- **Conflict deal cost**: (P1: **4**, P2: **6**).
- **Best deal**: **Split deliveries** (P1: **5**, P2: **5**).
- **Final allocation**:
  - **P1 delivers to A and B**.
  - **P2 delivers to C and D**.
- **This deal is Individually Rational and Pareto Optimal**.

## **Properties of Negotiation**

**Monotonic Concession Protocol**:

- **Termination is guaranteed**.
- **Does not guarantee social welfare maximization**.
- **Ensures Pareto optimality & individual rationality**.

**Zeuthen Strategy**:

- In **Nash equilibrium** (no agent benefits from deviation).

> **Agents may deceive** by **hiding or faking tasks**.

## **Resource (Re)Allocation:** How can agents reallocate resources for mutual benefit?

**Similar to combinatorial auctions**:

- Agents hold **resources** ($Z$).
- Agents have **valuation functions** ($ v_i: 2^Z \to \mathbb{R} $).
- **Negotiation** helps find a **mutually beneficial exchange**.

**Allocation change**:

- If **$ v_i(P_i) < v_i(Q_i) $**, agent **benefits** from exchange.
- If **$ v_i(P_i) > v_i(Q_i) $**, agent **loses** utility.

Agents negotiate to move from an initial allocation to another that is collectively more beneficial, given their individual valuation functions.

## **Side Payments**

Used to **compensate** agents for exchanging goods.

**Example**:

- Agent $i$ values item **at 5**.
- Agent $j$ values it **at 10**.
- Agent $j$ offers **payment ≥ 5** to compensate $i$.

**Payment vector**:

- $ p_i > 0 $ → Agent **pays**.
- $ p_i < 0 $ → Agent **receives**.

## **Side Payment Deals**

- **Individually Rational**: Agents **gain** or **break even**.
  - Even without payments, there may be deals where some agents are better off
- **Pareto Optimal**: No alternative improves some agent's utility **without harming others**.