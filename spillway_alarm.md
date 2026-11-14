# The Spillway Alarm

**The blackout game has two pure equilibria and one mixed equilibrium. The open-radio game has more equilibria.**

In the radio equilibrium with no point masses, the valley is safe with probability $3/4$. In the blackout mixed equilibrium, that probability is $5/6$.

Both give the same expected payoffs:

```math
\boxed{(U_1,U_2)=\left(\frac23,\frac12\right).}
```

However, the radio game also permits an initial launch chance. Those equilibria can give greater safety.

I will explain the simple cases first. Then I will give the complete equilibrium list and prove that it is complete.

Throughout, “equilibrium” means **Nash equilibrium in independent deadline or timer strategies**. Neither station can improve its expected payoff by changing its strategy alone.

---

## 1. The story: who will pay to save the valley?

Picture two operators beside their launch controls.

One drone can save the entire valley. Station 1 pays $1/3$ if its drone executes. Station 2 pays $1/2$.

The valley manager wants station 1 to launch at once. This gives certain protection at the lower cost.

Each operator has a different private preference. Each wants protection without paying for a launch.

With an open radio, an operator can wait for the other station. A rival launch gives free protection and permits cancellation. However, the flood can arrive during the wait.

During blackout, the timer cannot change. If one drone saves the valley, every other finite timer still executes. A late drone can therefore add cost without adding protection.

**This difference makes delay useful in the radio game. It removes that benefit from delay in the blackout game.**

### The payoff measure

Let $L_i$ be the event that station $i$’s drone executes. Then

```math
U_i
=
\Pr(\text{valley is protected})
-
c_i\Pr(L_i).
```

Let $W$ be the sum of both expected payoffs:

```math
W=U_1+U_2.
```

I will call $W$ **total welfare**.

### Why time $1$ needs special care

In the radio game, deadline $1$ and never launching give the same payoff.

If a rival launches earlier, the station cancels. Otherwise, the flood arrives before time $1$, with probability one.

In blackout, these actions differ. Suppose the rival launches at zero:

- A timer at $1$ later executes and pays its cost.

- A timer at $\infty$ never executes and pays no cost.

Thus, $1$ cannot replace $\infty$ in the blackout analysis.

---

## 2. Blackout: every finite equilibrium timer must be zero

This version has the simpler solution.

### 2.1 The payoff from a finite timer

Suppose station $i$ chooses a finite timer $x$. Let $Y$ be the rival’s timer.

Use the convention

```math
\min(x,\infty)=x.
```

The valley is protected exactly when

```math
T>\min(x,Y).
```

If protection occurs, station $i$’s finite timer executes. This is true even when the rival launches first.

Therefore,

```math
\boxed{
u_i(x;Y)
=
(1-c_i)\,
\mathbb E\!\left[1-\min(x,Y)\right].
}
```

The expectation is over the rival’s timer. The term $1-\min(x,Y)$ already includes the flood probability.

At $x=0$,

```math
u_i(0;Y)=1-c_i.
```

For any $x>0$,

```math
u_i(0;Y)-u_i(x;Y)
=
(1-c_i)\mathbb E[\min(x,Y)].
```

This difference is positive whenever $\Pr(Y>0)>0$.

There is one exceptional case. If $Y=0$ with certainty, every finite timer gives $1-c_i$. But never launching then gives $1$.

Thus, a positive finite timer is never a best response.

```math
\boxed{
\text{Every blackout equilibrium uses only }0\text{ and }\infty.
}
```

This result includes timer $1$.

### 2.2 The reduced game

The entire blackout game now becomes a two-action game.

Each matrix entry gives $(U_1,U_2)$.

| Station 1’s choice | Station 2: launch at $0$ | Station 2: never launch |
| --- | --- | --- |
| **Launch at $0$** | $\left(\frac23,\frac12\right)$ | $\left(\frac23,1\right)$ |
| **Never launch** | $\left(1,\frac12\right)$ | $(0,0)$ |

If both launch, both pay. If neither launches, the valley is lost.

### 2.3 The pure equilibria

The two pure equilibria are

```math
\boxed{(X_1,X_2)=(0,\infty)}
```

and

```math
\boxed{(X_1,X_2)=(\infty,0).}
```

If the rival never launches, an immediate launch is best.

If the rival launches immediately, never launching is best.

The outcomes are:

| Immediate launcher | Safety probability | Payoffs | Total welfare |
| --- | --- | --- | --- |
| Station 1 | $1$ | $\left(\frac23,1\right)$ | $\frac53$ |
| Station 2 | $1$ | $\left(1,\frac12\right)$ | $\frac32$ |

