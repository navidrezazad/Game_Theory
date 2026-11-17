# 61. First-Price Sealed-Bid Auction

## Problem statement

There are $N$ risk-neutral bidders with independent private values $v_i\sim U[0,1]$. Each submits one sealed bid; the highest bidder wins and pays their own bid. Find the symmetric increasing Bayesian Nash equilibrium bidding function and expected seller revenue.

## Solution

For $N\ge 2$, the symmetric increasing Bayesian Nash equilibrium is

```math
\boxed{\beta(v)=\frac{N-1}{N}v.}
```

The seller’s expected revenue is

```math
\boxed{\mathbb E[R]=\frac{N-1}{N+1}.}
```

Each bidder bids below their value. The difference, $v/N$, is their profit if they win.

We assume nonnegative bids and no reserve price.

## 1. The story: Maya wants a telescope

A seller offers one telescope. There are $N$ bidders. Each bidder wants the telescope for personal use.

Maya values the telescope at $0.80$ units of money. She knows her own value. She knows that each rival’s value comes independently from $U[0,1]$.

Maya writes a bid and seals it in an envelope. Each rival does the same. The seller opens the envelopes. The highest bidder receives the telescope and pays their own bid.

Maya faces two effects:

- A higher bid increases her chance of success.

- A higher bid reduces her profit if she succeeds.

If Maya bids $0.80$, her profit is zero even if she wins. If she bids $0.40$, her profit is $0.40$ if she wins. But the lower bid gives her a smaller chance of success.

**Her objective is to maximize expected profit.**

For a bidder with value $v$ and bid $b$, profit is

```math
u=
\begin{cases}
v-b, & \text{if the bidder wins},\\
0, & \text{if the bidder loses}.
\end{cases}
```

A risk-neutral bidder evaluates the probability-weighted average of this profit. Thus,

```math
\boxed{
\text{Expected profit}
=
\text{Profit if successful}
\times
\text{Probability of success}.
}
```

This equation controls the entire problem.

## 2. What equilibrium requires

Let $\beta(v)$ denote the bid that a bidder with value $v$ submits.

The requested equilibrium has three properties.

| Property | Meaning |
| --- | --- |
| Symmetric | Every bidder uses the same function $\beta$. |
| Increasing | A higher value produces a higher bid. |
| Bayesian Nash equilibrium | Given their own value, no bidder can increase expected profit through a different bid, while rivals follow $\beta$. |

Bidders use the same function. Their different values produce different bids.

The word “Bayesian” refers to the uncertainty about rival values. Each bidder uses the known distribution to calculate expected profit.

We first derive a candidate function. We then check all possible bid deviations.

## 3. Calculate the probability of success

### A useful way to describe a different bid

Suppose all rivals use a strictly increasing function $\beta$.

Your true value is $v$. You can submit the bid that the function assigns to another value $x$:

```math
b=\beta(x).
```

Here, $x$ describes your chosen bid. Your actual value remains $v$.

Because $\beta$ is strictly increasing,

```math
\beta(x)>\beta(v_j)
\quad\Longleftrightarrow\quad
x>v_j.
```

Thus, your bid beats rival $j$ exactly when that rival’s value is below $x$.

For $0\le x\le 1$, the uniform distribution gives

```math
\Pr(v_j\lt x)=x.
```

You must beat all $N-1$ rivals. Independence allows us to multiply their probabilities:

```math
\boxed{
\Pr(\text{win with bid }\beta(x))
=
x^{N-1}.
}
```

The exponent is $N-1$ because there are $N-1$ rivals.

The continuous value distribution gives ties probability zero.

### Expected profit from this bid

If you win, your profit is $v-\beta(x)$. Therefore,

```math
\boxed{
\pi(v,x)=\bigl[v-\beta(x)\bigr]x^{N-1}.
}
```

This formula separates the two effects:

```math
\underbrace{v-\beta(x)}_{\text{profit if successful}}
\quad\times\quad
\underbrace{x^{N-1}}_{\text{probability of success}}.
```

