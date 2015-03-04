
# Connected Cell Diffusion

## The Algorithm

There are three cases that the code handles.

1. Single cell diffusion
2. [Edge cell diffusion](#edge)
3. [General case diffusion](#general)

The single cell case is treated as a simple random walk. The edge cases and the general case are the more involved scenarios. Since cells can stretch or compress there are many different scenarios that can take place when cells try to move.
The method used to determine which possible outcome will be chosen is explained [at the bottom of the page](#method).

### <a id="edge"></a>Edge Case

The *edge case* refers to the cell at the end or the beginning of the 1D chain of cells. Since this cell has only one neighbor this leads to different scenarios then the general case.
In the following pictures assume that the **yellow** cell is the edge cell, and that the **blue** cell is its neighbor.

<a href="https://www.flickr.com/photos/jjjvar/16690495336" title="Yellow is the edge cell"><img src="https://farm9.staticflickr.com/8590/16690495336_e9a469e4c7_b.jpg" width="784" height="102" alt="cells_edge_0"></a>
<br><br>
If the edge cell wants to move *in* -- the *leftward* direction -- there are the following possible states.
<a href="https://www.flickr.com/photos/jjjvar/16527178878" title="Inward movement"><img src="https://farm9.staticflickr.com/8677/16527178878_794bcaf061_o.png" width="785" height="382" alt="cells_edge_cmp"></a>
<br><br>
If the edge cell wants to move *out* -- the *rightward* direction -- there are the following possible states.

<a href="https://www.flickr.com/photos/jjjvar/16715125541" title="Outward movement"><img src="https://farm9.staticflickr.com/8585/16715125541_af1fb4a0a4_b.jpg" width="787" height="381" alt="cells_edge_str"></a>
<br><br>
If the edge cell had been on the left as opposed to the right, the possible outcomes would be the reflections of the ones listed above.
<br><br>

### <a id="general"></a>General Case

The *general case* refers to a cell in the middle of the chain. This cell has neighbors on both of its sides.
In the following pictures assume that the **yellow** cell is the principal cell, the **blue** cell is its  left neighbor, and the **red** cell is its right neighbor.

<a href="https://www.flickr.com/photos/jjjvar/16509130417" title="Yellow is the principal cell"><img src="https://farm9.staticflickr.com/8595/16509130417_d7a1d23e94_b.jpg" width="786" alt="cells_3_0"></a>
<br><br>
If the principal cell wants to move *leftward* there are the following possible states.
<a href="https://www.flickr.com/photos/jjjvar/16094962943" title="Leftward movement"><img src="https://farm9.staticflickr.com/8566/16094962943_4d55b5b5ed_o.png" width="786" alt="cells_3_left"></a>
<br><br>
If the principal cell wants to move *rightward* there are the following possible states..
<a href="https://www.flickr.com/photos/jjjvar/16688995866" title="Rightward movement"><img src="https://farm9.staticflickr.com/8618/16688995866_f744fcc1fa_o.png" width="786" alt="cells_3_right"></a>
<br><br>

### <a id="method"></a>Choosing the State

We need a method to determine which state will be the chosen outcome. This is done by calculating the Hamiltonian of each state and then assigning a probability to that state.
For a given state $s$ the Hamiltonian is given by

$$
H_s = \sum_{j=1}^N \lambda\left(V_j-V_0\right)^2 - f\Delta x \ .\\
\begin{align*}
\lambda &\equiv \text{compression coefficient} \\
V_j &\equiv \text{volume off cell j} \\ V_0 &\equiv \text{relaxed cell volume} \\
f &\equiv \text{force cell exerts} \\ \Delta x &\equiv \text{distance cell moves}
\end{align*}
$$

The direction of the force is chosen randomly at the begin of each calculation. This will bias the principal cell's movement either to the left or right.

$$ f = \pm \vert\vec{f}\vert$$

The probability is given by 

$$ p_s \propto e^{-\beta H_s} \ .$$

The probabilities are normalized by summing over all the Boltzmann factors of the possible outcomes and the original state. The outcome is then chosen based on those normalized probabilities.

$$ Z=\sum_s e^{-\beta H_s} \ \rightarrow \ p_s=\frac{e^{-\beta H_s}}{Z} $$