### 2.4 The unique mixed equilibrium

Let

```math
q_i=\Pr(X_i=0).
```

The remaining probability is at $\infty$.

Station 1 gets $2/3$ from launching. It gets $q_2$ from never launching.

For station 1 to randomize, these payoffs must be equal:

```math
q_2=\frac23.
```

Station 2 gets $1/2$ from launching. It gets $q_1$ from never launching.

Thus,

```math
q_1=\frac12.
```

The mixed equilibrium is therefore

```math
\boxed{
X_1=
\begin{cases}
0,&\text{with probability }1/2,\\
\infty,&\text{with probability }1/2,
\end{cases}
}
```

```math
\boxed{
X_2=
\begin{cases}
0,&\text{with probability }2/3,\\
\infty,&\text{with probability }1/3.
\end{cases}
}
```

There are no other blackout equilibria. The reduced matrix has only these two pure equilibria and this mixed equilibrium.

### 2.5 The mixed outcome

The independent choices give four possible events:

| Event | Probability |
| --- | --- |
| Only station 1 launches | $\frac12\cdot\frac13=\frac16$ |
| Only station 2 launches | $\frac12\cdot\frac23=\frac13$ |
| Both launch | $\frac12\cdot\frac23=\frac13$ |
| Neither launches | $\frac12\cdot\frac13=\frac16$ |

Hence,

```math
\Pr(\text{protection})=1-\frac16=\boxed{\frac56}.
```

Expected total cost is

```math
C_{\mathrm{blackout}}
=
\frac13\cdot\frac12
+
\frac12\cdot\frac23
=
\boxed{\frac12}.
```

The expected payoffs are

```math
U_1=\frac56-\frac16=\frac23,
\qquad
U_2=\frac56-\frac13=\frac12.
```

Therefore,

```math
\boxed{W_{\mathrm{blackout}}=\frac76.}
```

Failure has a clear cause here. Both stations choose never to launch.

---

## 3. Open radio: the complete pure equilibrium list

With a radio, the later station cancels. This creates more pure equilibria than the blackout game permits.

### 3.1 Someone must launch at zero

Suppose one station launches first at a positive time.

It can improve by moving its launch to zero. This removes the chance that the flood arrives before its launch.

An exact simultaneous launch before time $1$ also fails the equilibrium test. Either station can wait slightly longer and avoid its cost.

Thus, every pure equilibrium has exactly one immediate launcher.

### 3.2 How late must the other deadline be?

Suppose station $i$ launches at zero. The rival has a positive deadline $y$.

Launching at zero gives station $i$

```math
1-c_i.
```

Waiting for the rival gives it

```math
1-y.
```

An earlier positive launch cannot improve on a launch at zero. Thus, zero is optimal exactly when

```math
1-c_i\ge 1-y,
```

or

```math
y\ge c_i.
```

Never launching also satisfies the required condition.

The complete pure equilibrium list is

```math
\boxed{
(X_1,X_2)=(0,y),
\qquad
y\in\left[\frac13,1\right]\cup\{\infty\},
}
```

and

```math
\boxed{
(X_1,X_2)=(x,0),
\qquad
x\in\left[\frac12,1\right]\cup\{\infty\}.
}
```

The threshold uses the cost of the **immediate launcher**.

For example, $(0,1/4)$ is not an equilibrium. Station 1 would prefer to wait for station 2:

```math
1-\frac14=\frac34>\frac23.
```

But $(0,1/2)$ is an equilibrium.

All these pure equilibria give certain protection. Their payoffs equal the corresponding pure blackout payoffs.

The later radio deadline never executes.

---

## 4. Open radio: the equilibrium with no point masses

We now allow both stations to select random deadlines.

An **atom** means positive probability at one exact time. First, consider distributions with no atoms.

### 4.1 The balance between waiting and launching

Let

```math
S_i(t)=\Pr(X_i>t)
```

be station $i$’s deadline survival function.

Let $f_i(t)$ be its density. Define its conditional launch rate by

```math
h_i(t)=\frac{f_i(t)}{S_i(t)}.
```

This is also called its **hazard rate**. It measures the launch chance per unit time, given no earlier launch.

Conditional on no flood by $t$, the flood rate is

```math
h_T(t)=\frac{1}{1-t}.
```

Now consider a station that has not launched.

A short wait has two main effects:

- If the rival launches, the station saves its cost $c_i$.

