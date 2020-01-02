Algorithmic foundations of programmable matter talk
	Self-organizing structures (nano to  macro) 
		Stuff like DNA, coral reefs
	Using this IRL using nano-sensors smart self-healing paint 
	Programmable matter 
		Self-organizing active computational particles
			No human intervention
			Scalable
			Undistinguishable 
		Programmable to change their collect physical properties
			What algorithms should we use?
			Local distributed rules that each particle runs in order to achieve the collective behaviors
Examples from today:
	DNA computing
	Swarm robotics
	Smart materials 
Basic problems:
Shape formation
Coating a surface(sealing an object also)
Compression
Bridging
Locomotion 
The Amoebot Model
	Assume a discretion of space (infinite and no coordination lattice) 
	Particles are anonymous and constant-size memory
	Chirality (clockwise and counterclockwise)
	Particles have an idea of left and right, but not of directions 
	Local communication (have to share a bond, can’t communicate through the whole space)
	Actively move (via expansions and contractions)
	System progresses concurrently and async (Atomicity and isolation)
	Understand minimal computational requirements at micro-level that can lead to the desired macro-behavior 
How can we elect a leader?
	Non-deterministically
		Deterministic works unless symmetries are “impossible” to break
		Uses movement to break symmetries 
	Randomization
	Geometric info- absolutely needed
		Use geometry of grid graph and limited randomization to break symmetry
	Needs to know it’s a sole leader
		Uses entry points or other stuff to say it’s the leader to the whole system
	Can not have chirality as long as no holes
Async Model
	Atomic enabled actions
		Particles do some local computation and/or movement per action
		Conflicts (of movement/read/write) resolved such that atomicity and isolation are enforced
	Round:
		Elapsed time until every particle is activated
Number of rounds is about equal to the concurrent running time
*thm - number of rounds in async execution is dominated by the numbers in a synch execution
Linearization atomic actions
Runtime O(n)

SOPS-self organization particle systems
Stochastic SOPS  
	Compression 
		Gather particle system as tightly together as possible (minimize perimeter of system config)
		Increasing the number of internal edges decreases the perimeter
		Markov Chain= input an init config connected hole-free and a bais parameter
Choose a particle from the system uniformly at random(particles activate independently acc to poisson clocks with different rates)
Choose an adjacent position at random (if occupied go back)
If local prop hold for maintaining connectivity and avoiding holes move to chosen position with prob (min{1, lambda raised triangle e}(e is neighbor count)-This prob is metropolis filter 
		Thinking about things like local minima and maxima 

Expansion
	We can see that with lambdas under 2.21 we expand
	And above 2 + sqrt 2 is compression
		Inbetween is weird 

Bridging 
	Ants build bridges to shorten the path but each ant in the bridge is no longer in the workforce
Tradeoff- make the total path shorter but without sacrificing too many particles  
	
Separation
		Giving the compression algro adifferent lamba and y gives wilding different stuff
		Locomotion
		Aggregation/dispersion 
Challenges in theoretical models
	Errors
Fault tolerance
Mix stochastic and non-stochasic 
Questions:
What does it mean to break symmetry
	Meeting the condition and using a algro (bigger id number, most north) to find an answer
What is arw36 poisson
expresses the probability of a given number of events occurring in a fixed interval of time or space if these events occur with a known constant rate and independently of the time since the last event.[1] The Poisson distribution can also be used for the number of events in other specified intervals such as distance, area or volume.

What does stochastic mean
randomly determined; having a random probability distribution or pattern that may be analyzed statistically but may not be predicted precisely.
