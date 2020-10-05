# train_simulation_simpy
The single queue simulation from the London Oak Commons to Birmingham Interchange. 


## The solution in this repository is a formulation of the problem stated below.

A high-speed train as planned for the HS2 line from London to Birmingham has a maximum
acceleration of 0.76m/s2, about the same as a commuter train. While the trains can brake in
an emergency at 2.5m/s2, the energy optimal deceleration (using regenerative braking) is
0.38m/s2.
The maximum travelling speed of the train is about 310km/h (86.1m/s). For the purpose of this project we will ignore the impact of air resistance. That means we assume a constant
acceleration up to maximum speed. Accelerating from 0 to the maximum speed takes therefore 113.3s during which time the train travels about 4,878m. A railway line consists of a sequence of signaling blocks. A train is only allowed to enter a block, when there is no other train in the block and the entry signal is green. When a train enters a block the entry signal switches to red. The entrance signal switches back to green 5 seconds after the end of the train has left the block. We assume for the purpose of this project that the signalling blocks have all equal length.
Depending on the speed of a train it requires a number of free blocks ahead of it, to maintain the current speed. This speed is determined so that the train is guaranteed to stop safely before a red signal.
This results in a trade-off. When the speed of the train is slower, it is possible to have more trains on the track, as there are less free blocks required between the trains. The faster a train the more free blocks are required in front of the train to continue maintaining the high speed. Given a number of blocks along a track there will be an optimal point for the number of trains per hour that could be run on the track at full speed. The control problem is to keep the trains moving at maximum possible safe speed. If there is
a slight delay in one train it may cause the train in the following block to decelerate potentially down to stop and then to reaccelerate, which in turn will delay the train
thereafter. Just like the “traffic jam” effect you know from the motorway. A train can run constantly at full speed if there is always at least the required number of free blocks ahead.

### Part 1 Simulation:
Create a simulation for the London Old Oak Commons to Birmingham Interchange section of the high-speed line. The distance between London Old Oak Common Station and
Birmingham Interchange Station is 145km. Assume that the track consists of k signalling blocks of equal length and that a fixed train schedule of n trains per hour is to be used. Verify the simulation model by inducing a temporary break down due to electrical malfunction of the 9am train from London to Birmingham. It takes 30 minutes to fix the
problem.
To reflect operational conditions introduce variability of travelling times using a suitable distribution on events. You can choose the distribution and the parameters as you deem appropriate. It may be useful to consider two types of variations: normal deviations (of just a few minutes for example caused by common weather events or delays in departure due to passenger movements), and rare events with bigger impact (like heavy rain or technical problems) that may impact also on later trains. Yuxiang Yang et al [1] report a log-normal distribution with μ= 3.378 and σ=0.751 for the delay times (in minutes( on a segment of a comparable Chinese high-speed train (including the knock-on effect on the following trains).

### Part 2 Optimisation:
For given parameters k and n create a train schedule that sets out the departure and arrival time for trains with the first train leaving at 7am and the last train leaving at 10pm. Using the simulation created in part 1 report the distribution of actual delay times. The aim is to maximise the number of trains operating per hour under the constraint that the average delay time should not be higher than half the scheduled time between consecutive trains. Report your recommendation for the layout of the track (k) and the schedule (n).


## To Run the Code

The 'Simulation.ipynb' randomly creates a schedule of the trains and the schedule has been saved into a csv file.

The 'Optimisation.ipynb' imports the schedule from the csv file and optimise the values and finds out the optimal value of **K** and **n**
