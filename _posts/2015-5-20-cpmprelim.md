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

<img src="https://c2.staticflickr.com/6/5323/17914128246_ba675a9e68_o.png" width="560" height="420" alt="1cell_msd">

So fitting our whole data we get the following values for $$\alpha$$ and $$D$$ (in simulation units).

$$ \alpha = 1.1418 \\ D = 0.0267 $$

This is in relatively good agreement with expectations and with the result from the Szabo paper which states that displacement grows with time as

$$ d \sim \sqrt{t} \ . $$

We can get closer agreement if we ignore the outlying, first three data points from our fit.

<img src="https://c4.staticflickr.com/8/7747/17320022923_82784b8741_o.png" width="560" height="420" alt="1cell_d_2">

Which yields... 

$$ \alpha  = 1.0719 \\ D = 0.0274 $$

## Resting Area of 50 Pixels

### Results

Here is a movie of a typical cell.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9NWY0bXVCVXJNU0E/preview" width="320" height="240"></iframe>
<b></b>

<img src="https://c1.staticflickr.com/9/8863/17291731253_55e2ae6dea_o.png" width="560" height="420" alt="1cell_msd_1">

The results look good! The single cell with a relaxed area of 50 pixels does exhibit normal diffusion. We can also compare our results to that of the [Szabo *et al* paper](http://iopscience.iop.org/1478-3975/7/4/046007) to see how our simulation compares. To do this one MC time step becomes one minute and the distance between one lattice site become 5$$\mu\text{m}$$.

We can translate our data into these units and plot the mean displacement.

<img src="https://c2.staticflickr.com/6/5339/17912201945_65007d2039_o.png" width="560" height="420" alt="1cell_msd_2">

This appears to be in good agreement with the results from the paper. At 10 hours the mean displacement is around $$10 \mu\text{m}$$ which is inline with the results from the$ paper.

I attempted to overlay this plot onto that from the paper in order to see how well the data matched up. 

<img src="https://c1.staticflickr.com/9/8817/17909154102_b134969b43_o.png" width="553" height="402" alt="szabo_comparison">

As you can see the data from the simulations (bottom blue) is very similar to the black curve from the paper. The slopes seem to be in agreement but there is an off set which corresponds to a difference in diffusion coefficients. I believe that some of the off set is due my plot not exactly lining up with how the plot from the paper scales but this still does not explain away the whole off set.

# Multiple Cells

In the case of multiple cells the re$lative values of the energy terms associated with free-cell and cell-cell boundaries are important.

$$ \alpha \equiv \text{cell-cell boundary energy} \\ \beta \equiv \text{free-cell boundary} $$

Please be aware of the difference between this use of $$\alpha$$ and that in the context of diffusion.

In the Szabo paper $$\alpha \in \{1,2,3,4\}$$ and $$\beta = 1$$. However, in the paper's simulations of cell monolayers there are no free-cell boundaries so the $$\beta$$ parameter becomes irrelevant. The paper reports that increasing $$\alpha$$ causes movement of cells within the monolayer to decrease. This makes sense since increasing $$\alpha$$ cause the energy due to changing the cell boundaries to increase making movement less probable.

I believe that mimicking the values of $$\alpha$$ and $$\beta$$ from the paper is not productive since we do want to consider a group of cells with free-cell boundaries. If $$\alpha > \beta$$ then cell-cell boundaries are not favorable which will cause the group of cells to break apart. Therefore, we should restrict the parameters to $$\alpha < \beta$$ in order to maintain cell-cell contact.

Here is a video for the case of $$\alpha = 2$$ and $$\beta=1$$.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9alRsUGRSSDlTbzg/preview" width="320" height="240"></iframe>
<b></b>

So I have chosen the following values for the parameters.

$$ \alpha = 0.5 \\ \beta = 1.0 $$

This satisfies the criteria for favorable cell-cell contact, and also keeps the same value of $$\beta$$ from single cell simulations.

Below is a a video for the case of $$\alpha = 0.5$$ and $$\beta = 1$$.

<iframe src="https://docs.google.com/file/d/0B9wUAi2m2Di9Ym1EVnFWd1B2ZkU/preview" width="320" height="240"></iframe>

# Results

The results shown will be for the case of $$\alpha = 0.5$$ and $$\beta = 1$$ and a relaxed area of 4 pixels. Below are the results for the MSD for groups of various number of cells.

<img src="https://c2.staticflickr.com/6/5459/17940797975_cf89ff1b62_o.png" width="560" height="420" alt="small_mltcells_msd_1">

We can get a better understanding for what is going on if we plot the fits for each respective data set.

<img src="https://c4.staticflickr.com/8/7718/17753204430_b2ec990e5f_o.png" width="560" height="420" alt="small_mltcells_msd_2">

<img src="https://c1.staticflickr.com/9/8852/17914400446_abee37c2cb_o.png" width="560" height="420" alt="small_mltcells_msd_3">

As you can see as the number of cells in a group increases so does $$\alpha$$. So as the number of cells increases diffusion of the group becomes more anomalous.

Lets see what happens to the diffusion coefficient as the group size changes.

<img src="https://c4.staticflickr.com/8/7695/17914443806_4e0e2693c1_o.png" width="560" height="420" alt="small_mltcells_diff">

The overall behavior is that as the group size increases the diffusion coefficient decreases and it seems to be approaching some lower bound. So even though $$\alpha$$ increases this does not lead to faster diffusion for larger groups since the diffusion coefficient decreases.

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

> Julien Varennes