As $x$ increases, the first factor decreases. The second factor increases.

In equilibrium, a bidder with value $v$ must find $x=v$ optimal.

## 4. Derive the equilibrium function

### Step 1: Find the optimality condition

We first search for a differentiable function $\beta$.

The bidder changes $x$, while their true value $v$ stays fixed. Differentiate expected profit with respect to $x$:

```math
\frac{\partial \pi(v,x)}{\partial x}
=
-\beta'(x)x^{N-1}
+
\bigl[v-\beta(x)\bigr](N-1)x^{N-2}.
```

For an interior value $v\in(0,1)$, equilibrium requires this derivative to equal zero at $x=v$:

```math
-\beta'(v)v^{N-1}
+
\bigl[v-\beta(v)\bigr](N-1)v^{N-2}
=0.
```

Divide by $v^{N-2}$:

```math
-v\beta'(v)+(N-1)\bigl[v-\beta(v)\bigr]=0.
```

Rearrange:

```math
\boxed{
v\beta'(v)+(N-1)\beta(v)=(N-1)v.
}
```

This is a differential equation for the unknown bid function.

### What the equation means

The same condition can be written as

```math
\underbrace{\beta'(v)v^{N-1}}_{\text{extra expected cost}}
=
\underbrace{\bigl[v-\beta(v)\bigr](N-1)v^{N-2}}_{\text{extra expected benefit}}.
```

A small increase in $x$ raises the bid. That increase costs more in the cases where the bidder already wins.

The increase also creates additional chances to win. Those extra wins produce additional profit.

At the optimal bid, these two effects balance.

### Step 2: Solve the equation

Multiply the differential equation by $v^{N-2}$:

```math
v^{N-1}\beta'(v)
+
(N-1)v^{N-2}\beta(v)
=
(N-1)v^{N-1}.
```

The left side is a product derivative:

```math
\frac{d}{dv}\left[v^{N-1}\beta(v)\right]
=
(N-1)v^{N-1}.
```

We need a boundary condition near zero.

In an equilibrium with nonnegative bids,

```math
0\le \beta(v)\le v.
```

To see the upper bound, suppose a positive-value bidder bids above their value. They win with positive probability and make a loss whenever they win. A zero bid guarantees nonnegative profit.

Therefore,

```math
0\le v^{N-1}\beta(v)\le v^N.
```

It follows that

```math
\lim_{v\downarrow 0}v^{N-1}\beta(v)=0.
```

Now integrate from $0$ to $v$:

```math
v^{N-1}\beta(v)
=
\int_0^v (N-1)t^{N-1}\,dt.
```

The integral equals

```math
v^{N-1}\beta(v)
=
\frac{N-1}{N}v^N.
```

For $v>0$, divide by $v^{N-1}$:

```math
\boxed{
\beta(v)=\frac{N-1}{N}v.
}
```

The function extends to $\beta(0)=0$.

Its slope is

```math
\beta'(v)=\frac{N-1}{N}>0.
```

Thus, the candidate function is strictly increasing for $N\ge2$.

## 5. Check that no different bid gives more profit

A zero derivative identifies a candidate optimum. We must also prove that this candidate gives the largest expected profit.

Define

```math
a=\frac{N-1}{N}.
```

Suppose every rival uses $\beta(t)=at$.

### Bids within the equilibrium range

Every bid in $[0,a]$ has the form $b=ax$, where $x\in[0,1]$.

For a bidder with true value $v$,

```math
\pi(v,x)=(v-ax)x^{N-1}.
```

Differentiate:

```math
\begin{aligned}
\frac{\partial\pi(v,x)}{\partial x}
&=(N-1)vx^{N-2}-Na x^{N-1}\\
&=(N-1)x^{N-2}(v-x).
\end{aligned}
```

For $x>0$, the sign depends on $v-x$.

| Choice of $x$ | Sign of the derivative | Effect of increasing $x$ |
| --- | --- | --- |
| $x\lt v$ | Positive | Expected profit increases. |
| $x=v$ | Zero | Expected profit reaches its maximum. |
| $x>v$ | Negative | Expected profit decreases. |

