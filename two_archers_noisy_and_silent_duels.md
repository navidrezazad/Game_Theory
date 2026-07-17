# Two Archers: Noisy and Silent Duels

## A story-first and mathematically rigorous guide

Two archers walk toward one another. Each has one arrow. At every location, each archer must balance two competing forces:

- Waiting makes the shot more accurate.
- Waiting also risks allowing the opponent to shoot first.

That tension creates a **timing game**. The noisy and silent versions look similar, but one information change completely alters the equilibrium:

- In the **noisy duel**, a missed shot is heard, so future behavior can react to it.
- In the **silent duel**, a missed shot is not observed, so firing plans cannot react to it.

The central lesson is that information changes not merely the payoffs, but what a strategy *is*.

---

## 1. Model and notation

Let the state variable be

$$
x\in[0,1].
$$

The duel begins at $x=1$, and $x$ decreases continuously as the archers approach one another. Thus:

$$
\boxed{\text{larger }x=\text{earlier and farther away},\qquad
\text{smaller }x=\text{later and closer}.}
$$

This reversed time orientation is worth remembering. If

$$
x_1>x_2,
$$

then Archer 1 fires **before** Archer 2.

The hit probabilities are

$$
p_1(x)=1-x,
\qquad
p_2(x)=1-x^2.
$$

The corresponding miss probabilities are

$$
q_1(x)=1-p_1(x)=x,
\qquad
q_2(x)=1-p_2(x)=x^2.
$$

For every interior point $x\in(0,1)$, Archer 2 is more accurate:

$$
p_2(x)-p_1(x)=x-x^2=x(1-x)>0.
$$

We use the following payoff convention throughout the silent-duel calculation:

- A player's payoff is the probability of being the sole winner.
- If both eventually miss, the outcome is a draw.
- If both fire simultaneously and both hit, the outcome is also a draw.

The exact handling of an exact simultaneous shot matters at a single point. We will state the convention explicitly whenever it matters.

---

# Part I. The noisy duel

## 2. The idea in ordinary language

Suppose Archer 1 shoots first.

- If Archer 1 hits, the duel is over.
- If Archer 1 misses, Archer 2 hears the shot.
- Archer 2 now knows that Archer 1 is unarmed.
- Archer 2 can safely keep walking until $x=0$, where the hit probability is $1$, and then win with certainty.

Therefore, when Archer 1 fires first at $x$, Archer 1's eventual chance of winning is simply

$$
p_1(x)=1-x.
$$

There is no extra factor involving Archer 2's later shot. If Archer 1 misses, the information carried by the sound lets Archer 2 convert that miss into a certain victory.

Now place yourself in Archer 1's position at some candidate point $x$. You compare two choices:

1. **Shoot just before Archer 2.** Your chance of winning is approximately
   \[
   p_1(x)=1-x.
   \]

2. **Let Archer 2 shoot first.** You win exactly when Archer 2 misses:
   \[
   q_2(x)=x^2.
   \]

So Archer 1 compares

$$
\boxed{1-x\quad\text{against}\quad x^2.}
$$

Archer 2 makes the analogous comparison:

$$
\boxed{1-x^2\quad\text{against}\quad x.}
$$

Far away, both archers are inaccurate, so each would rather let the other waste the arrow. Close up, both are accurate, so each wants to fire first. The equilibrium threshold is the boundary between those two regions.

---

## 3. Rigorous payoff functions

A noisy-duel strategy is not merely a planned firing point. It is a contingent rule:

> Fire at the planned threshold if nobody has fired; after hearing the opponent miss, wait until $x=0$ and take the certain shot.

Let $x_1$ and $x_2$ denote the thresholds while both players remain armed.

### Case 1: Archer 1 fires first

If

$$
x_1>x_2,
$$

then Archer 1 fires at $x_1$. Archer 1 wins if and only if that shot hits:

$$
U_1^{N}(x_1,x_2)=p_1(x_1)=1-x_1.
$$

If Archer 1 misses, Archer 2 hears the miss and later wins with certainty. Hence

$$
U_2^{N}(x_1,x_2)=q_1(x_1)=x_1.
$$

### Case 2: Archer 2 fires first

If

$$
x_2>x_1,
$$

then

$$
U_1^{N}(x_1,x_2)=q_2(x_2)=x_2^2,
$$

and

$$
U_2^{N}(x_1,x_2)=p_2(x_2)=1-x_2^2.
$$

Away from an exact tie, the noisy-duel payoffs are therefore

