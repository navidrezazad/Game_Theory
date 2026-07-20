## Equilibrium

The canonical **nondegenerate, increasing linear Bayesian Nash equilibrium** is

```math
\boxed{a^*(c)=\frac23c+\frac14}
```

for the seller, and

```math
\boxed{b^*(v)=\frac23v+\frac1{12}}
```

for the buyer.

Therefore,

```math
b^*(v)\ge a^*(c)
\quad\Longleftrightarrow\quad
v-c\ge \frac14.
```

So trade occurs only when the buyer values the object at least $1/4$ more than the seller’s cost. When trade occurs, the price is

```math
\boxed{
p(c,v)=\frac{a^*(c)+b^*(v)}2
      =\frac{c+v}{3}+\frac16.
}
```

---

# The economic story

Imagine the buyer standing on one side of a foggy bridge and the seller on the other.

The buyer knows $v$, but not $c$. Raising his bid does two things:

1. It opens the bridge to more seller types.
2. It raises the price by half the bid increase in every trade that was already going to occur.

The seller faces the mirror image. Raising her ask gives her a better price in trades that still occur, but causes her to lose some buyers.

The equilibrium is where each side balances these two effects exactly.

---

# 1. The buyer’s best response

Suppose the seller uses a general increasing linear ask

```math
a(c)=\alpha c+\beta,
\qquad \alpha>0.
```

A buyer of type $v$ considers submitting a bid $x$.

He trades with sellers satisfying

```math
x\ge \alpha c+\beta.
```

Thus the highest-cost seller willing to trade is

```math
\widehat c(x)=\frac{x-\beta}{\alpha}.
```

For the moment, suppose this cutoff lies strictly between $0$ and $1$. Because $c\sim U[0,1]$, the buyer’s expected payoff is

```math
U_B(x;v)
=
\int_0^{\widehat c(x)}
\left[
v-\frac{x+\alpha c+\beta}{2}
\right]dc.
```

There are two consequences of marginally increasing $x$.

- On all existing trades, the price rises by $1/2$ of the bid increase.
- A small additional group of sellers becomes willing to trade.

Differentiating,

```math
\frac{\partial U_B}{\partial x}
=
-\frac{\widehat c(x)}2
+
\frac{v-x}{\alpha}.
```

The second term is the gain from attracting the marginal seller. At the cutoff, that seller asks exactly $x$, so the buyer’s surplus from that marginal trade is $v-x$.

Substituting

```math
\widehat c(x)=\frac{x-\beta}{\alpha},
```

we get

```math
\frac{\partial U_B}{\partial x}
=
\frac{v-x-\frac12(x-\beta)}{\alpha}
=
\frac{2v-3x+\beta}{2\alpha}.
```

The first-order condition is therefore

```math
2v-3x+\beta=0,
```

or

```math
x^*(v)=\frac23v+\frac13\beta.
```

Moreover,

```math
\frac{\partial^2 U_B}{\partial x^2}
=
-\frac{3}{2\alpha}<0,
```

so this is indeed the unique optimum whenever the buyer trades with a nontrivial interval of seller types.

Consequently, if the buyer’s equilibrium bid has the form

```math
b(v)=\gamma v+\delta,
```

then the buyer’s best-response conditions imply

```math
\boxed{\gamma=\frac23},
\qquad
\boxed{\delta=\frac{\beta}{3}}.
```

---

# 2. The seller’s best response

Now suppose the buyer uses a general increasing linear bid

```math
b(v)=\gamma v+\delta,
\qquad \gamma>0.
```

A seller with cost $c$ considers submitting ask $y$.

Trade occurs when

```math
\gamma v+\delta\ge y.
```

Thus the lowest-value buyer who trades is

```math
\widehat v(y)=\frac{y-\delta}{\gamma}.
```

The seller’s expected payoff is

```math
U_S(y;c)
=
\int_{\widehat v(y)}^1
\left[
\frac{y+\gamma v+\delta}{2}-c
\right]dv.
```

Increasing the ask has two effects:

- It raises the price by half the ask increase in every continuing trade.
- It loses the marginal buyers whose bids are just below the new ask.

Differentiating gives

```math
\frac{\partial U_S}{\partial y}
=
\frac{1-\widehat v(y)}2
-
\frac{y-c}{\gamma}.
```

At the cutoff buyer, $b(\widehat v)=y$, so the seller’s profit on that marginal trade is $y-c$.

Substituting the cutoff,

```math
\frac{\partial U_S}{\partial y}
=
\frac{\gamma+\delta-y}{2\gamma}
-
\frac{y-c}{\gamma}
=
\frac{\gamma+\delta+2c-3y}{2\gamma}.
```

The first-order condition is

```math
\gamma+\delta+2c-3y=0,
```

so

```math
y^*(c)
=
\frac23c+\frac{\gamma+\delta}{3}.
```

Again,

```math
\frac{\partial^2 U_S}{\partial y^2}
=
-\frac{3}{2\gamma}<0,
```

so this is a maximum.

Therefore the seller’s strategy coefficients satisfy

```math
\boxed{\alpha=\frac23},
\qquad
\boxed{\beta=\frac{\gamma+\delta}{3}}.
```

