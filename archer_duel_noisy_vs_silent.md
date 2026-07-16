# The Archer's Dilemma: Noisy and Silent Probability Duels

This chapter studies a one-shot duel in which information—not marksmanship alone—changes the strategic answer. The same two archers, the same accuracy functions, and even the same golden-ratio threshold appear in both versions. Yet one version admits a natural threshold strategy, while the other drives the archers into a mixed-strategy preemption race.

The goal is to tell that story intuitively and then make every step mathematically precise.

## 1. The road narrows

Imagine two archers at opposite ends of a long road. Each has exactly one arrow. They walk toward one another at the same known speed, and each may fire at any moment.

Let $x\in[0,1]$ measure the remaining normalized distance:

| Position | Interpretation |
|---|---|
| $x=1$ | The duel begins; the archers are far apart. |
| $x=0$ | They have reached point-blank range. |

Time therefore moves in the direction

$$
x:1\longrightarrow 0.
$$

This orientation is easy to reverse accidentally:

> A larger firing coordinate means an earlier shot. Thus $x_1>x_2$ means Archer 1 shoots before Archer 2.

Their probabilities of hitting at coordinate $x$ are

$$
p_1(x)=1-x,
\qquad
p_2(x)=1-x^2.
$$

Their miss probabilities are

$$
q_1(x)=1-p_1(x)=x,
\qquad
q_2(x)=1-p_2(x)=x^2.
$$

Both become more accurate as $x$ falls. Archer 2 is the better shot at every interior point because

$$
p_2(x)-p_1(x)=x(1-x)>0
\qquad (0<x<1).
$$

We use the following basic outcome convention:

- a hit eliminates the opponent;
- an archer can fire at most once;
- a player values the probability of being the sole winner;
- if both archers survive after using their arrows, the result is a draw;
- the two hit events are independent if shots are simultaneous.

The important difference between the two games is what a miss reveals.

### Noisy duel

Every shot is heard. If an archer misses, the opponent immediately knows that the archer is now unarmed and can change plans.

### Silent duel

A missed shot is completely unobservable. The opponent neither hears the release nor sees evidence that the arrow has been spent. Unless someone is hit, each archer must continue according to a plan chosen in advance.

This single informational change alters the meaning of a strategy:

- in the noisy duel, a strategy is a contingent rule—when to shoot while both are armed and what to do after hearing a miss;
- in the silent duel, a strategy is a precommitted firing point or, in equilibrium, a probability distribution over firing points.

## 2. The noisy duel: a miss becomes a message

### 2.1 The story

Suppose Archer 1 fires first at coordinate $x$.

If the arrow hits, Archer 1 wins. If it misses, the sound of the shot tells Archer 2 three things at once:

1. Archer 1 fired.
2. Archer 1 missed.
3. Archer 1 has no arrow left.

Archer 2 no longer needs to take a risky shot. He can lower his bow, continue walking, and wait until $x=0$, where his hit probability is one.

The first miss is therefore not merely a failed attack. It is a confession: “I am unarmed.” That is why the first shooter's probability of winning is just the probability that the first shot hits.

### 2.2 Payoffs when one player fires first

Let $x_i$ denote Archer $i$'s intended firing point while both archers remain armed.

If $x_1>x_2$, Archer 1 fires first. Archer 1 wins with probability $p_1(x_1)$. If he misses, Archer 2 hears the miss and later wins with certainty. Hence

$$
U_1^{N}(x_1,x_2)=p_1(x_1)=1-x_1,
$$

$$
U_2^{N}(x_1,x_2)=q_1(x_1)=x_1.
$$

If $x_2>x_1$, Archer 2 fires first, so

$$
U_1^{N}(x_1,x_2)=q_2(x_2)=x_2^2,
$$

$$
U_2^{N}(x_1,x_2)=p_2(x_2)=1-x_2^2.
$$

Away from a simultaneous shot, the noisy-duel payoffs are therefore

$$
U_1^{N}(x_1,x_2)=
\begin{cases}
1-x_1, & x_1>x_2,\\
x_2^2, & x_2>x_1,
\end{cases}
$$

and

