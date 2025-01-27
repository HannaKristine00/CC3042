# Mechanism design: effective protocols for multi-agent systems

## Introduction

**Mechanism Design**, also known as **implementation theory** or **inverse game theory**. It focuses on designing **protocols** that lead to **desired behaviors** in multi-agent systems, even when agent preferences are unknown.

## **What is Mechanism Design?**

- A **strategic version** of **social choice theory**.
- Assumes agents **maximize their private payoffs**.
- Helps in **designing games** where desired behaviors emerge **naturally**.
- **Typical application**: **Auction Theory**.

## **Auctions**

- Auctions **efficiently allocate scarce resources** to those who value them most.
- Examples of auctioned items:
  - **Paintings**, **eBay items**, **mineral resources**, **spectrum licenses**, **stock shares**.

### **Auction Elements**

- **Participants**: An **auctioneer** and **bidders**.
- **Types of valuations**:
  - **Private value**: Different bidders assign different values to the same item.
  - **Common value**: All bidders assign the same value (e.g., a $1 bill).
  - **Correlated value**: Partially dependent on both private and external factors (e.g. bidding on items to sell later, oil fields).

## **Auction Protocols**

- **Winner determination**: **First-price** vs **Second-price** auctions.
- **Bid disclosure**: **Open cry** vs **Sealed-bid** auctions.
- **Bidders**: **Single-sided** (buyers) vs **Two-sided** (buyers & sellers).
- **Bidding mechanism**: **One-shot** vs **Ascending/descending** auctions.

## Auction for Single Items

### **English Auction**

**First-price**, **open cry**, **ascending**.

- Bidders **increase bids** until no one bids higher.
- **Winner’s Curse**: Paying too much due to overestimation.

> Dominant strategy: bid a small amount more than the current highest bid until
bid price reaches private evaluation.

### **Dutch Auction**

**Open cry**, **descending**.

- Price **starts high** and the auctioneer **decreases** the price until a bidder accepts.

### **Japanese Auctions**

**Open cry**, **ascending**.

- Auctioneer increases the price by some amount
- Price **rises** each round; bidders must **stay in or drop out**.

### **First-price Sealed-bid Auction**

**Single round**, **sealed-bid**.

> Best strategy: bid less (how much less?) than true valuation, given that it
would be enough to bid slightly more than the second highest bid.

### **Vickrey Auction (Second-Price Sealed-Bid)**

**Single round**, **sealed-bid**.

- **Highest bidder wins but pays the second-highest bid**.
- **Dominant strategy**: **Bid truthfully** (incentive-compatible).
- Not prone to **strategic manipulation**.

## **Bidder Behavior & Revenue**

- **Risk-neutral bidders**: Any protocol works.
- **Risk-averse bidders**: **Bid aggressively** to secure the item.
- **Risk-seeking bidders**: **Bid conservatively**, reducing auctioneer revenue.
- **Second-price auctions** tend to **maximize revenue**.

## **Combinatorial Auctions**

- **Bidders bid on bundles of goods** instead of single items.
- **Valuation functions** determine how bidders value bundles.


### **Valuation Types**

- **Substitutes**:
  - **Subadditive function**: The whole is worth **less** than the sum of its parts.
  - Example: A buyer only needs **one** of two similar items.
- **Complements**:
  - **Superadditive function**: The whole is worth **more** than the sum of its parts.
  - Example: A buyer needs **both** a printer and ink to get value.

---

## **Bid Evaluation & Satisfaction**

- **Atomic bids**: $ \beta = (Z, p) $ for bundle $ Z $ at price $ p $.
- **Bundle satisfies bid**: $ Z' $ must contain $ Z $.
- Example:
  - **Bid**: `{a, b}, 4`
  - **Satisfied by**: `{a, b, c}`
  - **Not satisfied by**: `{b, d}`


### **Types of Bids**

#### **OR Bids**

- Express **non-substitutable** valuations.
- Example:
  - $ \beta = ({a, b}, 3) \lor ({c, d}, 5) $
  - $ v_{\beta}({a, b, c, d}) = 8 $
- Cannot compute valuations serving atomic bids that are not strictly disjoint
- **Computationally expensive (NP-hard).**
  - We need to find out a disjoint subset of satisfied OR’ed atomic bids that maximizes the sum of their prices

#### **XOR Bids**

- Express **all possible valuation functions**.
- Example:
  - $ \beta = ({a, b}, 3) \oplus ({c, d}, 5) $
  - $ v_{\beta}({a, b}) = 3 $, $ v_{\beta}({c, d}) = 5 $, $ v_{\beta}({a, b, c, d}) = 5 $
- **Ensures mutual exclusivity.**

## **Winner Determination in Combinatorial Auctions**

An outcome of a combinatorial auction is an allocation of (some of) the
goods being auctioned among the agents.

An allocation is a list of sets $Z_1, ..., Zn$, one for each agent, where $Z_i$ is the set of goods allocated to agent $i$, such that for all $j \neq i$, we have $Z_i \cap Z_j = Ø$, no good is allocated to more than one agent.

- **Problem**: Allocate goods to maximize **social welfare**:
  $$ \max_{Z_1, ..., Z_n} \sum_{i=1}^{n} v_i(Z_i) $$
- **NP-hard problem** (Combinatorial optimization).

![Combinatorial Auctions Example](/figs/winnerdetcombiauc.png)

## **Vickrey-Clarke-Groves (VCG) Mechanism**

- Ensures **truthful bidding** leads to **maximum social welfare**.
- Payment by bidder $ i $:
  $$ P_i = \sum_{j \neq i} \hat{v}_j(\chi(\hat{v}_{-i})) - \sum_{j \neq i} \hat{v}_j(\chi(\hat{v})) $$
- **Generalization of Vickrey auctions**.
- **Truthful bidding is optimal** (incentive-compatible).

![VCG Mechanism Example](/figs/VCG.png)

## **Two-Sided Auctions**


**Buyers and sellers** bid simultaneously, e.g. **Stock market**.

- **Continuous Double Auction (CDA)**:
  - **Bids matched instantly** in the order book.
- **Call Market**:
  - Bids **collected**, **matched at set intervals**.

![callmarket](/figs/callmarketex.png)

Number 2 is ranked higher than number 1 because it bid a higher price, even though it bid later. Found a fault in the exampåle, its supposed to say 6@4$, not 2@4$.


