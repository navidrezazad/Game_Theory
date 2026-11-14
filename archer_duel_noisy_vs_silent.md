**The noisy duel has a fixed firing point. The silent duel requires random firing points.**

With your stated tie rules, the results are:

| Version | Equilibrium strategy | Archer 1 wins | Archer 2 wins | Draw |
| --- | --- | --- | --- | --- |
| Noisy, with sequential priority | Both plan to fire at $x\approx0.618034$ | $38.1966\%$ | $61.8034\%$ | $0\%$ |
| Silent | Both use random firing points below $x\approx0.677689$ | $32.2311\%$ | $54.0738\%$ | $13.6951\%$ |

The silent strategy has one essential detail. **Archer 2 chooses $x=0$ with probability $6.9045\%$.** Archer 1 has no such probability.

I use short sentences, active voice, and consistent terms, as the STE guidance recommends. I define the mathematical terms below. [asd-ste100.org](https://www.asd-ste100.org/STE_faq.html?utm_source=chatgpt.com)

## 1. The story: a miss can reveal valuable information

Imagine a line with marks from $1$ to $0$. The archers move toward the zero mark.

At $x=1$, neither archer can hit. At $x=0$, each archer hits with certainty. Between these points, Archer 2 has better aim:

```math
p_2(x)-p_1(x)
=(1-x^2)-(1-x)
=x(1-x)>0.
```

Each archer must balance two effects.

- A later shot has a higher hit probability.

- An earlier shot can eliminate the opponent before the opponent fires.

Remember the direction:

```math
\boxed{\text{Larger }x\text{ means earlier fire.}}
```

Now imagine two settings.

In the noisy setting, a missed arrow strikes a bell. The other archer hears the bell and knows that the opponent has no arrow.

In the silent setting, a missed arrow lands in sand. The other archer gets no signal. The opponent might still have an arrow.

That difference changes the game.

An **equilibrium** is a pair of strategies with this property: neither archer can increase their win probability by changing their own strategy alone.

Define the miss probabilities:

```math
q_1(x)=1-p_1(x)=x,
\qquad
q_2(x)=1-p_2(x)=x^2.
```

We will use these throughout.

## 2. The noisy duel

### After a heard miss, wait until $x=0$

Suppose Archer 1 fires and misses.

Archer 2 now knows that Archer 1 has no arrow. Archer 2 has no reason to risk an inaccurate shot. Archer 2 waits until $x=0$, then hits with certainty.

The same reasoning applies if Archer 2 fires first and misses.

Thus, at state $x$, Archer $i$ compares two possible roles:

| Role | Probability that Archer $i$ wins |
| --- | --- |
| Fire first | $p_i(x)$ |
| Let Archer $j$ fire first, then act after a miss | $q_j(x)=1-p_j(x)$ |

This comparison gives the critical state.

### Find the state where the two roles have equal value

The roles have equal value when

```math
p_i(x)=1-p_j(x).
```

For either archer, this is the same condition:

```math
p_1(x)+p_2(x)=1.
```

Substitute the given probabilities:

```math
(1-x)+(1-x^2)=1.
```

Therefore,

```math
x^2+x-1=0.
```

The root in $[0,1]$ is

```math
\boxed{
c=\frac{\sqrt5-1}{2}
\approx0.618033989.
}
```

It satisfies

```math
c^2=1-c.
```

At this state,

```math
p_1(c)=1-c=c^2,
\qquad
p_2(c)=1-c^2=c.
```

The comparison also explains the threshold.

For $x>c$,

```math
p_1(x)+p_2(x)\lt 1.
```

Each archer prefers the second role at that state. A first shot is still too inaccurate.

For $x\lt c$,

```math
p_1(x)+p_2(x)>1.
```

Each archer prefers the first role at that state. A first shot is now sufficiently accurate.

The state $c$ separates these two regions.

### The equilibrium strategy

Each archer uses this plan:

1. While both archers have arrows, wait until $x=c$.

2. At $x=c$, choose to fire.

3. If the opponent fires first and misses, keep the arrow until $x=0$.

4. At $x=0$, fire.

Your sequential priority rule resolves the planned tie.

A fair coin selects the first shot. If that shot misses, the other archer can keep their arrow until $x=0$.

### Why the tie gives the correct payoff

Under fair sequential priority, Archer $i$'s tie payoff at $x$ is

```math
T_i(x)
=
\frac12p_i(x)
+
\frac12q_j(x).
```

The first term covers first priority. The second term covers second priority.

At $x=c$, these two probabilities are equal:

```math
p_i(c)=q_j(c).
```

Therefore,

```math
T_i(c)=p_i(c).
```

The equilibrium win probabilities are

```math
\boxed{
v_1=c^2\approx0.381966011,
\qquad
v_2=c\approx0.618033989.
}
```

Their sum is $1$. No draw occurs.

A first hit ends the duel. A first miss lets the other archer make a certain hit at $x=0$.

### Check every unilateral change

Fix an opponent who follows the equilibrium plan.

**Fire earlier, at $x>c$.**

You fire first, but your accuracy is lower:

```math
p_i(x)\lt p_i(c)=v_i.
```

This change reduces your payoff.

**Keep the arrow past $c$.**

The opponent fires at $c$. You win exactly when that shot misses:

```math
q_j(c)=v_i.
```

This change gives the same payoff.

**Choose the tie at $c$.**

The sequential rule gives

```math
T_i(c)=v_i.
```

Thus, no pure change can improve the payoff. A random change cannot improve it either. Its payoff is an average of pure-choice payoffs.

There is a useful subtlety here. A later plan is a best response to an opponent fixed at $c$. It need not form another equilibrium pair. If one archer commits to a strictly later point, the other can delay their first shot and improve accuracy.

For a complete strategy, also specify what happens after an unexpected history. If both archers still have arrows at $x\lt c$, both choose to fire immediately. After a heard miss, the armed archer waits until $0$. These instructions give a **subgame-perfect equilibrium**: the plans remain optimal after every observed state.

## 3. The silent duel: why fixed firing points fail

Return to the version where a miss makes no sound.

Suppose the archers announce two different firing points.

The later archer can improve accuracy by moving their shot to $x=0$. Once that point is fixed, the earlier archer can delay while still firing first.

Thus, two different fixed firing points cannot be stable.

A fixed tie also fails.

At an interior state $x$, Archer $i$'s tie payoff is

```math
p_i(x)q_j(x).
```

A shot just before that state gives a payoff close to $p_i(x)$. This is strictly larger.

The endpoints fail too. A tie at $1$ gives two misses. A tie at $0$ gives two hits. In each case, an archer has a profitable change.

Therefore, the silent duel has **no pure equilibrium**.

The archers must use private random choices. Each draws a firing point, then keeps that plan if still alive.

### The correct payoff for two chosen points

Let Archer $i$ choose $x$. Let Archer $j$ choose $y$.

Then

```math
\boxed{
u_i(x,y)=
\begin{cases}
p_i(x), & x>y,\\[2mm]
p_i(x)q_j(y), & x\lt y,\\[2mm]
p_i(x)q_j(x), & x=y.
\end{cases}
}
```

Read each case carefully.

If $x>y$, Archer $i$ fires first. A hit makes Archer $i$ the sole winner.

If $x\lt y$, Archer $i$ must first survive the opponent's shot. Survival has probability $q_j(y)$. Archer $i$ must then hit.

At a tie, Archer $i$ must hit while the opponent misses. Independence gives the product $p_i(x)q_j(x)$.

The draw rule matters here. The silent game can produce two misses. Consequently,

```math
U_1+U_2=1-\Pr(\text{draw}),
```

which need not equal $1$.

Each archer maximizes their own win probability. We must use that objective throughout the calculation.

## 4. Derive the silent random strategies

### Describe a random firing point

Let $X_i$ denote Archer $i$'s chosen firing point.

Define its cumulative distribution function:

```math
F_i(x)=\Pr(X_i\le x).
```

Because the state decreases, $X_i\le x$ means that the planned shot occurs at $x$ or later.

Where the distribution has a density $f_i$,

```math
\Pr(x\lt X_i\lt x+h)\approx f_i(x)h
```

for small positive $h$.

A **point mass** assigns positive probability to one exact state. We must allow a possible point mass at $x=0$.

### Write the payoff against a random opponent

Suppose Archer $i$ chooses the fixed point $x$.

The opponent can eliminate Archer $i$ by hitting at a state $y\ge x$. The equality case includes a simultaneous shot.

Thus,

```math
\boxed{
U_i(x)
=
p_i(x)
\left[
1-\int_{[x,1]}p_j(y)\,dF_j(y)
\right].
}
```

The bracket is the probability that the opponent does not prevent Archer $i$'s sole win.

The closed lower endpoint, $[x,1]$, is essential. It includes the opponent's shot at an exact tie.

### Randomization requires equal payoffs on the chosen interval

Suppose an archer uses several firing points with positive probability.

All those points must give the same maximum payoff. Otherwise, the archer could move probability from a worse point to a better point.

This condition is called **indifference**.

We construct distributions on a common interval

```math
0\lt x\lt b.
```

We will check every possible deviation afterward.

Let $V_i$ be Archer $i$'s equilibrium win probability. On the continuous interval,

```math
V_i
=
p_i(x)
\left[
1-\int_x^b p_j(y)f_j(y)\,dy
\right].
```

At the earliest boundary $b$, the opponent has not fired earlier. There is no point mass at $b$. Therefore,

```math
\boxed{
V_1=p_1(b)=1-b,
\qquad
V_2=p_2(b)=1-b^2.
}
```

### Differentiate the indifference condition

Write

```math
A_j(x)=1-\int_x^b p_j(y)f_j(y)\,dy.
```

Then

```math
V_i=p_i(x)A_j(x),
\qquad
A_j'(x)=p_j(x)f_j(x).
```

Differentiate:

```math
0
=
p_i'(x)A_j(x)
+
p_i(x)p_j(x)f_j(x).
```

Since $A_j(x)=V_i/p_i(x)$,

```math
\boxed{
f_j(x)
=
-\frac{V_i p_i'(x)}
{p_i(x)^2p_j(x)}.
}
```

Notice the indices. Archer 2's distribution makes Archer 1 indifferent. Archer 1's distribution makes Archer 2 indifferent.

Substitute

```math
p_1'(x)=-1,
\qquad
p_2'(x)=-2x.
```

This gives

```math
\boxed{
f_1(x)
=
\frac{2(1-b^2)x}
{(1-x)^3(1+x)^2},
\qquad 0\lt x\lt b,
}
```

and

```math
\boxed{
f_2(x)
=
\frac{1-b}
{(1-x)^3(1+x)},
\qquad 0\lt x\lt b.
}
```

These are densities of the chosen firing points. They are not uniform distributions.

### Find $b$ and the point mass

Both archers cannot assign positive probability to $x=0$.

If the opponent assigns positive probability there, firing just before $0$ avoids a certain double hit on that event. An exact shot at $0$ is then worse.

Thus, at least one archer must have no point mass at $0$.

The valid solution makes Archer 1's continuous density integrate to $1$:

```math
\boxed{
(1-b^2)
\int_0^b
\frac{2x}{(1-x)^3(1+x)^2}\,dx
=1.
}
```

This equation gives

```math
\boxed{
b\approx0.6776886559442166.
}
```

For an explicit equation, define

```math
G_1(b)=
\frac{1}{4(1-b)^2}
+
\frac{1}{4(1+b)}
-\frac12
+
\frac18\log\frac{1-b}{1+b}.
```

Then $b$ is the unique root in $(0,1)$ of

```math
(1-b^2)G_1(b)=1.
```

At this value of $b$, Archer 2's density has total probability

```math
\int_0^b f_2(x)\,dx
\approx0.9309546528946457.
```

The remaining probability goes at $x=0$:

```math
\boxed{
m
=
1-\int_0^b f_2(x)\,dx
\approx0.0690453471053543.
}
```

Using the equation for $b$, this also has the exact expression

```math
\boxed{
m=2-b-\frac{b}{1-b^2}.
}
```

Could the point mass belong to Archer 1 instead?

That choice would require Archer 2's continuous density to integrate to $1$. It gives $b\approx0.700504$. At that boundary, Archer 1's continuous probability would be approximately $1.129145$.

A probability distribution cannot have total probability above $1$. Thus, the valid point mass belongs to **Archer 2**.

## 5. The complete silent equilibrium

### Archer 1

Draw a private firing point $X_1$ with density

```math
\boxed{
f_1(x)=
\frac{2(1-b^2)x}
{(1-x)^3(1+x)^2},
\qquad 0\lt x\lt b.
}
```

Fire at that point if still alive.

There is no point mass at $0$ or $b$.

### Archer 2

Use this private random plan:

- With probability $m\approx0.06904535$, choose $X_2=0$.

- With probability $1-m$, draw $X_2$ from the conditional density $f_2(x)/(1-m)$ on $(0,b)$.

Here,

```math
\boxed{
f_2(x)=
\frac{1-b}
{(1-x)^3(1+x)}.
}
```

Fire at the chosen point if still alive.

Both archers wait while $x>b$. Neither changes their plan after an unobserved miss.

### Check all possible firing points

The densities make every point in $0\lt x\le b$ equally good:

```math
U_i(x)=V_i.
```

A shot at $x>b$ occurs before the opponent's shot. Its accuracy is lower than the accuracy at $b$. Therefore,

```math
U_i(x)=p_i(x)\lt p_i(b)=V_i.
```

The exact endpoint $x=0$ needs a separate check.

Archer 2 faces no opponent point mass there. Thus,

```math
U_2(0)=V_2.
```

Archer 1 faces Archer 2's point mass $m$.

A shot just before $0$ gives Archer 1 a win on that event with probability approaching $1$. A shot exactly at $0$ produces two certain hits.

That change removes probability $m$ from Archer 1's payoff:

```math
U_1(0)=V_1-m\lt V_1.
```

The complete payoff check is therefore

```math
\boxed{
U_1(x)=
\begin{cases}
V_1-m, & x=0,\\[1mm]
V_1, & 0\lt x\le b,\\[1mm]
1-x, & b\lt x\le1,
\end{cases}
}
```

and

```math
\boxed{
U_2(x)=
\begin{cases}
V_2, & 0\le x\le b,\\[1mm]
1-x^2, & b\lt x\le1.
\end{cases}
}
```

Every point used by an archer gives their maximum payoff. No other point gives more.

Any random deviation averages these payoffs. It cannot improve them.

This proves equilibrium.

### Win and draw probabilities

The win probabilities are

```math
\boxed{
V_1=1-b
\approx0.3223113440557834,
}
```

```math
\boxed{
V_2=1-b^2
\approx0.5407380856045212.
}
```

Therefore,

```math
\boxed{
\Pr(\text{draw})
=
1-V_1-V_2
=
b+b^2-1
\approx0.1369505703396955.
}
```

Exact ties have probability zero in this equilibrium. Archer 1 has no point masses, including at $0$.

Thus, equilibrium draws come from **two misses**.

The exact tie rule still matters. It prevents Archer 1 from profitably joining Archer 2's point mass at $0$.

The random interval starts at $b>c$, which is earlier than the noisy threshold. Individual silent shots can occur on either side of $c$.

## 6. Literal simultaneous fire changes the noisy result

Now replace the noisy tie rule.

Suppose both arrows leave at the same instant. Both hit events resolve independently. Neither archer can keep their arrow after the other's miss.

At an exact tie, Archer $i$ wins only if their own arrow hits and the other arrow misses:

```math
S_i(x)=p_i(x)q_j(x).
```

At the noisy threshold $c$,

```math
p_i(c)=q_j(c)=v_i.
```

Thus,

```math
S_i(c)=v_i^2.
```

The payoffs become

```math
\boxed{
S_1(c)=c^4\approx0.145898034,
}
```

```math
\boxed{
S_2(c)=c^2\approx0.381966011.
}
```

The draw probability becomes

```math
\boxed{
1-S_1(c)-S_2(c)
=
2c^3
\approx0.472135955.
}
```

Both-hit and both-miss outcomes each have probability $c^3$.

### The threshold tie is no longer an equilibrium

Either archer can decline the tie and let the opponent fire at $c$.

If that shot misses, the armed archer hears it. That archer then waits until $0$ and wins.

This change gives

```math
q_j(c)=v_i,
```

which is strictly larger than $v_i^2$.

Therefore,

```math
\boxed{
\text{“Both fire at }c\text{” fails under literal simultaneous fire.}
}
```

There is a stronger result:

```math
\boxed{
\text{This noisy version has no exact Nash equilibrium}
}
```

in ordinary independent random firing plans.

The reason is the discontinuity at an exact tie. Distinct firing points can approach each other, while their payoffs remain very different from the tie payoff.

### Proof that ordinary random plans cannot fix the problem

Let $Y$ be the opponent's planned first-shot state. After a heard miss, the armed archer waits until $0$.

**First, each archer can obtain payoffs arbitrarily close to $v_i$.**

Choose a state $x>c$, arbitrarily close to $c$. Choose $x$ where the opponent has no point mass.

If you fire first, you get $p_i(x)$.

If the opponent fires first at $y>x$, you get $q_j(y)$. This exceeds $p_i(x)$, because $x>c$.

Thus, your payoff is at least $p_i(x)$, which tends to $v_i$.

Any equilibrium would therefore require

```math
U_1\ge v_1,
\qquad
U_2\ge v_2.
```

But

```math
U_1+U_2\le1=v_1+v_2.
```

Hence any equilibrium must satisfy

```math
U_1=v_1,\qquad U_2=v_2.
```

**Second, the opponent cannot assign positive probability above $c$.**

Let your chosen state approach $c$ from above, while avoiding point masses. Your payoff approaches

```math
v_i+
\int_{(c,1]}
\bigl[q_j(y)-v_i\bigr]\,dF_j(y).
```

For every $y>c$,

```math
q_j(y)>q_j(c)=v_i.
```

Any positive probability above $c$ would therefore let you obtain more than $v_i$.

So both distributions must lie in $[0,c]$.

**Third, the opponent cannot assign positive probability below $c$.**

Suppose

```math
r=\Pr(Y\lt c)>0.
```

Choose a point $x=c-\delta$ where the opponent has no point mass.

Then

```math
\begin{aligned}
U_i(x)-v_i
={}&
\bigl[p_i(x)-v_i\bigr]\Pr(Y\lt x)\\
&-
\int_{(x,c)}
\bigl[v_i-q_j(y)\bigr]\,dF_j(y).
\end{aligned}
```

The first term is positive. As $\delta$ tends to zero, it behaves like

```math
|p_i'(c)|\,r\,\delta.
```

The second term is smaller in order. Its magnitude is at most

```math
C\delta\,\Pr(c-\delta\lt Y\lt c)
```

for some fixed constant $C$. The probability in this shrinking interval tends to zero.

Thus, for sufficiently small $\delta$,

```math
U_i(c-\delta)>v_i.
```

That would be a profitable change.

Therefore, each distribution must put all probability exactly at $c$.

**Finally, that remaining possibility fails.**

If both choose $c$, literal simultaneous fire gives $v_i^2\lt v_i$.

This contradiction proves nonexistence.

### Approximate equilibria still exist

An **$\varepsilon$-equilibrium** allows each archer a possible improvement of at most $\varepsilon$.

For any

```math
0\lt \varepsilon\lt 1-c,
```

use these plans:

- Archer 1 plans to fire at $c+\varepsilon$.

- Archer 2 plans to fire at $c$.

- After a heard miss, the armed archer waits until $0$.

Archer 1 fires first. The payoffs are

```math
\boxed{
U_1=v_1-\varepsilon,
\qquad
U_2=v_2+\varepsilon.
}
```

Archer 2 already has a best response. Archer 1 can improve by exactly $\varepsilon$, by letting Archer 2 fire at $c$.

Thus, these plans form an $\varepsilon$-equilibrium.

As $\varepsilon$ tends to zero, the payoffs approach the sequential-priority values. At the exact tie, literal simultaneous fire causes the payoff drop. That is why arbitrarily accurate approximate equilibria exist, while an exact equilibrium does not.
