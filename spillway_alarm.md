# The Spillway Alarm

## A public-good timing game with visible and sealed controls

## Problem statement

Two research stations, Station 1 and Station 2, protect the same mountain valley from a glacial-lake outburst.

Either station can launch an emergency drone that opens a spillway. **One successful launch protects both stations**, and every launch succeeds with certainty. Launching is therefore not an attack on the rival; it is a costly public-good contribution that the rival would prefer to receive for free.

### Time and the external hazard

Time is normalized as

```math
t:0\longrightarrow 1.
```

A flood would occur at a random time

```math
T\sim \operatorname{Unif}(0,1).
```

Thus

```math
\Pr(T>t)=1-t,
\qquad
f_T(t)=1.
```

A drone protects the valley only if it launches strictly before $T$. If a launch and the flood occur at exactly the same instant, the flood wins. Because $T$ is continuous, this convention affects no equilibrium probability.

The flood time is independent of both stations’ randomizations.

### Asymmetric abilities

Opening the spillway gives each station a normalized safety value of $1$. A station whose own drone executes pays its launch cost:

```math
c_1=\frac13,
\qquad
c_2=\frac12.
```

Station 1 therefore has the more efficient intervention technology.

The realized payoff to Station $i$ is:

| Outcome for Station $i$ | Payoff |
| --- | ---: |
| Flood occurs before any launch | $0$ |
| Valley protected; Station $i$ launches | $1-c_i$ |
| Valley protected; Station $i$ does not launch | $1$ |

If both drones execute, both stations are protected and each pays its own cost. There is no draw: the physical outcome is either protection or flooding.

### Version O: open radio

- A launch is observed immediately by both stations.
- Once one drone launches, the other station cancels any future launch at zero cost.
- At each active time $t$, a station knows the current time, knows that no flood has yet occurred, and knows that no drone has yet launched.
- It does not know its rival’s privately randomized future launch time.
- A pure deadline $x_i$ means: launch at $x_i$ if neither a flood nor a rival launch has occurred first.
- A mixed strategy may be represented by a random deadline $X_i$, or equivalently by an instantaneous launch hazard.
- If both launch at exactly the same time before $T$, both drones execute and both stations pay their costs.

### Version B: radio blackout

- At $t=0$, each station privately programs a timer

```math
X_i\in[0,1]\cup\{\infty\}.
```

- $X_i=\infty$ means that Station $i$ never launches.
- Timers cannot be revised or canceled.
- A station cannot observe whether the rival has launched.
- If one timer beats $T$, the valley is protected. Every other finite timer later executes anyway and incurs its cost.
- Thus, if Station 1 programs $0.2$, Station 2 programs $0.8$, and $T=0.5$, Station 1 protects the valley at $0.2$, but Station 2’s autonomous drone still launches redundantly at $0.8$.
- If $T$ occurs before the earliest finite timer, the control system is destroyed; later timers do not execute and no launch cost is paid.
- A timer at $1$ is therefore not the same as $\infty$: it may execute redundantly at $1$ if the rival protected the valley earlier.

The tasks are to derive best responses, characterize pure equilibria, obtain a coordination-free mixed equilibrium in each version, verify all unilateral deviations, calculate outcome probabilities, and determine how the simultaneous-launch convention matters.

The attached benchmark emphasizes telling the intuitive story while making each step mathematically precise; the same two-layer standard is used below. Pasted markdown

---

# 1. The probability clock

Before studying strategy, isolate the external risk.

At time $t$, the unconditional probability that the valley has not yet flooded is

```math
S_T(t)=1-t.
```

Conditional on having survived to time $t$, the probability of a flood during the next small interval $dt$ is approximately

```math
\lambda(t)\,dt,
```

where

```math
\lambda(t)
=
\frac{f_T(t)}{S_T(t)}
=
\frac{1}{1-t}.
```

This $\lambda(t)$ is the **conditional flood hazard**.

The story is simple: at $t=0.9$, the valley has already been unusually lucky. Conditional on surviving that long, the remaining flood time is compressed into the short interval $(0.9,1)$, so the immediate danger is high.

The distinction

```math
f_T(t)=1
\qquad\text{but}\qquad
\lambda(t)=\frac1{1-t}
```

will matter in the mixed-strategy derivation.

---

# 2. Open radio: deterministic deadlines

## 2.1 When one station launches first

Let $x_i$ be Station $i$’s deterministic launch deadline.

Because ordinary time increases, the smaller deadline occurs first:

```math
x_1<x_2
\quad\Longrightarrow\quad
\text{Station 1 launches first}.
```

Suppose $x_1<x_2$.

There are two possible physical outcomes:

1. If $T\le x_1$, the flood arrives before either launch. Both receive $0$.
2. If $T>x_1$, Station 1 launches, the valley is protected, and Station 2 cancels.

Since

```math
\Pr(T>x_1)=1-x_1,
```

Station 1’s expected payoff is

```math
U_1^{O}(x_1,x_2)
=
(1-x_1)(1-c_1).
```

The factor $1-x_1$ is the probability that the launch occurs in time. The factor $1-c_1$ is Station 1’s payoff after paying its own cost.

Station 2 free-rides whenever the launch succeeds, so

```math
U_2^{O}(x_1,x_2)
=
1-x_1.
```