---

# 3. Solve the fixed-point equations

The buyer’s best response gave

```math
\gamma=\frac23,
\qquad
\delta=\frac{\beta}{3}.
```

The seller’s best response gave

```math
\alpha=\frac23,
\qquad
\beta=\frac{\gamma+\delta}{3}.
```

Substitute $\gamma=2/3$ and $\delta=\beta/3$:

```math
\beta
=
\frac{\frac23+\frac{\beta}{3}}{3}.
```

Hence

```math
3\beta=\frac23+\frac{\beta}{3},
```

and multiplying by $3$,

```math
9\beta=2+\beta.
```

Therefore

```math
8\beta=2,
\qquad
\boxed{\beta=\frac14}.
```

Then

```math
\boxed{\delta=\frac{\beta}{3}=\frac1{12}}.
```

Thus

```math
\boxed{
a^*(c)=\frac23c+\frac14,
\qquad
b^*(v)=\frac23v+\frac1{12}.
}
```

---

# 4. Boundary types and global verification

The calculus above describes types that potentially trade. We must also verify the types that optimally stay out.

## Low-value buyers

The lowest seller ask is

```math
a^*(0)=\frac14.
```

For $v\le 1/4$,

```math
b^*(v)=\frac23v+\frac1{12}\le\frac14.
```

Thus these buyers do not trade, except possibly with a probability-zero boundary seller.

This is optimal. For a buyer with $v<1/4$, the unconstrained optimal trading bid lies below the minimum ask. Any bid below $1/4$ gives zero payoff, while forcing trade by bidding above $1/4$ gives a nonpositive expected payoff.

## High-cost sellers

The highest buyer bid is

```math
b^*(1)=\frac34.
```

For $c\ge 3/4$,

```math
a^*(c)=\frac23c+\frac14\ge\frac34.
```

Thus these sellers do not trade, except possibly with a probability-zero boundary buyer.

This is also optimal. For $c>3/4$, the seller’s unconstrained optimal trading ask lies above the maximum bid. Any ask above $3/4$ gives zero payoff, while lowering the ask enough to force trade gives a nonpositive expected payoff.

The complete best-response behavior is therefore

```math
BR_B(v)=
\begin{cases}
\text{any bid no greater than }1/4, & v\le1/4,\\[4pt]
\frac23v+\frac1{12}, & v>1/4,
\end{cases}
```

and

```math
BR_S(c)=
\begin{cases}
\frac23c+\frac14, & c<3/4,\\[4pt]
\text{any ask no less than }3/4, & c\ge3/4.
\end{cases}
```

The displayed linear strategies select particular optimal actions for the nontrading types.

---

# 5. What the equilibrium means

Both sides strategically shade their offers.

For an active buyer,

```math
v-b^*(v)
=
v-\left(\frac23v+\frac1{12}\right)
=
\frac{v-\frac14}{3}.
```

So the buyer bids below his value.

For an active seller,

```math
a^*(c)-c
=
\frac23c+\frac14-c
=
\frac{\frac34-c}{3}.
```

So the seller asks above her cost.

These two forms of strategic shading create the no-trade wedge:

```math
b^*(v)\ge a^*(c)
\iff
\frac23v+\frac1{12}
\ge
\frac23c+\frac14
\iff
v-c\ge\frac14.
```

Efficient trade would occur whenever $v\ge c$. But in equilibrium, trades with

```math
0<v-c<\frac14
```

do not occur. Each side waits for a sufficiently favorable deal, and some mutually beneficial trades are lost.

The probability of trade is

```math
\Pr\left(v-c\ge\frac14\right)
=
\int_0^{3/4}\left(\frac34-c\right)dc
=
\boxed{\frac9{32}}.
```

The interim equilibrium payoffs are

```math
u_B(v)
=
\begin{cases}
0, & v\le1/4,\\[3pt]
\frac12\left(v-\frac14\right)^2, & v>1/4,
\end{cases}
```

and

```math
u_S(c)
=
\begin{cases}
\frac12\left(\frac34-c\right)^2, & c<3/4,\\[3pt]
0, & c\ge3/4.
\end{cases}
```

Ex ante, each side receives

```math
\mathbb E[u_B]=\mathbb E[u_S]=\frac9{128}.
```

---

## Final summary

| Quantity | Equilibrium expression |
| --- | ---: |
| Seller’s ask | $\displaystyle a^*(c)=\frac23c+\frac14$ |
| Buyer’s bid | $\displaystyle b^*(v)=\frac23v+\frac1{12}$ |
| Trade condition | $\displaystyle v-c\ge\frac14$ |
| Transaction price | $\displaystyle p(c,v)=\frac{c+v}{3}+\frac16$ |
| Probability of trade | $\displaystyle \frac9{32}$ |

This is the standard positive-trade linear equilibrium. Technically, because nontrading types are indifferent among many losing bids or asks, their off-trade actions are not unique. If constant functions are also counted as “linear,” weak no-trade equilibria such as $b(v)\equiv0$ and $a(c)\equiv1$ also exist; the solution above is the economically relevant increasing equilibrium with positive probability of trade.
