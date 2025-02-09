# PSO-Optimization
This is a SAS implementation of the Particle Swarm Optimization (PSO) algorithm. PSO is a stochastic optimization technique inspired by the collective behavior of birds flocking and fish schooling. Unlike gradient-based methods, PSO does not rely on derivatives, making it suitable for solving both linear and nonlinear optimization problems.


## How it works?
Particle Swarm Optimization (PSO) begins with randomly initializing a set of candidate solutions, known as particles. Each particle possesses a position and velocity within the search space and keeps track of its best-known position (pbest​) based on its past performance. Meanwhile, the swarm monitors the best position found by any particle (best​).

During each iteration, particles adjust their velocity by considering both their personal best position (pbest) and the global best position (gbest​). This velocity update directs particles toward promising regions of the search space while preserving some randomness to encourage exploration.

As the particles move, they continuously refine their positions to discover improved solutions. The process repeats until a predefined stopping criterion is satisfied (e.g., reaching a max number of iterations or achieving desired accuracy).

## Parameters:
Several key parameters must be initialized at the start of the PSO algorithm:

**Nbpcl**: Number of particles in the swarm.

**MaxIter**: Maximum number of iterations.

**Vmax**: Maximum allowed velocity for particles.

**MaxW**: Maximum inertia weight.

**MinW**: Minimum inertia weight.

**c1**: Personal acceleration factor, influencing a particle’s movement toward its own best position.

**c2**: Social acceleration factor, guiding a particle toward the swarm’s best position.

**pclPos**: Current position of a particle in the search space.

**pclVel**: Current velocity of a particle, determining its movement.

**pclBestPos**: The particle's best position yet.

**pclBestCost**: The particle's best function value yet.

**GBestPos**: The swarm's best particle's position.

**GBestCost**: The swarm's best particle's best function value yet.

