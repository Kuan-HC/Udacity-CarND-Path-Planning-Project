# Udacity-CarND-Path-Planning-Project

## Goals
In this project your goal is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. You will be provided the car's localization and sensor fusion data, there is also a sparse map list of waypoints around the highway. The car should try to go as close as possible to the 50 MPH speed limit, which means passing slower traffic when possible, note that other cars will try to change lanes too. The car should avoid hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car should be able to make one complete loop around the 6946m highway. Since the car is trying to go 50 MPH, it should take a little over 5 minutes to complete 1 loop. Also the car should not experience total acceleration over 10 m/s^2 and jerk that is greater than 10 m/s^3.

## Simulator
* You can download the Term3 Simulator which contains the Path Planning Project from the [releases tab (https://github.com/udacity/self-driving-car-sim/releases/tag/T3_v1.2).  

## Dependencies

* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```

## Running the Code
1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./path_planning`.
5. Run simulator

## Implementation
Three parts had been add to the ```main.cpp```. They are prediction, behavior and trajectory modules. 


### Prediction
Our car follows a serious a points which were generated from the trajectory module. 
At the beginning on each loop, we retrieve the points from ```previous_path``` which is the trajectory points that have not been reached. 
Since this position information is about future, future position of neighbouring vehicles are also calculated to determeint following situations.
* Is there a slow car aheads might cause collision
* Is left lane occupied by other car
* Is right lane occupied by other car

### Behavior
According to inputs from prediction module. One of the following action shall be choose
* Normal
  Vehicle has a default speed of 49 kph.
* Follow
  When all lanes are blocked, following the vehicle aheads
* Turn Left
  If there is a slow vehicle aheads and left lane is available, switch to left lane,  
  This action also has priority while both left and right lane are available. 
* Turn Right

### Trajectory
T○ smooth the transition, use the last two point from ```previous_path``` to make sure new trajectory will tangent to ```previous_path```.
Another 3 future points at S distance 30, 60 and 90 are generated for computing a smooth spline curve. 









---












