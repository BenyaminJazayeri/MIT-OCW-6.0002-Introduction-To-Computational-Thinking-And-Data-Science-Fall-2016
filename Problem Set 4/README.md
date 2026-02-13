# Bacteria Population & Antibiotic Resistance Simulation

A stochastic simulation of bacterial growth, mutation, and natural selection under antibiotic treatment. Models probabilistic birth/death, carrying capacity, and resistance mutation using Monte Carlo trials. Computes population statistics from scratch.

## Implementation

### Bacteria Classes

- `SimpleBacteria` — models a bacterium with probabilistic birth (dependent on population density and carrying capacity) and death (fixed probability per timestep). Birth probability follows a logistic growth model: `birth_prob * (1 - pop_density)`
- `ResistantBacteria(SimpleBacteria)` — adds a boolean resistance flag and a mutation probability. On reproduction, offspring may flip their resistance status with the given mutation probability

### Patient Classes

- `Patient` — manages a list of bacteria with a carrying capacity. `update()` simulates one timestep: kills bacteria probabilistically, then allows survivors to reproduce based on current population density
- `TreatedPatient(Patient)` — adds antibiotic treatment. When antibiotics are active, all non-resistant bacteria are killed before the reproduction phase

### Simulations

- `simulation_without_antibiotic()` — runs 300 timesteps tracking total population across multiple trials
- `simulation_with_antibiotic()` — runs 150 pre-treatment timesteps, activates antibiotics, then runs 250 post-treatment timesteps. Tracks both total and resistant subpopulations

### Statistical Analysis

- `calc_pop_avg()` — computes mean population across trials at each timestep
- `calc_pop_std()` — computes standard deviation across trials at each timestep
- `calc_95_ci()` — computes 95% confidence intervals using the standard error of the mean (SEM), implemented from scratch rather than using library functions
