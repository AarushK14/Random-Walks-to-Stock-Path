# Random-Walks-to-Stock-Path

Simulating random walks and a simple stock price model in Python, then using Monte Carlo to estimate the probability of a 10% gain over a year.

This is my second Monte Carlo project, following Estimating π with Monte Carlo.

What this project does

	1.	Random walks. Simulate a walker that moves +1 or -1 with equal probability at each step, and plot many walks on the same axes.
	2.	Where walks end up. Simulate 10,000 walks, record each final position, and compare the spread to the √n prediction.
	3.	A simulated stock price. Model a stock starting at £100, where each day the price is multiplied by 1 + drift + volatility × z and z is drawn from a standard normal distribution. Plot 50 simulated years.
	4.	A probability estimate. Simulate 10,000 years and estimate the probability that the price finishes at £110 or more, including a 95% confidence interval.

Model parameters

Parameter	Value	Meaning
Starting price	£100	
Daily drift	0.0005	average growth of 0.05% per day
Daily volatility	0.01	typical daily move of about 1%
Trading days	252	one year

Results

Experiment	Prediction	Result
Std. dev. of final position, 400-step walks (10,000 walks)	√400 = 20	19.77
Final stock price, mean (50 paths)	about £113
Final stock price, std. dev. (50 paths)	about £16
P(final price ≥ £110) (10,000 paths)	about 0.545	0.546 ± 0.010 (95% CI)

What I learned

	•	Spread grows like √n. The standard deviation of a random walk after n steps is √n, so quadrupling the number of steps only doubles the spread.
	•	The Central Limit Theorem at work. Each step is just ±1, but the sum of many steps is approximately bell-shaped.
	•	Histogram bins matter. Final positions after an even number of steps are always even, so the bin edges must be chosen carefully or the histogram looks jagged.
	•	Drift is direction, volatility is noise. Drift adds up in a straight line over time, while volatility grows only like √time.
	•	Monte Carlo accuracy improves as 1/√n. The standard error of the probability estimate is √(p(1−p)/n), so halving the error needs four times as many simulations.

How to run

The project is a Jupyter notebook using Python 3 with random, numpy and matplotlib.

pip install numpy matplotlib jupyter
jupyter notebook

Open the notebook and run the cells in order.

Next steps

	•	Price a European call option by Monte Carlo and compare it to the Black-Scholes formula
	•	Price an Asian option, which has no simple formula
	•	Speed up the simulation by vectorising with numpy
