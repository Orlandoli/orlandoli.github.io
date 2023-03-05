---
title: "Interest Rate Volatility Regime Classification"
excerpt: "Financial markets have the tendency to change their behavior over time, which can create regimes or periods of fairly persistent market conditions.Modeling various market regimes can enable macroeconomically aware investment decision-making and better management of tail risks.In this project, We use the Markov Switching Dynamic Regression model to quantitatively describes the dynamic behavior of interest rate volatility with different maturity in the presence of structural breaks or regime changes.The results proved the MS-DR model to be useful, to evaluate the characteristics of volatility regimes across the yield curve."
collection: portfolio
---
Background
============
A consistent challenge for quantitative traders is the frequent behaviour modification of financial markets, often abruptly, due to changing periods of government policy, regulatory environment and other macroeconomic effects. Such periods are known colloquially as "market regimes" and detecting such changes is a common, albeit difficult process undertaken by quantitative market participants.

These various regimes lead to adjustments of asset returns via shifts in their means, variances/volatilities, serial correlation and covariances, which impact the effectiveness of time series methods that rely on stationarity. In particular it can lead to dynamically-varying correlation, excess kurtosis ("fat tails"), heteroskedasticity (clustering of serial correlation) as well as skewed returns.

This motivates a need to effectively detect and categories these regimes in order to optimally select deployments of quantitative trading strategies and optimize the parameters within them. The modeling task then becomes an attempt to identify when a new regime has occurred and adjust strategy deployment, risk management and position sizing criteria accordingly.


Methodology
============

A principal method for carrying out regime detection is to use a statistical time series technique known as a hidden Markov model. These models are well suited to the task as they involve inference on "hidden" generative processes via "noisy" indirect observations correlated to these processes. 

At each time point, the HMM emits a symbol and changes a state with certain probability and can be used to analyze and predict time series or time dependent phenomena. Since there is not a one-to-one correspondence between the states and the observation, many states can be mapped to one symbol and vice-versa and hence the system provides a suitable basis to model non-stationary financial time series data.

Its basic elements include the following:

• A collection of hidden state numbers. The discrete set 𝑆 is often used to represent different hidden states:
$$\mathrm{S} = ${S_{1},,,S_{N}}$$$

where 𝑁 is the number of states. Use tiqs= to indicate that the HMM is in the hidden
state is at time 𝑡, and the hidden state sequence is

• The probability distribution 𝐴 of state transition. The probability distribution
of state transition can be expressed as:


• Probability distribution 𝐵 of the observed variable output under the condition of
state is . Assuming that the sample space of the observed variable is 𝑣, the probability
distribution of the output observed variable in the state is can be expressed as



\frac{\frac{G}{\eta_{gas}} - \frac{C}{\eta_{coal}}}{\frac{e_{coal}}{\eta_{coal}} - \frac{e_{gas}}{\eta_{gas}}}$$
![image](https://user-images.githubusercontent.com/36789660/222979462-a324a71f-8ffe-4f69-a81d-93299cf68d9b.png)


![image](https://user-images.githubusercontent.com/36789660/222973570-7ea58353-cea9-4b44-96c4-3fbf334d5e61.png)


