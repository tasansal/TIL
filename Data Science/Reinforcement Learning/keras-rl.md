# Keras Reinforcement Learning

Website: [Keras Low-Level RL](https://keras.io/examples/rl/) (not `keras-rl`, but RL with Keras)  
Source: [`keras-rl` GitHub](https://github.com/keras-rl/keras-rl)
Docs: [Here](https://keras-rl.readthedocs.io/en/latest/)

## Summary

* You can do RL directly with TensorFlow and Keras, however this library is a nice wrapper for modern methods.
* Works out-of-the-box with [OpenAI Gym](openai_gym.md)
* Supports (as of 4/10/2022)
  * Deep Q Learning (DQN)
  * Double DQN
  * Deep Deterministic Policy Gradient (DDPG) 
  * Continuous DQN (CDQN or NAF)
  * Cross-Entropy Method (CEM)
  * Dueling network DQN (Dueling DQN)
  * Deep SARSA

### Useful Links:
[Deep Q-Learning](https://arxiv.org/abs/1312.5602)  
[Keras - Atari Breakout (Deep-Q)](https://keras.io/examples/rl/deep_q_network_breakout/)  
[Keras - Cartpole [Proximal Policy Opt]](https://keras.io/examples/rl/ppo_cartpole/)