---
title: CPM Model Results
layout: post
---

# 1 Cell

## Resting Area of 4 Pixels

The simulation ran for 100 different instances each for a maximum of 60 Monte Carlo (MC) time steps.

From the simulations we were able to get statistics on the mean square displacement (MSD) and the displacement of the cell.

$$
d^2 \equiv \text{ Mean Square Displacement } \\
d \equiv \text{ Displacement }
$$

For 2-dimensional diffusion the MSD should obey the following relationship

$$ d^2 = 4Dt^\alpha \ . $$

Where $$D$$ is the *diffusion coefficient* and $$\alpha$$ should be equal to 1.

### Results

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9dWsya2l5T09MUUE/preview" width="320" height="240"></iframe>
<b></b>

<img src="https://c1.staticflickr.com/9/8844/17863794531_f335258cae_o.png" width="560" height="420" alt="1cell_msd">

<img src="https://c2.staticflickr.com/6/5451/17675752120_d2761332f4_o.png" width="560" height="420" alt="1cell_d_1">

So fitting our whole data we get the following values for $$\alpha$$ and $$D$$ (in simulation units).

$$ \alpha = 1.2618 \\ D = 0.0172 $$

This is in relatively good agreement with expectations and with the result from the Szabo paper which states that displacement grows with time as

$$ d \sim \sqrt{t} \ . $$

We can get closer agreement if we ignore the outlying, first three data points from our fit.

<img src="https://c1.staticflickr.com/9/8855/17860379992_d089218594_o.png" width="560" height="420" alt="1cell_d_2">

Which yields... 

$$ \alpha  = 1.1373 \\ D = 0.0266 $$

## Resting Area of 50 Pixels

### Results

No simulation data yet but here is a movie of a typical cell.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9NWY0bXVCVXJNU0E/preview" width="320" height="240"></iframe>

# Multiple Cells

In the case of multiple cells the relative values of the energy terms associated with free-cell and cell-cell boundaries are important.

$$ \alpha \equiv \text{cell-cell boundary energy} \\ \beta \equiv \text{free-cell boundary} $$

Please be aware of the difference between this use of $\alpha$ and that in the context of diffusion.

In the Szabo paper $$\alpha \in \{1,2,3,4\}$$ and $$\beta = 1$$. However, in the paper's simulations of cell monolayers there are no free-cell boundaries so the $\beta$ parameter becomes irrelevant. The paper reports that increasing $$\alpha$$ causes movement of cells within the monolayer to decrease. This makes sense since increasing $$\alpha$$ cause the energy due to changing the cell boundaries to increase making movement less probable.

I believe that mimicking the values of $$\alpha$$ and $$\beta$$ from the paper is not productive since we do want to consider a group of cells with free-cell boundaries. If $$\alpha > \beta$$ then cell-cell boundaries are not favorable which will cause the group of cells to break apart. Therefore, we should restrict the parameters to $$\alpha < \beta$$ in order to maintain cell-cell contact.

Here is a video for the case of $$\alpha = 2$$ and $$\beta=1$$.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9alRsUGRSSDlTbzg/preview" width="320" height="240"></iframe>
<b></b>

So I have chosen the following values for the parameters.

$$ \alpha = 0.5 \\ \beta = 1.0 $$

This satisfies the criteria for favorable cell-cell contact, and also keeps the same value of $$\beta$$ from single cell simulations.

Below is a a video for the case of $$\alpha = 0.5$$ and $$\beta = 1$$.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9Ym1EVnFWd1B2ZkU/preview" width="320" height="240"></iframe>

# Notes on Calculating Diffusion Coefficient and $$\alpha$$

Assume that the mean square displacement (MSD) follows the relationship

$$ d^2 = 4Dt^\alpha \ . $$

$$\begin{align*}
\ln d^2 &= \ln \left( 4Dt^\alpha \right)  \\ &= \ln 4D + \alpha \ln t
\end{align*}$$

The simulations give us data for $$d^2$$ as a function of the number of time steps taken $$t$$. Taking the logarithm of the data obtained we should be able to fit it to a linear function.

$$ \begin{align*}
\ln d^2 &\to y \\
\ln t &\to x \\
\end{align*}$$

$$ y = f(x) = p_1 x + p_0 $$

$$ \Rightarrow  \begin{align*}  p_1 &= \alpha \\ p_0 &= \ln 4D
\end{align*} \\ D = \frac{1}{4} \ e^{p_0}$$


> Written with [StackEdit](https://stackedit.io/).
