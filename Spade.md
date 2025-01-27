# SPADE

SPADE is a multi-agent platform that allows the development of multi-agent systems. It is based on the FIPA specifications and is written in Python. SPADE is a library that allows the development of agents that can communicate with each other.

## Agent

A SPADE agent is an asyncronous agent. That means that all the code to run an agent must be executed in an asyncronous loop. This is done by the spade.run() function. This function receives a coroutine as a parameter and runs it in an async loop. 

### Behaviour

**The behvaiours come from the spade.behaviour module.**

The behaviours are the main building blocks of the agents. They are used to define the agent's actions and reactions to the environment. There are several types of behaviours in SPADE. The most common are:


#### CyclicBehaviour

This class represents a cyclic behaviour with no specific period, that is, a loop-like behaviour. 


#### TimeoutBehaviour

You can also create a TimeoutBehaviour which **is run once** (like OneShotBehaviours) but its activation is triggered at a **specified datetime** just as in PeriodicBehaviours.

#### PeriodicBehaviour

This behaviour runs its run() body at a scheduled period. This period is set in **seconds**. You can also delay the startup of the periodic behaviour by setting a datetime in the start_at parameter.

#### OneShotBehaviour

This behaviour is only executed once.

#### FSMBehaviour

A behaviour composed of states (oneshotbehaviours) that may transition from one state to another. SPADE agents can also have more complex behaviours which are a finite state machine (FSM) which has registered states and transitions between states. The FSMBehaviour is a subclass of CyclicBehaviour.

### Communication

Templates is the method used by SPADE to dispatch received messages to the behaviour that is waiting for that message. When adding a behaviour you can set a template for that behaviour, which allows the agent to deliver a message received by the agent to that registered behaviour. 

```lisp
to: the jid string of the receiver of the message.
sender the jid string of the sender of the message.
body: the body of the message.
thread: the thread id of the conversation.
metadata: a (key, value) dictionary of strings to define metadata of the message. This is useful, for example, to include FIPA attributes like ontology, performative, language, etc.
```

