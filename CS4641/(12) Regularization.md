We put bounds onto our regression model to reduce the error
- Remember the bias variance tradeoff: L = $\text{bias}^2 + \text{variance}$ 
- We need to adjust our bias and variance just a little bit to achieve a good balance

The weights $\theta$ are what affect our regression curve the most, so if we bound $\theta$ with a constraint, then we can hopefully reduce loss
- This means, however, our constraint is a new hyperparameter

With hard constraints:
$y = \theta_0 + \theta_1z1 + \theta_2z_2 + \cdots + \theta_d z_d$
	s.t $\theta_d = 0$ for $d > 2$
$y = \theta_0 + \theta_1z_1 + \theta_2z_2 + 0 + 0 + \cdots + 0$

by doing this though, we end up losing data and losing valuable info, like $\theta_5$

Is there a way we can bound info without losing lots of data?