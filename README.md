# Recurrent Replay Non-Distributed Deeper Denser DQN - Gravitar
Submitted as part of the degree of Msci Natural Sciences (3rd year) to the Board of Examiners in the Department of Computer Sciences, Durham University. 
This summative assignment was assessed and marked by the professor of the module in question:
## Grade: 1st - 100/100, 1st in year (of 136 students).
> "This is an amazing agent that’s very impressive to see at an undergraduate RL course - you’ve clearly done
> a huge amount of research and spent many hours for this. It has top of the class high score - you could
> probably even publish some of the work here. Your agent design choices are all highly appropriate, picking
> many ways to balance exploration and exploitation with a recurrent architecture that can help with stability
> and analysis of long-term rewards while exploring within the difficult Gravitar environment. The agent in
> the video extremely intuitive, playing better than many humans. The convergence is outstanding, especially
> after 100k steps; increasing steadily after such a large amount of training is quite an achievement!" - Dr Chris G. Willcocks

## Architecture:
Recurrent Replay Non-Distributed Deeper Denser DQN (R2ND4) is a Reinforcement Learning Agent that was initially designed as a non-distributed version of R2D2 [1] and was later developed further. R2ND4 uses: 
* Double Q-Learning [4];
* Prioritized Replay Buffer [6] using transition sequences of length 120 [1];
* n-step Bellman Rewards and Targets [4];
* Invertible Value Function Rescaling (forward and inverse) [7];
* A Duelling Network Architecture [3];
* A CNN followed by an LSTM for state encodings (with burnin as per R2D2 [1]);
* A Novel Deeper Denser Architecture using Skip-Connections, inspired by D2RL's [2] findings;
* Gradient Clipping as recommended in [3];
* Frame Stacking;
* Observations resized to 84x84 and turned to greyscale using OpenCV.

**Note:** For training on a less complex environment or if prioritising faster convergence, the 2nd much wider linear layer from the Value and Advantage networks containing the skip connection to the CNN output can be removed entirely to allow the model to converge to a lower 3,000 rolling mean score after 180k episodes (and reaching 3,500 after 500k episodes).

## Contents:
* An interactive notebook with all code for R2ND4 provided, with detailed in-line comments and descriptions to aid others in using this notebook as a learning resource - R2ND4.ipynb.
* An example video of the (partially) converged agent playing Gravitar, achieving a score of 5050. This episode was not an anomaly nor an unusual result (see graph).
* Training logs for statistical analysis or plotting of data.
* A graph of the training scores over time. 
* 
To run notebook code (R2ND4.ipynb) open in Jupyter or upload to Google Colab. 

## Results:

### Demo video (taken from my [portfolio page](https://github.com/shadowbourne)):
  >![Gifdemo2](https://user-images.githubusercontent.com/18665030/136660504-c89f9c89-41d3-4070-982f-23473bda3fcb.gif)
  >
  > We were tasked with creating a Reinforcement Learning agent to play the notoriously difficult Gravitar from the Atari-57 suite. I therefore decided to look for the current state-of-the-art Reinforcement Learning model for Atari ([R2D2](https://openreview.net/pdf?id=r1lyTjAqYX)) and re-created it to the best I could with my limited hardware. I produced the best agent in the class, and my convergence graph was used as exemplar feedback to the cohort.


### Training graph of mean scores (rolling average over past 100 episodes):
![Training graph](training-graph.png?raw=true "Training graph")
**Note:** This graph was selected as the best in the cohort and included in the class feedback as one of two exemplar graphs.

As is clear from the graph, the agent has not yet fully converged.


## References:
The findings of the following papers were relied upon for the design of R2ND4:
* Recurrent Experience Replay in Distributed Reinforcement Learning (R2D2) [1]: https://openreview.net/forum?id=r1lyTjAqYX;
* D2RL: Deep Dense Architectures in Reinforcement Learning  [2]: https://arxiv.org/abs/2010.09163;
* Dueling Network Architectures for Deep Reinforcement Learning [3]: https://arxiv.org/abs/1511.06581;
* Rainbow: Combining Improvements in Deep Reinforcement Learning [4]: https://arxiv.org/abs/1710.02298;
* Distributed Prioritized Experience Replay [5]: https://arxiv.org/abs/1803.00933;
* Prioritized Experience Replay [6]: https://arxiv.org/abs/1511.05952;
* Observe and Look Further: Achieving Consistent Performance on Atari [7]: https://arxiv.org/abs/1805.11593.

The codebase is based upon and borrows from the following sources:
* SEED RL: Scalable and Efficient Deep-RL with Accelerated Central Inference [8]: https://github.com/google-research/seed_rl;
* Reinforcement Learning Assembly (rela) [9]: https://github.com/facebookresearch/rela;
* RL Adventure [10]: https://github.com/higgsfield/RL-Adventure;
* OpenAI Baselines [11]: https://github.com/openai/baselines;
* Distributed Reinforcement Learning [12]: https://github.com/chagmgang/distributed_reinforcement_learning.
