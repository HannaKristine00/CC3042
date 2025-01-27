# Social choice theory: group decisions on possible outcomes

- **Social choice theory** is concerned with making group decisions: given the preferences of different agents, how do we aggregate them to reflect the wishes of the population as a whole?
    - E.g. voting.
    - Taking other agents' preferences into account as well as its own.


## **Social Choice Model**

- **Voters**: Set of agents $Ag = \{1, 2, ..., n\}$.
- **Outcomes**: Set $\omega = \{\omega{_1}, \omega{_2}, ...\}$.
- **Types of voting**:
  - **Pairwise election** $|Ω| = 2$.
  - **General election** $|Ω| > 2$.
- **Preference Order**: Each voter ranks outcomes.

## **Preference Aggregation**

- Different voters have **different rankings**.

Let $\Pi(\omega)$ be the set of all possible rankings of outcomes $\omega$ (*preference profile*).

- Two ways to aggregate preferences:
  - **Social welfare function**: Produces a **ranking** of outcomes.
    - E.g. beauty contest.

  - **Social choice function**: Produces a **single winning outcome**.
    - E.g. election.

![Social Wellfare Function](/figs/socialwellfunc.png) ![Social Choice Function](/figs/socialchoicefunc.png)


## **Voting Procedures**

### **Plurality Voting**

- Each voter selects a single **preferred candidate**.
- Candidate with the most votes **wins**.
- **Paradox**: The winner may be the least preferred by the majority.

**Condorcet’s paradox:** there are situations in which, no matter
which outcome we choose, a majority of voters will be unhappy.

## **Sequential Majority Voting**

- Candidates compete **in rounds** (like a knockout tournament).
- **Agenda-setting** influences the outcome.
- **Manipulability**: The order of candidates **affects** the winner. Selecting a random order: democratic?


## **Majority Graphs**

- **Graph representation** is a compact representation of voter preferences.
- **Nodes** represent candidates.
- **Edges** indicate which candidate would win in **pairwise elections**.
- **Cycles** allow results to be manipulated.

To determine if $w_i$ is a possible winner we must find, for every other $w_j$, a
path from $w_i$ to $w_j$ in the majority graph.

### **Condorcet Winner**

A candidate that **beats all others** in **pairwise elections**.

![Condorset](/figs/condorcet.png)

 $w_1$ is the Condorcet winner since there is an edge from $w_1$ to every other candidate.



## **Borda Count Voting System**

- Each voter **ranks** all candidates.
- **Points assigned** based on rankings.
- **Advantage**: Uses **more information** than plurality voting.
- **Example Calculation**:
  - Candidate’s score is computed based on their **rank positions** across all votes.

![Borda Count](/figs/bordacount.png)

1. For each candidate, we count the strength of opinion in favor for it.
    - If $w_i$ appears in position $p$ in a preference order, we increment its counter by $k-p$.
    - The last candidate in a preference order is not incremented $k-p = 0$.
2. After considering all preference orders, we order the outcomes by their count.

## **Desirable Properties of Voting Procedures**

**Pareto Condition**

- If **all voters** prefer $\omega{_i}$ over $\omega{_j}$, then $\omega{_i}$ should be ranked **higher**.

---

**Condorcet Winner Condition**

- If a candidate $w_j$ is a **Condorcet winner**, they **should** win (ranked first).

---

**Independence of Irrelevant Alternatives (IIA)**

- The relative ranking between **two candidates** should not be affected by **other candidates**.

## **Arrow’s Theorem**

Are there any voting procedures that satisfy the Pareto condition and the Independence of Irrelevant Alternatives condition?

- **No perfect voting system exists**.
- The **only** voting system that satisfies both **Pareto** and **IIA** is a **dictatorship**.

## **Gibbard-Satterthwaite Theorem**

> A voting procedure is manipulable if a voter can obtain a better outcome by
unilaterally changing its announced preference profile

- **All voting systems** with three or more choices are **susceptible** to **strategic manipulation**.
- **Only dictatorship is immune**.
- **Some voting procedures** make manipulation **computationally difficult**.

## **Conclusion**

- **Social choice theory** is crucial in **multi-agent decision-making**.
- **Plurality, Borda Count, and Sequential Majority** have trade-offs.
- **Condorcet paradox and Arrow’s theorem** reveal **inherent limitations**.
- **Strategic manipulation is unavoidable** in voting systems.