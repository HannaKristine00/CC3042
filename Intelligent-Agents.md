# Exam Notes

## Agent-Based Computing

### Agent design problem (micro)

- How can we build agents that are capable of independent, autonomous action
whose behavior enables them to meet their design objectives, i.e., to
successfully carry out the tasks we delegate to them?

### Society design problem (macro)

- Which mechanisms should be in place that enable the interactions between
agents in a multi-agent system, in particular when they cannot be assumed to
share the same goals?

## Intelligent Agents

### Agent

An agent is a computational entity situated in an environment, capable
of autonomous action in order to meet its delegated objectives.

### Rational Agent

To develop a rational agent, we may take into account:

- The performance measure that defines the criterion of success
- The agent’s prior knowledge of the environment
- The actions that the agent can perform
- The agent’s percept sequence to date

An agent can be seen as a function that maps a percept sequence to an action.

For each possible percept sequence, a rational agent should select an action that is
expected to maximize its performance measure, given the evidence provided by the
percept sequence and whatever built-in knowledge the agent has.

> What is the right function? 

## Properties of Environments

- Fully/Partially Observable

Is there complete, accurate, up-to-date information about the environment's state available to the agent?

- Single/Multi-Agent

Are there several agents? Are they cooperative or competitive? Do they act simultaneously or sequentially?
How do they interact?

- Deterministic/Stochastic

Does the actions have a predetrmined outcome or is there some randomness involved?

- Episodic/Sequential

Do actions interfere with each other? Is the current decision independent of previous ones? Do actions interefere with subseqiuent decision making?

- Static/Dynamic

Does the environment change while the agent is deliberating? Does the enivrronment change in ways out of the agents control?

- Discrete/Continuous

Is there a fixed or finite number of distinct percepts and actions?

> Known or unknown? Does the agent have any knowledge of how the environment works?


## Different Agents

### Simple Reflex Agents

Selects actions on the basis of the current perception.

```lisp
Function: `agent: percept -> action`
persistent: rules, a set of condition-action rules

state <- interpret(percept)
rule <- rule-match(state, rules)
action <- rule-action(rule)

return action
```

> Simple, works well with fully observable environments.

### Model-Based Reflex Agents

Keeps track of the part of the world we can't see. Maintains an internal state that depends on the percept history. Knowledge (model) of the world. 

```lisp
Function: `agent: percept -> action`
persistent: 
state, the agent's current conception of the world
model, a description of how the next state depends on the current state and action
rules, a set of condition-action rules
action, the agent's most recent action, initially none

state <- update-state(state, action, percept, model)
rule <- rule-match(state, rules)
action <- rule-action(rule)

return action
```
Still a rigid approach, but can handle, decisions encoded into rules. Action effects are used to complete the state, not to make decisions. 

### Goal-Based Agents

Goal information describes situations that are desirable.

Goal-based action selection may be tricky when sequences of actions are
needed to achieve the goal

- Search and planning

Considerations about the future

- What will happen if I do such-and-such? Will that make me happy?

More flexible

- Knowledge that supports decisions is represented explicitly and can be
modified
- Different goals obtain different courses of action

Limitations

- How to distinguish between different ways of achieving the goal?
- What about conflicting goals?

### Utility-Based Agents

A utility function is an internalization of the performance measure, capturing the quality of each state. Utility can be used to tradeoff between conflicting goals, or weight the importance of different goals.
In partially observable and stochastic environments, utility-agents chooses the action based off expected utility. They are expected to derive the best possible action, given the information (probabilities and utilities) available of each outcome. 


### Learning Agents

Operate in initially unknown environments and become more competent than its initial knowledge, through learning. 

- Performance element: maps percepts to actions
- Learning element: improves the performance element
- Critic: provides feedback on the performance element, given a fixed performance standard
- Problem generator: suggests actions that lead to new and informative experiences

Learning in intelligent agents is the process of modifying each component to reach closer agreement with the available data (feedback information), improving the agent's overall performance.

### Desireable properties of intelligent agents

- Reactivity: the ability to respond to changes in the environment in a timely fashion.
- Proactiveness: the ability to take the initiative in order to achieve the agent's goals. Excecuting plans based on the current goals.
- Social ability: the ability to interact with other agents in order to achieve the agent's goals. Cooperation, coordination, negotiation, and communication. 

Cooperation is when agents work together to achieve a common goal. Coordination is managing interdependencies between multiple agents' actions (resopurces can't be shared). Negotiation is when agents reach an agreement on how to cooperate, reaching agreements on matters of common interest (offers, compromises).

## Deductive Reasoning Agents

**Key idea:** decision-making and action selection via logical reasoning
Symbolic AI. Traditional approach to AI. Provide a symbolic representation of the environment and desired behaviour, and use logical reasoning to derive new information.

Two key problems:

- The transduction problem: translating the real world into an accurate symbolic
description of the world in time for it to be useful
- The reasoning problem: manipulate/reason with symbolic representations in
time for the results to be useful

### Logic-Based Agents

The agents information about its environment and its beliefs is a database of formulas in first-order predicate logic. Decision making is based on logical inference, deduction rules. So first-order logic is used to represent the agent's knowledge and reasoning, and inference rules are used to derive new information. Actions are chosen if they can be derived from the agent's knowledge base, if not possible it chooses an action thats not explicitly forbidden by the knowledge base. 

Pros and Cons:

Advantage: Agents program is logic, so it's easy to understand and verify.
Disadvantage: Inference in first-order logic is computationally expensive. What if the environment is not fully observable? What if the agent's knowledge is incomplete or incorrect? If the environment is dynamic, the agent's knowledge base may become outdated.

## Practical Reasoning Agents

We don't only use logical reasoning in order to decide what to do, we can also use practical reasoning which is directed towards actions. 
Practical Reasoning = Deliberation + Means-Ends Reasoning

- Deliberation: decide what state of affairs we want to achieve – generate intentions
- Means-ends reasoning: decide how to achieve them – generate plans of action

Practical reasoning is the foundation for the [Belief-Desire-Intention (BDI)](/BDI.md) model of agency. 


## Reactive Agents

Reactive agents are agents that do not have a model of the environment, they react to the environment directly. They are based on the idea that the environment is too complex to model, and that the agent should react to the environment directly. 
An agent’s decision making is realized through a set of task-accomplishing
behaviors

- No complex symbolic representations nor reasoning
- Rules mapping perceptual input directly to actions

### Subsumption Architecture

Behaviours are arranged into layers, inhibiting each other. The lower layers are more reactive, and the higher layers are more deliberative. The higher layers can inhibit the lower layers. Lower layers correspond to “primitive” behaviors and have precedence over higher (more abstract) ones. 

### Advantages and Limitations

Advantages:

- Fast response to environmental changes
- Robustness to uncertainty, failure.
- Simplicity
- Can be encoded into hardware, giving constant decision time.
- Useful in real-time scenarios and dynamic environments, such as in
robotics

Limitations:

- No explicit representation of the environment
- Dependent on local information, current percepts.
- Hard too expand with many layers

## Hybrid Agents

Creating separate subsystems to deal with reactive and proactive
behaviors. They have layered architectures.