Therefore, the optimal choice is

```math
x=v,
```

which gives

```math
b=av=\frac{N-1}{N}v.
```

The same argument gives the endpoint choices. A bidder with value zero bids zero. A bidder with value one bids $a$.

### Bids above the equilibrium range

The largest possible rival bid is $a$. A bid of $a$ already wins with probability one.

Any bid $b>a$ also wins with probability one, but costs more:

```math
v-b\lt v-a.
```

We already checked the bid $a$ as the choice $x=1$. Therefore, bids above $a$ cannot improve expected profit.

This proves that the proposed function is a best response to itself. Hence, it is a symmetric Bayesian Nash equilibrium.

## 6. Return to Maya: a numerical example

Suppose there are two bidders. Then

```math
\beta(v)=\frac{v}{2}.
```

Maya’s value is $0.80$, so her equilibrium bid is

```math
\beta(0.80)=0.40.
```

Her rival also bids half their value.

For a bid $b\le0.50$, Maya wins when the rival’s value is below $2b$. Thus,

```math
\Pr(\text{win})=2b.
```

A bid of $0.50$ or more wins with probability one.

| Maya’s bid | Probability of success | Profit if successful | Expected profit |
| --- | --- | --- | --- |
| $0.20$ | $0.40$ | $0.60$ | $0.24$ |
| **$0.40$** | **$0.80$** | **$0.40$** | **$0.32$** |
| $0.50$ | $1.00$ | $0.30$ | $0.30$ |
| $0.80$ | $1.00$ | $0$ | $0$ |

The bid $0.20$ gives a large profit when Maya wins. But she wins too rarely.

The bid $0.50$ guarantees success. But its extra cost reduces expected profit.

The equilibrium bid $0.40$ gives expected profit $0.32$. The earlier derivative calculation proves that no other bid gives more.

## 7. Calculate the seller’s expected revenue

### Step 1: Identify the winner’s value

Because all bidders use the same increasing function, the bidder with the highest value submits the highest bid.

Let

```math
M=\max\{v_1,\ldots,v_N\}.
```

The seller receives the winner’s bid:

```math
R=\beta(M)=\frac{N-1}{N}M.
```

Thus, we need the expected maximum value.

### Step 2: Find the distribution of the maximum

For $0\le m\le1$, the maximum is at most $m$ exactly when every value is at most $m$.

Therefore,

```math
\begin{aligned}
F_M(m)
&=\Pr(M\le m)\\
&=\Pr(v_1\le m,\ldots,v_N\le m)\\
&=m^N.
\end{aligned}
```

The last equality uses independence.

Differentiate to obtain the probability density:

```math
f_M(m)=Nm^{N-1}.
```

Hence,

```math
\begin{aligned}
\mathbb E[M]
&=\int_0^1 m f_M(m)\,dm\\
&=\int_0^1 m\cdot Nm^{N-1}\,dm\\
&=N\int_0^1 m^N\,dm\\
&=\frac{N}{N+1}.
\end{aligned}
```

### Step 3: Apply the bid function

The bid function is linear. Therefore,

```math
\begin{aligned}
\mathbb E[R]
&=\frac{N-1}{N}\mathbb E[M]\\
&=\frac{N-1}{N}\cdot\frac{N}{N+1}\\
&=\boxed{\frac{N-1}{N+1}}.
\end{aligned}
```

This is the average revenue over the random values. A particular auction can produce a different payment.

### An independent revenue check

A bidder with value $v$ wins with probability $v^{N-1}$. Their expected payment, conditional on that value, is

```math
\beta(v)v^{N-1}.
```

The seller receives the sum of all bidders’ payments. Since the bidders are symmetric,

```math
\begin{aligned}
\mathbb E[R]
&=N\int_0^1 \beta(v)v^{N-1}\,dv\\
&=N\int_0^1 \frac{N-1}{N}v^N\,dv\\
&=\frac{N-1}{N+1}.
\end{aligned}
```