$$
\boxed{
U_1^{N}(x_1,x_2)=
\begin{cases}
1-x_1, & x_1>x_2,\\
x_2^2, & x_2>x_1,
\end{cases}}
$$

and

$$
\boxed{
U_2^{N}(x_1,x_2)=
\begin{cases}
x_1, & x_1>x_2,\\
1-x_2^2, & x_2>x_1.
\end{cases}}
$$

Notice that

$$
U_1^{N}+U_2^{N}=1.
$$

Once one player fires, the noisy information ensures that exactly one player eventually wins.

---

## 4. The critical threshold

Archer 1 is indifferent between firing first and allowing Archer 2 to fire first when

$$
p_1(x)=q_2(x).
$$

Substitution gives

$$
1-x=x^2.
$$

Archer 2's indifference condition is

$$
p_2(x)=q_1(x),
$$

or

$$
1-x^2=x.
$$

These are the same equation:

$$
x^2+x-1=0.
$$

The feasible root is

$$
\boxed{
r=\frac{\sqrt5-1}{2}\approx0.618034.
}
$$

It satisfies

$$
1-r=r^2,
\qquad
1-r^2=r.
$$

At this point,

$$
p_1(r)=r^2\approx0.381966,
\qquad
p_2(r)=r\approx0.618034.
$$

The threshold has a clean interpretation:

- For $x>r$, they are still relatively far apart, and both prefer the opponent to shoot first.
- For $x<r$, they are close enough that both prefer to preempt.
- At $x=r$, each player is indifferent between those two possibilities.

---

## 5. Is $(r,r)$ really a Nash equilibrium?

An exact statement requires a rule for simultaneous intended shots.

### Clean continuous-time convention: random priority at an exact tie

Suppose that if both intend to fire at precisely the same point, a fair coin selects whose shot is resolved first. If that first shot misses, the other archer hears it and can wait until $x=0$.

At a common threshold $x$, Archer 1's payoff is then

$$
U_1^{N}(x,x)
=\frac12p_1(x)+\frac12q_2(x),
$$

while Archer 2's payoff is

$$
U_2^{N}(x,x)
=\frac12p_2(x)+\frac12q_1(x).
$$

At $x=r$, the two terms in each average are equal, so

$$
U_1^{N}(r,r)=r^2,
\qquad
U_2^{N}(r,r)=r.
$$

Now fix Archer 2 at $r$. If Archer 1 deviates to some earlier point $y>r$, then

$$
U_1^{N}(y,r)=1-y<1-r=r^2.
$$

If Archer 1 chooses a later threshold $y<r$, Archer 2 fires first at $r$, and Archer 1 wins when Archer 2 misses:

$$
U_1^{N}(y,r)=r^2.
$$

Thus Archer 1 has no profitable deviation. The same calculation for Archer 2 gives

$$
U_2^{N}(r,y)\le r.
$$

Under this tie convention,

$$
\boxed{(r,r)\text{ is a pure-strategy Nash equilibrium of the noisy duel}.}
$$

The equilibrium is weak rather than strict: after deciding to let the opponent fire first, the exact unused threshold no longer matters because the player will react to the audible miss.

### Literal simultaneous independent shots

Suppose instead that both arrows are released simultaneously and independently, and a player receives payoff $1$ only for being the sole winner. Then at $(r,r)$,

$$
U_1^{N}(r,r)=p_1(r)q_2(r)=r^4,
$$

and

$$
U_2^{N}(r,r)=p_2(r)q_1(r)=r^2.
$$

Both can improve by moving an arbitrarily small amount earlier. Under that convention, $(r,r)$ is not an exact pure equilibrium; $r$ remains the natural limiting threshold and is handled through an $\varepsilon$-equilibrium or a refined tie rule.

This is a knife-edge issue about exact simultaneity, not a change in the main noisy-duel logic.

---

# Part II. The silent duel

## 6. The idea in ordinary language

Now suppose a missed arrow makes no detectable sound.

Imagine that Archer 2 plans to fire at $x_2$, while Archer 1 plans to fire later at $x_1<x_2$.

Archer 2 fires first. If Archer 2 hits, the duel ends. If Archer 2 misses, Archer 1 does **not** learn that Archer 2 has become harmless. Archer 1 simply continues according to the original plan and fires at $x_1$.

Therefore, Archer 1 wins only if two events both occur:

1. Archer 2 misses at $x_2$.
2. Archer 1 hits at $x_1$.

Hence

$$
P(\text{Archer 1 wins})
=q_2(x_2)p_1(x_1)
=x_2^2(1-x_1).
$$

