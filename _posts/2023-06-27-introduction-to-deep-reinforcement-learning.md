---
title: "Introduction to Deep Reinforcement Learning"
author: "Ahad Jawaid"
layout: post
date: "2023-06-27"
thumbnail: assets/img/posts/introduction-to-deep-reinforcement-learning/neural.png
description: My notes on Deep Reinforcement Learning (DRL) based on the first chapter of the 'Grokking Deep Reinforcement Learning' by Miguel Morales.
categories: [Deep Reinforcement Learning, Notes]
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

## Artificial Intelligence (AI)

* Artificial Intelligence (AI) is a domain of computer science dedicated to developing software capable of exhibiting attributes of intelligence.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/subfields_of_artificial_intelligence.jpg" class="img-fluid rounded z-depth-1" %}

## Machine Learning (ML)

* Machine learning, a subset of AI, tackles problems necessitating intelligent solutions by learning from data.
* **Supervised Learning (SL):** A method that learns from labeled data.
    * E.g., handwritten-digit-recognition 
* **Unsupervised Learning (UL):** A method that learns from unlabeled data
    * E.g., customer segmentaiton
* **Reinforcement Learning (RL):** A method that learns from trial and error
    * E.g., pong-playing agent

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/main_branches_of_machine_learning.jpg" class="img-fluid rounded z-depth-1" %}

## Deep Learning (DL)

* Deep Learning employs multi-layered non-linear function approximations, also known as neural networks, to address ML tasks. Essentially, it is a suite of techniques that utilize neural networks to solve ML challenges.


{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/deep_learning_is_a_powerful_toolbox.jpg" class="img-fluid rounded z-depth-1" %}

### Deep Reinforcement Learning (DRL)

* Deep Reinforcement Learning learns through trial and error from feedback that’s simultaneously sequentially, evaluative, and sampled by leveraging non-linear function approximation (neural networks).

## Reinforcement Learning (RL)

### Similar fields

* **Reinforcement Learning (RL):** Investigates methods of resolving complex sequential decision-making problems under uncertain conditions.
* **Control Theory (CT)**: Examines methods of controlling complex known dynamic systems.
* **Operations Research (OR)**: Investigates decision-making under uncertain conditions, generally featuring a larger action space than in DRL.
* **Psychology**: Studies human behavior, which frequently encapsulates complex sequential decision-making problems under uncertainty.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/the_synergy_between_similar_fields.jpg" class="img-fluid rounded z-depth-1" %}

### Agent and Enviroment

* **Agent:** Refers exclusively to the decision-making entity.
    * For instance, if you are training a robot arm to pick up a toy, the agent is the code that makes the decisions, not the robot arm itself.

* **Environment:** Includes everything external to the agent, beyond the agent's control, and everything that follows the agent's decisions.
    * In the context of training a robot arm to pick up a toy, the objects to be picked up, the tray where the objects reside, atmospheric conditions like wind, and even the robot arm itself are all considered parts of the environment.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/boundary_between_agent_and_environment.jpg" class="img-fluid rounded z-depth-1" %}

### States and Observations

* **State Space:** The set of all possible variables and values that can represent the state of the environment.
* **State:** A comprehensive description of the environment, or an instantiation of the state space.
* **Observation:** A partial or incomplete description of the environment.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/states_vs_observations.jpg" class="img-fluid rounded z-depth-1" %}

### Reinforcement Learning Cycle

* **Transition Function:** The mapping from the agent's action to a potentially new state.
* **Reward Function:** The mapping from the action taken to the potential reward signal.
    * Goals are defined via the reward function.
* **Model:** A set of the transitions and rewards.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/the_reinforcement_learning_cycle.jpg" class="img-fluid rounded z-depth-1" %}

#### Agent’s Improvement process:

1. Interact with the environment.
2. Evaluates its behavior.
3. Improves its responses.

#### Agent’s can be designed to learn:

* **Policy:** The mapping from observations to actions.
* **Models:** A model of the environment on mappings. 
* **Value Functions:** The mapping of a state to its estimated value.

### Experiences

* **Time Step:** A single cycle of interaction between the agent and the environment.
* **Experience:** The set consisting of the state, the action, the reward, and the new state in a single time step.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/experience_tuples.jpg" class="img-fluid rounded z-depth-1" %}


* **Episodic Task:** Tasks that have a natural ending or goes on finitely many step.
    * E.g., video games
* **Continuing Task:** Tasks that don't have a natural ending or could go on indefinitely.
    * E.g., learning forward motion


### Credit Assignment Problem

* **Temporal Credit Assignment Problem:** the challenge in determining which state and/or action is responsible for a reward the agent recieves
    * Usually occurs when the agent may have delayed rewards from an action or state that caused it hence the temporal aspect of the problem

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/temporal_credit_assignment_problem.jpg" class="img-fluid rounded z-depth-1" %}

### Exploration vs. Exploitation

* **Evaluative Feedback:** Feedback that provides an indication of performance but not correctness.
* **Exploration versus Exploitation trade-off:** The balance between collecting new information from the environment and using known information to maximize rewards.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/exploration_vs_exploitation.jpg" class="img-fluid rounded z-depth-1" %}

### Sampled Feedback

* Learning from sparse or weak feedback becomes more challenging with samples only. The agent must be capable of generalizing to learn from sampled feedback.

{% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/learning_from_sampled_feedback.jpg" class="img-fluid rounded z-depth-1" %}

### Types of Agents

* **Policy-based:** Designed to approximate policies.
* **Model-based:** Designed to approximate models.
* **Value-based:** Designed to approximate value functions.
* **Actor-critic:** Designed to approximate both policies and value functions.

### Pros and Cons

**Strength:** Reinforcement learning excels in mastering specific tasks.

**Weaknesses:** To learn a well-performing policy, it generally requires millions of samples.

## History of Deep Reinforcement Learning

* **Alan Turing - 1930:** Developed the Turing Test, a test of a machine's ability to exhibit intelligent behavior indistinguishable from that of a human.

*  **John McCarthy - 1955:** Coined the term “Artificial Intelligence”.

* **Andrew Ng - 2002:** Trained an autonomous helicopter to perform stunts by observing human-expert flights using inverse reinforcement learning.

* **Nate Kohl and Peter Stone - 2002:** Applied policy-gradient methods to train a soccer-playing robot.

* **Mnih et al. - 2013, 2015:** Introduced the DQN algorithm, which learned to play Atari games from raw pixels.
    {% include figure.liquid loading="eager" path="assets/img/posts/introduction-to-deep-reinforcement-learning/atari_dqn.jpg" class="responsive-img" class="img-fluid rounded z-depth-1" %}* 

* **Silver et al. - 2014:** Released the deterministic policy gradient (DPG) algorithm.

* **Lillicrap et al. - 2015:** Improved DPG with deep deterministic policy gradient (DDPG)

* **Schulman et al. - 2016:** Released trust region policy optimization (TRPO) and generalized advantage estimation (GAE) methods.

* **Sergey Levine et al. - 2016:** Published Guided Policy Search (GPS)

* **Silver et al. - 2016:** Demonstrated AlphaGo

* ...

## References

Morales, M. (2020). Grokking Deep Reinforcement Learning. Originally Published: October 15, 2020.

_All figures are sourced from this book._