$$
U_2^{N}(x_1,x_2)=
\begin{cases}
x_1, & x_1>x_2,\\
1-x_2^2, & x_2>x_1.
\end{cases}
$$

Notice what is absent: the second player's originally planned accuracy. After hearing a miss, that player abandons the old plan and waits for a certain shot at $x=0$.

### 2.3 The invisible line on the road

At some candidate coordinate $x$, Archer 1 compares two possibilities:

- fire first and win with probability $p_1(x)=1-x$;
- let Archer 2 fire first and win if Archer 2 misses, with probability $q_2(x)=x^2$.

Archer 1 is indifferent when

$$
1-x=x^2.
$$

Archer 2 makes the parallel comparison:

- fire first and win with probability $p_2(x)=1-x^2$;
- let Archer 1 fire first and win if Archer 1 misses, with probability $q_1(x)=x$.

Archer 2 is indifferent when

$$
1-x^2=x.
$$

These are the same equation:

$$
x^2+x-1=0.
$$

The feasible root is

$$
r=\frac{\sqrt{5}-1}{2}\approx 0.618034.
$$

It satisfies

$$
1-r=r^2,
\qquad
1-r^2=r.
$$

Thus

$$
p_1(r)=q_2(r)=r^2\approx0.381966,
$$

$$
p_2(r)=q_1(r)=r\approx0.618034.
$$

The road now has an invisible strategic line:

- when $x>r$, the archers are still relatively far apart, and each prefers that the other waste the first arrow;
- when $x<r$, they are close enough that each prefers to shoot before the other.

Indeed, for $x>r$,

$$
p_1(x)<q_2(x),
\qquad
p_2(x)<q_1(x),
$$

whereas both inequalities reverse for $x<r$.

### 2.4 A natural noisy-duel equilibrium

An exact equilibrium at a common deterministic firing point requires a rule for what happens when both archers try to act at the same instant. A standard noisy-duel convention is sequential priority at a tie: a fair random device selects one archer to act first, and if that shot misses, the other hears it and may revise the plan.

Under that convention, the following is a (weak) Nash equilibrium:

1. while both archers are armed, wait until $x=r$;
2. at $r$, use the priority rule to determine who fires first;
3. if that shot misses, the armed archer waits until $x=0$ and then fires.

Why does no one deviate?

- Shooting earlier means choosing $x>r$. Accuracy is then lower, and $p_i(x)<p_i(r)$.
- Waiting beyond $r$ lets the opponent fire first. The player's probability of winning is then the opponent's miss probability at $r$, which equals the player's equilibrium value.
- At $r$, being selected as the first or second mover gives the same value because $p_1(r)=q_2(r)$ and $p_2(r)=q_1(r)$.

The equilibrium win probabilities are

$$
V_1^N=r^2\approx0.381966,
\qquad
V_2^N=r\approx0.618034.
$$

They add to one because, under this strategy, a first miss is followed by a certain point-blank hit.

### 2.5 Why the tie convention must be stated

Suppose instead that both archers literally fire simultaneously at $r$, the two hit events are independent, and a player wins only by hitting while the opponent misses. Then

$$
U_1^N(r,r)=p_1(r)q_2(r)=r^4,
$$

$$
U_2^N(r,r)=p_2(r)q_1(r)=r^2.
$$

Either player can improve by firing an instant earlier. For example,

$$
U_1^N(r+\varepsilon,r)
=1-r-\varepsilon
=r^2-\varepsilon
>r^4
$$

for sufficiently small $\varepsilon>0$.

Thus $r$ is always the important noisy-duel threshold, but the statement “both shoot at $r$” is an exact pure equilibrium only after the simultaneous-action rule is specified appropriately. Under literal simultaneous independent fire, one needs an equilibrium refinement, timing randomization, or an $\varepsilon$-equilibrium interpretation.

This is not a technical footnote to ignore: discontinuous timing games are often decided precisely by what happens at a tie.

## 3. The silent duel: the forest swallows the sound

### 3.1 The story

Now imagine that the bowstring, arrow, and impact make no sound at all. A missed arrow vanishes into the darkness.

