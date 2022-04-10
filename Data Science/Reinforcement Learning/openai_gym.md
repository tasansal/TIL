# OpenAI Gym

Website: [OpenAI Gym](https://gym.openai.com/)  
Source: [GitHub](https://github.com/openai/gym)  
Docs: [New](https://www.gymlibrary.ml/), [Old](https://gym.openai.com/docs/)

## Summary

* OpenAI Gym is a framework API for connecting physics engines and agents.
* Works out-of-the-box with [`keras-rl`](keras-rl.md)
* Has a bunch of existing environments.
* For custom problems you need:
  * Custom environment
  * Custom physics engine
  * Custom engine
* Can use [Pygame](https://github.com/pygame/pygame) for nice visualiation and demos.
* [Tiled](https://www.mapeditor.org/) is a cool tool to make 2D game assests with tiles.

### Useful Links:
[RL From Scratch](https://www.learndatasci.com/tutorials/reinforcement-q-learning-scratch-python-openai-gym/)  
[Bipedal Walker Env](https://github.com/openai/gym/blob/master/gym/envs/box2d/bipedal_walker.py)  
[Environments (from old docs)](https://gym.openai.com/envs/#classic_control)  
[Creating Custom Environments](https://blog.paperspace.com/creating-custom-environments-openai-gym/)

## Installation Details
`gym` has a bunch of extras with demo environments. Some of the physics engines are written in `C` and has to be installed carefully.

The [Mujoco](https://mujoco.org/) physics engine is free, but is not open-source. DeepMind bought them. They're in the process of open-sourcing right now (as of 4/10/2022).

## Lunar Lander Example
You can replce the environment for different stuff.  
This prints the current "observation" for each iteration.  
There is no brains behind it, the lunar lander will just do random actions.
```python
import gym

env = gym.make('LunarLander-v2')
for i_episode in range(20):
    observation = env.reset()
    for t in range(100):
        env.render()
        print(observation)
        action = env.action_space.sample()
        observation, reward, done, info = env.step(action)
        if done:
            print("Episode finished after {} timesteps".format(t + 1))
            break
env.close()
```