The probability factor matters. Only the winner pays.

## 8. What competition changes

The difference between value and bid is called **bid shading**.

Here,

```math
\boxed{
v-\beta(v)=\frac{v}{N}.
}
```

For a fixed value, more bidders cause less bid shading.

| Number of bidders $N$ | Equilibrium bid $\beta(v)$ | Expected highest value | Expected seller revenue |
| --- | --- | --- | --- |
| $2$ | $\frac12v$ | $\frac23$ | $\frac13$ |
| $3$ | $\frac23v$ | $\frac34$ | $\frac12$ |
| $5$ | $\frac45v$ | $\frac56$ | $\frac23$ |
| $10$ | $\frac9{10}v$ | $\frac{10}{11}$ | $\frac9{11}$ |

More bidders help the seller through two effects:

- The expected highest value increases.

- Each bidder bids a larger fraction of their value.

As $N$ increases without bound,

```math
\beta(v)\longrightarrow v,
\qquad
\mathbb E[R]\longrightarrow1.
```

The gain from each additional bidder gets smaller. In fact,

```math
\mathbb E[R_{N+1}]-\mathbb E[R_N]
=
\frac{2}{(N+1)(N+2)}.
```

## 9. Where the remaining value goes

The winner keeps the difference between their value and their payment.

For a bidder with value $v$,

```math
\text{Profit if successful}=\frac{v}{N},
```

and

```math
\Pr(\text{success})=v^{N-1}.
```

Therefore, their expected profit is

```math
\boxed{
U(v)=\frac{v^N}{N}.
}
```

Before the bidder learns their value, their expected profit is

```math
\begin{aligned}
\mathbb E[U(V)]
&=\int_0^1 \frac{v^N}{N}\,dv\\
&=\frac{1}{N(N+1)}.
\end{aligned}
```

Across all $N$ bidders, total expected profit is

```math
\frac{1}{N+1}.
```

This gives a useful accounting check:

```math
\underbrace{\frac{N-1}{N+1}}_{\text{seller revenue}}
+
\underbrace{\frac{1}{N+1}}_{\text{total bidder profit}}
=
\underbrace{\frac{N}{N+1}}_{\text{winner's expected value}}.
```

The payment transfers value from the winner to the seller. Their combined gain equals the winner’s value.

## 10. A deeper interpretation of the equilibrium bid

Let $Y$ be the highest rival value:

```math
Y=\max_{j\ne i}v_j.
```

A bidder with value $v>0$ wins in equilibrium when $Y\lt v$.

Conditional on this event, all rival values lie below $v$. Each rival value is then uniform on $[0,v]$.

The expected maximum of these $N-1$ values is

```math
\mathbb E[Y\mid Y\lt v]
=
\frac{N-1}{N}v.
```

Therefore,

```math
\boxed{
\beta(v)=\mathbb E[Y\mid Y\lt v].
}
```

Your equilibrium bid equals the expected highest rival value, conditional on your value being highest. This interpretation also appears in Jonathan Levin’s Stanford auction notes. [web.stanford.edu](https://web.stanford.edu/~jdlevin/Econ%20286/Auctions.pdf?utm_source=chatgpt.com)

It also explains a connection to a second-price auction. In that auction, truthful bids make the winner pay the highest rival value. Under this problem’s assumptions, both auction formats have the same expected seller revenue. This result is an instance of **revenue equivalence**. [web.stanford.edu](https://web.stanford.edu/~jdlevin/Econ%20286/Auctions.pdf?utm_source=chatgpt.com)

Payments can differ for a particular set of values. For example, suppose two bidders have values $0.80$ and $0.60$.

- In the first-price equilibrium, their bids are $0.40$ and $0.30$. The seller receives $0.40$.

- In the truthful second-price equilibrium, the seller receives $0.60$.

Revenue equivalence concerns the average over all value draws.

**Single-bidder case:** If $N=1$, a zero bid wins under the stated rules. Revenue is zero. The equilibrium function is constant in this case.