If $x_2<x_1$, the roles reverse:

```math
U_1^{O}(x_1,x_2)=1-x_2,
```

```math
U_2^{O}(x_1,x_2)=(1-x_2)(1-c_2).
```

Under the base simultaneous-launch convention, if $x_1=x_2=x<\infty$, both drones execute whenever $T>x$. Hence

```math
U_i^{O}(x,x)
=
(1-x)(1-c_i).
```

Thus the deterministic payoff function for Station $i$, facing Station $j$, is

```math
\boxed{
U_i^{O}(x_i,x_j)=
\begin{cases}
(1-x_i)(1-c_i), & x_i<x_j,\\[4pt]
1-x_j, & x_j<x_i,\\[4pt]
(1-x_i)(1-c_i), & x_i=x_j<\infty.
\end{cases}
}
```

If both choose $\infty$, the flood occurs with probability one and both receive $0$.

---

## 2.2 Best response to a known rival deadline

Suppose Station $j$ has announced a deadline $y$.

Station $i$ has two economically distinct responses.

### Response A: volunteer before $y$

If Station $i$ intends to launch before $y$, its payoff from deadline $x<y$ is

```math
(1-x)(1-c_i).
```

Because $1-c_i>0$, this expression strictly decreases with $x$:

```math
\frac{d}{dx}\big[(1-x)(1-c_i)\big]
=
-(1-c_i)<0.
```

Therefore, once Station $i$ has decided to be the volunteer, it should not delay at all. Its best volunteering action is

```math
x=0,
```

which yields

```math
V_i^{\text{volunteer}}=1-c_i.
```

There is no technological benefit from waiting. Waiting merely creates additional flood risk.

### Response B: wait behind $y$

If Station $i$ chooses any deadline later than $y$, then Station $j$ launches first whenever $T>y$, and Station $i$ cancels.

Its payoff is therefore

```math
V_i^{\text{free ride}}=1-y.
```

The station compares

```math
\underbrace{1-c_i}_{\text{launch immediately}}
\qquad\text{with}\qquad
\underbrace{1-y}_{\text{wait for the rival}}.
```

It is indifferent when

```math
1-c_i=1-y,
```

or

```math
\boxed{y=c_i.}
```

Thus:

```math
\boxed{
\begin{aligned}
y<c_i
&\quad\Longrightarrow\quad
\text{wait behind }y,\\
y>c_i
&\quad\Longrightarrow\quad
\text{launch immediately},\\
y=c_i
&\quad\Longrightarrow\quad
\text{indifferent}.
\end{aligned}
}
```

The interpretation is especially clean because the flood time is uniform. Waiting until $y$ exposes the station to flood probability $y$. The station volunteers when that probability exceeds its launch cost.

For the two stations:

```math
c_1=\frac13,
\qquad
c_2=\frac12.
```

So Station 1 launches immediately if it expects Station 2 to wait beyond $1/3$, while Station 2 launches immediately if it expects Station 1 to wait beyond $1/2$.

---

# 3. Pure equilibria with open radio

## 3.1 The two simplest equilibria

Consider

```math
(x_1,x_2)=(0,\infty).
```

Station 1 launches immediately. Its payoff is

```math
U_1^{O}(0,\infty)
=
1-c_1
=
\frac23.
```

If Station 1 delays to any $x>0$ while Station 2 never acts, its payoff becomes

```math
(1-x)(1-c_1)
<
1-c_1.
```

If it never acts, its payoff is $0$. Therefore Station 1 has no profitable deviation.

Station 2 receives

```math
U_2^{O}(0,\infty)=1.
```

It cannot obtain more than $1$. Launching simultaneously would reduce its payoff to $1-c_2=1/2$, and any later launch is canceled. Therefore Station 2 also has no profitable deviation.

Hence

```math
\boxed{(0,\infty)\text{ is a Nash equilibrium}.}
```

By symmetry of the strategic roles,

```math
\boxed{(\infty,0)\text{ is also a Nash equilibrium}.}
```

These equilibria are asymmetric even though both stations benefit from protection. One station is assigned the costly volunteer role; the other free-rides.

Because the designated volunteer acts immediately whenever the game remains active and the other never acts, these role-assigned strategies can also be interpreted as subgame-perfect strategies.

---

## 3.2 Full deterministic-deadline characterization

Suppose Station 1 launches at $0$, while Station 2’s off-path backup deadline is $y>0$.

Station 1 receives $1-c_1$. If it deviates and waits for Station 2, it receives $1-y$. Therefore Station 1 is willing to retain the volunteer role exactly when

```math
1-c_1\ge 1-y,
```

or

```math
y\ge c_1.
```

Station 2 is happy to wait behind $0$, since it obtains the maximum payoff $1$.

Thus every profile

```math
(0,y),
\qquad
y\in[c_1,1]\cup\{\infty\},
```

is a deterministic-deadline Nash equilibrium.

Similarly,

```math
(x,0),
\qquad
x\in[c_2,1]\cup\{\infty\},
```

is an equilibrium.

With the numerical costs,

```math
\boxed{
\mathcal E_{\mathrm{pure}}^{O}
=
\left\{(0,y):y\in\left[\frac13,1\right]\cup\{\infty\}\right\}
\cup
\left\{(x,0):x\in\left[\frac12,1\right]\cup\{\infty\}\right\}.
}
```