This product is the signature of the silent duel.

In the noisy duel, an observed miss lets the armed player change plans and wait for a certain shot. In the silent duel, no such conditioning is possible. A pure strategy is a firing point chosen in advance; a mixed strategy is a private lottery over firing points.

---

## 7. Rigorous pure-strategy payoff functions

### Case 1: Archer 1 fires first

If

$$
x_1>x_2,
$$

then Archer 1 wins if the first shot hits:

$$
U_1^{S}(x_1,x_2)=p_1(x_1)=1-x_1.
$$

Archer 2 wins only if Archer 1 misses and Archer 2 later hits:

$$
U_2^{S}(x_1,x_2)
=q_1(x_1)p_2(x_2)
=x_1(1-x_2^2).
$$

The probability that both miss is

$$
q_1(x_1)q_2(x_2)=x_1x_2^2.
$$

### Case 2: Archer 2 fires first

If

$$
x_2>x_1,
$$

then Archer 1 wins only if Archer 2 misses and Archer 1 later hits:

$$
U_1^{S}(x_1,x_2)
=q_2(x_2)p_1(x_1)
=x_2^2(1-x_1).
$$

Archer 2 wins if the first shot hits:

$$
U_2^{S}(x_1,x_2)=p_2(x_2)=1-x_2^2.
$$

Thus, away from ties,

$$
\boxed{
U_1^{S}(x_1,x_2)=
\begin{cases}
1-x_1, & x_1>x_2,\\
x_2^2(1-x_1), & x_2>x_1,
\end{cases}}
$$

and

$$
\boxed{
U_2^{S}(x_1,x_2)=
\begin{cases}
x_1(1-x_2^2), & x_1>x_2,\\
1-x_2^2, & x_2>x_1.
\end{cases}}
$$

If both fire simultaneously at $x$, independent-shot sole-victory payoffs are

$$
U_1^{S}(x,x)=p_1(x)q_2(x)=(1-x)x^2,
$$

and

$$
U_2^{S}(x,x)=p_2(x)q_1(x)=(1-x^2)x.
$$

Unlike the noisy duel, the sum of the win probabilities can be less than one because both archers may miss.

---

## 8. Best response to a fixed firing point

Suppose Archer 2 has committed to a known point $x_2$. What should Archer 1 do?

### Option A: Preempt Archer 2

To fire first, Archer 1 needs $x_1>x_2$. Within this region,

$$
U_1^{S}(x_1,x_2)=1-x_1.
$$

This payoff increases as $x_1$ decreases. Therefore, Archer 1 wants to fire as late as possible while still being first:

$$
x_1=x_2+\varepsilon,
\qquad \varepsilon>0\text{ arbitrarily small}.
$$

The limiting value is

$$
\lim_{\varepsilon\downarrow0}
\left[1-(x_2+\varepsilon)\right]
=1-x_2.
$$

### Option B: Let Archer 2 fire first

If $x_1<x_2$, then

$$
U_1^{S}(x_1,x_2)=x_2^2(1-x_1).
$$

Once Archer 1 has accepted being second, this expression is maximized by waiting all the way to

$$
x_1=0.
$$

Then Archer 1 hits with certainty if Archer 2 has missed, producing value

$$
x_2^2.
$$

Thus Archer 1 compares

$$
\boxed{1-x_2\quad\text{against}\quad x_2^2.}
$$

Archer 2 similarly compares

$$
\boxed{1-x_1^2\quad\text{against}\quad x_1.}
$$

The same golden-ratio point

$$
r=\frac{\sqrt5-1}{2}
$$

appears as the point where a player switches between the two pure-response ideas.

But this does **not** make $(r,r)$ a silent-duel equilibrium.

---

## 9. Why $(r,r)$ is not a pure-strategy equilibrium

### The story from Archer 1's perspective

You are Archer 1. You calculate $r\approx0.618$ and announce:

> “At $r$, shooting just before Archer 2 and waiting for Archer 2 to miss are equally attractive. I will shoot at $r$.”

But Archer 2 hears your plan and thinks:

> “Then I will shoot at $r+\varepsilon$, an instant before you.”

Because $\varepsilon$ can be tiny, Archer 2 gains first-shot priority while sacrificing almost no accuracy.

You respond:

> “Then I will shoot at $r+2\varepsilon$, just before you.”

Archer 2 moves slightly earlier again. There is no smallest positive lead. Every announced deterministic time creates a target that can be undercut by an arbitrarily small amount.

