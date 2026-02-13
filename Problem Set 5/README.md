# Climate Data Regression & Overfitting Analysis

A data analysis pipeline modeling temperature trends across 21 US cities (1961-2015) using polynomial regression. Implements moving average smoothing, model evaluation metrics, and a train/test split demonstrating overfitting.

## Implementation

### Data

`Climate` class parses a large CSV of daily temperatures across 21 US cities from 1961 to 2015 into a nested dictionary structure (city -> year -> month -> day -> temperature).

### Core Functions

- `generate_models()` — fits polynomial regression models of specified degrees using `pylab.polyfit` and `pylab.polyval`
- `r_squared()` — computes the R² coefficient of determination
- `rmse()` — computes root mean squared error
- `gen_cities_avg()` — computes temperature averages across multiple cities for each year
- `moving_average()` — smooths data with a sliding window, handling edge cases where fewer than `window_length` prior values are available

### Analysis Progression

- **Part A** — fits a single day's temperature trend in New York, then annual averages
- **Part B** — aggregates across all 21 cities for national temperature averages
- **Part C** — applies moving average smoothing to reduce noise
- **Part D** — compares degree 1, 2, and 20 polynomial fits on training data (1961-2009) vs. testing data (2010-2015), demonstrating that a degree-20 polynomial overfits (fits training well but generalizes poorly)
- **Part E** — analyzes standard deviation of daily temperatures as a measure of climate variability over time