- If the flood arrives, the station loses the net value $1-c_i$.

For the station to randomize over nearby deadlines, these effects must balance:

```math
c_i h_j(t)
=
\frac{1-c_i}{1-t}.
```

Thus,

```math
h_j(t)
=
\frac{1-c_i}{c_i(1-t)}.
```

Substitution gives

```math
\boxed{h_1(t)=\frac{1}{1-t}},
\qquad
\boxed{h_2(t)=\frac{2}{1-t}}.
```

**Each station’s launch rate must keep the other station willing to wait.**

This explains an apparent surprise. The more costly station has the greater launch rate.

### 4.2 Derive the distributions

A survival function satisfies

```math
\frac{d}{dt}\log S_i(t)=-h_i(t).
```

With no atom at zero, $S_i(0)=1$. Integration gives

```math
S_1(t)=1-t,
\qquad
S_2(t)=(1-t)^2.
```

Therefore,

```math
\boxed{F_1(t)=t},
\qquad
\boxed{F_2(t)=2t-t^2},
\qquad 0\le t\le1.
```

Station 1 chooses a uniform deadline. Station 2 has density

```math
f_2(t)=2(1-t),
```

which puts more probability on early deadlines.

Neither station puts probability at $1$ or $\infty$.

### 4.3 Check every possible deviation

The local balance equation suggests an equilibrium. A full check must also cover distant deadlines and never launching.

Against a rival with a continuous distribution, deadline $t$ gives

```math
U_i(t)
=
\int_0^t(1-s)f_j(s)\,ds
+
(1-c_i)(1-t)S_j(t).
```

The first term covers a rival launch before $t$. The second covers the station’s own launch at $t$.

Differentiation gives

```math
U_i'(t)
=
c_i(1-t)f_j(t)
-
(1-c_i)S_j(t).
```

The proposed distributions make this derivative zero everywhere on $(0,1)$.

Thus, every deadline gives the same payoff as zero:

```math
U_1(t)=\frac23,
\qquad
U_2(t)=\frac12.
```

The payoff from never launching is the same limiting value.

No unilateral deviation can improve either payoff. This proves that the distributions form an equilibrium.

Never launching is an individual best response to these distributions. However, adding probability at infinity changes the rival’s incentives. It does not produce another equilibrium of this form.

---

## 5. Open radio: all the other mixed equilibria

The preceding equilibrium is the unique one with no atoms. It is not the only mixed equilibrium.

There are two further features to include.

### 5.1 One station can have an atom at zero

Let

```math
p_i=\Pr(X_i=0).
```

Suppose neither station launches at zero with certainty. Then the complete family is

```math
\boxed{
\begin{aligned}
\Pr(X_1>t)&=(1-p_1)(1-t),\\
\Pr(X_2>t)&=(1-p_2)(1-t)^2,
\end{aligned}
\qquad 0\le t\lt 1,
}
```

where

```math
\boxed{
0\le p_1,p_2\lt 1,
\qquad
p_1p_2=0.
}
```

There is no mass at any positive exact time, at $1$, or at $\infty$.

Conditional on no initial launch, each station uses its previous continuous deadline law.

The restriction $p_1p_2=0$ is essential. Both stations cannot have an atom at zero.

If the rival has an initial atom, a small positive deadline is better than zero. It avoids the tie cost when the rival launches immediately. The added flood risk tends to zero with the delay.

Therefore, at most one station can use an initial atom.

#### Why an atom for one station works

Suppose $p_1>0$ and $p_2=0$.

Station 2’s distribution remains unchanged. Station 1 is therefore indifferent among all its deadlines, including zero.

Station 2 prefers a positive deadline to zero. With probability $p_1$, it receives free protection immediately. Otherwise, it faces the original continuous game.

Thus,

```math
U_2
=
p_1+(1-p_1)\frac12
=
\frac12+\frac{p_1}{2}.
```

Station 1 still receives $2/3$.

The other branch works in the same way. In general,

```math
\boxed{
U_1=\frac23+\frac{p_2}{3},
\qquad
U_2=\frac12+\frac{p_1}{2}.
}
```

An initial launch chance raises the rival’s payoff. The station with that chance keeps its original payoff.

### 5.2 A sure immediate launcher permits many standby mixtures

There is another class of mixed strategies.

Suppose station $i$ launches at zero with certainty. The rival can randomize over positive deadlines and infinity.

Every such rival deadline cancels after the immediate launch. The rival therefore receives payoff $1$.

However, the rival’s distribution must still keep station $i$ willing to launch at zero.

