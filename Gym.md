# Gymnasium Environment

Gymnasium is an open-source toolkit for developing and benchmarking Reinforcement Learning (RL) algorithms. It provides a standardized API for interacting with environments, making it easier to implement, compare, and test RL algorithms.

## Wrappers

Wrappers are used to modify environments without altering their core logic. They can:

- Normalize observations/rewards.
- Apply frame stacking.
- Convert action spaces.
- Modify rendering.

1. ClipAction
    - Clips the action pass to step to be within the environment’s action_space.
2. ClipReward
    - Clips the reward pass to step to be within the environment’s reward range. Clips the rewards for an environment between an upper and lower bound.
3. RescaleAction
    - Affinely (linearly) rescales a Box action space of the environment to within the range of [min_action, max_action].
4. RescaleObservation
    - Affinely (linearly) rescales a Box observation space of the environment to within the range of [min_obs, max_obs].
5. TransformAction
    - Applies a function to the action before passing the modified value to the environment step function.
6. TransformObservation
    - Applies a function to the observation received from the environment’s reset and step that is passed back to the user.
7. TransformReward
    - Applies a function to the reward received from the environment’s step.

## Vectorize

Vector environments can provide a linear speed-up in the steps taken per second through sampling multiple sub-environments at the same time. Gymnasium contains two generalised Vector environments: AsyncVectorEnv and SyncVectorEnv along with several custom vector environment implementations. 

