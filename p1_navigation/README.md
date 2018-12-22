[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

[image2]: ./plots/agent_001.png "Early Test"
[image3]: ./plots/agent_002.png "Final Parameters"


# Project 1: Navigation

### Introduction

This project considers the application of deep reinforcement learning to the colleciton of bananas as an agent navigates a square geometry world space.

#### Rewards and Goals
A reward of +1 is awarded when a yellow banana has been collected, and a reward of -1 is awared for a blue banana. The goal is for the agent to collect as many yellow bananas as possible and avoid blue bananas.

#### Environment Definition

The state space has 37 dimensions, including the agent's velocity. Forward motion of the agent includes ray-based perception of objects around the agent's direction.  The goal is for the agent to learn how to best select actions (through rewards).  Four discrete motion actions are available to the agent:

- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

#### Solving the Game

The task is episodic, and in order to solve the environment the agent must recieve an average score of +13 over 100 consecutive episodes.

### Code Architecture

There are three elements to the program architecture: the environment, the agent, and the network model>

#### Navigation.ipynb
This defines the interaction between the agent and the neural network model. The Unity Banana environment is defined and explored, reporting back the 37 dimensions of the space. A Deep Q Network (DQN) function is defined which defines the episode loop, number of episodes, and references the agent.

#### dqn_agent.py
A basic DQN agent is defined, including intialization, setp, act, learn, and soft_update functions. A replay buffer is also defined. The neural network model is called from the QNetwork, which is contained in the model.py file.

#### model.py
A relavitly simple neural network is defined with a ReLu activation function and fully connected layers, coded in PyTorch. The QNetwork class is defined which is called from the agent.

| Layer | In         | Out         |
|-------|------------|-------------|
| fc1   | state_size | 64          |
| fc2   | 64         | 64          |
| fc3   | 64         | action_size |


### Performance
The environment was solved in 382 episodes with Average Score = 13.03

Graphs of the scores and episode numbers are shown below with the associated parameters listed in the titles:

![alt text][image2]

![alt text][image3]


### Future Improvements
Although the current implementation solves the environments, different approaches can be evlauted and their relative performances compared to achieve better results.

In particular, the use of actor-critic or dueling networks would ideally lead to improved results, similar to the performance improvements seen in Generative Adversarial Network (GAN) design which have been used in other deep learning applications.