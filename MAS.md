# Multi Agent Systems

## Introduction

A multiagent system is one that consists of a number of agents, which
interact with one-another. In the most general case, agents will be acting on
behalf of users with different goals and motivations. To successfully interact,
they will require the ability to cooperate, coordinate, and negotiate with
each other, much as people do.

**Cooperation**

- Working together as a team to achieve a shared goal
- No one agent can achieve the goal alone, or cooperation will obtain a better
or faster result

**Coordination**

- Managing interdependencies between activities
- Non-sharable resource that several agents need to use

**Negotiation**

- Ability to reach agreements on matters of common interest
- Typically involves offers and counter-offers, with compromises
made by participants


> All these (usually) require communication.

## Communication

> Communicative actions, agents can influence other agents. Speech act theory is the basis of how multi-agent approaches communication.

Communication includes two kinds of semantics:

- Semantics of the communication protocol (which must be domain
independent)
- Semantics of the enclosed message (which typically depends on the domain)

# [FIPA](http://www.fipa.org/subgroups/ROFS-SG-docs/2007-TAAS-specifying-MAS.pdf)

> Foundation for Intelligent Physical Agents (FIPA) is an ACL, Agent Communication Language, standard for multi-agent systems.

## Message Components

- Content: the message itself, using a representation language and an ontology
- Message: wraps the message content – defines the type of interaction.
- Communication: low-level parameters, such as the identity of the sender and receiver –
“envelope”.

Typical message (performative + parameters)

```lisp
(<performative>
:sender <word>
:receiver <word>
:language <word>
:ontology <word>
:content <expression>
...)
```

- The semantics of performatives is domain independent
- The semantics of the message is defined by :content, :language: and :ontology

Two main performatives:

- inform: the sender wants the receiver to believe this content. Basic mechanism for communicating information
- request: the sender requests the receiver to perform an action. 

FIPA ACL Semantics: meaning of inform and request defined in terms of:

- “feasibility precondition”.
- “rational effect”.

![Performatives](/figs/CA.png)

### FIPA ACL Semantics for Inform and Request

#### INFORM

The content is a statement
**Pre-condition:**

- Sender believes the content is
true
- Sender does not believe the
recipient is aware of whether the
content is true

**Rational effect:**

- Sender intends the recipient to
believe the content


#### REQUEST

The content is an action
**Pre-condition:**

- Sender believes recipient can
perform the action
- Sender does not believe that
recipient already intends to
perform action

**Rational effect:**

- Sender intends the recipient to
execute the action

### Ontologies

- ACL specifies message structure and performatives

> The role of an ontology is to fix the meaning of the terms used by agents in their communication.

Class hierarchies and instances provide inheritance (just as in OOP). We usually define new terms with respect to the old ones.

```lisp
Example:
– Alice: ‘Did you read Prey?’
Bob: ‘No, what is it?’
Alice: ‘A science fiction novel. Well, it is also a bit of a horror novel, actually.
It’s about multiagent systems going haywire.’
– Prey is a science fiction horror novel: it inherits the properties of novels, and
of the science fiction and horror genres
– Bob is assumed to be familiar with these concepts
– Thus, Alice is defining a
```

### FIPA Interaction Protocols

![FIPA Interaction Protocols](/figs/IP.png)
Interaction protocols define conversations, that is, sequences of messages
that together define a semantically meaningful interaction
One of the most basic and well-known is the ContractNet protocol:

- A manager agent announces a task it wants to assign
- Responder agents bid for the task execution
- The manager assigns the task by comparing
the bids
- The assignee finally sends the result of
task execution

# AGENT-BASED MODELING AND SIMULATION


Agent-based model

- Computational model for simulating the actions and
interactions of autonomous agents
- Assess overall properties or evolution of the system as a whole

Goal

- Understand global or emergent phenomena associated with complex adaptive systems
- Agents are mostly homogeneous, simple, reactive

> … but there are exceptions to this

An agent-based model (ABM) is a computational model for simulating the
actions and interactions of autonomous agents in order to understand the
behavior of a system and what governs its outcomes.

Usually, combines elements of [game theory](/GameTheory.md), complex systems, emergence,
computational sociology, multi-agent systems, and evolutionary programming.

Unlike in multi-agent systems, the goal of ABM is to search for explanatory
insight into the collective behavior of agents obeying simple rules, rather than
in designing agents or solving specific practical or engineering problems.

> ABMs are typically implemented as computer simulations.

## Elements of an ABM

- The agents representing the individual entities of interest
- Decision-making heuristics specifying agent behavior
- Learning rules or adaptive processes providing means for the agents to
evolve
- An interaction topology specifying how and when agents can interact with
each other
- The shared environment where the action takes place and emergence will
be observed.

## Elements of an ABMS Tool

Agent-based model:

- Agents: behaviors, learning rules, interaction typology
- Environment: usually a common physical space
- Model: create the environment, populate it with agents and run the simulation

Scheduler:

- discrete-event simulator
- time/tick stepped
- agent-based: ynamic processes of agent behavior and interaction are simulated repeatedly over time

Data collection and visualization

Environment displays.