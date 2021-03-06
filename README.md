# Deep Reinforcement Learning with Transfer Learning - DJI Tello Drone and Real Environment (DRLwithTL-Real)

## What is DRLwithTL-Real?
This repository uses Transfer Learning (TL) based approach to reduce on-board computation required to train a deep neural network for autonomous navigation via Deep Reinforcement Learning for a target algorithmic performance. A library of 3D realistic meta-environments is manually designed using Unreal Gaming Engine and the network is trained end-to-end. These trained meta-weights are then used as initializers to the network in a **real** test environment and fine-tuned for the last few fully connected layers. Variation in drone dynamics and environmental characteristics is carried out to show robustness of the approach.
The repository containing the code for **simulated** environment on a **simulated** drone can be found @ [DRLwithTL-Sim](https://github.com/aqeelanwar/DRLwithTL)

![Cover Photo](/images/tello.png)
![Cover Photo](/images/cover.png)


## Installing DRLwithTL-Sim
The current version of DRLwithTL-Sim supports Windows and requires python3. It’s advisable to [make a new python virtual environment](https://towardsdatascience.com/setting-up-python-platform-for-machine-learning-projects-cfd85682c54b) for this project and install the dependencies. Following steps can be taken to download get started with DRLwithTL-Real

### Clone the repository
```
git clone https://github.com/aqeelanwar/DRLwithTL_real.git
```
### Install required packages
The provided requirements.txt file can be used to install all the required packages. Use the following command
```
cd DRLwithTL_real
pip install –r requirements.txt
```
This will install the required packages in the activated python environment.


## Running DRLwithTL-Real
Once you have the required packages, you can take the following steps to run the code

### Download imagenet weight (Optional)
Download the imagenet weights for the network from the [here](https://gtvault-my.sharepoint.com/:u:/g/personal/manwar8_gatech_edu/Ef52J48ugL1CnrWmrUVj0JgBOd1-PIiPU2ZUcQ5mqnP0tA?e=QD53S0) and place it in 
```
DeepNet/models/imagenet.npy
```

### Connect with DJI Tello
1. Turn DJI Tello On
2. Connect your workstation with DJI Tello over Wi-Fi

### Modify the configuration file (Optional)
The RL parameters for the DRL algorithm can be set using the provided config file and are self-explanatory.

```
cd DRLwithTL_real\configs
notepad config.cfg (#for windows)
```

### Run the Python code
The DRL code can be started using the following command

```
cd DRLwithTL
python main_code.py
```

While the simulation is running, RL parameters such as epsilon, learning rate, average Q values and loss can be viewed on the tensorboard. The path depends on the env_type, env_name and train_type set in the config file and is given by 'DeepNet/models/&lt;run_name>/&lt;env_type>/'. An example can be seen below



```
cd DeepNet/models/Tello_indoor/VanLeer/
tensorboard --logdir agent

```

### Runtime Controls
Pygame screen can be used to control the DJI Tello drone on the fly. Following control keys are supported

1. **'M'** : Top toggle between automatic and manual mode. In automatic phase, the drone uses RL training to navigate around the environment using epsilon greedy algorithm. In manual phase (default starting phase) the user has control over the drone and can use **left, right, up, down, w, a, s, d** keys to navigate. All the other control keys mentioned below only works when the drone is in the manual mode
2. **'Escape'**: Quits the code
3. **'L'** : Save the DNN weights and Replay memory to the path specified in the config file.

## Citing
If you find this repository useful for your research please use the following bibtex citations

```
@ARTICLE{2019arXiv191005547A,
       author = {{Anwar}, Aqeel and {Raychowdhury}, Arijit},
        title = "{Autonomous Navigation via Deep Reinforcement Learning for Resource Constraint Edge Nodes using Transfer Learning}",
      journal = {arXiv e-prints},
     keywords = {Computer Science - Machine Learning, Statistics - Machine Learning},
         year = "2019",
        month = "Oct",
          eid = {arXiv:1910.05547},
        pages = {arXiv:1910.05547},
archivePrefix = {arXiv},
       eprint = {1910.05547},
 primaryClass = {cs.LG},
       adsurl = {https://ui.adsabs.harvard.edu/abs/2019arXiv191005547A},
      adsnote = {Provided by the SAO/NASA Astrophysics Data System}
}
```
```
@article{yoon2019hierarchical,
  title={Hierarchical Memory System With STT-MRAM and SRAM to Support Transfer and Real-Time Reinforcement Learning in Autonomous Drones},
  author={Yoon, Insik and Anwar, Malik Aqeel and Joshi, Rajiv V and Rakshit, Titash and Raychowdhury, Arijit},
  journal={IEEE Journal on Emerging and Selected Topics in Circuits and Systems},
  volume={9},
  number={3},
  pages={485--497},
  year={2019},
  publisher={IEEE}
}
```

## Authors
* [Aqeel Anwar](https://www.prism.gatech.edu/~manwar8) - Georgia Institute of Technology

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details
