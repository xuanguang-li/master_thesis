This file provides the structure of the slide to show following points:
1. What I mean by propagation of idiosyncratic shock
2. Why lumpy investment assumption is important
3. Why we can use the reduced-form investment demand shock in estimation (add a shock directly on investment)

## Intermediate goods producers

Under standard New-Keynesian model, output is aggregated by CES aggregator
$$Y_t = \left(\int_0^1 y_{jt}^{\frac{\eta-1}{\eta}} \, dj\right)^{\frac{\eta}{\eta-1}} $$
Each intermediate goods producer faces demand $y_{jt} = \left(\frac{p_{jt}}{P_t}\right)^{-\eta} Y_t$, and their production function is $y_{jt} = a_{jt} k_{jt}$.

Combine both of them and derive their real current revenue
$$
r_{jt} (a_{jt}, k_{jt})
=
\frac{p_{jt}y_{jt}}{P_t}
=
\underbrace{\left(
\left(\frac{p_{jt}}{P_t}\right)^{-\eta}
\right)^{\frac{1-\eta}{-\eta}}
Y_t^{\frac{1-\eta}{-\eta}}}_{y_{jt}^{\frac{1-\eta}{-\eta}}} Y_t^{1-\frac{1-\eta}{-\eta}}
=
\left(a_{jt}k_{jt}\right)^{1-\frac{1}{\eta}}
Y_t^{\frac{1}{\eta}}
$$
## Lumpy investment and investment threshold

They decide how to invest ($x_{j, t}$) by the following optimal problem:
$$\max_{\{x_{t+k}\}_{k=0}^{\infty}}\, \mathbb{E}_t\left[\sum_{k=0}^{\infty}\Lambda_{t, t+k} \left(r_{j, t+k} - x_{j, t+k}\right)\right],\,\, s.t.\,k_{j,t+1} = (1-\delta)k_{j,t} + x_{j,t}$$

Suppose investment can be any value, the derivative of the objective function
$$\frac{\partial V}{\partial k_{t+k}} = \mathbb{E}_t\left[\Lambda_{t,t+k}\left(\frac{\partial r_{j,t+k}}{\partial k_{t+k}} + (1-\delta)\right) - \Lambda_{t, t+k+1}\right]$$

This derivative is strictly decreasing, approaching to infinity when $k_{t+k}$ approaches to zero, and approaching to negative infinity when $k_{t+k}$ approaches to infinity *(instruction: check my argument)*. Thus, the plot of this function looks like this (*instruction: please add one tikzplot, also consider the following usage of the plot, Figure 1).

However, they also face lumpy investment constraint, and for simplicity, I assume firms can't invest multiple $\lambda^n$.
$$x_{j,t+k} \in \{0,\, \lambda k_{j, t+k}\}$$
We leverage the plot to find out the investment threshold:
1. We find an interval $[k^*, \lambda k^*]$ around the unique peak such that $k^*$ and $\lambda k^*$ receive the same value.
2. If $(1-\delta)k_{j,t}$ sit the left hand side of $k^*$, $\lambda k^*$ leads us to the side of the peak, but the value of the objective function is the same
3. If $(1-\delta)k_{j,t}$ sit on the right hand side of $k^*$, as $\lambda k' >\lambda k^*$, we will be in the right hand side of $\lambda k^*$, getting less value.
*instruction: also use Figure 1 to interpret*

Further, If we sit right on $k^*$, invest or not are equivalent, which gives us an equation to calculate $k^*$. Suppose the firm knows its future technology, we get the threshold *(instruction: add the expression of \Psi)*
$$k_{j,t+1}^* = a_{j,t+1}^{\eta  - 1} \Phi_t Y_{t+1}, \,\, \Phi_t = $$

To normalize the capital holding,  define the distance to the threshold.
$$s_{jt} = \frac{\log \frac{k_{jt}}{k_{jt}^*}}{\log \lambda}$$
## Stationary distribution and investing fraction

There two dimensions of heterogeneity: technology and capital holding, and thus the stationary (cross-section) distribution means $F(a, s)$.

For simplicity, I assume $a_t\in \{a_1, a_2\}$, and under some assumptions, $s_t|a_t \sim U[0,1)$.
- $[0,1)$ support: At time $t$, the firm will invest once they realize $s_{j, t+1}<0$ and stay inactive if they think $s_{j, t+1} \in [0,1]$. Thus, at time $t+1$, those who invested will let $s_{j, t+1} \in [0, 1)$, and those who didn't invest will also let $s_{j, t+1} \in [0, 1)$.
- The uniform distribution attributes to other assumptions
*instruction: insert a plot to illlustrate, Figure 2*

