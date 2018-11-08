# Project 1: Continuous Control

## Introduction

This file describes the implementation of the Continuous Control project, such us the choosen algorithm for the DDPG agent to the files composing the project.

## DDPG Algorithm

For this project the **Deep Deterministic Policy Gradient** algorithm was selected in order to solve the environment. This algorithm combines the actor-critic approach with the Deep Q Network algorithm using Deep Networks for aproximating the actor and the critic which excels in continuous action spaces environments. In order to obtain more stability during the learning process the *soft update* of the target network and the local network were delayed every 5 learning steps. No noise was introduce to the action values

## Project files

The project contains three files:
	
- *Continuous_control.ipynb*: This is the main file implemented as a jupyter notebook that contains all the necessary code in order to get the Unity Environment set up and running and the agent trained and tested. To execute the file just follow the instructions within the notebook. You will find all the descriptions regarding the code as well as the plots for agent evaluation.

- *ddpg_agent.py*: This python file contains the class of the DDPG agent as well as the ReplayBuffer class.

- *ddpg_model.py*: File with the Actor and Critic's deep networks implemented in pytorch.

- *replaybuffer.py*: File containing the Replay buffer for experience replay.

### Classes description

- *Agent*: Main class that implements the DDPG learning algorithm. Contains the principals functions for the learning process such as step or act.
- *ReplayBuffer*: Class that implements the experience replay memory.
- *Actor*: Deep Neural Network class, contains 3 fully connected layers with 400 neurons for the first layer and 300 neurons for the second and third layer, each and *relu* as activation function except for the output layer that has a Tanh activation function to constrain the output between -1 and 1 (action space). Input and output layers have the state and action size input/output dimension respectively.
- *Critic*: Deep Neural Network class implementing the Critic: contains 3 fully connected layers with 400 for the firs layer and 300 for the second and third. Each layer uses a *relu* activation function. The first layers inputs the state values and the second layer concatenates the first layer output and the action values as proposed in the DDPG paper.

## Hyper-parameters

The selection of the hyper-parameters were the following:
- **Critic LR = Actor LR = 1e-3** *learning rate*
- **Gamma = 0.99** *discount factor*
- **TAU = 1e-3** *parameter for soft update between target and local network weights*
- **UPDATE_EVERY = 5** *target network update every 5 steps*
- **BATH_SIZE = 128** *mini batch size for experience replay sampling*