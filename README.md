# OpenAI GYM'S Lunar Lander - by Peter Burgs & Starea

## Requirements

This project requires these libraries:

- Python version 3.7.9
- TensorFlow version 1.15.0
- OpenAI Gym version 0.18.0
- Numpy version 1.19.2

To install them all, make sure you activate a virtual environment and then run the following commands:

```shell
$ pip install numpy tensorflow gym
$ pip install Box2D
```

## Run this project in JupyterLab

We work with JupyterLab version 2.2.6 installed in Anaconda. Make sure your python is version 3.7.

![JupyterLab](https://github.com/peterburgs/lander/blob/master/src/img/anaconda.png)

There are 2 folders:

- lander_after: the result after training the model.
- lander_before: when the model has not been trained.

Path to file:

```shell
./src/lander_after (or lander_before)/lunar_lander.ipynb
```

![File](https://github.com/peterburgs/lander/blob/master/src/img/file.png)

You can run the code in training or testing mode.

![Train||Test](https://github.com/peterburgs/lander/blob/master/src/img/train-test.png)

- To train the agent, make sure the `TRAINING` constant is set to `True`.
- Setting the `TRAINING` constant to `False` will run the simulator using the previously saved weights. I included as part of this repository a set of weights that can be used to test the agent without needing to train it first (inside the `/weights` folder).

The output of the simulator displays the episode number, the reward obtained on the current episode, the accumulated reward over the last 100 episodes, and the current value of epsilon. Here is an example of what this looks like:

```
Alpha: 0.0001 Gamma: 0.990 Epsilon 0.99941
0, -100.90, -100.90, 1.00
1, -148.32, -124.61, 1.00
2, -184.54, -144.59, 1.00
3, -188.26, -155.50, 1.00
4, -339.68, -192.34, 1.00
5, -114.51, -179.37, 1.00
6, -335.28, -201.64, 1.00
7, -166.12, -197.20, 1.00
8, -152.09, -192.19, 0.99
9, -400.20, -212.99, 0.99
10, -278.13, -218.91, 0.99
...
```

## Hyperparameters in the source code

The specific values for the hyperparameters that I explored during the implementation of the simulator are set up in the source code. Here are the more important ones:

```
LEARNING_RATE = [0.01, 0.001, 0.0001]
DISCOUNT_FACTOR = [0.9, 0.99, 0.999]
EPSILON_DECAY = [0.99910, 0.99941, 0.99954, 0.99973, 0.99987]
```

Feel free to change these values or include your own. Whatever it takes to make things run better.

## Agent results

Here is a look at the individual reward obtained by our agent while training using the best set of hyperparameters selected from the previous experiments. The accumulated reward is also displayed for context:

![Rewards per training episode — Using α=.0001, γ=.99, and ε = 0.99941](https://github.com/peterburgs/lander/blob/master/src/img/chart3.jpg)

- After 3000 to 4000 episodes, the results quite good.
- After 5000 episodes, the lander knows how to land successfully, 100 testing episodes show that more than 95 testing episodes are successful.

## Some images when run the project

`Before training: the lander always fail to land`

![success](https://github.com/peterburgs/lander/blob/master/src/img/before.gif)

`After training: the lander lands successfully`

![success](https://github.com/peterburgs/lander/blob/master/src/img/after.gif)

`After training 5000 episodes: the result looks quite good, the average reward is more than 200 which is pretty excellent.`

![success](https://github.com/peterburgs/lander/blob/master/src/img/training-result.gif)

## References

Automatic identification of fossils and abiotic grains .... https://arxiv.org/pdf/2009.11429

Neural networks and deep learning. http://neuralnetworksanddeeplearning.com/chap1.html

Neural networks and deep learning. http://neuralnetworksanddeeplearning.com/chap1.html

Introduction to Neural Networks: Part 2 | by Syed Faraaz .... https://codeburst.io/introduction-to-neural-networks-part-2-d85eb772e5e

Neural networks and deep learning. http://neuralnetworksanddeeplearning.com/chap1.html

Introduction to RL and Deep Q Networks | TensorFlow Agents. https://www.tensorflow.org/agents/tutorials/0_intro_rl

Deep Q-Learning | An Introduction To Deep Reinforcement .... https://www.analyticsvidhya.com/blog/2019/04/introduction-deep-q-learning-python/

GitHub - svpino/lunar-lander: OpenAI Gym's LunarLander-v2 .... https://github.com/svpino/lunar-lander/
