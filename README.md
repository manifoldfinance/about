

<!--
Copyright 2020 - Sam Bacha
SPDX-License-Identifier: SSPL-1.0 / CC-NC-ND-2.5
 -->

class: center, middle
# Embedded Volumetric Optionality Protocol

sam@manifoldfinance.com
github.com/sambacha



Copyright 2020 - All Rights Reserved

---
class: center, middle
## Abstract

We propose a crypto-derived functional asset in which controllable volumetric functions are embedded
within the operational utility of the asset. As a result this function exhibits desirable properties
as a _unit of account_ for its underlying asset. We propose as a first iteration **GasEVO**, an
ethereum-based 'ERC-20 compliant' protocol in which _Gwei_, the computational unit of account for
the Ethereum Blockchain, is provided in a sort of packaged derivative in which agents may use to
position themselves from higher transactional volumes of the network at large (i.e. higher gwei
pricing events, typically of 2-3 stddev).

---
class: center, middle
# Value Proposition


- For People looking to gain exposure to crypto-assets

- Who wan't exposure without the numerous downside risks

- Our product is new category: *embedded volumetric optionality*

- 'EVO' provides the key benefit of downside price movement protection

- Unlike other strategies such as 'staking' or 'lending protocols'

We have the ability to integrate any asset, 
- Without the need for integration, simply deposit and create the market.

---


# Unique & Experienced

Different
Mechanics of Operation (similar to early withdrawal penalties or uber surcharge pricing, but distributed fees amongst everyone)
Utilizes Floating Point Math
Technically difficult to implement (utilize an excellent library, ABDK 64x64)
Team is:
Sam Bacha, Founder
2 Engineers from contract firm
1 Potential Partner, Sandy (an expert in KDB+/Quant)
Expense Model is LIGHT
Advocating for new assets to utilize protocol
Layer2 already in progress for design
Unique Value Proposition
This can create opportunities for teams to integrate "Staking as a Service"
Simply deposit tokens, just like creating a Uniswap Market

---

# Structure Speed Leverage

- Timing is in our benefit 
- Leverage possible with correct partners / backing
- Structure is small from operations perspective: 4 years of learned lessons in operating in this
space

Customers: 
    + Top - ERC-based Assets / Crypto-based Assets
    + Bottom - Individuals
    - Requires Buy-in from others

Advantage:
    + Ready to go to market (software is ready, 
     - still need additional marketing positioning & inital  liquidity)


Goals:
    + Multiple Asset Classes Covered
    - Legal Risk


---

# Whitepaper Breakdown

Questions: sam@manifoldfinance.com

---

## Overview

In essence by _acceleration_ and _deceleration_ (i.e. **velocity**) that the speed of the ERC20
token transfers (e.g. average transaction rate/mean transaction rate) can help to _counter-balance_
and reduce the market price volatility of the faster base currency (\$ETH). Our focus is on
purely-virtual crypto currencies, which are based on computational assets e.g. as BTC, which is
based on "mining", or ETH, which is based on computational "GAS".

> _Note_ We call this _Embedded Transactional Optionality_


---


## Token Value

Traditionally, commodities (e.g. like precious and rare metals) or assets of much lesser liquidity
or even fully illiquid assets (all of which are not without their own limitations), GasEVO
approximates its value by utilizing the unit of account- **block time**.

> _Note_ A more accurate representation would be _acceleration_ and _deceleration_ of the velocity
of liquidity 

---


## Transaction Inclusion as a Function of Time

 Liquidity and velocity, as a property of *indifference curves* (re: willingness) is a deterministic
property for any transactional instrument and its market exchange rate.

> TL:DR: Intangible worth is hard to approximate or convey, unless it is _time_


---


## Utility

Given enough liquidity (assuming frequent transactions) GasEVO has a way to compute the `exchange
rate` towards the base instrument (ETH). Like this, movements of the bigger or significant volumes
can be interpreted as market trends (i.e. higher gwei pricing.)

By utilizing small volume movements and disincentivizing the larger ones without compensation to
holders every exceeding unusual trade of the token is tracked by the smart contract and higher
"interest" fees are applied (re: withdraw, or 'consumption').

Transference of funds _below_ daily volume threshold does not impose any interest fee.

When the threshold has been exceeded some percentage of tokens gets burned, for the transfer, for
deposit or for withdraw of the base instrument (ETH).

Thresholds are tracked individually per address as the average rate and have a function by which
they operate on.

---

<!-- @format -->







---


### Protocol Overview

EVO tokens are minted and burned **on-demand** by deposit and withdraw operations directly via the
contract.

