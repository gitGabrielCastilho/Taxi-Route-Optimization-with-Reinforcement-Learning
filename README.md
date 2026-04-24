# Taxi Route Optimization with Reinforcement Learning

This project trains a Q-learning agent to solve Gymnasium's `Taxi-v4` environment. The notebook walks through environment setup, Q-table training, policy evaluation, reward tracking, and a final GIF that shows the learned taxi behavior.

## Project Overview

The goal is to teach an agent to pick up and drop off passengers efficiently in the taxi grid world. Because the environment has a discrete state and action space, a tabular Q-learning approach is enough to learn a usable policy.

The notebook covers:

- seeding the environment for reproducibility
- training a Q-table with an epsilon-greedy exploration strategy
- tracking episode rewards and epsilon decay during learning
- evaluating the learned policy on separate episodes
- rendering the trained agent and exporting the run as a GIF

## Repository Contents

- `notebook.ipynb` - complete training, evaluation, visualization, and GIF export workflow
- `requirements.txt` - Python dependencies required to run the notebook
- `taxi_agent_behavior.gif` - saved animation of the trained agent navigating the environment

## Training Configuration

The notebook uses the following core settings:

- algorithm: Q-learning
- training episodes: 2000
- evaluation episodes: 100
- maximum actions per episode: 100
- learning rate (`alpha`): 0.1
- discount factor (`gamma`): 0.99
- epsilon schedule: starts at 1.0, decays by 0.995, and bottoms out at 0.01
- random seed: 42

## Recorded Results

The saved notebook output reports these results after training:

| Metric | Value |
| --- | ---: |
| Final epsilon | 0.01 |
| Training success rate | 0.725 |
| Mean reward over last 100 training episodes | 6.05 |
| Evaluation success rate | 0.74 |
| Evaluation mean reward | -38.01 |
| Evaluation mean steps | 35.64 |
| Demo episode reward | 8 |

The training plot saved in the notebook shows a clear upward trend in reward while exploration steadily decays toward the minimum epsilon.

## Demo

The trained agent behavior is exported as a GIF:

![Trained taxi agent](taxi_agent_behavior.gif)

## Setup

1. Create and activate a virtual environment.
2. Install the dependencies from `requirements.txt`.
3. Launch Jupyter and open the notebook.

Example commands:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter notebook
```

If you use Git Bash or another shell, activate the virtual environment with the command that matches your shell.

## How to Run

1. Open `notebook.ipynb` in Jupyter or VS Code.
2. Run the cells from top to bottom.
3. Review the training reward and epsilon plots.
4. Run the final visualization cell to regenerate `taxi_agent_behavior.gif`.

## Dependencies

The project depends on:

- `numpy`
- `gymnasium`
- `imageio`
- `pygame`
- `matplotlib`
- `ipython`
- `jupyter`

## Notes

- The notebook uses `render_mode="rgb_array"` so frames can be captured and stitched into a GIF.
- Because the notebook sets seeds for NumPy and the environment, repeated runs should be reasonably reproducible.
- Results may still vary slightly across library versions.