Every pure equilibrium assigns one station the immediate-volunteer role.

---

## 3.3 Why no equal positive deadline is an equilibrium

Suppose both choose the same $x<1$.

Station $i$’s tie payoff is

```math
(1-x)(1-c_i).
```

Now let Station $i$ move an instant later, to $x+\varepsilon$. When $T>x$, the rival launches at $x$, and Station $i$ free-rides. As $\varepsilon\downarrow0$, its payoff approaches

```math
1-x.
```

The improvement is

```math
(1-x)-(1-x)(1-c_i)
=
(1-x)c_i>0.
```

So a known simultaneous deadline is unstable.

Notice the direction of the deviation:

> In this public-good game, a player moves slightly **later** to let the rival bear the cost.

That is the opposite of a preemption race in which a player moves slightly earlier.

At $x=1$, both effectively allow the flood to occur and receive $0$. Either can deviate to $0$ and receive $1-c_i>0$.

Thus no equal deadline is a pure equilibrium.

---

## 3.4 Why an unequal positive pair is not an equilibrium

Suppose $0<x_1<x_2$, so Station 1 is the volunteer.

Its payoff is

```math
(1-x_1)(1-c_1).
```

Moving from $x_1$ to $0$ preserves its role as first actor but eliminates unnecessary flood risk:

```math
1-c_1
>
(1-x_1)(1-c_1).
```

Therefore any pure equilibrium volunteer must act at $0$.

Combining this fact with the previous subsection proves the pure-equilibrium characterization.

---

# 4. Why a coordination-free equilibrium requires mixing

Pure equilibria exist, so randomization is not logically necessary for Nash equilibrium.

But every pure equilibrium requires the stations to agree, explicitly or implicitly, on who will be the volunteer. Without such a role assignment:

- both choosing the same deadline is unstable because each wants to wait just after the other;
- both waiting forever is unstable because either station prefers paying its cost to receiving zero;
- an unequal positive pair is unstable because the volunteer prefers to act immediately.

Thus an equilibrium in which **both stations retain a positive probability of being the volunteer** must use random timing.

The strategic story is a war of attrition against an external hazard:

- waiting creates a chance that the rival will pay;
- waiting also creates a chance that the flood will arrive;
- launching ends the uncertainty but imposes a private cost.

A predictable mass point is exploitable. If the rival is likely to launch at a known time $t$, a station would like to wait just beyond $t$, free-riding on that probability mass while adding almost no flood exposure. The role-free equilibrium therefore uses continuous distributions.

---

# 5. Open-radio mixed equilibrium

## 5.1 Launch hazards

Let

```math
h_i(t)
```

be Station $i$’s instantaneous launch hazard at time $t$, conditional on the game still being active.

Formally,

```math
h_i(t)\,dt
```

is approximately the probability that Station $i$ launches during $[t,t+dt)$, conditional on:

- no flood before $t$;
- no previous launch;
- Station $i$ not having launched before $t$.

At an active history, Station $i$ can launch immediately and secure

```math
1-c_i.
```

In an interior mixed equilibrium, it must be indifferent between launching now and waiting for the next $dt$.

If it waits:

- with probability $h_j(t)dt$, Station $j$ launches, and Station $i$ gets $1$;
- with probability $\lambda(t)dt$, the flood occurs, and Station $i$ gets $0$;
- otherwise, the game continues, with value $1-c_i$.

Therefore

```math
1-c_i
=
h_j(t)dt\cdot 1
+
\lambda(t)dt\cdot 0
+
\left[1-\big(h_j(t)+\lambda(t)\big)dt\right](1-c_i)
+
o(dt).
```

Subtract $1-c_i$ from both sides and divide by $dt$:

```math
0
=
h_j(t)
-
\big(h_j(t)+\lambda(t)\big)(1-c_i).
```

Expanding gives

```math
0
=
c_i h_j(t)
-
(1-c_i)\lambda(t).
```

Hence

```math
\boxed{
h_j(t)
=
\frac{1-c_i}{c_i}\lambda(t).
}
```

Since

```math
\lambda(t)=\frac1{1-t},
```

we obtain

```math
\boxed{
h_j(t)
=
\frac{1-c_i}{c_i(1-t)}.
}
```

The indices cross: Station $j$’s hazard is chosen to make Station $i$ indifferent.

Therefore

```math
h_1(t)
=
\frac{1-c_2}{c_2(1-t)},
```

```math
h_2(t)
=
\frac{1-c_1}{c_1(1-t)}.
```

Substituting the costs,

```math
\boxed{
h_1(t)=\frac1{1-t},
\qquad
h_2(t)=\frac2{1-t}.
}
```

The hazards increase as the deadline approaches because the conditional flood hazard also increases.

---

## 5.2 From hazards to probability distributions

Let

```math
F_i(t)=\Pr(X_i\le t)
```

be Station $i$’s planned-deadline distribution, and let

```math
S_i(t)=1-F_i(t)=\Pr(X_i>t).
```

For a continuous hazard,

```math
S_i(t)
=
\exp\left(-\int_0^t h_i(s)\,ds\right).
```

Define

