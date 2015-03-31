---
title: Cell Volume Notes
layout: post
---


# Cell Volume as a function of Alpha

## Model

$$ \beta H_s = \sum_{j=1}^N \left[\alpha\left(V_j/V_0-1\right)^2-\sigma_j\gamma\right] $$

A simple check that the simulations are working is to see how the cell volume $$V_j$$ changes as $$\alpha$$ changes.

We expect that for large values of $$\alpha$$ energy costs for stretching and compression are high and so the cell will stay near the relaxed volume. Whereas when $$\alpha$$ decreases the spread in cell volume will get larger.

# Results

All results were done with $$\gamma=10.0$$ and a simulation space of 1,000 lattice points.

## 1 Cell Chain

The legend indicates the value of $$\alpha$$ for the respective run.

The relaxed volume size (black bar) was varied as well.

<a href="https://www.flickr.com/photos/jjjvar/16957182566" title="alpha_comparison2 by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8742/16957182566_8b66d714f1_b.jpg" width="800" height="600" alt="alpha_comparison2"></a>

<a href="https://www.flickr.com/photos/jjjvar/16360751034" title="alpha_comparison by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7587/16360751034_6c4c59d17e_b.jpg" width="800" height="600" alt="alpha_comparison"></a>

<a href="https://www.flickr.com/photos/jjjvar/16360752734" title="alpha_comparison by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7620/16360752734_4f2964ee80_b.jpg" width="800" height="600" alt="alpha_comparison"></a>

## 3 Cell Chain

The legend indicates the cell in the chain. They are numbered from the reflective boundary out.

The relaxed volume size (black bar) was varied as well.

<a href="https://www.flickr.com/photos/jjjvar/16368894323" title="multicell_comparison1 by Julien Varennes, on Flickr"><img src="https://farm9.staticflickr.com/8754/16368894323_ed777c4d52_b.jpg" width="800" height="600" alt="multicell_comparison1"></a>

<a href="https://www.flickr.com/photos/jjjvar/16801277258" title="multicell_comparison2 by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7588/16801277258_e8251ba768_b.jpg" width="800" height="600" alt="multicell_comparison2"></a>

<a href="https://www.flickr.com/photos/jjjvar/16989167525" title="multicell_comparison4 by Julien Varennes, on Flickr"><img src="https://farm8.staticflickr.com/7602/16989167525_3f01e1c50a_b.jpg" width="800" height="600" alt="multicell_comparison4"></a>

## Observations

 - As alpha increases the distributions become more sharply peaked about the relaxed cell volume.
 - As alpha decreases the distributions become wider.
	 -  As alpha gets smaller the symmetry in the distribution is broken by the fact that the volume cannot get smaller than 1.
 - Relaxed cell volume does have an effect on the distribution.
	 - As $$V_0$$ increases the distribution becomes more spread out.
		 - This makes sense since changes in $$V_j$$ will now lead to smaller changes in the quantity $$ \left(V_j/V_0-1\right)^2 $$
		- And so the energy cost for stretching/compression decreases.
		- Making the relaxed volume large gives the benfit of a more symmetric distribution but at the cost of widening that distribution for all values of alpha.

It seems that having a small relaxed volume is more beneficial than a large one. With $$V_0=50$$ the distributions keep more of their desired shape even for small $$\alpha$$.