Here is the exact condition.

Let $Y$ be the rival’s deadline, with

```math
\Pr(Y=0)=0,
```

and define

```math
S(t)=\Pr(Y>t).
```

Then the strategy pair is an equilibrium if and only if

```math
\boxed{
\int_0^t S(s)\,ds
+
c_i(1-t)S(t)
\ge c_i
\quad
\text{for every }0\le t\le1.
}
\tag{*}
```

This condition describes **all** such standby mixtures.

#### What the condition means

The limiting payoff from launching just after $t$ is

```math
1-\int_0^t S(s)\,ds-c_i(1-t)S(t).
```

The integral is the limiting failure probability. The last term is the expected launch cost.

Condition $(*)$ says that this payoff cannot exceed $1-c_i$.

The phrase “just after” matters when the rival has an atom. An exact tie can only reduce the payoff through an added cost.

For a pure rival deadline $y$, condition $(*)$ reduces to

```math
y\ge c_i.
```

This recovers the pure equilibrium list.

A mixed standby distribution can also include deadlines below $c_i$. Those early deadlines must have sufficiently little probability.

For example, let station 1 launch at zero. Let station 2 choose $1/4$ or $\infty$, each with probability $1/2$.

Station 1’s limiting payoff from waiting just after $1/4$ is

```math
\frac12\cdot\frac34
+
\frac12\cdot\frac23\cdot\frac34
=
\frac58
\lt
\frac23.
```

Earlier positive launches and later deadlines also give less than $2/3$. Thus, this is an equilibrium.

This example shows why a complete list needs condition $(*)$. A rule that bans every standby deadline below $c_i$ would miss equilibria.

All these standby mixtures produce certain protection and one immediate execution.

---

## 6. Compare the outcomes

### 6.1 Radio outcomes for the full mixed family

Define

```math
A=(1-p_1)(1-p_2).
```

Because $p_1p_2=0$,

```math
A=1-p_1-p_2.
```

The flood wins when it arrives before both deadlines. Independence gives

```math
\begin{aligned}
\Pr(\text{flood first})
&=\int_0^1 S_1(t)S_2(t)\,dt\\
&=A\int_0^1(1-t)^3\,dt\\
&=\frac A4.
\end{aligned}
```

Therefore,

```math
\boxed{\Pr(\text{protection})=1-\frac A4.}
```

The execution probabilities are

```math
\boxed{
\Pr(L_1)=p_1+\frac A4,
\qquad
\Pr(L_2)=p_2+\frac A2.
}
```

No two drones execute together with positive probability. The rival cancels after the first launch.

Expected total cost is

```math
\boxed{
C_{\mathrm{radio}}
=
\frac{p_1}{3}
+
\frac{p_2}{2}
+
\frac A3.
}
```

Total welfare is

```math
\boxed{
W_{\mathrm{radio}}
=
\frac76+\frac{p_1}{2}+\frac{p_2}{3}.
}
```

#### A useful explanation of the fractions

After no initial launch, the three conditional event rates have a fixed ratio:

```math
\text{station 1}:\text{station 2}:\text{flood}
=
1:2:1.
```

Thus, their probabilities of being first are

```math
\frac14,\qquad \frac12,\qquad \frac14.
```

This gives a direct explanation of the radio outcome.

### 6.2 The two benchmark mixed equilibria

The most direct comparison uses the radio equilibrium with no atoms.

| Quantity | Radio: no atoms | Blackout: mixed |
| --- | --- | --- |
| Only station 1 executes | $\frac14$ | $\frac16$ |
| Only station 2 executes | $\frac12$ | $\frac13$ |
| Both execute | $0$ | $\frac13$ |
| Neither executes | $\frac14$ | $\frac16$ |
| Protection probability | $\frac34$ | $\frac56$ |
| Expected total cost | $\frac13$ | $\frac12$ |
| Station 1 payoff | $\frac23$ | $\frac23$ |
| Station 2 payoff | $\frac12$ | $\frac12$ |
| Total welfare | $\frac76$ | $\frac76$ |

Blackout raises protection by

```math
\frac56-\frac34=\frac1{12}.
```

Each protected station receives value $1$. Thus, the added expected safety value is

```math
2\cdot\frac1{12}=\frac16.
```

The added expected cost is also

```math
\frac12-\frac13=\frac16.
```

The two changes cancel exactly.

**Blackout gives more protection in this comparison. It also gives more duplicate cost.**

The causes of failure differ:

