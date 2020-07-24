# DOOR-SLAM

These documents are installation instructions for MRG usage with mostly MRG forked repos but with the original citations and references

## Installation without docker (MRG)

1) Install argos3
You can either do this with a .deb file **(recommended)**
```
[ARGoS Download Page](https://www.argos-sim.info/core.php)
```

or by building and installing from source
```
cd ~
git clone https://github.com/ilpincy/argos3.git argos3
cd argos3
mkdir build_myrobot
cd build_myrobot
cmake -DARGOS_BUILD_FOR=myrobot ../src
make
make doc
sudo make install
cd ~
```
2) Install Buzz
```
cd ~
git clone https://github.com/MISTLab/Buzz.git buzz
cd buzz
mkdir build
cd build
cmake ../src
make
cd buzz/build
sudo make install
sudo ldconfig
cd ~
```
3) Install Multi-Robot separators + source the ROS ws
```
sudo apt-get install ros-melodic-rtabmap-ros
cd ~
git clone --recurse-submodules git@github.com:MarineRoboticsGroup/multi_robot_SLAM_separators.git
cd multi_robot_SLAM_separators/ros_ws
catkin init
cs src
catkin build
source devel/setup.bash
cd ~
```
4) Clone the current repo
```
cd ~
git clone --recurse-submodules git@github.com:MarineRoboticsGroup/DOOR-SLAM.git
cd DOOR-SLAM/simulation/robust_distributed_slam_simulation/buzz_slam/robust_distributed_mapper/cpp/
mkdir build && cd build
cmake ..
make -j6
cd ../../../src 
mkdir build && cd build
cmake ..
make -j6
```
5) Run 
```
cd ../../../../argos_simulation
argos3 -c robust_distributed_slam_dataset.argos
```
[Read the paper!](https://arxiv.org/abs/1909.12198)
[Code documentation here!](https://mistlab.ca/DOOR-SLAM/)

[<img src="docs/doorslam.png" width="640" height="360" />](http://www.youtube.com/watch?v=h0bqURQlZGA "DOOR-SLAM: Distributed, Online, and Outlier Resilient SLAM for Robotic Teams")

If you reuse parts of this work, please cite:
```
Pierre-Yves Lajoie, Benjamin Ramtoula, Yun Chang, Luca Carlone, 
and Giovanni Beltrame,
“DOOR-SLAM: Distributed, online, and outlier resilient SLAM for robotic teams,” 
Tech. Rep., 2019, arXiv preprint: 1909.12198.
```
BibTex:
```
@misc{lajoie2019doorslam,
    title={DOOR-SLAM: Distributed, Online, and Outlier Resilient SLAM 
    for Robotic Teams},
    author={Pierre-Yves Lajoie and Benjamin Ramtoula and Yun Chang and 
    Luca Carlone and Giovanni Beltrame},
    year={2019},
    eprint={1909.12198},
    archivePrefix={arXiv},
    primaryClass={cs.RO}
}
```