#### Initiated Protocol Operations

* Deposit
* Withdraw
* Transfer


These **operations** contribute to the *transfer rates*. Transfer rates are tracked both **in
aggregate** and **individually** (i.e. *per address*). The *period* of time for tracking is the last
`25 days`

> 25 days has `36000 minutes`, which *divided by* `block_time=4` gives `9000`


---


**GasEVO** is determined both in aggregate (dynamically) and individually for each address based on
transactional (i.e. volumetric transactional information) stored and updated through the smart
contract during the previous transactions. 


All three operations such as deposit, withdraw and transfer can equally contribute to the transfer
rates that are tracked totally and individually(as per holder) by the smart contract for the period
of the last 25 days.The token price is determined dynamically(and individually for each holder)
based on the information stored or updated in the smart contract during previous transactions:

---

{equation.gasevo}

$$
P_{t+1}(h, a):=\sqrt{\frac{D_{t}}{S_{t}}}+I_{t+1}^{\prime}(h, a)
$$



The above equation will compute the price for a holder $$h$$ to purchase a certain amount of `EVO`
tokens in exchange for a base deposit in `ETH/WETH` at the given discrete time - $$t +1$$ , where
$$Dt$$ stands for the deposit of `ETH` in the smart contract at previous time - point and $$St$$
stands for the total supply of `EVO` tokens so far.


---


The first component with the token - base ratio $$Dt/St$$ under the square root is the *indicative
price* and **does not depend on the purchase/transferred** amount, ``$a$.``

Ergo, the component $$I_{t+1}^{\prime}(h, a)$$ is called the *discounted interest rate* and it can
grow *proportionally* to a within a range of $$[0, 0.24]$$ of ``$$a$$.``


---