The problem is no longer finding a more clever number. The problem is **predictability itself**.

### The mathematical $\varepsilon$-test

At $(r,r)$, Archer 1's simultaneous-shot win probability is

$$
U_1^{S}(r,r)
=p_1(r)q_2(r)
=r^2\cdot r^2
=r^4.
$$

If Archer 1 moves slightly earlier to $r+\varepsilon$, Archer 1 fires first and obtains

$$
U_1^{S}(r+\varepsilon,r)
=1-r-\varepsilon
=r^2-\varepsilon.
$$

For all sufficiently small $\varepsilon>0$,

$$
r^2-\varepsilon>r^4.
$$

So Archer 1 profits by moving slightly earlier.

At $(r,r)$, Archer 2's simultaneous-shot payoff is

$$
U_2^{S}(r,r)
=p_2(r)q_1(r)
=r\cdot r
=r^2.
$$

Moving slightly earlier gives

$$
U_2^{S}(r,r+\varepsilon)
=1-(r+\varepsilon)^2,
$$

which tends to

$$
1-r^2=r
$$

as $\varepsilon\downarrow0$. Since $r>r^2$, Archer 2 also gains.

Therefore,

$$
\boxed{(r,r)\text{ is not a pure-strategy Nash equilibrium of the silent duel}.}
$$

### Why no other unequal pure pair works

Suppose $x_1>x_2$, so Archer 1 fires first. Archer 1 can choose a point $x_1'$ satisfying

$$
x_2<x_1'<x_1.
$$

Archer 1 still fires first, but now fires later and is more accurate:

$$
1-x_1'>1-x_1.
$$

Thus no profile with $x_1>x_2$ can be an equilibrium. The same argument rules out $x_2>x_1$.

At an equal point, the $\varepsilon$-test gives a profitable preemption. Hence, under the stated simultaneous-shot convention, there is no pure-strategy Nash equilibrium.

---

## 10. Why both archers are pushed toward mixed strategies

A mixed strategy means privately drawing a firing point from a probability distribution.

This is not randomization caused by confusion. It is randomization used as concealment.

Suppose Archer 2 chooses one deterministic point. Archer 1 can exploit it by either:

- firing an instant before it, or
- deliberately going second and waiting until $x=0$.

Therefore Archer 2 must hide the exact firing point. The same is true for Archer 1.

But merely “being random” is not sufficient. Imagine Archer 2 uses some distribution that makes firing at $x=0.55$ strictly better for Archer 1 than firing anywhere else. Archer 1 would then abandon all other times and choose $0.55$ with probability one.

Consequently, an equilibrium distribution must satisfy the **indifference principle**:

$$
\boxed{\text{Every firing point used with positive probability must give the same expected payoff}.}
$$

Each archer chooses a distribution designed to make the *other* archer indifferent across an entire interval.

The strategic objective changes:

- In a pure strategy, you search for one best time.
- In a mixed strategy, you shape a lottery so that your opponent cannot identify any best time to exploit.

---

## 11. Expected payoff against a distribution

Let $X_i$ be Archer $i$'s random firing point, and define the cumulative distribution function

$$
F_i(x)=P(X_i\le x).
$$

Remember that smaller $x$ means later. Thus, if Archer 1 chooses the pure point $x$:

- $X_2<x$ means Archer 2 plans to fire later, so Archer 1 fires first.
- $X_2>x$ means Archer 2 fires earlier, so Archer 1 wins only if Archer 2 misses.

Assume for the moment that the opponent has no atom at the interior point $x$. Archer 1's expected payoff from choosing $x$ is

$$
\boxed{
U_1(x)
=(1-x)
\left[
F_2(x)+\int_x^1 y^2\,dF_2(y)
\right].}
$$

The bracket has two parts:

- $F_2(x)$: Archer 2 fires later, so Archer 1 only needs to hit.
- $\int_x^1 y^2\,dF_2(y)$: Archer 2 fires earlier at $y$, misses with probability $y^2$, and then Archer 1 must hit at $x$.

Similarly, Archer 2's expected payoff from choosing $x$ is

$$
\boxed{
U_2(x)
=(1-x^2)
\left[
F_1(x)+\int_x^1 y\,dF_1(y)
\right].}
$$

In equilibrium, these expressions must be constant on the portions of the support where the player randomizes:

$$
U_1(x)=V_1,
\qquad
U_2(x)=V_2.
$$

Here $V_i$ is Archer $i$'s equilibrium probability of winning.

---

## 12. Deriving the equilibrium densities