```math
\alpha_1=\frac{1-c_2}{c_2},
\qquad
\alpha_2=\frac{1-c_1}{c_1}.
```

Then

```math
h_i(t)=\frac{\alpha_i}{1-t}.
```

Thus

```math
\begin{aligned}
S_i(t)
&=
\exp\left(
-\int_0^t\frac{\alpha_i}{1-s}\,ds
\right)\\
&=
\exp\left(
\alpha_i\ln(1-t)
\right)\\
&=
(1-t)^{\alpha_i}.
\end{aligned}
```

Consequently,

```math
\boxed{
F_i(t)=1-(1-t)^{\alpha_i}.
}
```

The densities are

```math
\boxed{
f_i(t)
=
\alpha_i(1-t)^{\alpha_i-1}.
}
```

For the numerical costs,

```math
\alpha_1
=
\frac{1-\frac12}{\frac12}
=
1,
```

```math
\alpha_2
=
\frac{1-\frac13}{\frac13}
=
2.
```

Therefore

```math
\boxed{
F_1(t)=t,
\qquad
f_1(t)=1,
}
```

and

```math
\boxed{
F_2(t)=1-(1-t)^2=2t-t^2,
\qquad
f_2(t)=2(1-t).
}
```

Station 1 draws uniformly from $[0,1]$. Station 2’s density is larger near $0$, so it tends to choose earlier deadlines.

---

## 5.3 Boundary and normalization checks

For Station 1,

```math
F_1(0)=0,
\qquad
F_1(1)=1,
```

and

```math
\int_0^1 f_1(t)\,dt
=
\int_0^1 1\,dt
=
1.
```

For Station 2,

```math
F_2(0)=0,
\qquad
F_2(1)=1,
```

and

```math
\int_0^1 f_2(t)\,dt
=
\int_0^1 2(1-t)\,dt
=
1.
```

Neither distribution has an atom at $0$, at a positive time, or at $1$.

The exploding conditional hazards near $1$ do not create infinite probability. They integrate to distributions with total mass one.

Because both distributions are continuous,

```math
\Pr(X_1=X_2)=0.
```

The simultaneous-launch convention therefore has no effect on this equilibrium.

---

# 6. Global verification of every deterministic deviation

The local hazard calculation is suggestive, but Nash equilibrium requires a global deviation check.

Suppose Station $i$ chooses a deterministic deadline $t$ against Station $j$’s continuous distribution $F_j$, with density $f_j$.

Station $i$ can obtain a positive payoff in two ways.

### The rival launches first

If Station $j$’s deadline is $s<t$, it launches first only if the flood has not yet occurred. This has probability density

```math
(1-s)f_j(s).
```

Station $i$ then free-rides and receives $1$.

The expected contribution is

```math
\int_0^t (1-s)f_j(s)\,ds.
```

### Station $i$ reaches its own deadline

Station $i$ launches at $t$ only if:

- $T>t$, which has probability $1-t$;
- $X_j>t$, which has probability $1-F_j(t)$.

These events are independent, so their joint probability is

```math
(1-t)\big[1-F_j(t)\big].
```

Station $i$ then receives $1-c_i$.

Thus

```math
\boxed{
U_i^{O}(t)
=
\int_0^t (1-s)f_j(s)\,ds
+
(1-c_i)(1-t)\big[1-F_j(t)\big].
}
```

Now use the equilibrium distribution that makes Station $i$ indifferent. Let

```math
a=\frac{1-c_i}{c_i}.
```

Then the rival’s survival function and density are

```math
1-F_j(s)=(1-s)^a,
```

```math
f_j(s)=a(1-s)^{a-1}.
```

The free-riding term becomes

```math
\begin{aligned}
\int_0^t (1-s)f_j(s)\,ds
&=
a\int_0^t(1-s)^a\,ds\\
&=
\frac{a}{a+1}
\left[
1-(1-t)^{a+1}
\right].
\end{aligned}
```

Because

```math
a+1
=
\frac{1-c_i}{c_i}+1
=
\frac1{c_i},
```

and

```math
\frac{a}{a+1}=1-c_i,
```

the first term is

```math
(1-c_i)
\left[
1-(1-t)^{1/c_i}
\right].
```

The own-launch term is

```math
\begin{aligned}
(1-c_i)(1-t)\big[1-F_j(t)\big]
&=
(1-c_i)(1-t)^{a+1}\\
&=
(1-c_i)(1-t)^{1/c_i}.
\end{aligned}
```

Adding the two terms gives

```math
\begin{aligned}
U_i^{O}(t)
&=
(1-c_i)
\left[
1-(1-t)^{1/c_i}
\right]\\
&\quad+
(1-c_i)(1-t)^{1/c_i}\\
&=
1-c_i.
\end{aligned}
```

Therefore

```math
\boxed{
U_i^{O}(t)=1-c_i
\qquad
\text{for every }t\in[0,1].
}
```

Choosing never to launch gives the limiting payoff

```math
U_i^{O}(\infty)
=
\int_0^1(1-s)f_j(s)\,ds
=
1-c_i.
```

Thus every deterministic deadline, including never, gives exactly the equilibrium value. A randomized deviation is only an average of deterministic-deadline payoffs, so it cannot do better.

The equilibrium values are therefore