Before the duel, Archer 1 privately writes a firing point $x_1$ on a slip of paper. Archer 2 privately writes $x_2$. Each promises to fire when the shrinking distance reaches the chosen number.

Suppose Archer 2 chose the larger coordinate and therefore fires first. If Archer 2 hits, the duel ends. If Archer 2 misses, Archer 1 receives no message. Archer 1 keeps walking and fires only when the distance reaches the preselected $x_1$.

Archer 1 must therefore survive Archer 2's shot and then hit with his own:

$$
\Pr(\text{Archer 1 wins})
=
\Pr(\text{Archer 2 misses})
\Pr(\text{Archer 1 hits}).
$$

The multiplication is the signature of the silent duel. The second archer cannot hear a miss and replace the original plan with a point-blank shot.

### 3.2 Pure-strategy payoff functions

If $x_1>x_2$, Archer 1 fires first. He wins if his shot hits:

$$
U_1^S(x_1,x_2)=p_1(x_1)=1-x_1.
$$

Archer 2 wins only if Archer 1 misses and Archer 2 later hits:

$$
U_2^S(x_1,x_2)
=q_1(x_1)p_2(x_2)
=x_1(1-x_2^2).
$$

Both miss with probability

$$
q_1(x_1)q_2(x_2)=x_1x_2^2.
$$

If $x_2>x_1$, Archer 2 fires first. Then

$$
U_1^S(x_1,x_2)
=q_2(x_2)p_1(x_1)
=x_2^2(1-x_1),
$$

$$
U_2^S(x_1,x_2)
=p_2(x_2)
=1-x_2^2,
$$

and both miss with probability $x_2^2x_1$.

Consequently,

$$
U_1^S(x_1,x_2)=
\begin{cases}
1-x_1, & x_1>x_2,\\
x_2^2(1-x_1), & x_2>x_1,
\end{cases}
$$

and

$$
U_2^S(x_1,x_2)=
\begin{cases}
x_1(1-x_2^2), & x_1>x_2,\\
1-x_2^2, & x_2>x_1.
\end{cases}
$$

These expressions differ fundamentally from the noisy payoffs. If Archer 2 fires first and misses, for example, Archer 1's silent-duel payoff is

$$
q_2(x_2)p_1(x_1),
$$

not merely $q_2(x_2)$. Archer 1 still has to arrive at the precommitted point and make the planned shot.

If both fire simultaneously at $x$, our sole-winner convention gives

$$
U_1^S(x,x)=p_1(x)q_2(x),
\qquad
U_2^S(x,x)=p_2(x)q_1(x).
$$

### 3.3 Why the same golden-ratio threshold appears

Suppose Archer 2 has announced a deterministic point $x_2>0$. Archer 1 has two strategically relevant responses.

#### Response A: fire just before Archer 2

Archer 1 chooses

$$
x_1=x_2+\varepsilon,
\qquad \varepsilon>0.
$$

He fires first, and as $\varepsilon\downarrow0$, his payoff approaches

$$
\lim_{\varepsilon\downarrow0}
\left[1-(x_2+\varepsilon)\right]
=1-x_2.
$$

#### Response B: deliberately go second

If $x_1<x_2$, Archer 1's payoff is

$$
x_2^2(1-x_1).
$$

Once he has decided to go second, he should maximize the accuracy of the planned second shot by choosing $x_1=0$. His payoff then becomes

$$
x_2^2.
$$

Archer 1 therefore compares

$$
\underbrace{1-x_2}_{\text{preempt Archer 2}}
\quad\text{with}\quad
\underbrace{x_2^2}_{\text{commit to point blank}}.
$$

He is indifferent when

$$
1-x_2=x_2^2.
$$

Likewise, Archer 2 compares $1-x_1^2$ with $x_1$, producing

$$
1-x_1^2=x_1.
$$

The same number

$$
r=\frac{\sqrt5-1}{2}
$$

appears again.

But the stories behind the same equation are different:

- noisy duel: “I will hear your miss and then change my behavior.”
- silent duel: “I cannot hear your miss, so I commit in advance to a point-blank second shot.”

The optimized comparison happens to be the same. The games and their general payoff functions are not.