Suppose the distributions have densities $f_1$ and $f_2$ on an interior support interval.

Define

$$
H_2(x)=F_2(x)+\int_x^1 y^2\,dF_2(y).
$$

Then

$$
H_2'(x)
=f_2(x)-x^2f_2(x)
=(1-x^2)f_2(x).
$$

Since

$$
(1-x)H_2(x)=V_1,
$$

differentiating gives

$$
-H_2(x)+(1-x)(1-x^2)f_2(x)=0.
$$

Using $H_2(x)=V_1/(1-x)$, we obtain

$$
\boxed{
f_2(x)
=\frac{V_1}{(1-x)^2(1-x^2)}.}
$$

This is Archer 2's density, chosen so that Archer 1 is indifferent.

Likewise, define

$$
H_1(x)=F_1(x)+\int_x^1 y\,dF_1(y).
$$

Then

$$
H_1'(x)=(1-x)f_1(x).
$$

Differentiating

$$
(1-x^2)H_1(x)=V_2
$$

yields

$$
\boxed{
f_1(x)
=\frac{2xV_2}{(1-x^2)^2(1-x)}.}
$$

This is Archer 1's density, chosen so that Archer 2 is indifferent.

A useful conceptual point is that the indices cross:

$$
\boxed{f_2\text{ is determined by Archer 1's indifference, and }f_1\text{ by Archer 2's indifference}.}
$$

---

## 13. Boundary conditions and the numerical equilibrium

Solving the equilibrium conditions gives a common continuous support

$$
0<x\le a,
$$

where $a$ is the earliest point at which either archer may fire. No one fires while $x>a$, because that would be unnecessarily early and inaccurate.

At the upper endpoint $a$, the opponent never fires earlier. Therefore,

$$
V_1=p_1(a)=1-a,
$$

and

$$
V_2=p_2(a)=1-a^2.
$$

Archer 1 has no atom at $x=0$, so the density $f_1$ must integrate to one:

$$
(1-a^2)
\int_0^a
\frac{2x}{(1-x^2)^2(1-x)}\,dx
=1.
$$

This equation has the numerical solution

$$
\boxed{a\approx0.677688656.}
$$

Consequently,

$$
\boxed{V_1=1-a\approx0.322311344,}
$$

and

$$
\boxed{V_2=1-a^2\approx0.540738086.}
$$

Archer 1's equilibrium density is

$$
\boxed{
f_1(x)
=\frac{2x(1-a^2)}{(1-x^2)^2(1-x)},
\qquad 0<x\le a.}
$$

Archer 2's continuous density is

$$
\boxed{
f_2(x)
=\frac{1-a}{(1-x)^2(1-x^2)},
\qquad 0<x\le a.}
$$

That continuous part has total probability approximately

$$
0.930954653.
$$

The remaining probability is an atom at point-blank range:

$$
\boxed{
P(X_2=0)
\approx0.069045347.}
$$

Thus the equilibrium strategies are:

| Archer | Continuous randomization | Atom at $x=0$ |
|---|---:|---:|
| Archer 1 | Density $f_1$ on $(0,a]$ | None |
| Archer 2 | Density $f_2$ on $(0,a]$ | About $6.90\%$ |

Because draws are possible,

$$
V_1+V_2<1.
$$

The equilibrium draw probability is

$$
1-V_1-V_2
\approx0.136950570.
$$

### Why does the stronger archer have an atom at $0$?

The continuous density required to keep Archer 1 indifferent uses only about $93.1\%$ of Archer 2's probability mass. The remaining mass must be placed somewhere that does not create an exploitable interior jump.

An interior atom would invite the opponent to fire an instant before it. Point $x=0$ is different: there is no later point. Placing the residual mass there also discourages Archer 1 from waiting all the way to zero, because a simultaneous point-blank encounter would not produce a sole victory for Archer 1.

---

## 14. Verifying the mixed equilibrium

A candidate mixed equilibrium must satisfy two requirements:

1. Every point used with positive probability gives the equilibrium payoff.
2. Every unused point gives no larger payoff.

The density equations guarantee that for every interior point $x\in(0,a]$,

$$
U_1(x)=V_1,
\qquad
U_2(x)=V_2.
$$

For $x>a$, the player fires earlier than the entire opponent support. Hence

$$
U_1(x)=1-x<1-a=V_1,
$$

and

$$
U_2(x)=1-x^2<1-a^2=V_2.
$$

