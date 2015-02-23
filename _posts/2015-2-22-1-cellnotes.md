---
layout: post
title: 1D Diffusion Notes
---

## 1 Cell Diffusion with No State Switching

### \$$ P(x|t) $$

#### Prediction
The probability density for cell location given a time $$t$$ should look like a normal distribution. As time increases this prediction becomes less accurate since more and more particles get absorbed at the right side boundary.

$$
P(x|t) = \frac{2}{\sqrt{2\pi\sigma^2}} e^{-x^2/2\sigma^2} \\
\sigma^2 = 2Dt
$$

The extra factor of two in $$P(x|t)$$ is because of the reflective boundary at the origin. In an 1D random walk so $$\left<x\right> = 0$$, therefore $$\sigma^2 = \left<x^2\right>$$, and $$\left<x^2\right> = Nb^2$$.

$$
\Rightarrow 2Dt = Nb^2 \\
t = N \Delta t \\
\Rightarrow D = \frac{b^2}{2\Delta t}
$$


#### Results

At small times the data is very much inline with prediction.

<a href="https://www.flickr.com/photos/130911384@N02/16396305775" title="pdf_0500 by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8657/16396305775_a2e38602de_o.png" width="560" height="420" alt="pdf_0500"></a>
<a href="https://www.flickr.com/photos/130911384@N02/15776281203" title="pdf_1000 by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7300/15776281203_74b9126df3_o.png" width="560" height="420" alt="pdf_1000"></a>

At large times the data starts to diverge from a normal distribution as more and more cells are absorbed.

<a href="https://www.flickr.com/photos/130911384@N02/16208672288" title="pdf_2000 by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7433/16208672288_451affdd11_o.png" width="560" height="420" alt="pdf_2000"></a>
<a href="https://www.flickr.com/photos/130911384@N02/16210076679" title="pdf_3000 by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8629/16210076679_cab3613259_o.png" width="560" height="420" alt="pdf_3000"></a>


### $$P(t)$$

#### Prediction

$$P(t)$$ is the probability density of the first passage time. It is expressed as the following:

$$
P(t) = -D \frac{\partial P(x|t)}{\partial x} |_{x=L}
$$

This equation has a solution for our set of initial and boundary conditions. In the large time limit this solution can be expressed as:

$$
P(t) = \frac{2D}{L^2} \sum_{m=1}^{\infty} \beta_m e^{-\beta_m^2 D t / L^2} 
\sin\left(\beta_m \frac{x}{L}\right) |_{x=L}
$$

In the following plots only the first term, $$m=1$$, from the series is used.

**Update**
I have added a short time prediction for $$P(t)$$ to the plots below. We observed that at short times $$P(x|t)$$ looks like a normal distribution. Hence an appropriate approximation for the small time behavior of $$P(t)$$ can be calculated from the normal distribution.

$$
P(x|t) = \frac{2}{\sqrt{2\pi\sigma^2}} e^{-x^2/2\sigma^2} \Rightarrow
\frac{\partial P(x|t)}{\partial x} = \frac{-2x}{\sigma^2\sqrt{2\pi\sigma^2}}e^{-x^2/2\sigma^2} \\
$$

Therefore the short time approximation is the following:

$$
P(t) = \frac{x}{t\sqrt{2\pi\sigma^2}}e^{-x^2/2\sigma^2} |_{x=L}
$$


#### Results - **Update**

The results are plotted here on a normal scale and on a semilog scale. The prediction at large times does seems to be in agreement with the simulations.

**Update 2**, I have added the small time prediction to the plots. At small times it does seems to be in agreement with the simulations. The semilog plot illustrates that the the exponential increase in $$P(t)$$ is well described by the small time approximation.

<a href="https://www.flickr.com/photos/130911384@N02/16430050780" title="time_pdf_3_histfix by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8662/16430050780_0292de2ace_o.png" width="560" height="420" alt="time_pdf_3_histfix"></a>

<a href="https://www.flickr.com/photos/130911384@N02/16431267559" title="time_pdf_semilog3_histfix by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8601/16431267559_57aee7f7cc_o.png" width="560" height="420" alt="time_pdf_semilog3_histfix"></a>

**Update 1**, I have since gone back and remade the plots as a histogram. In creating the histograms I weight the probability density in each bin by the width of the bin to ensure that the whole probability density is properly normalized.

<a href="https://www.flickr.com/photos/130911384@N02/16247635328" title="time_pdf_2_histfix by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8615/16247635328_17305344e9_o.png" width="560" height="420" alt="time_pdf_2_histfix"></a>

<a href="https://www.flickr.com/photos/130911384@N02/16247886800" title="time_pdf_semilog2_histfix by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7400/16247886800_111203f12c_o.png" width="560" height="420" alt="time_pdf_semilog2_histfix"></a>

> **Old Plots**
>I believe the thickness of the band in the data is due in part because of the large time scale plotted and that on small timescales there is lots of variation in the probability density.

<a href="https://www.flickr.com/photos/130911384@N02/16210405037" title="time_pdf_1 by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7329/16210405037_eafd986ffe_o.png" width="560" height="420" alt="time_pdf_1"></a>
<a href="https://www.flickr.com/photos/130911384@N02/15776281253" title="time_pdf_semilog1 by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8665/15776281253_b299280112_o.png" width="560" height="420" alt="time_pdf_semilog1"></a>


> Written with [StackEdit](https://stackedit.io/).
