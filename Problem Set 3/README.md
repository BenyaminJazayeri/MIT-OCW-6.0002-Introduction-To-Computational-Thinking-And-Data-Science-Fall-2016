# Robot Room Cleaning Monte Carlo Simulation

A Monte Carlo simulation of robot vacuum cleaners in rooms with and without furniture. Features a multi-level OOP hierarchy with abstract base classes. Estimates expected cleaning time through repeated stochastic trials.

## Implementation

### Room Classes

- `RectangularRoom` — abstract base class defining the room interface (tile tracking, cleaning status, random position generation)
- `EmptyRoom(RectangularRoom)` — standard rectangular room where all tiles are cleanable
- `FurnishedRoom(RectangularRoom)` — room with furniture tiles that cannot be cleaned. Uses rejection sampling for random position generation to ensure positions land on open tiles

### Robot Classes

- `Robot` — abstract base class with position, direction, speed, and room reference. Handles trigonometric position calculations for movement at an angle
- `StandardRobot(Robot)` — moves in a straight line cleaning tiles, changes direction randomly when hitting a wall
- `FaultyRobot(Robot)` — has a 15% chance of getting "distracted" at each step, randomly rotating without moving or cleaning

### Simulation

- `run_simulation()` — runs Monte Carlo trials with configurable number of robots, room dimensions, minimum clean fraction, and robot type. Averages the number of time steps across all trials to estimate expected cleaning time
- Visualization support with Tkinter for watching robots clean in real-time
- Plotting functions to compare robot strategies and room shapes using matplotlib
