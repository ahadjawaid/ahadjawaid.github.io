---
title: "Modeling the Reinforcement Learning Problem"
author: "Ahad Jawaid"
layout: post
date: "2023-07-01"
description: My notes on the second chapter of 'Grokking Deep Reinforcement Learning' by Miguel Morales. This post covers the components of the environment and how to model it using Markov Decision Processes (MDPs).
categories: [Deep Reinforcement Learning]
---

<style>
.responsive-img {
    width: 100%;
}

@media (min-width: 992px) {
    .responsive-img {
        width: 75%;
    }
}
</style>

This post will discuss how to model the reinforcement learning problem using the mathematical framework of a Markov Decision Process (MDP). We'll cover what an environment is in reinforcement learning, its components, and how to model it through an MDP.

To understand what we are modeling, we must first familiarize ourselves with the components of reinforcement learning:

## Components of Reinforcement Learning

- *Reinforcement Learning* is A solution for managing complex, uncertain sequential decision-making.
    - *Complex:* Pertains to the large scale of the state and action spaces that the agent needs to navigate.
    - *Sequential:* Denotes the delayed effect of an agent's actions, essentially the credit assignment problem.
    - *Uncertainty:* Highlights the unpredictability of the impact of an agent's actions on the environment, tying to balance the exploration vs exploitation trade-off.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/reinforcement-learning-interaction-cycle.jpg" class="responsive-img" />

### The agent: The decision maker

- **Agents:** These are entities solely responsible for making decisions that may influence the environment.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/internal-steps.jpg" class="responsive-img" />

- **Agent's Improvement Process:**
    1. Interact
    2. Evaluate
    3. Improve

### The environment: Everything else
- The *environment* symbolizes the problem at hand. It encapsulates everything external to the agent, anything that's beyond the agent's control but responds to the agent's decisions.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/environment-process.jpg" class="responsive-img" />

Pay attention to how we try to emulate the possible reactions of the environment to the agent's actions.

## Unraveling the Environment:

- The environment is made up of states, actions, transition probabilities, and a reward function.

### States: Specific configurations of the environment
- A *state* provides a comprehensive description of the environment.

- **State Space:** A combiniation of all possible variables and values that can characterize the environment.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/state-space.jpg" class="responsive-img" />

- **Initial States:** A subset of states where the agent starts in the environment.

- **Terminal States:** The final state in an episodic task, any transition from this state will leads back to itself.

- **Observation:** The set of variables that the agent perceives. It might not be as comprehensive as a state.

- **Observation Space:** All possible values of the variables observed by the agent.

### Actions: A mechanism to influence the environment
- An *action* signifies a choice that an agent can make to potentially alter the environment. The set of actions available to an agent may vary across states and during the agent's learning process.

- **Action Space:** The set of all actions in all states.