## 4. Why $(r,r)$ is not a silent-duel equilibrium

### 4.1 Archer 1 moves one heartbeat earlier

Imagine that both slips of paper say $r$. Archer 1's hit probability is

$$
p_1(r)=1-r=r^2,
$$

and Archer 2's miss probability is

$$
q_2(r)=r^2.
$$

Under simultaneous independent fire, Archer 1 is the sole winner only if he hits and Archer 2 misses:

$$
U_1^S(r,r)=r^2\cdot r^2=r^4\approx0.145898.
$$

Archer 1 now thinks:

> Why shoot exactly with Archer 2? I can fire one heartbeat earlier and sacrifice almost no accuracy.

He replaces $r$ with $r+\varepsilon$. Because a larger coordinate occurs earlier, Archer 1 now fires first. His payoff is

$$
U_1^S(r+\varepsilon,r)
=1-r-\varepsilon
=r^2-\varepsilon.
$$

For sufficiently small $\varepsilon$,

$$
r^2-\varepsilon>r^4.
$$

The tiny loss in accuracy buys a large strategic gain: a successful first shot prevents Archer 2 from firing at all.

Archer 2 sees the same opportunity. At $(r,r)$,

$$
U_2^S(r,r)=p_2(r)q_1(r)=r^2.
$$

By choosing $r+\varepsilon$, Archer 2 fires first and obtains

$$
1-(r+\varepsilon)^2
\longrightarrow
1-r^2=r
>r^2.
$$

So neither player is willing to remain at the deterministic point $r$.

### 4.2 The preemption race

The story then accelerates:

- Archer 1 plans $r+\varepsilon$.
- Archer 2 plans $r+2\varepsilon$, one instant earlier.
- Archer 1 responds with $r+3\varepsilon$.
- Archer 2 wants $r+4\varepsilon$.

Every known firing point can be preempted at an arbitrarily small accuracy cost.

Why not end the race by firing extremely early? Because far away, accuracy is nearly zero. An archer who fires too early is likely to miss, allowing the opponent's later planned shot to decide the duel. Each player is trapped between two dangers:

- wait too long and risk being preempted;
- shoot too early and waste the only arrow.

There is no stable, predictable time that balances these dangers.

### 4.3 A short proof that no pure equilibrium exists

The argument is not special to $(r,r)$.

Suppose $x_1>x_2$, so Archer 1 fires first. Archer 1 can choose a point $x_1'$ satisfying

$$
x_2<x_1'<x_1.
$$

He still fires first, but he is closer and therefore more accurate:

