# The BDI Model

The BDI model is a model of rational agency that is based on the idea that agents have beliefs, desires, and intentions. The BDI model is used to describe how agents can reason about their environment and make decisions based on their beliefs, desires, and intentions.

It consists of three components:

- Beliefs: The agent's beliefs about the world, including its current state and the possible actions it can take - information.
- Desires: The agent's desires or goals, which describe the states of the world that the agent finds desirable - motivation.
- Intentions: The agent's intentions, which describe the actions that the agent plans to take in order to achieve its goals - deliberation.

## BDI Control Flow

**Belief Revision Function**

- Updates the agent's beliefs baseed on new information. and previous beliefs.

**Option Generation Function**

- Use beliefs and existing intentions to generate a set of alternatives (desires)

**Filter**

- Choose between competing alternatives and commit to their achievement
(intentions).

**Action Selection Function**

- Given the current beliefs and intentions, select the next action to perform (generate a plan).

## BDI Control Loop

B <- B_0 Initial Beliefs
I <- I_0 Initial Intentions

While True:
    P <- Perceive()
    B <- Belief Revision Function(B, P)
    D <- Option Generation Function(B, I)
    I <- Filter(D)
    A <- Action Selection Function(B, I)
    Execute(A) if possible.

Alternative formulation of loop:

initialize-state
repeat
options: option-generator (event-queue)
selected-options: deliberate(options)
update-intentions(selected-options)
execute()
get-new-external-events()
drop-unsuccessful-attitudes()
drop-impossible-attitudes()
end repeat



## Properties of Intentions

- Intentions are stronger than desires. Desires are merely potential influences on the actions. 
- Intentions drive means-ends reasoning.
- Intentions persists.
- Intentions constrain future deliberation, avoids inconsistency.
- Intentions influence beliefs upon which future deliberation is based, plan on the assumption that the intention will be achieved.

