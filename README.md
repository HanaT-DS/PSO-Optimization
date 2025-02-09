# PSO-Optimization
This is a SAS implementation of the Particle Swarm Optimization (PSO) algorithm. PSO is a stochastic optimization technique inspired by the collective behavior of birds flocking and fish schooling. Unlike gradient-based methods, PSO does not rely on derivatives, making it suitable for solving both linear and nonlinear optimization problems.


## How it works?
Particle Swarm Optimization (PSO) begins with randomly initializing a set of candidate solutions, known as particles. Each particle possesses a position and velocity within the search space and keeps track of its best-known position (pbest​) based on its past performance. Meanwhile, the swarm monitors the best position found by any particle (gbest​).
During each iteration, particles adjust their velocity by considering both their personal best position (pbest) and the global best position (gbest​). This velocity update directs particles toward promising regions of the search space while preserving some randomness to encourage exploration.
As the particles move, they continuously refine their positions to discover improved solutions. The process repeats until a predefined stopping criterion is satisfied (e.g., reaching a max number of iterations or achieving desired accuracy).