$$
p_1(x_1')>p_1(x_1).
$$

Thus no unequal pair with Archer 1 first can be an equilibrium. The symmetric argument eliminates every unequal pair with Archer 2 first.

At an equal interior point $0<x<1$, either archer can move to $x+\varepsilon$ and preempt. At $(0,0)$, both hit simultaneously and neither is the sole winner, while a small positive firing coordinate gives a positive chance of winning first. At $(1,1)$, both miss with certainty, so either archer can instead plan a later shot at some $x<1$ and obtain a positive winning probability after the opponent's certain miss. Hence the silent duel has no pure-strategy Nash equilibrium under the stated convention.

## 5. The silent mixed strategy: make the shot unpredictable

### 5.1 The story

The archers stop writing a fixed number on their slips.

Instead, Archer 1 privately draws $X_1$ from a probability distribution, and Archer 2 privately draws $X_2$ from another distribution. Neither knows the other's realized number.

Now “shoot one heartbeat before the opponent” is no longer a usable plan. There is no known heartbeat to preempt.

An earlier draw gives a better chance of firing first but lower accuracy. A later draw gives greater accuracy but a growing chance that the opponent will already have fired. In equilibrium, these forces balance so precisely that every firing point used with positive probability gives the same expected payoff.

Randomization does not improve either archer's aim. It removes exploitable predictability.

### 5.2 Expected payoff against a distribution

Let

$$
F_i(x)=\Pr(X_i\le x)
$$

be Archer $i$'s cumulative distribution of firing coordinates. Remember that $X_i\le x$ means Archer $i$ plans to fire at $x$ or later in time, because smaller coordinates occur later.

Suppose the positive part of each distribution has support $(0,a]$, where $a$ is the largest coordinate and therefore the earliest possible equilibrium shot.

If Archer 1 chooses a particular $x>0$, his expected payoff against $F_2$ is

$$
U_1(x)
=p_1(x)
\left[
F_2(x)
+
\int_{(x,a]}q_2(y)\,dF_2(y)
\right].
$$

The terms inside the brackets have direct interpretations:

- $F_2(x)$: Archer 2 draws $X_2\le x$, so Archer 1 fires first;
- $y>x$: Archer 2 fires first at $y$, and Archer 1 gets to use his planned shot only if Archer 2 misses, which occurs with probability $q_2(y)$.

Similarly,

$$
U_2(x)
=p_2(x)
\left[
F_1(x)
+
\int_{(x,a]}q_1(y)\,dF_1(y)
\right].
$$

In equilibrium,

$$
U_1(x)=V_1,
\qquad
U_2(x)=V_2
$$

at every positive coordinate in the support.

### 5.3 Deriving the equilibrium densities

Let $f_i$ denote the continuous density of $F_i$ on $(0,a)$. Define

$$
H_2(x)
=F_2(x)+\int_{(x,a]}q_2(y)\,dF_2(y).
$$

For an interior point,

$$
H_2'(x)
=f_2(x)-q_2(x)f_2(x)
=p_2(x)f_2(x).
$$

Because $U_1(x)=p_1(x)H_2(x)=V_1$, differentiating the indifference condition gives

$$
0=p_1'(x)H_2(x)+p_1(x)p_2(x)f_2(x).
$$

Using $H_2(x)=V_1/p_1(x)$,

$$
f_2(x)
=-\frac{V_1p_1'(x)}
{p_1(x)^2p_2(x)}.
$$

The same argument with the players reversed gives

$$
f_1(x)
=-\frac{V_2p_2'(x)}
{p_2(x)^2p_1(x)}.
$$

For the present accuracy functions,

$$
\boxed{
f_2(x)
=\frac{V_1}
{(1-x)^2(1-x^2)}
}
$$

and

$$
\boxed{
f_1(x)
=\frac{2xV_2}
{(1-x^2)^2(1-x)}
}.
$$

At the upper endpoint $a$, an archer choosing $a$ fires before almost every opponent draw. Therefore

$$
V_1=p_1(a)=1-a,
\qquad
V_2=p_2(a)=1-a^2.
$$

No player can place an atom at a positive coordinate: the opponent could move to $x+\varepsilon$, preempt that mass, and lose only an arbitrarily small amount of accuracy.

At most one player can have an atom at $x=0$. Solving the normalization conditions gives the feasible case in which Archer 1 has no atom. Thus $a$ is determined by

$$
1
=\int_0^a f_1(x)\,dx
=(1-a^2)
\int_0^a
\frac{2x}
{(1-x^2)^2(1-x)}
\,dx.
$$

Numerically,

$$
a\approx0.677688656.
$$

Using this value,

$$
V_1=1-a\approx0.322311344,
$$

$$
V_2=1-a^2\approx0.540738086.
$$

Archer 2's continuous density integrates to less than one:

$$
\int_0^a f_2(x)\,dx
\approx0.930954653.
$$

The remaining probability is an atom at point blank:

$$
m_2
=1-\int_0^a f_2(x)\,dx
\approx0.069045347.
$$

The equilibrium distributions can therefore be written as

$$
F_1(x)=\int_0^x f_1(t)\,dt,
\qquad 0<x\le a,
$$

and

$$
F_2(x)=m_2+\int_0^x f_2(t)\,dt,
\qquad 0<x\le a.
$$

Archer 1 continuously randomizes over $(0,a]$. Archer 2 uses the same positive support but, with probability about $6.9\%$, commits to waiting all the way to $x=0$.

### 5.4 What the numbers mean

| Equilibrium quantity | Value |
|---|---:|
| Earliest possible shot, $a$ | $0.677688656$ |
| Archer 1 sole-win probability, $V_1$ | $0.322311344$ |
| Archer 2 sole-win probability, $V_2$ | $0.540738086$ |
| Archer 2 atom at $x=0$ | $0.069045347$ |
| Draw probability, $1-V_1-V_2$ | $0.136950570$ |

Several points are worth emphasizing:

1. Since larger $x$ occurs earlier, $a$ is the earliest firing coordinate, not the latest.
2. Neither archer fires while $x>a$; at those distances the accuracy cost is too high.
3. Every positive point in $(0,a]$ gives the corresponding player exactly $V_i$. If one point gave more, the player would concentrate there; if it gave less, the player would remove it from the support.
4. Archer 2's point-blank atom is not an extra assumption. It is the probability mass left over when the continuous density is normalized.
5. Positive-coordinate ties occur with probability zero because the positive parts of both strategies are continuous.

The equilibrium also passes the outside-support check. If a player chooses $x>a$, that player certainly fires first but receives

$$
p_i(x)<p_i(a)=V_i.
$$

Archer 2 is indifferent between the continuous support and the atom at $0$. Archer 1 does not use $0$: doing so would risk meeting Archer 2's point-blank atom, whereas firing at an arbitrarily small positive coordinate preempts that atom with almost perfect accuracy.

## 6. What changed when the sound disappeared?

| Feature | Noisy duel | Silent duel |
|---|---|---|
| Is a miss observed? | Yes | No |
| Meaning of a strategy | A contingent action rule | A precommitted point or distribution |
| If the opponent fires first and misses | Change plans and wait until $x=0$ | Continue to the already chosen firing point |
| Follower payoff after a shot at $y$ | $q_j(y)$ | $q_j(y)p_i(x_i)$ |
| Role of $r\approx0.618$ | Boundary between waiting and preemption | Best-response indifference threshold |
| Equilibrium form under the conventions above | Natural pure threshold with sequential priority | Mixed timing strategy |

The same equation,

$$
1-x=x^2,
$$

appears in both games because a silent player who deliberately chooses to go second can precommit to $x=0$, reproducing the same optimized payoff that a noisy player obtains by reacting after hearing a miss.

But equal threshold equations do not imply equal games. In the noisy duel, the sound creates a new decision node after a miss. In the silent duel, that decision node does not exist. The player must encode every future action in the original plan.

## 7. Common mistakes

### Mistake 1: treating larger $x$ as later

The distance is shrinking. Therefore $r+\varepsilon$ is reached before $r$, not after it.

### Mistake 2: using the noisy payoff in the silent game

If Archer 2 silently misses at $x_2$, Archer 1 does not automatically win. Archer 1 must still hit at the preselected $x_1$, so the payoff contains the product

$$
q_2(x_2)p_1(x_1).
$$

### Mistake 3: calling $r$ an equilibrium merely because both players are indifferent there

Indifference identifies a threshold. Nash equilibrium additionally requires checking deviations and specifying what happens at simultaneous actions. The $\varepsilon$-test exposes the silent game's preemption incentive.

### Mistake 4: thinking randomization is indecision

The mixed strategy is deliberate. It makes every firing point in the support equally good and prevents the opponent from targeting a predictable time.

### Mistake 5: forgetting the possibility of a draw

In the silent game, the first shooter can miss and the second shooter can also miss. Consequently, the two sole-win probabilities need not sum to one.

## 8. Final picture

In the noisy duel, the arrow carries two things: a chance to hit and, if it misses, information. The sound tells the survivor when it is safe to wait. The golden-ratio coordinate $r$ marks the point where each archer is exactly indifferent between taking the first shot and gambling on the opponent's miss.

In the silent duel, a miss carries no message. The archers must choose their future actions before knowing whether the other arrow has already been spent. A deterministic firing point can always be preempted by moving an instant earlier, but firing too early destroys accuracy. The only stable resolution is to hide the firing point inside a probability distribution.

The larger lesson extends well beyond archery:

> Information changes not only what a player knows, but what a strategy is allowed to be.

The noisy player may condition on an observed event. The silent player must commit. That difference turns a threshold problem into a mixed-strategy timing game.
