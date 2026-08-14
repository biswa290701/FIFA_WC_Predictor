# FIFA World Cup Predictor

## How to Use

### 1. Clone the Repository

```bash
git clone <repository-url>
cd ML_WC_PREDICTOR
```

### 2. Create and Activate the Virtual Environment

On Windows:

```bash
python -m venv venv
.\venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Jupyter will open in your browser.

### 5. Run the Predictor

For the current complete tournament simulation, open:

```text
notebooks/11_world_cup_simulator.ipynb
```

Run the notebook from top to bottom:

**Kernel → Restart & Run All**

The notebook will:

1. Load the historical football data.
2. Prepare the Elo and recent-form features.
3. Load/build the trained Random Forest model.
4. Generate World Cup match probabilities.
5. Simulate the group stage.
6. Determine the teams advancing to the knockout stage.
7. Simulate the knockout rounds.
8. Produce a World Cup champion.

### 6. Run Multiple Tournament Simulations

The simulator supports Monte Carlo simulation.

The default example runs:

```python
run_simulations(n=1000)
```

This simulates the entire World Cup **1,000 times**.

The final output gives each team's:

- Champion count
- Championship probability

For example:

```text
Team        Champion Probability
Spain             14.0%
Argentina         12.6%
France            11.2%
Brazil             9.8%
```

You can increase the number of simulations by changing `n`:

```python
run_simulations(n=10000)
```

or:

```python
run_simulations(n=100000)
```

More simulations generally produce more stable probability estimates, but take longer to run.

### 7. Predict an Individual Match

The World Cup match predictor can also be used for individual fixtures through:

```python
predict_world_cup_match(team_a, team_b, neutral=True)
```

Example:

```python
predict_world_cup_match("Brazil", "Germany", neutral=True)
```

The result provides probabilities for:

- Brazil win
- Draw
- Germany win

For a match played on a host nation's home soil, use:

```python
predict_world_cup_match(
    "United States",
    "Germany",
    neutral=False
)
```

For normal World Cup matches, use:

```python
neutral=True
```

### 8. Notebook Order

The notebooks are numbered chronologically:

```text
01 → Baseline Model
02 → Elo Model
03 → Elo + Recent Form
04 → Chronological Evaluation
05 → Class-Balanced Model
06 → Difference Features
07 → Custom Class Weights
08 → Probability Model
09 → World Cup Match Predictor
10 → 2026 World Cup Structure
11 → World Cup Simulator
```

For simply **using the current predictor**, start with:

```text
notebooks/11_world_cup_simulator.ipynb
```

For an individual World Cup match prediction, use:

```text
notebooks/09_world_cup_match_predictor.ipynb
```