```math
\boxed{
V_1^{O}=1-c_1=\frac23,
\qquad
V_2^{O}=1-c_2=\frac12.
}
```

This proves that the displayed pair of distributions is a Nash equilibrium. It is the unique atomless full-support equilibrium, although the game also has the role-assigned pure equilibria already identified.

---

# 7. Outcome probabilities under open radio

Define

```math
K=1+\alpha_1+\alpha_2.
```

The three competing conditional hazards are:

```math
\text{Station 1: }\frac{\alpha_1}{1-t},
```

```math
\text{Station 2: }\frac{\alpha_2}{1-t},
```

```math
\text{Flood: }\frac1{1-t}.
```

The probability that no event has occurred by $t$ is

```math
\begin{aligned}
A(t)
&=
\Pr(T>t,X_1>t,X_2>t)\\
&=
(1-t)(1-t)^{\alpha_1}(1-t)^{\alpha_2}\\
&=
(1-t)^K.
\end{aligned}
```

The density that Station 1 is the first event at time $t$ is

```math
A(t)h_1(t)
=
\alpha_1(1-t)^{K-1}.
```

Therefore

```math
\Pr(\text{Station 1 launches first})
=
\int_0^1 \alpha_1(1-t)^{K-1}\,dt
=
\frac{\alpha_1}{K}.
```

Similarly,

```math
\Pr(\text{Station 2 launches first})
=
\frac{\alpha_2}{K},
```

and

```math
\Pr(\text{flood first})
=
\frac1K.
```

Here

```math
\alpha_1=1,
\qquad
\alpha_2=2,
\qquad
K=4.
```

Hence

```math
\boxed{
\Pr(\text{Station 1 launches first})=\frac14,
}
```

```math
\boxed{
\Pr(\text{Station 2 launches first})=\frac12,
}
```

```math
\boxed{
\Pr(\text{flood})=\frac14.
}
```

The valley is protected with probability

```math
\frac14+\frac12=\frac34.
```

There are no redundant launches.

The expected launch cost is

```math
\frac14\cdot\frac13
+
\frac12\cdot\frac12
=
\frac1{12}+\frac14
=
\frac13.
```

The equilibrium payoffs can be checked directly:

```math
V_1^{O}
=
\frac12\cdot1
+
\frac14\cdot\frac23
+
\frac14\cdot0
=
\frac23,
```

```math
V_2^{O}
=
\frac14\cdot1
+
\frac12\cdot\frac12
+
\frac14\cdot0
=
\frac12.
```

---

## 7.1 Why the expensive station acts more often

Station 2 has the higher launch cost, yet it launches first with probability $1/2$, compared with Station 1’s probability $1/4$.

This is not an arithmetic error. Mixed-equilibrium probabilities are determined by **cross-indifference**.

Station 2’s launch behavior must make cheap Station 1 indifferent between paying $1/3$ and waiting. Because Station 1 is relatively willing to launch, Station 2 must create a substantial prospect of free protection to keep Station 1 waiting.

Conversely, expensive Station 2 is easier to persuade to wait. Station 1 needs only a smaller launch probability to make Station 2 indifferent.

Thus a player’s equilibrium mixing probability need not reflect its own willingness to act. It is chosen to control the rival’s incentives.

---

# 8. Radio blackout: why positive delayed timers disappear

Open radio makes delay valuable because a station can cancel after observing a rival launch.

Under blackout, that option vanishes. A delayed timer still fires even after the rival has protected the valley. Delay therefore combines two disadvantages:

- it creates flood exposure;
- it does not avoid the launch cost after a rival intervention.

This changes the mathematics sharply.

---

## 8.1 Payoffs from finite timers

Suppose both stations choose finite timers $x$ and $y$. Let

```math
m=\min\{x,y\}.
```

If $T\le m$, the flood arrives before either timer and both receive $0$.

If $T>m$, at least one timer protects the valley. Since both timers are finite and cannot be canceled, both drones eventually execute. Station $i$ receives $1-c_i$.

Therefore

```math
\boxed{
U_i^{B}(x,y)
=
(1-m)(1-c_i),
\qquad
m=\min\{x,y\},
}
```

when both timers are finite.

If Station $i$ chooses $\infty$ and Station $j$ chooses a finite timer $y$, Station $i$ receives full protection whenever $T>y$:

```math
U_i^{B}(\infty,y)=1-y.
```

If both choose $\infty$,

```math
U_i^{B}(\infty,\infty)=0.
```

---

## 8.2 Acting later is dominated once a station intends to act

Let $Y$ be the rival’s possibly random timer, with $\min(x,\infty)=x$.

If Station $i$ chooses a finite timer $x$, protection occurs precisely when

```math
T>\min(x,Y).
```

Whenever protection occurs, Station $i$’s finite timer eventually executes, so its payoff is $1-c_i$. Therefore

```math
\boxed{
U_i^{B}(x;Y)
=
(1-c_i)
\mathbb E\!\left[1-\min(x,Y)\right].
}
```

At $x=0$,

```math
U_i^{B}(0;Y)=1-c_i.
```

For any $x>0$,

```math
\begin{aligned}
U_i^{B}(0;Y)-U_i^{B}(x;Y)
&=
(1-c_i)
\mathbb E[\min(x,Y)]\\
&\ge0.
\end{aligned}
```

