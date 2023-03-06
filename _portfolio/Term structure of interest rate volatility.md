---
title: "Term Structure of Interest Rate Volatility"
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
$$S = \{S_{1},,,S_{N}\} $$

where 𝑁 is the number of states. Use tiqs= to indicate that the HMM is in the hidden
state is at time 𝑡, and the hidden state sequence is
$${Q} = \{q_{1},,,q_{N}\}$$

• The probability distribution 𝐴 of state transition. The probability distribution
of state transition can be expressed as:
$$A = \{P(q_{t+1}=S_j|q_{t}=S_{i})，1&lti,j&lt N\}$$


• Probability distribution 𝐵 of the observed variable output under the condition of
state is . Assuming that the sample space of the observed variable is 𝑣, the probability
distribution of the output observed variable in the state is can be expressed as

$$B = \{f(q_{t+1}=v|q_{t}=S_{i})，1&lt i&lt N,v&lt N\}$$

where $𝑄_t$ is the observed random variable at time 𝑡,

• The probability distribution of the initial state of the system 𝜋. The probability
distribution of the initial state of the system can be expressed as

$$&pi = \{P(q=S_i)，1&lti &lt N\}$$


![image](https://user-images.githubusercontent.com/36789660/222986374-39d26f0c-1069-4826-9e12-a351ea994259.png)

Algorithm
============


Model Selection
============

The biggest question of this project is to find a choice of number of states for an adequate
model, given a series of observation of log-return data. The maximum number of potential
states we decided is four. Then we will proceed to inspect the fitted models and investigate
the impact of increasing the number of states. After that we will validate the model to check
if a candidate model adequately explains the data-generating process by plotting the pseudoresiduals
of the model and then compare model selection criteria to get an overall assessment
of candidate models.

### Two-states Hidden Markov Models

The two-hidden-states Markov model is characterised by two separate regimes where state
1 corresponds to a low volatility regime and state 2 corresponds to a high volatility regime
as seen in figure bellowed where the states of five-year interest rate are labelled using the
Viterbi algorithm.

![image](https://user-images.githubusercontent.com/36789660/222986888-2dc51ec1-168a-4bdb-817d-89154211a34b.png)

![image](https://user-images.githubusercontent.com/36789660/222986897-7122b8ff-7027-4f56-909e-1bacdaf3cc7f.png)


### Three-states Hidden Markov Models

The 3-state hidden Markov model add another market state – medium volatility regime
between low volatility regime and high volatility regime
When adding a third state we notice that we get three separate regimes where the state
representing the high volatility regime now is split into two states; state one with slightly
mean and slightly higher volatility than state two. We still observe that all three regimes
represent clusters with varying mean and volatility.

![image](https://user-images.githubusercontent.com/36789660/222986937-4fad58b7-6d0d-4f48-8579-399f6c3d49b6.png)

![image](https://user-images.githubusercontent.com/36789660/222986946-52da692b-6f1c-4576-9132-d1fd4bd09bb0.png)


### Four-states Hidden Markov Models

The 4-state HMM taking both the market condition and the volatility into the consideration
may give a more elaborate description of the market conditions compared with the above
two models. Specifically, the 4-state HMM is dividing the market states into 4 states, which
are the bull with low volatility state, bull with high volatility state, bear with high volatility
state and bear with low volatility.
The reason to distinguish between bull and bear markets is that market volatility is higher in
declining markets than in rising markets. This means that volatility will increase more given
a 10% drop from current price levels than given a 10% gain. Market psychology plays a role
in this phenomenon since people can overreact with fear or panic to selloffs.
The four-state model can easily be compared to both the two-state and the three-state model.
Roughly speaking, the two states are now split into four states and each state has a low
transition probability. We discussed in the previous paragraph that regime 0 was divided into
two regimes when adding an extra state. Here, regime 2 in the two-state model is now split
with an extra regime where the downside returns of state 2 now have their own regime.
Hence, we now have four states corresponding to a bear market, semi-bull market, bull
market, and semi-bear market respectively. Although such a partition could be motivated if
we were just aiming to decode the regimes in the market, it is probably too complex in this
type of application where we aim to predict the next regime.

![image](https://user-images.githubusercontent.com/36789660/222986974-527c1250-ba2e-444a-a849-bc15fc46e1f7.png)

![image](https://user-images.githubusercontent.com/36789660/222986997-ac194cf6-2917-47c6-a704-5066ee93f919.png)


In order to get an overall assessment of the candidate models the BIC and AIC values are
plotted in the above figure for the three models respectively. We conclude that the BIC favors
the two-hidden-states Markov model whereas there is a small difference between the two
and three-hidden-state models with slightly more favorable to the three-hidden state's model
when comparing AIC values. This is consistent since BIC often favors models with fewer
parameters than AIC does. Based on the above findings we will choose the HMM with two
hidden states for five-year interest rates. There is not much evidence in favor of three hidden
states over two hidden states and as the purpose of the model is to predict future, unknown
outcomes we base the decision on parsimony and choose the lower number of states.

![image](https://user-images.githubusercontent.com/36789660/222987019-4240e55b-abb1-4bda-9643-bdcb00df70af.png)


### 2-state HMM with Different Maturity

![image](https://user-images.githubusercontent.com/36789660/222987192-edbc8736-f4d0-454b-ac0e-978e1c720525.png)

![image](https://user-images.githubusercontent.com/36789660/222987204-94854b26-6b05-4e07-a75a-a6629cd396b7.png)

![image](https://user-images.githubusercontent.com/36789660/222987215-fb910be9-535d-4b3a-be3f-d354cadfc29e.png)

![image](https://user-images.githubusercontent.com/36789660/222987226-2c4cd3ca-2f22-4dbf-a9d4-97708aad965c.png)

Notice that between 2004 and 2007 the markets were calmer and hence the Hidden Markov Model has given a high posterior probability to the low volatility regime for this period. However, between 2007-2009 the markets were incredibly volatile due to the subprime crisis. This has the initial effect of rapidly changing the posterior probabilities between the two states but being fairly consistently in high volatility regime during 2008 itself.
The markets became calmer in 2010 but additional volatility occurred in 2011, leading once again for the HMM to give a high posterior probability to high volatility regime. Subsequent to 2011 the markets became calmer once again and the HMM is consistently giving a high probability of a low volatility regime. In 2015 the markets once again became choppier and this is reflected in the increased switching between regimes for the HMM. After 2017, the market became calm again and the states switched to a low volatility regime. Since the covid

pandemic period, the market becomes really volatile and the HMM gives a high posterior probability of high volatility regime. All the market information can be reflected by the two-state Hidden Markov Model from the figures above, which means the two-state Hidden Markov Model fits the interest rate with different maturity.
From the figures above, we also find that the volatility regime of the different tenor of interest rates has some correlation. During some periods (in the year 2020), they all go into the high volatility regime but with different entry points. To make it more obvious, we extract the high volatility regime states with different interest rate maturity from the above figures and plot them into a graph.

Volatility Regimes Across the Yield Curve
============

In the previous chapter, we discussed the yield curve term structure. Just as the yield curve has a term structure, so does the volatility of interest rates. The expression term structure refers to the relationship between a variable and time. Therefore, the term structure of volatility is the relationship between yield volatility and time.
But different from the yield curve term structure, the Term structure of yield volatility does not have to follow a particular shape. For example, short-term yield volatility could be higher than long-term yield volatility. In this case, the term structure is downward sloping.
But the 2-year interest rates and 3-year rates overlap by 2/3, thus high volatility in 2-year rates almost certainly means it in 3 years However, the 2-year rates and 10-year rates only overlap by 20%, which means that the correlation between 2-year rates and 10-year rates are much lower compared with 2-year rates and 10-year rates.

![image](https://user-images.githubusercontent.com/36789660/222987274-3f133970-1b83-4e0b-bab1-7a32629c11b1.png)

From the figure, we can find that the y-axis is the state variable. 1 means high volatility regime, and 0 means low volatility regime. If we look at the period after 2016, this is a clear pattern that one-year rates vol enters into a low volatility regime, later two-year rates enter into the low regime, and then five-year rates and ten-year rates as well.
This is a really exciting market phenomenon we have observed in the market. But instead of qualitatively describing the phenomena, we want to know if one-year interest rates fall into a low volatility regime, when will two-year interest rate falls into low volatility regime as well. We know that there is a lag effect between one-year interest rates and two years interest rates. We want to have a clear formula to depict the correlation between one-year interest rates volatility regime and two-year interest rates volatility regime.



Markov Switching Dynamic Regression Model
============

After finding the exciting market phenomenon, we use the Markov-switching dynamic regression model to quantitatively describes the dynamic behavior of time series variables in the presence of structural breaks or regime changes.
The Markov Switching Dynamic Regression model is a type of Hidden Markov Model that can be used to represent phenomena in which some portion of the phenomenon is directly observed while the rest of it is ‘hidden’. In our example, one year interest rates volatility regime is observable and two years interest rates volatility regime
Our regression goal is to explain the variance in two years interest rate volatility using the variance in the one-year interest rate volatility in the presence of regime changes.

we have also introduced a state-specific variance. We are saying that the residual errors of the model are normally distributed around a zero mean and a variance that switches between two values depending on which state the underlying Markov process is in.

![image](https://user-images.githubusercontent.com/36789660/222987407-dad0bde9-f9b0-4275-866e-cd9b69752760.png)

And the transaction matrix is

![image](https://user-images.githubusercontent.com/36789660/222987445-5942fd64-392e-497a-8a2d-fe29d50ceb3b.png)



###To be continued

Reference
============

Hardy, M. .A Regime-Switching Model of Long-Term Stock Returns. North American Actuarial Journal, 5(2), pp.41-53.

Ang, Andrew, and Geert Bekaert.  How Do Regimes Affect Asset Allocation. Financial Analysts Journal 60: 86–99