At $x=0$, Archer 2 is indifferent and may place an atom there. Archer 1 obtains strictly less than $V_1$ at exactly zero because Archer 2 also has positive mass at zero, so Archer 1 does not use that point.

Therefore neither player can improve by moving probability to a different firing point.

---

## 15. Why the golden-ratio threshold is not the silent equilibrium endpoint

Two different calculations have appeared:

$$
r\approx0.618034
$$

and

$$
a\approx0.677689.
$$

They answer different questions.

- $r$ is the point where a player is indifferent between two best responses to a **known deterministic opponent time**: preempt that time or wait until zero.
- $a$ is the upper endpoint of the equilibrium support against an **entire probability distribution** of opponent times.

Once the opponent randomizes, the relevant comparison is no longer between two outcomes at one known point. It is an average over all possible earlier and later opponent shots. Therefore there is no reason for $a$ to equal $r$.

This distinction is general:

$$
\boxed{\text{An indifference threshold against a pure action need not be the support boundary in a mixed equilibrium}.}
$$

---

# Part III. The two games side by side

## 16. Structural comparison

| Feature | Noisy duel | Silent duel |
|---|---|---|
| Is a missed shot observed? | Yes | No |
| Can a strategy react after a miss? | Yes | No |
| What is a pure strategy? | A contingent threshold rule | A precommitted firing point |
| If the first shooter misses | The armed opponent learns this and can wait to $0$ | The opponent follows the original plan without knowing |
| Typical payoff when opponent shoots first | Opponent's miss probability | Opponent's miss probability times your later hit probability |
| Pure threshold equation | $1-x=x^2$ | Same equation appears only as a best-response switch point |
| Exact pure equilibrium? | Yes under random-priority tie resolution | No under independent simultaneous-shot convention |
| Strategic phenomenon | Waiting versus preemption | Preemption plus concealment |
| Equilibrium form | Common threshold $r$ | Mixed distributions over firing points |

The deepest distinction is not “one formula has an extra factor.” It is this:

$$
\boxed{
\begin{aligned}
\text{Noisy duel: }&\text{information arrives, so strategies can be contingent};\\
\text{Silent duel: }&\text{information does not arrive, so unpredictability substitutes for reaction}.
\end{aligned}}
$$

---

## 17. A reusable method for timing games

When solving similar games, use the following sequence.

### Step 1: Fix the timeline

State clearly which direction means earlier. Here,

$$
x_i>x_j\iff i\text{ acts first}.
$$

### Step 2: Write payoffs by chronology

Separate the cases

$$
x_1>x_2,
\qquad
x_2>x_1,
\qquad
x_1=x_2.
$$

Do not add conditional probabilities from mutually exclusive cases. Write a piecewise payoff function.

### Step 3: Optimize each branch using monotonicity

Before taking derivatives, ask whether the payoff is monotone within a region. Timing games often place the best response at a boundary:

- just before the opponent, or
- as late as possible after the opponent.

### Step 4: Compare “preempt” with “wait”

The critical equation often has the form

$$
\text{payoff from moving first}
=\text{payoff from allowing the opponent to move first}.
$$

### Step 5: Apply the $\varepsilon$-test

Ask whether moving an arbitrarily small amount earlier improves the payoff:

$$
U_i(x_i+\varepsilon,x_j)>U_i(x_i,x_j).
$$

If so, the candidate cannot be a pure-strategy equilibrium.

### Step 6: If predictability is exploitable, mix

Let the opponent use a distribution. Compute your expected payoff from each pure action and impose

$$
U_i(x)=V_i
$$

throughout the support. Differentiating that indifference equation usually produces the opponent's equilibrium density.

### Step 7: Check boundaries and atoms

Continuous-time games often place probability atoms at endpoints, but interior atoms are usually vulnerable to an infinitesimal preemption.

---

# 18. Final intuition

In the noisy duel, sound supplies information. After an opponent misses, you know it is safe to wait. That makes the game collapse to one central question:

> At what point does the value of shooting first equal the value of letting the opponent shoot and miss?

The answer is the golden-ratio threshold

$$
r=\frac{\sqrt5-1}{2}.
$$

In the silent duel, there is no reassuring sound. You can never condition on knowing that the opponent is unarmed. A known firing time becomes exploitable: the opponent can move an instant before it. Therefore the objective changes from choosing the perfect time to concealing the time through a carefully calibrated probability distribution.

That is why the two games, despite sharing the same archers and the same accuracy functions, have fundamentally different equilibrium structures:

$$
\boxed{\text{Noise permits reaction; silence forces randomization}.}
$$
