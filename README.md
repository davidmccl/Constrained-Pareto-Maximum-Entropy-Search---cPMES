# Algorithmic Contract Design with Reinforcement Learning Agents

This repository contains the code associated with the paper titled **"Algorithmic Contract Design with Reinforcement Learning Agents."** The cPMES framework leverages Multi-Objective Bayesian Optimization to optimize the contract design, aligning the joint policies of the agents with the principal's objective. 

## Overview

The goal of this project is to provide a reproducible implementation of cPMES. The framework is built upon a combination of Multi-Objective Bayesian Optimization (BO) and the Multi Type Mean Field Reinforcement Learning algorithm to tackle the problem of efficient contract design with Reinforcement Learning agents.

## Repository Structure

- **`sequential_social_dilemma_games/`**: Contains the source code for the Cleanup Environment adapted from (https://github.com/eugenevinitsky/sequential_social_dilemma_games) and the Multi Type Mean Field RL (Subramanian et al. [1])
- **`evaluate_ssd/`**: Includes scripts to run the testing episodes. 
- **`plot/`**: Includes scripts to generate plots.
- **`spec-file.txt`**: A list of dependencies required to run the code.


## 1. Run the experiment
1. Set parameters in `parsed_args_ssd.py`. 
   Main parameters
   1. args.env
   - Used in `sequential_social_dilemma_games/social_dilemmas/env/env_creater.py` to define the environment.
   2. args.num_agents 
   3. args.lv_penalty 
   4. args.num_episodes
   5. args.save_freq
2. Run `main_ssd.py`.

## 2. Get the test results
### 2-1. Get the test results from saved networks
1. Set parameters in `evaluate_ssd/evaluate_ssd_main.py`.
- For example, set the value (string) `../results_ssd/<your_folder_name_in_results_ssd>/saved/*.tar` for the key `single_alpha` in the dict `path_pol_dir_dict`.
2. Run `evaluate_ssd/evaluate_ssd_main.py`.
- It will save the test results in the evaluation folder `results_ssd`. 
### 2-2. Get the video from the saved network
1. Set parameters in `evaluate_ssd/evaluate_ssd_save_video.py`.
- Contrast to the Section 2-1, you must set a specific `.tar` file, not multiple `.tar` files.
- The function to get videos from the multiple `.tar` files has not been (and will not be) developed yet.
- In addition, you also have to set `num_tests` as `1` and `is_draw` as `True`.
2. Run `evaluate_ssd/evaluate_ssd_save_video.py`.
- It will save the video in the `../results_ssd/<evaluation_folder>/videos` folder. 
- Folder name (in the `results_ssd` folder) will be `evaluation_<current_time>`. 
- File name (in the evaluation folder) will be `trajectory_test_episode_<# of episodes trained>.mp4`.
- You only need `trajectory_test_episode_<# of episodes trained>.mp4`.

## Draw the figure that contains the collective rewards for the training and the testing
1. Set parameters in `plot/plot_ssd.py`.
- You need train outcomes (from `main_ssd.py`) and test outcomes (from `evaluate_ssd_main.py`). 
- You should set `folder_name`, `y_axis_limit`, `i`(total number of episodes), and `data_test_name`. 
- You don't have to change `data_train_name`.
2. Run `plot/plot_ssd.py`.
- It will save three figures, which are figures for train, test, and all, respectively. 

## References

[1] Subramanian, S. G., Poupart, P., Taylor, M. E., & Hegde, N. (2022). *Multi Type Mean Field Reinforcement Learning*.

## Citation

If you use this code in your research, please cite the paper:
```bash
@misc{molinaconcha2024algorithmiccontractdesignreinforcement,
      title={Algorithmic Contract Design with Reinforcement Learning Agents}, 
      author={David Molina Concha and Kyeonghyeon Park and Hyun-Rok Lee and Taesik Lee and Chi-Guhn Lee},
      year={2024},
      eprint={2408.09686},
      archivePrefix={arXiv},
      primaryClass={cs.MA},
      url={https://arxiv.org/abs/2408.09686}, 
}
