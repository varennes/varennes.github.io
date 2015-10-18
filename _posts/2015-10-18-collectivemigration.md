---
title: Collective Migration
layout: post
---

# Multicellular Sensing and Migration

As previously discussed cell sensing and communication is modelled using the LEGI framework. The polarization vector $$\vec{p}$$ is updated based on the downstream output of the LEGI model and the repulsion vector $$\vec{q}$$.

$$
\frac{d\vec{p}}{dt} = r \left[ -\vec{p} + \epsilon \frac{R}{\sigma_R} \vec{q} \right]
$$ 

We can measure the mean first passage time (mFPT) for clusters of cells who are in the presence of a chemical gradient.

<img src="https://farm1.staticflickr.com/619/21664220753_c7e4db8976.jpg" width="500" height="388" alt="mFPTvN_7">

The different lines are for different values of $$\Gamma$$, which is related to the exchange rate of *Y* molecules between cells $$\gamma$$.

$$ \gamma = \Gamma \cdot L $$

So as the exchange of *Y* molecules increases the mFPT decreases. This is a consequence of having better communication between cells and so cells can more accurately measure the mean chemical concentration of the whole cluster.

Increasing the number of cells also decreases the mFPT until some critical number of cells is reached, $$N_\text{crit} \approx 20$$ in most cases. For $$N > N_\text{crit}$$ the mFPT increases, but it is not at a constant rate. The mFPT seems to level off as more cells are added to the cluster, at large values of $N$ adding more cells seems to have negligible effect.

## Multicellular Migration

In order to better understand why the mFPT levels off at large cluster sizes we examine mFPT results for cells whose polarization is independent of sensing. 

$$
\frac{d\vec{p}}{dt} = r \left[ -\vec{p} + \epsilon \vec{q} \right]
$$

$$\vec{q}$$ is no longer the repulsion vector but instead a unit vector with direction defined by a Gaussian distributed random variable $$\theta$$.

$$
\vec{q} = \left( \cos\theta, \sin\theta \right) \\
\text{E}[\theta] = 0 , \ \text{Var}[\theta] = \pi^2/4
$$

Here are the results.

<img src="https://farm6.staticflickr.com/5793/22272391012_5d81dd7723.jpg" width="500" height="400" alt="mFPTvN_2">

As the cluster size increases the mFPT increases. This is expected since coherent forward motion should be more difficult as more cells are added to the cluster. However, as the number of cells increases the rate of increase in mFPT decreases and mFPT seems to level off.

This is in agreement with the sensing dependent migration simulations. The cost of increasing the cluster size decreases with larger cluster sizes.



> Written with [StackEdit](https://stackedit.io/).