Higher interest payouts can slow down, **deaccelerate**, the price movement. Interest rate
determines how fast, or **accleration**, such price can change depending on the market demand &
supply pressure for EVO-based tokens. Interest[#] is computed individually for each EVO holder. 


*Note* that all interest payments are contributed to the same common deposit `Dt` on the smart
contract, which is supporting the indicative price. This means that interest is shared by all
holders that *choose not to trade their tokens* at the moment.

An ERC20 smart contract will contain the information about the balance of every address,

---


##### Address Information (i.e. wallets)
$$B(h) s.t. Bt + 1(h, a): = Bt(h) + a$$.

In addition to the individual balances, GasEVO contract keeps track about how much each holder has
transferred in the last epoch (i.e. 25days)

##### Total average transfer rate for an address
$$avg(Rt + 1(h, a)): = avg(Rt(h)) + a$$

##### Total average daily transfer rate for all holders 
$$avg(R¯ t + 1(h, a)): = avg(R¯t(h)) + a$$.

---


### Calculations
More formally calculation of the individual interest rate as well as the applied ownership discount
can be described in following steps:

For: $$l := 4 , m := 26$$ are the *low* and *high* *transfer rate constants* and 

$$\beta=\frac{\operatorname{avg}\left(B_{t+1}(h, a)\right)}{S_{t+1}}$$, the *future balance ratio*,
we resolve $$\tau=\frac{\operatorname{avg}\left(R_{t+1}(h,
a)\right)}{\operatorname{avg}\left(\bar{R}_{t+1}(h, a)\right)}$$ is the *future transfer ratio* and
$$\theta=\frac{B_{t}(h)}{S_{t}}$$ is the ownership ratio at a *discrete point in `block time`* then
we resolve the **interest rate**;

---


$$
P_{t+1}(h, a):=\sqrt{\frac{D_{t}}{S_{t}}}+I_{t+1}^{\prime}(h, a)
$$

thereby applying the ownership ratio for discount 

$$l_{t+1}^{\prime}(h, a):=\frac{a \times \sqrt{l * \max \left(\min \left(\theta, l^{2}\right),
1\right)}}{100}$$

whereas %$$I`$$ is the *discount**, thereby computing the *discounted interest* as,

$$I_{t+1}^{\prime}(h, a):=\max \left(I_{t+1}(h, a), l_{t+1}^{\prime}(h,
a)\right)-l_{t+1}^{\prime}(h, a)$$

Price dynamics of equation (1) depends on the transactions volume conducted by all of the involved
market participants and bounded by $$O(sqrt(n))$$.

---

Therefore it can be expected that the demand for EVO Protocol based tokens like GasEVO will be able
to represent the *demand* for the value storage, whereas GasEVO represents the value of storage as a
derivative function of the underlying asset, Ethereum (i.e. gwei, or as a fixed unit of account for
contracting)

---

---


## Appendix

### Window Calculation

> informative
> 525600 / 4 = 131400
> 131400 / 25
> windows = 5256


###### tags: ``{erc20.balance_wallet}``

### Address Balance
$$B(h) s.t.$$

$B_{t+1}(h, a):=B_{t}(h)+a$

### Adress Balance
$$B(h) s.t. B_{t+1}(h, a):=B_{t}(h)+a$$

### Discrete Transfer Rate 
###### tags: ``{calculation.25day_transfer_rate_discrete}``


### Equations
<!-- 
$$\operatorname{avg}\left(R_{t+1}(h, a)\right):=\operatorname{avg}\left(R_{t}(h)\right)+a$$
-->

### Aggreagte Transfer Rate
###### tags: ``{calculation.transfer_rate_aggregate}``
$$\operatorname{avg}\left(\bar{R}_{t+1}(h,
a)\right):=\operatorname{avg}\left(\bar{R}_{t}(h)\right)+a$$

### Future Balance Ratio
###### tags: ``{equations.future_balance:ratio}``
$$\beta=\frac{\operatorname{avg}\left(B_{t+1}(h, a)\right)}{S_{t+1}}$$

###### tags: ``{equations.future-transfer:ratio}``
$$\tau=\frac{\operatorname{avg}\left(R_{t+1}(h, a)\right)}{\operatorname{avg}\left(\bar{R}_{t+1}(h,
a)\right)}$$

###### tags:``{equations.ownership:ratio(DISCRETE_POINT)}``
$$\theta=\frac{B_{t}(h)}{S_{t}}$$

###### tags: {equations.gasevo}

``P_(t+1)(h,a):=sqrt((D_(t))/(S_(t)))+I_(t+1)^(')(h,a)``

$$
P_{t+1}(h, a):=\sqrt{\frac{D_{t}}{S_{t}}}+I_{t+1}^{\prime}(h, a)
$$

### 2 Interest Rate
###### tags: {equations.interest_rate}
<!--
$$I_{t+1}(h, a):=\frac{a \times \min (\operatorname{avg}(\beta, \tau), m)}{100}$$
-->

$$I_{t+1}(h, a):=\frac{a \times \min (\operatorname{avg}(\beta, \tau), m)}{100}$$

### 3 Ownership Rate
###### tags: {equations.ownership_ratio}
<!--
l_{t+1}^{\prime}(h, a):=\frac{a \times \sqrt{l * \max \left(\min \left(\theta, l^{2}\right),
1\right)}}{100}
-->

$$l_{t+1}^{\prime}(h, a):=\frac{a \times \sqrt{l * \max \left(\min \left(\theta, l^{2}\right),
1\right)}}{100}$$

### 4 Discounted Interest Rate
###### tags: {equations.discounted_interest_rate}
<!-- 
I_{t+1}^{\prime}(h, a):=\max \left(I_{t+1}(h, a), l_{t+1}^{\prime}(h, a)\right)-l_{t+1}^{\prime}(h,
a)
-->

$$I_{t+1}^{\prime}(h, a):=\max \left(I_{t+1}(h, a), l_{t+1}^{\prime}(h,
a)\right)-l_{t+1}^{\prime}(h, a)$$

###### tags: {equations.discounted_interest_rate_qed}
<!--
I_{t+1}^{\prime}(h, a) \in[0,0.24]
-->

$$I_{t+1}^{\prime}(h, a) \in[0,0.24]$$

###### tags: {equation.stress_test}

> appendix scenario: *Firesale* 


$$\sqrt{\frac{\left(m-\max \left(l^{\prime}\right)\right) * D_{t}}{100}},$$ $$where; 
m:=26, l:=8$ and S_{t}=B_{t}(h)=1$$

## Epilogue

---

# Volumetric Manifolds

> A constructed mechanism for facilitation of efficient and effective contract$^[1]$ trading 

$$
G:=(V, E, w)
$$



weighted by the function $w: E \rightarrow \mathbb{R}^{+}$ corresponding to the price of some trade
$e \in E$


$$ V,|V| \leq|\mathbb{N}| $$



Consider an abstract liquid trading (ALT) system as a weighted directed graph $G:=(V, E, w),$ where
set of vertices $V,|V| \leq|\mathbb{N}|$ contains digital representation of all tradeable assets in
$G,$ set of edges $E=\{e \in V \times V:$ $w(e)>0\}$ represents all possible atomic $^{79}$
asymmetric $^{80}$ trades, which are weighted by the function $w: E \rightarrow \mathbb{R}^{+}$
corresponding to the price of some trade $e \in E$

### Liquidity Point/Vertex

$$
\text { Any liquid vertex } v \in V \text { has both } d e g^{-}(v) \geq 1 \text { and }
\operatorname{deg}^{+}(v) \geq 1
$$


### Liquidity Indifference Preference Paths$^{2}$

$$C_{B}(v):=\sum_{s \neq t \neq v \in V} \frac{\sigma_{s t}(v)}{\sigma_{s t}}: \forall(s, t) \in S,
\text { where } \sigma_{s t}:=\sum_{(s, t) \in S} \sum_{e \in(s, t)} w(e)$$





Vertex $v \in V$ represents half-liquid asset  when either $\operatorname{deg}^{-}(v)=0$ (source)
$\operatorname{or} \operatorname{deg}^{+}(v)=0(\operatorname{sink}),$ where
$\operatorname{deg}^{(-1+)}: V \rightarrow \mathbb{N}$ is respectively a number
of tail ends (indegree) and a number of head ends (outdegree) from vertices adjacent to $v$.


## Liquidity Preference Path

Let $S \subset V \times V$ contain all shortest paths from vertex $s$ to vertex $t: \forall s, t \in
V$ Also let vertex $v \in V$ have the maximal $^{82}$ betweenness centrality measure
$C_{B}(v):=\sum_{s \neq t \neq v \in V} \frac{\sigma_{s t}(v)}{\sigma_{s t}}: \forall(s, t) \in S,$
where $\sigma_{s t}:=\sum_{(s, t) \in S} \sum_{e \in(s, t)} w(e)$
and $\sigma_{s t}(v)$ 
is a sum of only those shortest paths in $S$ which contain $v .$ We say that $(s, t) \in S$ **is a
path with preferable liquidity if it ends with** 

   $v$ `in essence,` $t=v$

So that we may compute the approximate list of *preferable assets*, we highlight two distinct
properties that are both necessary and sufficient.

In order to capture a desired hyper-manifold liquidity property of an always preferable asset, $G,$
, we identify such asset not only as a preferable "exit" (that is to say, the position can be
unwound within a resonable amount of blocks without materially affecting price of the asset)
$vertex$, but also as the one that can be consequently traded for any other liquid asset in $G$ at
the most best settlement price.


### List

$(\operatorname{manifold})$
$(\operatorname{hyper-manifold})$
$(\operatorname{supra-manifold})$
$(\operatorname{inter-manifold})$


## References

cont...


## 

Let $S \subset V \times V$ contain all shortest paths from vertex $s$ to vertex $t: \forall s, t \in
V$ Also let vertex $v \in V$ have the maximal $^{82}$ betweenness centrality measure
$C_{B}(v):=\sum_{s \neq t \neq v \in V} \frac{\sigma_{s t}(v)}{\sigma_{s t}}: \forall(s, t) \in S,$
where $\sigma_{s t}:=\sum_{(s, t) \in S} \sum_{e \in(s, t)} w(e)$


and $\sigma_{s t}(v)$ is a sum of only those shortest paths in $S$ which contain $v .$

We say that $(s, t) \in S$ is a path with **preferable liquidity** if it ends with $v,$ i.e. $t=v$


In order to capture a desired liquidity preference curve ("hyper manifold") property of an always
preferable asset in an 
"ALT"-system $G,$ we must first identify such asset. Such an asset must exhibit the properties of
not only having *genuine* liquidity (that is to say, "a preferable "exit" $(\operatorname{sink})$
vertex"), but also as the one that can be consequently traded for any other liquid asset in $G$ at
the most attractive price.

### Flash Loan led path-finding

A "liquid"$^[3]$ vertex $v \in V\left(G^{\prime}\right)$ of a complete liquid subgraph $G^{\prime}
\subseteq G$ is called a *hyper*-liquid vertex when any preferable liquidity path 

<!-- 
\label{preferable liquidity path}
-->
$p=(s, v)$ 



can be almost surely continued with an efficient trade for any other liquid $u \in
V\left(G^{\prime}\right), u \neq v$ in such a way that $\sum_{e \in(s, u)} w(e) \leq \sum_{e \in(s,
v)} w(e)+\sum_{e \in(v, u)} w(e)$ and $(s, u)$ is
a shortest path.


### Footnotes

$^[1]$ Contracts meaning *Smart Contracts*

^[3] Pockets of Liquidity is a well known microstructure in markets. Further research in the
microstructural differences between AMM's and traditional settlement procedures (e.g. LMM, FIFO,
etc) must be pursued.

^[4]Dijkstra’s algorithm
is priority ﬁrst search on G starting at s using priority P(v) = min

MPL-2.0

