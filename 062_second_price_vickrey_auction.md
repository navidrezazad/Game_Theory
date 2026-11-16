# 62. Second-price / Vickrey auction

## Problem statement

There are $N$ bidders with independent private values. Each submits one sealed bid; the highest bidder wins and pays the second-highest bid. Prove or disprove that truthful bidding is weakly dominant, and calculate expected revenue for $v_i\sim U[0,1]$.

## Solution

**Truthful bidding is weakly dominant.** Each bidder can maximize their utility by bidding their true value, for every possible set of other bids. This is the standard Vickrey auction result. [timroughgarden.org](https://timroughgarden.org/f13/l/l2.pdf?utm_source=chatgpt.com)

When all bidders use this strategy and their values are independent uniform draws,

```math
\boxed{\mathbb E[\text{seller revenue}]=\frac{N-1}{N+1}}.
```

Assume $N\ge 2$, so a second-highest bid exists. Also assume that the auction has no reserve price.

The main idea is simple:

> **Fix the other bids. Your bid controls whether you win. The highest other bid sets your payment if you win.**

We will use this idea to prove the bidding result. Then we will calculate revenue.

## 1. A story: the camera auction

A university sells one used camera. Each bidder puts one bid in a sealed envelope.

Maya values the camera at **\$80**. This value measures the benefit that she gets from owning it.

If Maya buys the camera for \$60, her net gain is

```math
80-60=20.
```

If she buys it for \$90, her net gain is

```math
80-90=-10.
```

We call this net gain **utility**. Maya wants to maximize her utility.

The auctioneer announces two rules:

1. The highest bidder gets the camera.

2. The winner pays the second-highest bid.

Maya considers bids of \$50, \$80, and \$100. Compare these bids under two possible sets of other bids.

| Highest other bid | Maya’s bid | Result for Maya | Maya’s payment | Maya’s utility |
| --- | --- | --- | --- | --- |
| \$60 | \$50 | Loses | \$0 | \$0 |
| \$60 | \$80 | Wins | \$60 | \$20 |
| \$60 | \$100 | Wins | \$60 | \$20 |
| \$90 | \$50 | Loses | \$0 | \$0 |
| \$90 | \$80 | Loses | \$0 | \$0 |
| \$90 | \$100 | Wins | \$90 | $-\\$10$ |

The table shows two possible costs of changing the truthful bid.

**A lower bid can prevent a useful purchase.** When the highest other bid is \$60, a \$50 bid makes Maya lose a \$20 gain.

**A higher bid can cause a harmful purchase.** When the highest other bid is \$90, a \$100 bid makes Maya lose \$10.

Bidding \$80 makes the correct purchase decision in both cases. Maya wins when the required price is below her value. She loses when the required price is above her value.

Notice another feature. When the highest other bid is \$60, bids of \$80 and \$100 give the same payment.

A higher winning bid gives Maya no price advantage.

## 2. State the model and the claim

Let bidder $i$ have true value $v_i$. Let their submitted bid be $b_i$.

We use the standard utility model:

```math
u_i=
\begin{cases}
v_i-p_i, & \text{if bidder }i\text{ wins and pays }p_i,\\[4pt]
0, & \text{if bidder }i\text{ loses}.
\end{cases}
```

This model is called **quasilinear utility**. It measures the value of the object and the payment in the same money units. A losing bidder pays zero. [timroughgarden.org](https://timroughgarden.org/f13/l/l2.pdf?utm_source=chatgpt.com)

Each bidder knows their own value. Each bidder can submit that value as their bid.

Let

```math
\mathbf b_{-i}
```

denote all bids except bidder $i$’s bid.

For a fixed true value $v_i$, truthful bidding is weakly dominant if

```math
\boxed{
u_i(v_i,\mathbf b_{-i})
\ge
u_i(b_i,\mathbf b_{-i})
\quad
\text{for every }b_i\text{ and every }\mathbf b_{-i}.
}
```

The first input of $u_i$ is the submitted bid. The true value $v_i$ stays fixed throughout this comparison.

In plain language:

> For each possible set of other bids, truthful bidding gives at least as much utility as every alternative bid.

This requirement is strong. It includes other bidders who bid above their values. It also includes other bidders who bid below their values.

We must prove the claim for all these cases.

## 3. Prove weak dominance

### Step 1: Fix the other bids

Choose any bidder $i$. Fix their true value $v_i$.

Now fix any set of other bids. Define

```math
m=\max_{j\ne i}b_j.
```

Thus, $m$ is the highest other bid.

From bidder $i$’s position, $m$ is the price required to win, subject to the rule for equal bids.

There are three possible outcomes:

- If $b_i\lt m$, bidder $i$ loses.

- If $b_i>m$, bidder $i$ wins and pays $m$.

- If $b_i=m$, the auction’s tie rule selects a winner.

If bidder $i$ wins a tie, the payment is still $m$. At least one other bidder also submitted $m$.

Let $q_i\in[0,1]$ be bidder $i$’s probability of winning that tie. A fixed priority rule gives $q_i=0$ or $q_i=1$.

The utility function is therefore

```math
u_i(b_i,\mathbf b_{-i})
=
\begin{cases}
0, & b_i\lt m,\\[4pt]
q_i(v_i-m), & b_i=m,\\[4pt]
v_i-m, & b_i>m.
\end{cases}
```

At a random tie, this expression gives expected utility over the tie rule.

We now compare the true value $v_i$ with the required price $m$.

### Case A: The value is above the price

Suppose

```math
v_i>m.
```

Truthful bidding sets $b_i=v_i>m$. Bidder $i$ wins and gets

```math
u_i(v_i,\mathbf b_{-i})=v_i-m>0.
```

An alternative bid has three possible effects.

- A winning bid gives the same utility, $v_i-m$.

- A losing bid gives utility $0$.

- A tied bid gives expected utility $q_i(v_i-m)\le v_i-m$.

Thus, no alternative bid gives more utility.

The economic reason is direct. The purchase creates a positive gain. Truthful bidding secures that purchase.

### Case B: The value is below the price

Suppose

```math
v_i\lt m.
```

Truthful bidding sets $b_i=v_i\lt m$. Bidder $i$ loses and gets

```math
u_i(v_i,\mathbf b_{-i})=0.
```

An alternative losing bid also gives zero.

An alternative winning bid gives

```math
v_i-m\lt 0.
```

A tied bid gives

```math
q_i(v_i-m)\le 0.
```

Thus, no alternative bid gives more utility.

Here, winning would require an excessive payment. Truthful bidding avoids that payment.

### Case C: The value equals the price

Suppose

```math
v_i=m.
```

Winning gives utility

```math
v_i-m=0.
```

Losing also gives utility zero.

Therefore, truthful bidding is optimal under every tie rule.

### Complete the proof

The three cases show that truthful bidding gives

```math
u_i(v_i,\mathbf b_{-i})
=
\max\{v_i-m,0\}.
```

Every alternative bid gives at most this amount. Hence,

```math
\boxed{
u_i(b_i,\mathbf b_{-i})
\le
\max\{v_i-m,0\}
=
u_i(v_i,\mathbf b_{-i}).
}
```

We chose the bidder, their value, and the other bids arbitrarily. The inequality therefore proves weak dominance. $\square$

### What the proof does not need

The proof makes no probability calculation. It applies to each fixed set of other bids.

Thus, **independence is unnecessary for the dominance result**. A bidder also needs no estimate of the other bidders’ values.

We will use independence in the revenue calculation.

## 4. Why the word “weakly” matters

Weak dominance permits equal utility.

Return to Maya. Her value is \$80, and the highest other bid is \$60.

A bid of \$70 and a bid of \$80 both win. Both require a \$60 payment. Both give utility \$20.

Thus, truthful bidding does not give strictly greater utility in every comparison.

However, each different bid creates some cases in which the bidder does worse.

To see this precisely, take an alternative bid $b_i\ne v_i$. Choose the highest other bid as

```math
m=\frac{b_i+v_i}{2}.
```

If $b_i\lt v_i$, then

```math
b_i\lt m\lt v_i.
```

The alternative bid loses. The truthful bid wins and gives positive utility.

If $b_i>v_i$, then

```math
v_i\lt m\lt b_i.
```

The truthful bid loses and gives zero utility. The alternative bid wins and gives negative utility.

So a different bid can match truthful bidding in some situations. It cannot improve on truthful bidding, and it performs worse in some situations.

This explains the precise strength of the result.

It also explains why everyone bidding truthfully forms an equilibrium. No bidder can gain by changing their bid alone.

## 5. Identify the seller’s revenue

We now calculate revenue **when all bidders use their truthful strategies**.

Write the random values as

```math
V_1,\ldots,V_N
\overset{\text{iid}}{\sim}U[0,1].
```

Here, “iid” means independent and identically distributed.

Sort the values from smallest to largest:

```math
V_{(1)}\le V_{(2)}\le\cdots\le V_{(N-1)}\le V_{(N)}.
```

These sorted values are called **order statistics**.

Under truthful bidding:

- The highest value, $V_{(N)}$, is the winning bid.

- The second-highest value, $V_{(N-1)}$, is the payment.

Therefore, seller revenue is

```math
\boxed{R=V_{(N-1)}}.
```

This connection between revenue and the second-highest value is the standard order-statistic description of the Vickrey auction. [pi.math.cornell.edu](https://pi.math.cornell.edu/~mec/Winter2009/Spulido/Auctions/revenue.html?utm_source=chatgpt.com)

For example, suppose five values are

```math
0.15,\quad 0.32,\quad 0.46,\quad 0.71,\quad 0.93.
```

The bidder with value $0.93$ wins. The seller receives $0.71$.

Each auction has its own realized price. Expected revenue averages that price across all possible value draws.

## 6. Derive the expected revenue

We will derive the answer directly. The main step is to find the distribution of $R$.

### Step 1: Express a price event as a count

Choose a number $x\in[0,1]$.

The event

```math
R\le x
```

means that the second-highest value is at most $x$.

This happens exactly when **at most one value exceeds $x$**.

There are two possible cases:

1. All $N$ values are at most $x$.

2. Exactly one value exceeds $x$.

These cases cannot occur together.

### Step 2: Calculate each probability

For a uniform value on $[0,1]$,

```math
\Pr(V_i\le x)=x,
\qquad
\Pr(V_i>x)=1-x.
```

Because the values are independent,

```math
\Pr(\text{all }N\text{ values are at most }x)=x^N.
```

Now consider exactly one value above $x$.

There are $N$ choices for that bidder. The selected bidder exceeds $x$ with probability $1-x$. Each remaining bidder has value at most $x$ with probability $x$.

Therefore,

```math
\Pr(\text{exactly one value exceeds }x)
=
N(1-x)x^{N-1}.
```

Adding the two probabilities gives the **cumulative distribution function** of revenue:

```math
\begin{aligned}
F_R(x)
&=\Pr(R\le x)\\
&=x^N+N(1-x)x^{N-1}\\
&=Nx^{N-1}-(N-1)x^N,
\qquad 0\le x\le1.
\end{aligned}
```

This function answers a concrete question: how often does the seller receive at most $x$?

### Step 3: Find the density

Differentiate the cumulative distribution function:

```math
\begin{aligned}
f_R(x)
&=\frac{d}{dx}F_R(x)\\
&=N(N-1)x^{N-2}-N(N-1)x^{N-1}\\
&=N(N-1)x^{N-2}(1-x),
\qquad 0\lt x\lt 1.
\end{aligned}
```

Thus,

```math
\boxed{
f_R(x)=N(N-1)x^{N-2}(1-x).
}
```

The density gives the probability per unit of price near $x$.

Its factors also have a useful interpretation:

- $N(N-1)$ counts choices for the winner and the bidder with the second-highest value.

- $x^{N-2}$ places the remaining values below $x$.

- $1-x$ places the highest value above $x$.

### Step 4: Average the price

Weight each possible price by its density:

```math
\mathbb E[R]
=
\int_0^1 x f_R(x)\,dx.
```

Substitute the density:

```math
\begin{aligned}
\mathbb E[R]
&=N(N-1)\int_0^1x^{N-1}(1-x)\,dx\\[4pt]
&=N(N-1)
\left(
\int_0^1x^{N-1}\,dx
-
\int_0^1x^N\,dx
\right)\\[4pt]
&=N(N-1)
\left(
\frac1N-\frac1{N+1}
\right)\\[4pt]
&=N(N-1)\frac{1}{N(N+1)}\\[4pt]
&=\boxed{\frac{N-1}{N+1}}.
\end{aligned}
```

This completes the revenue calculation.

## 7. Understand the denominator $N+1$

The formula has a useful geometric explanation.

Imagine the $N$ values as random points on the interval $[0,1]$. Include both endpoints:

```math
0,\quad V_{(1)},\quad V_{(2)},\quad\ldots,\quad V_{(N)},\quad1.
```

These points create $N+1$ gaps.

For independent uniform draws, the gaps have a symmetric joint distribution. Thus, each gap has the same expected length.

Their total length is $1$. Therefore,

```math
\mathbb E[\text{each gap}]=\frac{1}{N+1}.
```

Individual draws can have very unequal gaps. The equality concerns their expected lengths.

The second-highest value has two gaps above it:

1. The gap between the second-highest and highest values.

2. The gap between the highest value and $1$.

Therefore,

```math
\mathbb E[V_{(N-1)}]
=
1-\frac{2}{N+1}
=
\frac{N-1}{N+1}.
```

For a rigorous basis for the symmetry, the sorted uniform points have constant joint density $N!$. Changing from points to gaps preserves this constant density. Permuting the gaps preserves the allowed set.

More generally, the uniform order-statistic formula is

```math
\boxed{
\mathbb E[V_{(k)}]=\frac{k}{N+1}.
}
```

Setting $k=N-1$ gives the revenue result directly. [www2.stat.duke.edu](https://www2.stat.duke.edu/courses/Spring12/sta104.1/Lectures/Lec15.pdf?utm_source=chatgpt.com)

## 8. Check the answer through one bidder’s payment

A second calculation helps clarify when a bidder actually pays.

Fix bidder $i$’s value at $v$. Assume all other bidders bid truthfully.

Let

```math
M_i=\max_{j\ne i}V_j
```

be the highest rival value.

There are $N-1$ rivals. Independence gives

```math
\Pr(M_i\le m)=m^{N-1},
\qquad 0\le m\le1.
```

Hence,

```math
f_{M_i}(m)=(N-1)m^{N-2}.
```

Bidder $i$ wins when $M_i\lt v$. In that case, the payment is $M_i$. Otherwise, the payment is zero.

Ties have probability zero here because the values have continuous distributions.

Let $P_i$ denote bidder $i$’s payment. Its conditional expectation is

```math
\begin{aligned}
\mathbb E[P_i\mid V_i=v]
&=\int_0^v m f_{M_i}(m)\,dm\\[4pt]
&=(N-1)\int_0^v m^{N-1}\,dm\\[4pt]
&=\frac{N-1}{N}v^N.
\end{aligned}
```

The upper integration limit is $v$. It ensures that we count payments only when bidder $i$ wins.

Now average over bidder $i$’s own uniform value:

```math
\begin{aligned}
\mathbb E[P_i]
&=\int_0^1\frac{N-1}{N}v^N\,dv\\[4pt]
&=\frac{N-1}{N(N+1)}.
\end{aligned}
```

Seller revenue equals the sum of all bidder payments:

```math
R=\sum_{i=1}^N P_i.
```

By linearity of expectation,

```math
\begin{aligned}
\mathbb E[R]
&=\sum_{i=1}^N\mathbb E[P_i]\\
&=N\frac{N-1}{N(N+1)}\\
&=\frac{N-1}{N+1}.
\end{aligned}
```

Both calculations give the same result.

## 9. Check small cases and interpret the result

### Two bidders

With $N=2$, the second-highest value is the smaller value.

Thus,

```math
R=\min\{V_1,V_2\}.
```

The formula gives

```math
\mathbb E[R]=\frac13.
```

We can check this without order-statistic notation. Revenue exceeds $x$ exactly when both values exceed $x$:

```math
\Pr(R>x)=(1-x)^2.
```

Therefore,

```math
\mathbb E[R]
=
\int_0^1\Pr(R>x)\,dx
=
\int_0^1(1-x)^2\,dx
=
\frac13.
```

### Three bidders

With $N=3$, revenue equals the middle value.

The uniform distribution is symmetric around $1/2$. The middle value therefore has expectation $1/2$.

Our formula agrees:

```math
\frac{3-1}{3+1}=\frac12.
```

### More bidders

| Number of bidders $N$ | Expected revenue | Approximate value |
| --- | --- | --- |
| 2 | $1/3$ | $0.333$ |
| 3 | $1/2$ | $0.500$ |
| 5 | $2/3$ | $0.667$ |
| 10 | $9/11$ | $0.818$ |
| 100 | $99/101$ | $0.980$ |

Expected revenue increases with the number of bidders.

More precisely,

```math
\begin{aligned}
\mathbb E[R_{N+1}]-\mathbb E[R_N]
&=\frac{N}{N+2}-\frac{N-1}{N+1}\\
&=\frac{2}{(N+1)(N+2)}>0.
\end{aligned}
```

Each additional bidder gives a smaller expected increase.

Also,

```math
\lim_{N\to\infty}\mathbb E[R_N]=1.
```

With many independent draws, the auction is likely to have at least two values near the upper limit.

### The economic lesson

A high winning value alone can produce low revenue.

For example, consider values

```math
0.99,\quad 0.10,\quad 0.05.
```

The highest-value bidder wins, but the seller receives only $0.10$.

The second-highest value measures the competition that sets the price.

Under truthful bidding, the winner’s utility is

```math
V_{(N)}-V_{(N-1)}.
```

Using the uniform order-statistic means,

```math
\begin{aligned}
\mathbb E[\text{winner's utility}]
&=\frac{N}{N+1}-\frac{N-1}{N+1}\\
&=\frac{1}{N+1}.
\end{aligned}
```

The expected winning value therefore splits into two parts:

```math
\underbrace{\frac{N}{N+1}}_{\text{expected winning value}}
=
\underbrace{\frac{N-1}{N+1}}_{\text{expected seller revenue}}
+
\underbrace{\frac{1}{N+1}}_{\text{expected winner's utility}}.
```

The highest value determines who receives the object. The second-highest value determines how much of that value the seller receives.