- In the radio equilibrium, both stations plan finite launches. The flood can arrive before either launch.

- In the blackout equilibrium, failure occurs when both stations choose never to launch.

### 6.3 Blackout is not safer than every radio equilibrium

Let

```math
p=p_1+p_2.
```

The radio family has protection probability

```math
\Pr(\text{protection})
=
1-\frac{1-p}{4}
=
\frac{3+p}{4}.
```

Comparison with $5/6$ gives

```math
\boxed{
\begin{array}{ll}
p\lt 1/3:&\text{blackout mixed gives greater protection},\\[2pt]
p=1/3:&\text{protection probabilities are equal},\\[2pt]
p>1/3:&\text{radio mixed gives greater protection}.
\end{array}
}
```

Thus, the safety comparison depends on which radio equilibrium occurs.

### 6.4 The efficient outcome

The greatest possible total welfare comes from station 1 launching at zero:

```math
\boxed{W_{\max}=2-\frac13=\frac53.}
```

This gives certain protection with one launch at the lower cost.

Both versions can support this outcome as a pure equilibrium.

They also support less efficient equilibria. The rules alone do not select which equilibrium the stations will use.

---

## 7. Why the radio equilibrium list is complete

The calculations above establish that the listed strategies work. A complete solution must also exclude other atoms, gaps, and distributions.

This final argument supplies that check.

### 7.1 Set aside the sure launch at zero

Condition $(*)$ already covers every case with a sure immediate launcher.

Now suppose neither station launches at zero with certainty.

In the radio game, merge deadline $1$ with infinity. They give the same payoffs.

Let $b$ be the smaller of the two upper support endpoints.

The **support** contains times whose arbitrarily small neighborhoods have positive probability.

For every $t\in(0,b)$, both stations have positive probability of waiting beyond $t$.

### 7.2 No positive atom can occur before $b$

Suppose station $j$ has an atom of size $m>0$ at time $t\lt 1$.

Station $i$’s payoff rises when its deadline moves from exactly $t$ to just after $t$. The limiting rise is

```math
c_i(1-t)m>0.
```

Waiting past the atom avoids the tie cost.

Thus, station $i$ cannot use deadlines in a sufficiently short interval immediately before the atom.

But station $j$ can then move its atom slightly earlier within that interval. This improves protection without losing a chance for rival cancellation.

That is a profitable deviation.

Therefore, neither station has a positive atom on $(0,b)$.

### 7.3 The supports cannot have gaps

Suppose one station assigns no probability to an open interval.

Within that interval, the other station gains no additional chance of rival cancellation by waiting. Its payoff strictly decreases with delay.

Thus, the other station also assigns no probability there.

Any gap must therefore be a common gap.

However, payoffs fall across a common gap. Its two endpoints cannot both be optimal deadlines.

An initial positive waiting interval also fails. At least one station gains by moving its launch earlier.

Consequently, both supports fill $(0,b)$.

### 7.4 Indifference forces the power distributions

Every deadline in this interval must give the same payoff.

The exact indifference equation is

```math
0=dU_i
=
c_i(1-t)\,dF_j(t)
-
(1-c_i)S_j(t)\,dt.
```

This equation forces an ordinary density on $(0,b)$. It then gives

```math
S_1(t)=K_1(1-t),
\qquad
S_2(t)=K_2(1-t)^2.
```

The constants are the probabilities of passing time zero without a launch:

```math
K_1=1-p_1,
\qquad
K_2=1-p_2.
```

Thus, the previously stated family is necessary.

### 7.5 The support must extend to time $1$

Both power functions remain positive at every time below $1$.

If $b\lt 1$, at least one station would need an atom at $b$ to exhaust its remaining probability.

A lone atom fails while the rival still has a positive tail. Two atoms at the same time fail because either station can avoid the tie.

Hence,

```math
b=1.
```

Both survival functions approach zero there. No mass remains at $1$ or infinity.

Finally, both stations cannot have atoms at zero. This gives the required restriction

```math
p_1p_2=0.
```

The radio list is therefore exhaustive:

1. The stated pure deadline equilibria.

2. The two mixed branches with at most one atom at zero.

3. A sure launch at zero with any standby mixture that satisfies condition $(*)$.

The blackout list contains only its two pure equilibria and its unique mixed equilibrium.

*Style reference: ASD-STE100 recommends short sentences and one topic per paragraph.* [asd-ste100.org](https://www.asd-ste100.org/assets/files/ASD-STE100_ISSUE9.pdf?utm_source=chatgpt.com)
