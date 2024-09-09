Last updated date: 221014_1551
## 1. Run the experiment
1. Set parameters in `parsed_args_ssd.py`. 
   Main parameters
   1. args.env
   - Used in `sequential_social_dilemma_games/social_dilemmas/env/env_creater.py` to define the environment.
   2. args.num_agents 
   3. args.num_episodes
   4. args.save_freq
2. Run `main_ssd.py`.

## 2. Get the test results
### 2-1. Get the test results from multiple (or single) saved networks
1. Set parameters in `evaluate_ssd/evaluate_ssd_main.py`.
- For example, set the value (string) `../results_ssd/<your_folder_name_in_results_ssd>/saved/*.tar` for the key `single_alpha` in the dict `path_pol_dir_dict`.
2. Run `evaluate_ssd/evaluate_ssd_main.py`.
- It will save the test results in the evaluation folder that is in `results_ssd` folder. 
- Folder name (in the `results_ssd` folder) will be `evaluation_<current_time>`. 
- File name will be `test_results_<current_time>`.
- You only need `test_results_<current_time>.tar` (and `test_results_<current_time>.png`).
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