# Project 1: Navigation - Report

### Implementation

The project implement a deep Q network that trained from the environment iteratively and demonstrate it's learnings at the end. The neural network has fully connected hidden layers each with 64 nodes, and relu-activition layers are added after each hidden layer. The implementation applies a few extra technique that further improves DQN, such as fixed Q targets with double DQN, experience replay, and soft update.

### Learning Algorithm

The learning algorithm is based on DQN with simple additions such as double DQN, experience replay, and soft update to improve the performance. On every step, the experience is added to memory. The replay memory has a buffer size of 1e5 in an effort to keep a large number of experiences while not stressing on memory. Every four steps, 64 random experiences will be sampled and used for training. The attempt to train on every four steps is to keep model update as frequent as possibly yet not every single step that make the training too slow. At training, it first calculates the Q target: Q_target = reward + gamma * Max_Q_next. Gamma is selected to be 0.99, which helps value the closer actions higher than future Q estimated rewards that's far away. The algorithm then arrive at the expected current Q value by calling the neural network with current action. Next it uses pytorch's mse_loss method to calculate loss, and Adam optimizer to optimize and update the network. Last but not least, it does a soft update on the network that used to estimate Q next. With a tau of 1e-3, this target network updates very slowly in an attempt to stabilized the training process. A neural network is used together with the Q learning techniques. The neural network contains 2 fully connected hidden layers each with 64 nodes, relu-activition layers are added after each hidden layer. 

### Plot of Rewards

![Alt text](Screenshot.png?raw=true "Number of Episode Trained vs Score")

A score of 16.0 was achieved after training. Please refer to Navigation.html for result.

### Ideas for Future Work

The network had been trained on a laptop without GPU access. The overall process took over an hour. For future training improvement, working on AWS could be a solution that speeds up the training process. At algorithmic level, prioritized experience replay is a technique can be tried to prompt experiences happen infrequently. 

