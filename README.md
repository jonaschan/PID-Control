# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

## Rubric Reflection Questions

### Describe the effect each of the P, I, and D components had in your implementation
In this project, I have used the PID Controller primarily to control the steering angle of the vehicle.

The Proportional element of the PID controller, or P, is the term which is proportinal to the Cross Track Error (CTE). Having just a P controller is marginally stable which meant that it although it reaches the set point  it oscillates about the set point. Putting this into perspective, the having this element of the controller abled the vehicle to react quickly to changes in the CTE but having only this component may cause the vehicle to overshoot the set point and oscillates around it. The higher the value of the P controller, the faster the oscillation occurs.

On the other hand, the Differential element of the PID controller, or D, is the term which is proportional to the change in CTE over time which is responsible to dampen and eventually eliminate the oscillations when used together with the P element (PD controller)

The last parameter is the Integral element of the PID controller, or I which computes the sum of the cross track error over time, this is essential in order to bring the vehicle back to its intended trajectory should the vehicle is far from the set point or in other words, reduces the value of the CTE towards zero.

### Describe how the final hyperparameters were chosen
In this case, I have chosen to tune all the parameters manually. I chose to follow the tuning steps mentioned in http://www.ni.com/white-paper/3782/en/. The steps taken were:
1. Set the I and D parameters to zero first.
2. Increase the proportional gain.
    - At this stage, steering values started to oscillate like crazy! And the vehicle eventually ended up in the lake or sometimes on the top of the hill!
3. Increase the integral term to reduce the oscillations but noticed some overshoot in the  
   steering values.
4. Increase the Derivative term until vehicle quickly resides back to its set point.
5. Then manually play around with the values until eventually the vehicle starts to drive as intended!

The final values chosen are:
Kp = 0.225, Ki = 0.001, Kd = 15.

I have uploaded a video of the making a drive around the set and the link is here:
https://youtu.be/cCSFEZMXjkA

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
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!

More information is only accessible by people who are already enrolled in Term 2
of CarND. If you are enrolled, see [the project page](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/f1820894-8322-4bb3-81aa-b26b3c6dcbaf/lessons/e8235395-22dd-4b87-88e0-d108c5e5bbf4/concepts/6a4d8d42-6a04-4aa6-b284-1697c0fd6562)
for instructions and the project rubric.

## Hints!

* You don't have to follow this directory structure, but if you do, your work
  will span all of the .cpp files here. Keep an eye out for TODOs.

## Call for IDE Profiles Pull Requests

Help your fellow students!

We decided to create Makefiles with cmake to keep this project as platform
agnostic as possible. Similarly, we omitted IDE profiles in order to we ensure
that students don't feel pressured to use one IDE or another.

However! I'd love to help people get up and running with their IDEs of choice.
If you've created a profile for an IDE that you think other students would
appreciate, we'd love to have you add the requisite profile files and
instructions to ide_profiles/. For example if you wanted to add a VS Code
profile, you'd add:

* /ide_profiles/vscode/.vscode
* /ide_profiles/vscode/README.md

The README should explain what the profile does, how to take advantage of it,
and how to install it.

Frankly, I've never been involved in a project with multiple IDE profiles
before. I believe the best way to handle this would be to keep them out of the
repo root to avoid clutter. My expectation is that most profiles will include
instructions to copy files to a new location to get picked up by the IDE, but
that's just a guess.

One last note here: regardless of the IDE used, every submitted project must
still be compilable with cmake and make./