### Transition Function: Consequences of agent actions
- A *transition function* determines how the environment changes in response to an action. 
- Denoted as $T(s, a, s')$, where $s$ is the current state, $a$ is the action taken, and $s'$ is the resulting state.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/transition-function.jpg" class="responsive-img" />

- **Stochastic Transitions:** Transitions that don't guarantee a single resulting state but could lead to multiple states, each with a different probability.

- In RL, we often assume that transition distributions remain stationary, whether they're stochastic or deterministic. While this assumption can be relaxed to some degree, for most agents, the transitions must at least appear stationary.

### Reward Function
- A *reward function* steers the agent towards its goal. It maps a state or an action to a scalar reward, indicative of the goodness but not necessarily the correctness of the agent's state or action.

- Reward signals supervise your agent. A denser reward signal leads to quicker learning but imposes more bias on the agent's task-solving approach. Conversely, a sparser (less frequent) reward signal results in a less biased agent, potentially leading to novel, emergent behavior.

- **Return:** The sum of the rewards collected in a single episode.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/reward-function.jpg" class="responsive-img" />


### Common Types of Environments: 

- **Grid-World Environment:** An environment that is a square grid of any size.
    - **Walk / Corridor:** A type of grid-world environment with a single row.

- **Bandit Environment:** An environment with a single non-terminal state, named 'bandit' as an analogy to a slot machine that will empty your pockets the same way bandits do.

#### Ways to represent an environment:

<img src="assets/img/posts/modeling-reinforcement-learning-problem/bandit-walk.jpg" class="responsive-img" />

<img src="assets/img/posts/modeling-reinforcement-learning-problem/bandit-walk-graph.jpg" class="responsive-img" />

**Table Form**

<img src="assets/img/posts/modeling-reinforcement-learning-problem/bandit-walk-table.jpg" class="responsive-img" />

## Markov Decision Process (MDPs): The engine of the environment
- *Markov Decision Processes (MDPs)* is a mathematical framework for modeling complex decision-making problems under uncertainty. It consists of system states, per-state actions, a transition function, a reward signal, a horizon, a discount factor, and an initial state distribution.

- In RL, it's often assumed that all environments operate based on an underlying MDP, whether this assumption holds true or not.

### Markov Property
- For a state to have the *markov property*, it must contain all necessary variables to make it independent of all other states.
- More formally, the probability of the next state, given the current state and action, is independent of the history of interactions.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/markov-property.jpg" class="responsive-img" />

-  The markov assumption is useful as it allows us to keep the number of variables in a state to a minimum since the more variables you add, the longer it will take the agent to learn. However, completely adhering to the markov assumption may be impractical or even impossible. 


### Horizon: Time changes what’s optimal
- A *time step* is a global clock synchronizing all parties and discretizing time.
- An *episode* is a sequence of consecutive time steps from the start to the end of an episodic task.

- **Planning Horizon:** It's the temporal depth the agent must plan for.
- **Finite Horizon:** It's a planning horizon that terminates after a specific number of steps.
- **Infite / Indefinite Horizon:** It's an unlimited planning horizon, assuming that the task can continue indefinitely.
- **Greedy Horizon:** It's a planning horizon of a single time step.


### Discount: The future is uncertain, value it less
- To handle the possibility of infinite sequences of interactions, we must convey to the agent that immediate rewards are more valuable than future ones. This concept is handled by introducing a *discount factor* that reduces the value of future rewards, stabilizing the learning of the task.
- Moreover, the more we look into the future, the more uncertainty we accumulate. Introducing a discount factor discounts these highly uncertain future rewards, preventing them from affecting our value estimates significantly.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/effect-of-discount-factor.jpg" class="responsive-img" />

- The discount factor, $\gamma$ or gamma, reduces the variance of the value prediction by considering future, more uncertain, rewards less than immediate ones, fostering urgency in the agent.

<img src="assets/img/posts/modeling-reinforcement-learning-problem/discount-factor.jpg" class="responsive-img" />



### Extensions to MDPs
- **Partially observable Markov decision process (POMDP):** When the agent can't fully observe the environment state.
- **Factored Markov decision process (FMDP):** It compactly represents the transition and reward functions, enabling the representation of large MDPs.
- **Continuous Markov decision process:** When either time, action, state, or any combination of them are continuous.
- **Relational Markov decision process (RMDP):** It allows combining probabilistic and relational knowledge.
- **Semi-Markov decision process (SMDP):** It allows the inclusion of abstract actions that take multiple time steps to complete.
- **Multi-agent Markov decision process (MMDP):** It allows multiple agents in the same environment.
- **Decentralized Markov decision process (Dec-MDP):** It allows multiple agents to collaborate and maximize a common reward.

### Putting it all together

<img src="assets/img/posts/modeling-reinforcement-learning-problem/mdps-vs-pomdps.jpg" class="responsive-img" />


## References

Morales, M. (2020). Grokking Deep Reinforcement Learning. Originally Published: October 15, 2020.

_All figures are sourced from this book._