The inequality is strict whenever

```math
\Pr(Y>0)>0.
```

If instead $Y=0$ with probability one, choosing a positive finite timer gives $1-c_i$, but choosing $\infty$ gives $1$, because the rival certainly protects the valley and Station $i$ avoids its redundant cost.

Therefore no positive finite timer can be a best response in equilibrium.

The blackout game collapses to two strategically relevant actions:

```math
A=\text{launch immediately at }0,
```

```math
N=\text{never launch}.
```

This is a major information effect. Under open radio, the equilibrium uses an entire continuum of launch times. Under blackout, all interior times disappear.

---

# 9. The reduced blackout game

Under the base convention that both simultaneous commands execute, the payoff matrix is

```math
\begin{array}{c|cc}
 & A_2 & N_2\\
\hline
A_1
&
(1-c_1,\;1-c_2)
&
(1-c_1,\;1)
\\[4pt]
N_1
&
(1,\;1-c_2)
&
(0,\;0)
\end{array}
```

Substituting

```math
c_1=\frac13,
\qquad
c_2=\frac12,
```

gives

```math
\boxed{
\begin{array}{c|cc}
 & A_2 & N_2\\
\hline
A_1
&
\left(\frac23,\frac12\right)
&
\left(\frac23,1\right)
\\[6pt]
N_1
&
\left(1,\frac12\right)
&
(0,0)
\end{array}.
}
```

The logic is the volunteer’s dilemma:

- against $A$, a station prefers $N$, because it can receive $1$ instead of $1-c_i$;
- against $N$, a station prefers $A$, because $1-c_i>0$.

---

# 10. Pure equilibria under blackout

The two asymmetric profiles are Nash equilibria:

```math
\boxed{(A_1,N_2)}
```

and

```math
\boxed{(N_1,A_2)}.
```

At $(A_1,N_2)$:

- Station 1 receives $2/3$. Deviating to $N$ produces a flood and payoff $0$.
- Station 2 receives $1$. Launching would reduce its payoff to $1/2$.

The other profile is analogous.

Neither $(A,A)$ nor $(N,N)$ is an equilibrium:

- At $(A,A)$, either station can stop launching and increase its payoff from $1-c_i$ to $1$.
- At $(N,N)$, either station can launch and increase its payoff from $0$ to $1-c_i>0$.

Thus the blackout game has exactly two pure equilibria after eliminating dominated positive timers.

As in the open-radio game, every pure equilibrium assigns the volunteer role to one station.

---

# 11. Blackout mixed equilibrium

Let

```math
q_i=\Pr(\text{Station }i\text{ chooses }A).
```

Station $i$’s payoff from $A$ is always

```math
1-c_i.
```

It pays its cost whether or not the rival also launches.

Its payoff from $N$ is:

- $1$ if the rival chooses $A$;
- $0$ if the rival chooses $N$.

Therefore

```math
U_i(N)=q_j.
```

For Station $i$ to mix,

```math
1-c_i=q_j.
```

Hence

```math
\boxed{
q_1=1-c_2,
\qquad
q_2=1-c_1.
}
```

Substituting the costs gives

```math
\boxed{
q_1=\frac12,
\qquad
q_2=\frac23.
}
```

The equilibrium distributions are therefore atomic:

```math
\boxed{
\Pr(X_1=0)=\frac12,
\qquad
\Pr(X_1=\infty)=\frac12,
}
```

```math
\boxed{
\Pr(X_2=0)=\frac23,
\qquad
\Pr(X_2=\infty)=\frac13.
}
```

The masses normalize:

```math
\frac12+\frac12=1,
```

```math
\frac23+\frac13=1.
```

The equilibrium values are

```math
\boxed{
V_1^{B}=1-c_1=\frac23,
\qquad
V_2^{B}=1-c_2=\frac12.
}
```

---

## 11.1 Explicit deviation check for every positive timer

It remains to verify that a station cannot profit by returning to a timer $x\in(0,1]$.

Against the rival’s equilibrium mixture:

- with probability $q_j$, the rival launches at $0$; Station $i$’s later timer still executes redundantly, giving $1-c_i$;
- with probability $1-q_j$, the rival never launches; Station $i$’s timer succeeds with probability $1-x$, giving expected payoff $(1-x)(1-c_i)$.

Thus

```math
\begin{aligned}
U_i^{B}(x)
&=
q_j(1-c_i)
+
(1-q_j)(1-x)(1-c_i)\\
&=
(1-c_i)
\left[
q_j+(1-q_j)(1-x)
\right]\\
&=
(1-c_i)
\left[
1-(1-q_j)x
\right].
\end{aligned}
```

Since $0<q_j<1$, every $x>0$ satisfies

```math
U_i^{B}(x)<1-c_i=V_i^{B}.
```

Therefore no positive finite timer is profitable.

The only best responses are the two support actions $0$ and $\infty$, which yield equal payoff. Any other mixed deviation is an average of weakly lower payoffs.

---

# 12. Outcome probabilities under blackout

Using

```math
q_1=\frac12,
\qquad
q_2=\frac23,
```

the four action profiles have probabilities:

```math
\Pr(A_1,A_2)
=
\frac12\cdot\frac23
=
\frac13,
```

