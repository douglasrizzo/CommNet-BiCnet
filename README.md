# CommNet-BiCnet
[CommNet](https://arxiv.org/abs/1605.07736) and [BiCnet](https://arxiv.org/abs/1703.10069) implementation in TensorFlow.

## Training
Train CommNet using DDPG algorithm:
```sh
python train_comm_net.py
```

Train BiCNet:
```sh
python train_comm_net.py
```

## Visualization
To view the training process, call `tensorboard --logdir=summaries`, where summaries is a directory inside the repo in which training logs are saved to.

## Hyperparameter search
To find the optimal hyperparameters such as `actor_lr` or `critic_lr`, a simple grid search has been implemented. It launches multiple instances of the trainer in parallel based on the number of CPU cores.
```sh
python hypersearch.py
```

## Guessing sum environment
It is a simple game described in the [BiCnet](https://arxiv.org/abs/1703.10069) paper for testing if the communication works. The environment implements the crucial methods of the core gym interface from OpenAI.

Each agent receives a scalar sampled between `[−10, 10]` under a truncated Gaussian. Each agent needs to output the sum of all inputs received among the agents. An agent gets a normalized reward between `[0, 1]` based on the absolute difference between the sum and its output.

## Results
Maximum Q-value and reward for CommNet (orange) and BiCNet (blue) in the guessing sum environment.

![](docs/reward_2agents.png)

![](docs/qmax_2agents.png)