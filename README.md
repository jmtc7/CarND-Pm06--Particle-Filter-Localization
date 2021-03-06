# **Particle Filter-based Localization | Pm06**
### Project from the sixth module of the Self-Driving Car Engineer Udacity's Nanodegree

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

The aim of this project is to localize a car (its positions X and Y and its orientation *theta*) in a 2D map with sparse features using a Particle Filter (PF) based approach. The target was to obtain a low error and to compute all the simulated movement steps in real time.


This project uses the [Term 2 CarND Simulator](https://github.com/udacity/self-driving-car-sim/releases) in order to provide data to the *main.cpp* and to visualize this data, the estimated object position (blue circle) and the (X, Y and *theta*) errors of the predictions being compared with the ground-truth (blue car). 


In particular, the **goals** of this project are implementing the following points in the *src/particle_filter.cpp* file:
- The Particle Filter **initialization**, including the map sampling, hyper-parameter definition and particles creation.
- The PF **prediction step**, consisting in applying the motion model to the robot and the particles.
- The PF **update step** by performing data association and importance weights computation.
- The PF **resampling**.


The outcome of this project was a localization algorithm for its usage with 2D feature maps based in the Particle Filter. With the provided testing data, it managed to reach errors of 0.109, 0.114 and 0.004 for the car's X and Y positions (in meters) and its orientation (in radians), respectively, using 50 particles. This can be visualized in the following **YouTube demo**, where we can see the ground truth position (blue car), the estimated one (blue circle) and the observed features at each time (green lines connecting the car with the map features) in executions with 25, 50 and 100 particles:

[![Demo video](pm06.gif)](https://www.youtube.com/watch?v=TIojotfJl8k)


This work will be followed by a brief documentation/overview contained in this file. This project is a completed version of the sample project template provided by the Self-Driving Car Engineer Udemy's Nanodegree. The un-completed original version is [this repository](https://github.com/udacity/CarND-Kidnapped-Vehicle-Project).


## Installation and usage
This repository includes a file that can be used to set up and install [uWebSocketIO](https://github.com/uWebSockets/uWebSockets) for Linux systems (*install-ubuntu.sh*). For Windows you can use either Docker, VMware, or even [Windows 10 Bash on Ubuntu](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install uWebSocketIO. Please see the uWebSocketIO Starter Guide page in the classroom within the EKF Project lesson for the required version and installation scripts.

Once the install for uWebSocketIO is complete, the main program can be built and run by doing the following from the project's root directory:

```
./clean.sh # Delete files from previous builds
./build.sh # Compile the project
./run.sh # Execute and evaluate
```


## Testing data
The data used in the simulation (*map_data.txt*) is provided in a text file in the *data* folder of this repository. It consists in a series of landmark positions (X and Y coordinates in the global map coordinate system) followed by the landmark ID. The rest of the necessary data is provided by the [simulator](https://github.com/udacity/self-driving-car-sim/releases), such as the car velocity and yaw rate or the car observations in each filter iteration.


## Result analysis
As shown in the [YouTube](https://www.youtube.com/watch?v=TIojotfJl8k), we can appreciate a relevant error reduction when using 50 particles instead of 25 (from [0.136, 0.122, 0.005] to [0.109, 0.114, 0.004]). However, when I augment the number of particles to a 100, the error does not varies too much ([0.110, 0.107, 0.004]), even the computational cost is way bigger. This proofs how important it is to know our algorithms and to configure them properly to optimize the balance between required resources and results.