```math
\Pr(A_1,N_2)
=
\frac12\cdot\frac13
=
\frac16,
```

```math
\Pr(N_1,A_2)
=
\frac12\cdot\frac23
=
\frac13,
```

```math
\Pr(N_1,N_2)
=
\frac12\cdot\frac13
=
\frac16.
```

Thus

```math
\boxed{
\Pr(\text{flood})=\frac16,
}
```

and

```math
\boxed{
\Pr(\text{protection})=\frac56.
}
```

The probability of two redundant launches is

```math
\boxed{
\Pr(\text{both launch})=\frac13.
}
```

The expected number of launches is

```math
q_1+q_2
=
\frac12+\frac23
=
\frac76.
```

The expected total launch cost is

```math
q_1c_1+q_2c_2
=
\frac12\cdot\frac13
+
\frac23\cdot\frac12
=
\frac16+\frac13
=
\frac12.
```

Station 1’s payoff check is

```math
\begin{aligned}
V_1^{B}
&=
\Pr(N_1,A_2)\cdot1\\
&\quad+
\Pr(A_1,N_2)\cdot\frac23\\
&\quad+
\Pr(A_1,A_2)\cdot\frac23\\
&=
\frac13
+
\frac16\cdot\frac23
+
\frac13\cdot\frac23\\
&=
\frac23.
\end{aligned}
```

Similarly,

```math
V_2^{B}=\frac12.
```

---

# 13. What observability changed

The two mixed equilibria give the same private values:

```math
V_1=\frac23,
\qquad
V_2=\frac12.
```

But they achieve those values through different physical outcomes.

## Open radio

- Stations can cancel after observing a rival launch.
- They spread their possible launch times continuously.
- Flood probability is $1/4$.
- Redundant-launch probability is $0$.
- Expected total launch cost is $1/3$.

## Blackout

- A delayed timer cannot be canceled.
- Every plan to act collapses to acting immediately.
- Randomization occurs between $0$ and $\infty$.
- Flood probability falls to $1/6$.
- Redundant-launch probability rises to $1/3$.
- Expected total launch cost rises to $1/2$.

The blackout stations act more aggressively because they cannot rely on a finely timed, observable waiting process. That reduces flood risk but wastes more resources through duplication.

The equality of private equilibrium values is not evidence that information is irrelevant. Indifference pins each player to $1-c_i$, while observability changes how risk and cost are distributed underneath those values.

---

# 14. Dependence on the simultaneous-launch convention

The base convention says that if both stations launch simultaneously, both drones execute and both stations pay.

This convention has no effect on the open-radio continuous equilibrium because

```math
\Pr(X_1=X_2)=0.
```

It matters greatly in the blackout equilibrium because both strategies place positive atoms at $0$:

```math
\Pr(A_1,A_2)=\frac13.
```

Consider an alternative rule.

## Fair deduplicating controller

If both commands arrive simultaneously, a central controller selects one drone with probability $1/2$ each. Only the selected station pays its launch cost.

Let $\theta_i$ be the probability that Station $i$ pays its cost conditional on simultaneous commands. Then:

- base both-pay rule: $\theta_i=1$;
- fair one-drone rule: $\theta_i=1/2$.

If Station $i$ chooses $A$ and the rival chooses $A$, its expected payoff is

```math
1-\theta_i c_i.
```

If Station $i$ chooses $A$ and the rival chooses $N$, its payoff is

```math
1-c_i.
```

Against rival activation probability $q_j$,

```math
\begin{aligned}
U_i(A)
&=
q_j(1-\theta_i c_i)
+
(1-q_j)(1-c_i)\\
&=
1-c_i+c_i(1-\theta_i)q_j.
\end{aligned}
```

Waiting gives

```math
U_i(N)=q_j.
```

Indifference requires

```math
1-c_i+c_i(1-\theta_i)q_j=q_j.
```

Therefore

```math
\boxed{
q_j
=
\frac{1-c_i}
{1-c_i(1-\theta_i)}.
}
```

Under the fair rule, $\theta_i=1/2$. Thus

```math
q_2
=
\frac{1-\frac13}
{1-\frac13\cdot\frac12}
=
\frac{\frac23}{\frac56}
=
\frac45,
```

and

```math
q_1
=
\frac{1-\frac12}
{1-\frac12\cdot\frac12}
=
\frac{\frac12}{\frac34}
=
\frac23.
```

So the new mixed strategy is

```math
\boxed{
q_1=\frac23,
\qquad
q_2=\frac45.
}
```

The equilibrium values are

```math
V_1=q_2=\frac45,
\qquad
V_2=q_1=\frac23.
```

The outcome probabilities become

```math
\Pr(A_1,A_2)
=
\frac23\cdot\frac45
=
\frac8{15},
```

```math
\Pr(A_1,N_2)
=
\frac23\cdot\frac15
=
\frac2{15},
```

```math
\Pr(N_1,A_2)
=
\frac13\cdot\frac45
=
\frac4{15},
```

```math
\Pr(N_1,N_2)
=
\frac13\cdot\frac15
=
\frac1{15}.
```

Thus

```math
\boxed{
\Pr(\text{flood})=\frac1{15}.
}
```

Because simultaneous activation can now lead to protection without both stations paying, both stations activate more frequently.