Under the assumption before, macro variables are all stationary, $Y = Y_t = Y_{t+1}$ and $\Phi = \Phi_t = \Phi_{t+1}$, and  there are four groups: $\{a_t = L, a_{t+1} = L\}$, $\{a_t = H, a_{t+1} = L\}$... In each group, we calculate how many of them will invest in time $t$:
$$
\begin{aligned}
s_{j,t+1}(a_{j,t} = a, a_{j, t+1} = a') & = \frac{\log k_{j,t+1} - \log k^*_{j,t+1}(a')}{\log \lambda} \\
& = \frac{\log (1-\delta)k_{j,t} - \log k^*_{j,t}(a) + \log k^*_{j,t} (a) - \log k^*_{j,t+1}(a')}{\log \lambda} \\
& = s_{j,t}(a) - \frac{\log (1-\delta) + \log k^*_{j,t+1}(a') - \log k^*_{j,t}(a)}{\log \lambda} \text{ (macro variables are constant)}\\
& = s_{j,t}(a) - \underbrace{\frac{\log (1-\delta) + \log a' - \log a }{\log \lambda}}_{>0 \text{ by assumption}}
\end{aligned}
$$

As mentioned before, those who expect $s_{j, t+1}<0$ will invest. Since $s_{t}$ is distributed uniformly in $[0, 1)$ conditional on $a_{t}=a$, thus lower $\frac{\log (1-\delta) + \log a' - \log a}{\log \lambda}$ fraction of firm will invest. *instruction: also use Figure 2 to interpret the point*

Motivated by this, we define **investing fraction**:
$$s^*(a, a') = \frac{\log (1-\delta) + \log a' - \log a}{\log \lambda}$$
## Idiosyncratic shock and propagation

Now I add an $i.i.d$ idiosyncratic shock $\varepsilon$ on $a'$ in a certain group $(a, a') = (b, b')$, and we call $\omega(b,b')\nu$ as **$\varepsilon$-induced investing fraction**:
$$s^*(b, \varepsilon b') = \frac{\log (1-\delta) + \log \varepsilon b' - \log b}{\log \lambda} = s^*(b, b') + \underbrace{\frac{\log \varepsilon}{\log \lambda}}_{\nu}$$The shock literally increases the investing fraction within group, and indirectly increases the future aggregate output, by which I mean **propagation**:
$$
\begin{aligned}
Y_{t+1}(b, b', \nu) &= \left(\omega(b, b')\int_0^1 (b'k_{t+1}(s_t))^{\frac{\eta-1}{\eta}}\, dF(s_t\,|\,a_t=b)\right)^{\frac{\eta}{\eta-1}}\\
&= \left(\omega(b, b') \left(\underbrace{\int_0^{s^*(b, b')+\nu} (b'k_{t+1}(s_t))^{\frac{\eta-1}{\eta}}\, dF(s_t\,|\,a_t=b)}_{\text{investing firms}}
+ \underbrace{\int_{s^*(b, b')+\nu}^1 (b'k_{t+1}(s_t))^{\frac{\eta-1}{\eta}}\, dF(s_t\,|\,a_t=b)}_{\text{those not investing}}\right)\right)^{\frac{\eta}{\eta-1}}\\
&= \left(\omega(b, b')\left(\int_0^{s^*(b, b')+\nu} (b'\underbrace{\lambda}_{\text{with investment}}(1-\delta)\underbrace{\lambda^{s_t}b^{\eta-1}\Phi Y}_{k_{t} = \lambda^{s_t}k^*_t})^{\frac{\eta-1}{\eta}}\, dF(s_t\,|\,a_t=b)
+ \int_{s^*(b, b')+\nu}^1 (b'(1-\delta)\underbrace{\lambda^{s_t}a^{\eta-1}\Phi Y}_{k_t})^{\frac{\eta-1}{\eta}}\, dF(s_t\,|\,a_t=b)\right)\right)^{\frac{\eta}{\eta-1}}
\end{aligned}
$$

Remark: 
- $\Phi$ is stationary because I assume the firms first influenced by $\varepsilon$ still use stationary scenario to form expectation. 
- $\omega(b, b')$ is the measure of this group. *(instruction: add a plot to illustrate the measure of each group (only four groups), Figure 3)*

The increase of $Y_{t+1}$ propagate to each group through non-stationary investing fraction:
$$s^*_t(a, a', \nu) = \frac{\log (1-\delta) + \log a' - \log a + \log Y_{t+1}(\nu) -\log Y_t}{\log \lambda}$$

In each group, the induced investing fraction is:
$$
\Delta s_t^*(a, a',\nu) = s^*(a, a',\nu) - s^*(a, a', 0) = \frac{\log Y_{t+1}(\nu) - \log Y_t(0)}{\log \lambda}
$$
In aggregation, the **$\nu$-induced investing fraction** is:
$$
\Delta s_t^*(\nu) = \sum_{(a, a')} \omega(a, a')\Delta s_t^*(a, a', \nu) =  \frac{\log Y_{t+1}(\nu) - \log Y_t(0)}{\log \lambda}
$$
The shock $\varepsilon$ caused the $\nu$ fraction of firm in group $(b, b')$ to spike investment. Through multiplier effect in the general equilibrium, $\nu$ induced $\Delta s_t^*(\nu)$ again. The effect will continue to iterate, and finally reach to another equilibrium.

The theoretic result provides some charateristic property of the propagation,
$$\lim_{\nu\to 0} \frac{\Delta s_t^*(\nu)}{\omega(b, b')\nu} = 1$$which says the $\nu$-induced investing fraction has the same scale with $\varepsilon$-induced investing fraction ($\nu\to 0$ literally means the small scale of idiosyncratic shock), and thus the fraction won't decrease in the iteration.

## Macro-level investment shock

But think the case: though in every iteration there are some firms invest more, but the amount of the investment decay very fast. In such case, aggregate investment may move just a little, and it is where the amplification effect of the lumpy investment works--if you want to invest, you have to invest a fairly large amount.

We can finally prove that when the number of firms goes to infinite, though the $i,i,d$ idiosyncratic shock vanishes, the induced investment over iteration remains a degenerated random variable, which justify adding the shock before investment rather than in the technology.