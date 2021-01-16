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

![Rewards per training episode — Using α=.0001, γ=.99, and ε = 0.99941](https://github.com/peterburgs/lander/blob/master/src/img/chart3.png)

Notice how the behavior of the agent is very erratic during the first three thousand iterations, but as it gets closer to the end, it becomes less intermittent because it starts exploiting what it has learned.

![Reward obtained when testing the agent using the learned weights during 100 episodes — Using α=.0001, γ=.99, and ε = 0.99941](https://github.com/peterburgs/lander/blob/master/src/img/chart4.png)

Finally, the above chart shows the results obtained by the agent after training is complete. In this case, the agent was run three times, and the individual episode reward was plotted. Notice how no crashes happened during the 100 episodes for any of the runs indicating the training process was successful and our agent solved the environment. The average reward for each run, as shown in the legend of the chart, was 209, 213, and 216.

## Some images when run the project

Lander after being trained could land successfully.

![success](https://github.com/peterburgs/lander/blob/master/src/img/lander-success.png)

Lander before being trained usually crashes when landing.

![success](https://github.com/peterburgs/lander/blob/master/src/img/lander-fail.png)

## References

V. Mnih, K. Kavukcuoglu, D. Silver, A. A. Rusu, J. Veness, M. G. Bellemare, A. Graves, M. Riedmiller, A. K. Fidjeland, G. Ostrovski, S. Petersen, C. Beattie, A. Sadik, I. Antonoglou, H. King, D. Kumaran, D. Wierstra, S. Legg, and D. Hassabis. _Human-level Control Through Deep Reinforcement Learning._ (2015). Nature, 518(7540):529–533. http://dx.doi.org/10.1038/nature14236.

T. Lillicrap, J. Hunt, A. Pritzel, N. Heess, T. Erez, Y. Tassa, D. Silver, and D. Wierstra. _Continuous Control With Deep Reinforcement Learning._ (2015). arXiv preprint arXiv:1509.02971.

R. Liu, J. Zou. _The Effects of Memory Replay in Reinforcement Learning._ (2017). arXiv:1710.06574.