A positive delayed timer remains unprofitable. Against an opponent using only $0$ and $\infty$, a timer $x>0$ receives

```math
(1-c_i)\left[1-(1-q_j)x\right]
\le 1-c_i,
```

while the fair-rule equilibrium value is strictly larger than $1-c_i$.

The tie rule therefore changes the atomic blackout equilibrium but not the atomless open-radio equilibrium.

---

# 15. Comparison

| Feature | Open radio | Blackout, both-pay tie |
| --- | --- | --- |
| Strategic conflict | Delay to free-ride, but risk flood | Decide whether to volunteer immediately |
| Rival launch observable? | Yes | No |
| Can a later launch be canceled? | Yes | No |
| Pure equilibria | One station launches immediately; other waits | One station launches immediately; other never launches |
| Coordination-free mixed form | Continuous random deadlines | Atoms at $0$ and $\infty$ |
| Station 1 strategy | $F_1(t)=t$ | $\Pr(0)=1/2$ |
| Station 2 strategy | $F_2(t)=2t-t^2$ | $\Pr(0)=2/3$ |
| Station 1 value | $2/3$ | $2/3$ |
| Station 2 value | $1/2$ | $1/2$ |
| Flood probability | $1/4$ | $1/6$ |
| Both launch | $0$ | $1/3$ |
| Expected number of launches | $3/4$ | $7/6$ |
| Expected total launch cost | $1/3$ | $1/2$ |
| Sensitive to launch-time tie rule? | No in the continuous equilibrium | Yes, because of atoms at $0$ |

---

# 16. Intuitive summary

- **A station that knows it must volunteer acts immediately.** Launch cost is constant, so delaying only adds flood risk.
- **A station that expects the rival to act soon prefers to wait.** Open radio lets it cancel and receive the full safety payoff without paying.
- **Continuous mixing balances two hazards.** At every active instant, the chance that the rival launches must exactly compensate for the risk that the flood arrives.
- **Blackout destroys the value of interior timing.** A delayed autonomous timer cannot be canceled, so it still pays the launch cost after a rival intervention while adding flood exposure beforehand.
- **The stronger station need not act more often in a mixed equilibrium.** Each station’s probability is selected to make the other station indifferent.
- **Pure equilibria are efficient role assignments; mixed equilibrium reflects coordination failure.** If the stations could reliably designate Station 1 as the volunteer, immediate protection would cost only $1/3$ and the flood probability would be zero.

---

# 17. Common mistakes

### Mistake 1: treating the uniform density as the conditional hazard

The flood density is

```math
f_T(t)=1,
```

but the conditional hazard is

```math
\lambda(t)=\frac1{1-t}.
```

The latter, not the former, enters the local mixed-strategy calculation.

### Mistake 2: thinking the open-radio player should launch just before a known rival time

If the rival is expected to launch at $y$, a station either:

- launches immediately, eliminating unnecessary flood risk; or
- waits behind $y$ and free-rides.

A positive deadline just before $y$ is inferior to $0$.

### Mistake 3: reversing the profitable infinitesimal deviation

At a predictable simultaneous deadline, a station moves slightly **later**, not earlier. It wants the rival to pay.

### Mistake 4: using the open-radio payoff in the blackout game

Under open radio, a later plan is canceled after a rival launch.

Under blackout, the later finite timer still executes and incurs its cost. This is why

```math
U_i^{B}(x;Y)
=
(1-c_i)\mathbb E[1-\min(x,Y)]
```

contains the station’s cost even when the rival’s timer is earlier.

### Mistake 5: treating $1$ and $\infty$ as identical under blackout

A timer at $1$ may launch redundantly if the rival protected the valley earlier. A timer at $\infty$ never launches and never incurs cost.

### Mistake 6: claiming that the game has no pure equilibrium

Both versions have asymmetric pure equilibria. Mixing is needed only for an equilibrium that does not preassign the volunteer role and gives both stations a positive chance of acting.

### Mistake 7: inferring willingness to act from the player’s own mixing probability

Station 2 acts more frequently even though its launch is more expensive. Its probability is chosen to discipline Station 1, not to reveal Station 2’s isolated preference.

### Mistake 8: ignoring tie rules when strategies have atoms

Tie rules do not affect continuous distributions because ties have probability zero. They materially change the blackout equilibrium because both stations place positive probability at time $0$.

---

# 18. Broader game-theory lesson

This game separates three ideas that are often conflated.

First, **timing can be strategic even when actions succeed with certainty**. The uncertainty comes from an external event and from the rival’s behavior, not from imperfect aim.

Second, **observability changes the available contingent plans**. Open radio lets a station wait while retaining the option to cancel. Blackout turns a delayed action into an irrevocable duplicate commitment.

Third, **mixed strategies can solve a coordination problem rather than a preemption problem**. The random deadline is not meant to surprise an enemy before an attack. It makes the station’s willingness to volunteer unpredictable, balancing the chance of free-riding against the chance of collective failure.

The central principle is:

```math
\boxed{
\text{Information changes the value of waiting because it changes what can be canceled.}
}
```

In the visible game, waiting is a flexible option, producing continuous timing hazards. In the sealed game, waiting while still intending to act is dominated, so equilibrium randomization moves to the two endpoints: act now or never.
