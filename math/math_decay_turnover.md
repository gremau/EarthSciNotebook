# Decay, turnover, and residence time of pools of stuff

Mathmatical models describing the decay or turnover of stuff. I use
these to describe the docomposition of organic matter, the size of
organic matter pools as a function of their inputs and outputs, but the
same concepts and mathematical models are applicable to the decay of
radionuclides, hydrologic turnover, and other phenomena.

#### Decay functions (no inputs)

The general function for decay of leaf litter (for example) is: $$
L_t = L_0e\^{-kt} $$ or, $$ ln \\frac{L_t}{L_0} = -kt $$

where $L_0$ is the mass at time 0, $L_t$ is the mass at time
$t$, and $k$ is the decomposition constant. The mean residence time,
or time required for $L_0$ to decompose under steady state conditions
equals $\\frac{1}{k}$.

### Dual pool decay

#### Turnover functions (inputs and outputs)

When a pool of stuff has both inputs and outputs, the change in the pool
with time is defined as

$$ \\frac{\\partial S}{\\partial t} = I - kS$$

where $I$ is the input to the pool, $k$ is the decomposition rate,
and $S$ is the size of the pool.

 **Resources **

<http://www.plantsciences.ucdavis.edu/agroecology/staff/documents/encycl.pdf>
