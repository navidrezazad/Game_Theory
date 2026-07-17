# Famous Game-Theory Problems for Quantitative Research Interview Practice

A standalone bank of **170 public, classical, or semi-classical game-theory problems** selected for the kinds of reasoning useful in quantitative research and trading interviews: equilibrium analysis, probability, strategic information, optimization, market design, stochastic processes, and discrete invariants.

> **Scope note:** These are original restatements of well-known public problems and models. They are not claimed to be actual, leaked, or proprietary questions from any firm. Only titles and problem statements are included; there are no solutions.

## Contents

- [I. Core Matrix Games, Mixed Strategies, and Social Dilemmas](#i-core-matrix-games-mixed-strategies-and-social-dilemmas)
- [II. Sequential Games, Bargaining, Commitment, and Repetition](#ii-sequential-games-bargaining-commitment-and-repetition)
- [III. Bayesian Games, Signaling, Information, and Learning](#iii-bayesian-games-signaling-information-and-learning)
- [IV. Auctions, Contests, and Mechanism Design](#iv-auctions-contests-and-mechanism-design)
- [V. Industrial Organization, Market Microstructure, and Quant-Market Games](#v-industrial-organization-market-microstructure-and-quant-market-games)
- [VI. Stochastic Games, Optimal Stopping, Timing, and Search](#vi-stochastic-games-optimal-stopping-timing-and-search)
- [VII. Combinatorial and Discrete Strategy Games](#vii-combinatorial-and-discrete-strategy-games)
- [VIII. Matching, Cooperative Games, Voting, Fair Division, and Networks](#viii-matching-cooperative-games-voting-fair-division-and-networks)

## I. Core Matrix Games, Mixed Strategies, and Social Dilemmas

### 1. Prisoner’s Dilemma

Two players simultaneously choose **Cooperate** or **Defect**. Their payoffs are
```math
(C,C)=(3,3),\quad (C,D)=(0,5),\quad (D,C)=(5,0),\quad (D,D)=(1,1).
```
Find all Nash equilibria, identify the Pareto-efficient outcomes, and explain how the strategic conclusion changes when the game is repeated.

### 2. Stag Hunt

Two hunters simultaneously choose **Stag** or **Hare**. Hunting stag succeeds only if both choose Stag. Payoffs are
```math
(S,S)=(4,4),\quad (S,H)=(0,3),\quad (H,S)=(3,0),\quad (H,H)=(2,2).
```
Find all pure and mixed Nash equilibria, and determine which pure equilibrium is payoff-dominant and which is risk-dominant.

### 3. Chicken / Hawk–Dove

Two drivers approach each other and simultaneously choose **Straight** or **Swerve**. The payoffs are
```math
(\text{Straight},\text{Straight})=(-10,-10),\quad
(\text{Straight},\text{Swerve})=(2,-1),
```
```math
(\text{Swerve},\text{Straight})=(-1,2),\quad
(\text{Swerve},\text{Swerve})=(0,0).
```
Find all Nash equilibria and the equilibrium collision probability under symmetric mixing.

### 4. Battle of the Sexes

Two players want to meet but prefer different events. Each simultaneously chooses **Opera** or **Football**. Payoffs are
```math
(O,O)=(2,1),\quad (F,F)=(1,2),\quad (O,F)=(F,O)=(0,0).
```
Find all Nash equilibria, including the mixed equilibrium, and compute the players’ expected payoffs under mixing.

### 5. Matching Pennies

Each player simultaneously chooses **Heads** or **Tails**. Player 1 receives $+1$ when the choices match and $-1$ otherwise; Player 2 receives the negative of Player 1’s payoff. Find the minimax strategies and the value of the game.

### 6. Rock–Paper–Scissors

Each player simultaneously chooses Rock, Paper, or Scissors. A win gives $+1$, a loss gives $-1$, and a tie gives $0$. Find all Nash equilibria. Then repeat the analysis when Rock beating Scissors is worth $2$ instead of $1$.

### 7. Odd or Even

Each player simultaneously shows either one or two fingers. Player 1 wins one unit if the sum is odd; Player 2 wins one unit if the sum is even. Find the equilibrium mixed strategies and game value. Generalize to unequal rewards for odd and even totals.

### 8. Inspection Game

An employee chooses **Work** or **Shirk**, while an inspector simultaneously chooses **Inspect** or **Not Inspect**. Working costs the employee $c>0$; shirking creates private benefit $b>0$; inspection costs the inspector $k>0$; and detected shirking produces a fine $f>0$. Specify payoffs explicitly, then find the mixed-strategy equilibrium and the comparative statics in $b,c,k,f$.

### 9. Hide-and-Seek Matrix Game

A hider chooses one of $n$ locations and a seeker simultaneously chooses one location to search. If the seeker chooses the hider’s location, the seeker receives $1$; otherwise the seeker receives $0$. Locations may have unequal search costs $c_j$ and unequal hiding values $v_j$. Formulate the zero-sum payoff matrix and find equilibrium hiding and searching distributions.

### 10. Colonel Blotto

Two players each allocate six identical troops among three battlefields simultaneously. A battlefield is won by the player assigning more troops there; a tie splits that battlefield. Each battlefield is worth one point, and total payoff is points won minus points lost. Find a Nash equilibrium in mixed strategies. Then consider unequal battlefield values $1,2,3$.

### 11. Traveler’s Dilemma

Two travelers independently write an integer claim between $2$ and $100$. If the claims match, each receives that amount. If they differ, both receive the lower claim, but the lower claimant receives an additional reward $R=2$ and the higher claimant pays a penalty $R=2$. Find the Nash equilibrium and analyze iterated elimination of dominated strategies.

### 12. Volunteer’s Dilemma

There are $N\ge 2$ players. Each simultaneously chooses whether to volunteer. If at least one player volunteers, everyone receives benefit $B$, while each volunteer pays cost $c$, where $0<c<B$. If nobody volunteers, everyone receives $0$. Find all asymmetric pure equilibria and the symmetric mixed equilibrium.

### 13. Linear Public-Goods Game

Each of $N$ players receives an endowment $w$ and chooses a contribution $g_i\in[0,w]$ to a public account. The total contribution is multiplied by $m$, where $1<m<N$, and divided equally among all players. Player $i$’s payoff is
```math
u_i=w-g_i+\frac{m}{N}\sum_{j=1}^N g_j.
```
Find the Nash equilibrium and the socially efficient contribution profile.

### 14. Common-Pool Resource Game

Each of $N$ firms chooses extraction effort $e_i\ge0$. Total output is $Q(E)$, where $E=\sum_i e_i$, and firm $i$ receives the share $e_i/E$ of output while paying cost $ce_i$. For $Q(E)=aE-bE^2$, find the symmetric Nash equilibrium and compare it with the cooperative optimum.

### 15. Market-Entry / Crowding Game

There are $N$ identical firms. Each simultaneously chooses **Enter** or **Stay Out**. If $k$ firms enter, each entrant earns $V/k-c$, while each nonentrant earns $0$. Find all pure equilibria and the symmetric mixed equilibrium as functions of $N,V,c$.

### 16. Minority Game

An odd number $N$ of players simultaneously chooses $A$ or $B$. Every player in the minority group receives $1$; every player in the majority receives $0$. Characterize the pure Nash equilibria and find a symmetric mixed equilibrium.

### 17. Keynesian Beauty Contest

Each of $N$ players chooses a number in $[0,100]$. The winner is the player whose number is closest to $p$ times the average chosen number, where $0<p<1$; ties split a fixed prize. Analyze the game for $p=2/3$, including iterated elimination and Nash equilibrium.

### 18. El Farol Bar Problem

Each of $N$ people independently chooses whether to attend a bar. Attending gives payoff $1$ if total attendance is at most capacity $L$, but payoff $-c$ if attendance exceeds $L$. Staying home gives payoff $0$. Find symmetric mixed equilibria and the induced attendance distribution.

### 19. Threshold Coordination Game

Each of $N$ players simultaneously chooses whether to invest. Investment costs $c$. Every investor receives benefit $B>c$ if at least $K$ players invest, and receives no benefit otherwise. Noninvestors receive $0$. Find all pure equilibria and symmetric mixed equilibria.

### 20. Evolutionary Hawk–Dove Game

A population repeatedly plays Hawk–Dove for a resource of value $V>0$. A Hawk–Hawk encounter causes each player expected injury cost $C>V$; Hawk obtains the resource against Dove; two Doves split the resource. Write the payoff matrix, find evolutionarily stable strategies, and identify the stationary points of the replicator dynamic.

## II. Sequential Games, Bargaining, Commitment, and Repetition

### 21. Centipede Game

Two players alternate choosing **Take** or **Pass** along a finite game tree. At node $1$, taking gives $(2,0)$; passing leads to node $2$, where taking gives $(1,3)$; subsequent terminal payoffs are $(4,2),(3,5),(6,4),(5,7)$, and passing at the final node gives $(8,6)$. Find the subgame-perfect equilibrium and all Nash equilibria.

### 22. Ultimatum Game

A proposer offers the responder a share $x\in[0,1]$ of a unit pie. The responder observes $x$ and chooses **Accept** or **Reject**. Acceptance gives payoffs $(1-x,x)$; rejection gives $(0,0)$. Find all subgame-perfect equilibria under continuous and discrete offer spaces.

### 23. Dictator Game

A dictator chooses a transfer $x\in[0,1]$ to a passive recipient from a unit endowment. Payoffs are $(1-x,x)$. State the prediction under purely self-interested preferences, then reformulate the problem when the dictator’s utility includes inequity aversion or altruism parameters and characterize the optimal transfer.

### 24. Trust / Investment Game

Player 1 receives one unit and chooses an amount $x\in[0,1]$ to send to Player 2. The amount sent is multiplied by $m>1$. Player 2 then chooses a return $y\in[0,mx]$. Final monetary payoffs are $1-x+y$ for Player 1 and $mx-y$ for Player 2. Find the subgame-perfect equilibrium and compare it with the surplus-maximizing outcome.

### 25. Nash Demand Game

Two players simultaneously demand shares $x,y\in[0,1]$ of a unit surplus. If $x+y\le1$, they receive $x$ and $y$; if $x+y>1$, both receive $0$. Find all pure Nash equilibria and discuss equilibrium selection under small demand-grid perturbations.

### 26. Rubinstein Alternating-Offers Bargaining

Two players bargain over a unit surplus. Player 1 proposes at dates $0,2,4,\ldots$, Player 2 proposes at dates $1,3,5,\ldots$, and the responder may accept or reject. Player $i$ discounts one period by $\delta_i\in(0,1)$. Find the stationary subgame-perfect equilibrium allocation and acceptance rules.

### 27. Alternating Offers with Random Breakdown

Two players bargain over a unit surplus by alternating offers. After each rejection, negotiations break down with probability $1-\rho$, yielding both players $0$; otherwise bargaining continues with the other player proposing. Find the stationary subgame-perfect equilibrium and relate it to the version with time discounting.

### 28. Dollar Auction

Two players bid sequentially for a prize worth one dollar. Bids must increase by at least one cent. When a player quits, the higher bidder receives the dollar, but both players pay their final bids. Analyze subgame-perfect behavior for a finite bid cap and discuss what changes when bids are unbounded.

### 29. Chain-Store Paradox

An incumbent faces one potential entrant in each of $T$ markets, sequentially. In each market the entrant chooses **Enter** or **Stay Out**; after entry, the incumbent chooses **Fight** or **Accommodate**. Fighting is costly to both sides, while accommodation gives both positive profit. Find the subgame-perfect equilibrium by backward induction and compare it with reputation-based intuition.

### 30. Entry Deterrence with Capacity Commitment

An incumbent first chooses capacity $K$ at cost $c(K)$. A potential entrant observes $K$ and chooses whether to enter. If entry occurs, firms compete in quantities or prices; otherwise the incumbent is a monopolist. Determine the incumbent’s optimal capacity, the entrant’s response, and conditions under which excess capacity deters entry.

### 31. Stackelberg Quantity Competition

Firm 1 chooses quantity $q_1\ge0$, then Firm 2 observes $q_1$ and chooses $q_2\ge0$. Market price is $P(Q)=a-bQ$, where $Q=q_1+q_2$, and both firms have constant marginal cost $c<a$. Find the subgame-perfect equilibrium quantities and profits.

### 32. Cournot Duopoly

Two firms simultaneously choose quantities $q_1,q_2\ge0$. Inverse demand is $P(Q)=a-bQ$, and each firm has constant marginal cost $c<a$. Find the Nash equilibrium, monopoly output, competitive output, and welfare loss.

### 33. Bertrand Price Competition

Two firms with identical constant marginal cost $c$ simultaneously choose prices. Consumers buy entirely from the lower-priced firm and split demand at equal prices; market demand is $D(p)=a-bp$. Find all Nash equilibria. Then analyze unequal marginal costs.

### 34. Bertrand–Edgeworth Capacity Game

Two firms have constant marginal cost $c$, fixed capacities $K_1,K_2$, and simultaneously choose prices. Demand is downward sloping, and a low-price firm can sell only up to capacity; residual demand may go to the high-price firm. Determine whether a pure price equilibrium exists and, if not, formulate a mixed equilibrium.

### 35. Hotelling Location Game

Two vendors simultaneously choose locations $x_1,x_2\in[0,1]$ on a line populated uniformly by consumers. Consumers buy from the closer vendor, splitting ties, and prices are fixed and equal. Find the Nash equilibrium locations. Then extend the problem to three vendors.

### 36. War of Attrition

Two players compete for a prize worth $V$. Each privately chooses a quitting time $t_i\ge0$. The player who quits first loses the prize, and both players pay waiting cost equal to the time elapsed until the first quit. Find the symmetric mixed-strategy equilibrium distribution.

### 37. Preemption Game

Two firms choose irreversible investment times. The first investor receives leader value $L(t)$, the second receives follower value $F(t)$, and simultaneous investment gives each $M(t)$, with $L(t)>F(t)$ over a preemption region. Characterize pure and mixed timing equilibria and identify the preemption point.

### 38. Finitely Repeated Prisoner’s Dilemma

The Prisoner’s Dilemma with payoffs $T>R>P>S$ is repeated exactly $T_0<\infty$ times, with all past actions observed and total payoff equal to the sum of stage payoffs. Find all subgame-perfect equilibria under standard assumptions and analyze the effect of adding a small probability that the game continues.

### 39. Infinitely Repeated Prisoner’s Dilemma

The Prisoner’s Dilemma is repeated forever with common discount factor $\delta\in(0,1)$. Determine for which values of $\delta$ cooperation can be sustained by grim-trigger strategies, tit-for-tat-like strategies, or finite punishment strategies.

### 40. Repeated Cournot Collusion

Two firms play the Cournot duopoly game every period forever with discount factor $\delta$. They propose producing half the monopoly quantity each and reverting forever to the one-shot Cournot equilibrium after any deviation. Find the discount-factor condition under which this trigger strategy is a subgame-perfect equilibrium.

## III. Bayesian Games, Signaling, Information, and Learning

### 41. Akerlof’s Market for Lemons

A seller owns a good of quality $q\sim U[0,1]$ and observes $q$. The seller values the good at $q$, while a buyer values it at $3q/2$. The buyer posts one price $p$, and the seller accepts iff $p\ge q$. Find the rational-expectations trading outcome and characterize adverse selection.

### 42. Spence Job-Market Signaling

Workers are either high productivity $a_H$ or low productivity $a_L<a_H$, with known prior probability. A worker observes type and chooses education $e\ge0$, which does not affect productivity but has type-dependent cost $c_H(e)<c_L(e)$. Competitive firms observe $e$ and pay expected productivity. Find separating, pooling, and semi-separating equilibria under a stated refinement.

### 43. Beer–Quiche Signaling Game

Nature selects a strong or weak incumbent. The incumbent observes type and chooses Beer or Quiche for breakfast. An entrant observes breakfast but not type and chooses whether to fight. Strong and weak types have different breakfast preferences, and fighting is profitable only against the weak type. Find perfect Bayesian equilibria and apply an equilibrium refinement.

### 44. Bayesian Entry Deterrence

An incumbent is privately either **Tough** or **Weak**. A potential entrant observes a prior probability of each type and chooses whether to enter. After entry, the incumbent chooses Fight or Accommodate; fighting is optimal only for the Tough type. Find the perfect Bayesian equilibria and the entrant’s cutoff belief.

### 45. Crawford–Sobel Cheap Talk

A sender privately observes $\theta\sim U[0,1]$, sends a costless message, and a receiver chooses action $a$. The receiver’s payoff is $-(a-\theta)^2$, while the sender’s payoff is $-(a-\theta-b)^2$ for bias $b>0$. Characterize partition equilibria and determine how the number of informative messages depends on $b$.

### 46. Bayesian Persuasion

A sender knows a binary state $\theta\in\{0,1\}$ and commits ex ante to an information structure. A receiver observes the signal and chooses action $a\in\{0,1\}$, taking action $1$ only when the posterior probability of $\theta=1$ exceeds a threshold. The sender always prefers action $1$. Find an optimal signal subject to Bayes plausibility.

### 47. Sequential Information Cascade

A binary state is equally likely to be Good or Bad. Players move sequentially, each receiving an independent private signal that is correct with probability $p>1/2$, observing all earlier actions but not earlier signals, and choosing an action matching one of the states. Determine when an information cascade begins and the probability that it is wrong.

### 48. Restaurant Herding Problem

Two restaurants are equally likely to be better. Customers arrive sequentially, receive private noisy recommendations, observe previous customers’ restaurant choices, and choose one restaurant. Formulate the Bayesian updating rule and characterize when rational herding can cause nearly everyone to choose the inferior restaurant.

### 49. Global Currency-Attack Game

A continuum of speculators decides whether to attack a currency. The central bank abandons the peg if the mass of attackers exceeds an unknown fundamental $\theta$. Each speculator observes a noisy private signal of $\theta$, earns a gain from a successful attack, and pays a cost for an unsuccessful one. Find a monotone Bayesian equilibrium cutoff.

### 50. Diamond–Dybvig Bank-Run Game

Depositors place funds in a bank that invests in a long-term technology. Each depositor may withdraw early or wait. Early liquidation is costly, and the bank can honor only a limited mass of early withdrawals. Some depositors genuinely need early consumption; others do not. Characterize the efficient equilibrium, the run equilibrium, and the effect of deposit insurance or suspension.

### 51. Rubinstein’s Electronic-Mail Game

Two players must coordinate between a safe action and a risky action. A favorable state is initially known only to Player 1. Messages confirming the state are sent back and forth, but each message is independently lost with small probability. After communication stops, players act simultaneously. Find the Bayesian equilibrium and analyze the limit as message failure probability tends to zero.

### 52. Dirty Faces / Common-Knowledge Puzzle

A group of $n$ children may have dirty faces. Each sees everyone else’s face but not their own. A teacher truthfully announces, “At least one of you has a dirty face,” and then repeatedly asks all children simultaneously whether they know their own status. If exactly $k$ faces are dirty, determine in which round the dirty children can infer their status and explain the role of common knowledge.

### 53. Aumann’s Agreeing-to-Disagree Problem

Two Bayesian agents share a common prior over a finite state space and have posterior probabilities for an event based on their private information partitions. Their posterior beliefs become common knowledge. Determine whether the posteriors can differ, and prove the relevant result under the stated assumptions.

### 54. Bayesian Cournot with Private Costs

Two firms simultaneously choose quantities. Firm $i$’s marginal cost is privately either $c_L$ or $c_H$, independently drawn from a common prior. Inverse demand is $P(Q)=a-bQ$. Find a Bayesian Nash equilibrium in type-contingent quantities.

### 55. Bayesian Bertrand with Private Costs

Two firms simultaneously choose prices. Each firm privately observes its own marginal cost, independently drawn from a known continuous distribution. Demand goes to the lower-price firm, with ties split. Formulate and solve for a monotone symmetric Bayesian equilibrium bidding or pricing function under a specified demand rule.

### 56. Principal–Agent Moral Hazard

A risk-neutral principal hires a risk-averse agent whose effort $e$ is unobservable. Output is $Y=e+\varepsilon$, where $\varepsilon$ is noise, and effort costs the agent $c(e)$. The principal offers a linear contract $w(Y)=a+bY$. Choose $a,b$ to satisfy participation and incentive compatibility and maximize the principal’s expected profit.

### 57. Adverse Selection and Screening

A monopolist sells quantity $q$ to a buyer whose private type $\theta\in\{\theta_L,\theta_H\}$ determines value $\theta v(q)$. The seller offers a menu $(q_L,p_L),(q_H,p_H)$. Find the profit-maximizing menu subject to incentive-compatibility and participation constraints.

### 58. Limit Pricing as a Signal

An incumbent privately knows whether its marginal cost is low or high. It chooses a first-period price observed by a potential entrant, who then decides whether to enter in period 2. Low prices are more costly for the high-cost incumbent. Find pooling and separating perfect Bayesian equilibria and apply an intuitive-criterion-style refinement.

### 59. Beauty Contest with Private Signals

A fundamental $\theta$ is unknown. Each player observes a private signal $s_i=\theta+\varepsilon_i$ and chooses action $a_i$. Player $i$ minimizes
```math
(1-r)(a_i-\theta)^2+r(a_i-\bar a)^2,
```
where $0<r<1$. Find the linear Bayesian Nash equilibrium and quantify the weight placed on public versus private information when a public signal is added.

### 60. Kuhn Poker

A deck contains three cards $J<Q<K$. Each of two players receives one card privately. Player 1 may check or bet; after a check, Player 2 may check or bet; after a bet, the opponent may call or fold. Antes and bet sizes are one chip. Find a Nash equilibrium in behavioral strategies and the value of the game.

## IV. Auctions, Contests, and Mechanism Design

### 61. First-Price Sealed-Bid Auction

There are $N$ risk-neutral bidders with independent private values $v_i\sim U[0,1]$. Each submits one sealed bid; the highest bidder wins and pays their own bid. Find the symmetric increasing Bayesian Nash equilibrium bidding function and expected seller revenue.

### 62. Second-Price / Vickrey Auction

There are $N$ bidders with independent private values. Each submits one sealed bid; the highest bidder wins and pays the second-highest bid. Prove or disprove that truthful bidding is weakly dominant, and calculate expected revenue for $v_i\sim U[0,1]$.

### 63. English Ascending Auction

Bidders with independent private values participate in an ascending-price auction. Bidders may drop out irreversibly, and the last remaining bidder wins at the price at which the second-to-last bidder exits. Find optimal dropout strategies and compare the outcome with a second-price sealed-bid auction.

### 64. Dutch Descending Auction

A clock price starts high and falls continuously. The first bidder to stop the clock wins and pays the current price. Bidders have independent private values drawn from a known distribution. Find a symmetric equilibrium stopping rule and compare it with the first-price sealed-bid auction.

### 65. All-Pay Auction

There are $N$ risk-neutral bidders with independent values $v_i\sim U[0,1]$. The highest bidder wins the object, but every bidder pays their bid. Find the symmetric increasing equilibrium bid function and expected total expenditure.

### 66. Common-Value Oil-Lease Auction

An oil tract has unknown common value $V$. Bidder $i$ observes signal $S_i=V+\varepsilon_i$, with conditionally independent noise. The highest bidder wins and pays their bid. Formulate a symmetric equilibrium condition that accounts for the information conveyed by winning.

### 67. Winner’s Curse

There are $N$ bidders for an asset with common value $V$. Each observes an unbiased noisy estimate $S_i$ and submits a bid. Compute or characterize
```math
\mathbb E[V\mid S_i=s,\;S_i=\max_j S_j],
```
and determine how a rational bidder should adjust a naive estimate-based bid.

### 68. Myerson Optimal Reserve Price

A seller auctions one object to $N$ risk-neutral bidders with i.i.d. values $v_i\sim U[0,1]$. The seller may set a reserve price $r$ in a second-price auction. Choose $r$ to maximize expected revenue, and compare expected revenue with the no-reserve auction.

### 69. Revenue Equivalence Comparison

For $N$ risk-neutral bidders with i.i.d. private values and identical allocation rules, compare expected payments in first-price, second-price, English, and Dutch auctions. State the assumptions needed for revenue equivalence and identify what breaks when bidders are risk-averse or values are affiliated.

### 70. Procurement Auction with Private Costs

A buyer needs one contract. Each of $N$ suppliers has private cost $c_i\sim U[0,1]$ and submits a sealed price. The lowest bid wins and is paid its own bid. Find the symmetric increasing equilibrium bidding function and the buyer’s expected payment.

### 71. Multi-Unit Uniform-Price Auction

A seller has $K$ identical units. Each bidder submits a demand schedule; the $K$ highest marginal bids win, and every winner pays the highest rejected bid. Construct a strategic-demand-reduction example and find equilibrium bids in a small instance with two bidders and two units.

### 72. Discriminatory / Pay-as-Bid Auction

A seller has $K$ identical units. Bidders submit marginal bids, the $K$ highest bids win, and each winning unit is paid at its own bid. For a specified set of decreasing marginal values, determine equilibrium bidding incentives and compare revenue with a uniform-price auction.

### 73. VCG Public-Project Mechanism

A public project costs $C$. Agent $i$ privately values the completed project at $v_i$. Design the Vickrey–Clarke–Groves decision and transfer rule, determine when the project is built, and compute payments for a given vector of reported values.

### 74. VCG Assignment Auction

There are $n$ bidders and $m$ heterogeneous items, with bidder $i$’s value $v_{ij}$ for item $j$. Each bidder may receive at most one item. Find the welfare-maximizing assignment and compute VCG payments in a specified numerical valuation matrix.

### 75. Generalized Second-Price Ad Auction

There are three advertising slots with click-through rates $\alpha_1>\alpha_2>\alpha_3$ and three advertisers with per-click values $v_1,v_2,v_3$. Advertisers submit bids; rank determines slots, and each winner pays the next bid per click. Find pure-strategy equilibria and compare them with VCG payments.

### 76. Chatterjee–Samuelson Double Auction

One seller has private cost $c\sim U[0,1]$, and one buyer has private value $v\sim U[0,1]$, independently. The seller submits an ask $a(c)$, the buyer submits a bid $b(v)$, and trade occurs at the average $(a+b)/2$ if $b\ge a$. Find linear Bayesian Nash equilibrium strategies.

### 77. Myerson–Satterthwaite Bilateral Trade

A seller privately knows cost $c$ and a buyer privately knows value $v$, drawn independently from overlapping distributions. A mechanism should be Bayesian incentive compatible, individually rational, budget balanced, and ex post efficient. Determine whether all four properties can be achieved simultaneously and establish the relevant impossibility result for a concrete distributional example.

### 78. Tullock Rent-Seeking Contest

Two players choose efforts $e_1,e_2\ge0$ at unit cost. Player $i$ wins a prize worth $V_i$ with probability
```math
\frac{e_i^r}{e_1^r+e_2^r},
```
with an appropriate tie convention at zero effort. Find Nash equilibrium efforts for $r=1$, and analyze how effort changes with prize asymmetry.

### 79. War-of-Attrition Auction

Two players privately value a prize at $v_i$. Each chooses a nonnegative bid interpreted as waiting cost. The higher bid wins the prize, but both players pay the lower bid; ties are split. Find a symmetric Bayesian equilibrium for i.i.d. private values.

### 80. Combinatorial Auction and Exposure

Two complementary items $A,B$ are sold. Bidder 1 values only the bundle $\{A,B\}$ at $10$ and values either item alone at $0$. Bidders 2 and 3 value only $A$ and $B$, respectively. Compare separate first-price auctions with a package-bidding mechanism, and formulate equilibrium or strategic-exposure issues.

## V. Industrial Organization, Market Microstructure, and Quant-Market Games

### 81. Kyle One-Period Insider-Trading Model

An asset value $v\sim N(0,\Sigma_0)$ is observed by an informed trader. Noise order flow is $u\sim N(0,\sigma_u^2)$. The insider submits order $x(v)$, the market maker observes total order flow $y=x+u$, and sets $p(y)=\mathbb E[v\mid y]$. Find a linear equilibrium $x(v)=\beta v$, $p(y)=\lambda y$.

### 82. Glosten–Milgrom Sequential-Trade Model

An asset value is either $v_H$ or $v_L$. In each round, the arriving trader is informed with probability $\mu$ and otherwise is a noise trader who buys or sells with equal probability. A competitive market maker posts bid and ask prices before seeing the order and must earn zero expected profit conditional on the order. Find the bid, ask, and spread.

### 83. Kyle Model with Multiple Informed Traders

There are $N$ risk-neutral insiders who all observe the same asset value $v$, choose orders simultaneously, and trade against Gaussian noise order $u$. A competitive market maker observes aggregate order flow and sets the conditional-expectation price. Find a symmetric linear equilibrium and study how market depth and insider profits depend on $N$.

### 84. Limit Order versus Market Order

A trader must buy one unit before a deadline. A market order executes immediately at ask $A$. A limit buy at price $L<A$ executes with probability $q(L)$; if it does not execute before the deadline, the trader must buy at random terminal ask $A_T$. Choose $L$ or a market order to minimize expected cost, and identify the strategic effect of other traders choosing queue prices.

### 85. Queue-Position Game at the Best Bid

Two liquidity providers simultaneously choose either to join the current best bid queue or improve the bid by one tick. Joining preserves price but gives lower fill priority; improving gains priority but sacrifices one tick. Given fill probabilities, adverse-selection loss, and inventory value, find pure and mixed Nash equilibria.

### 86. Latency Race / Sniping Game

After a public value jump, the first fast trader to reach a stale quote earns prize $V$. Each of $N$ traders chooses speed investment $e_i\ge0$, pays cost $c(e_i)$, and wins with probability proportional to $e_i$. Find symmetric equilibrium investment and expected rent dissipation.

### 87. Frequent Batch Auction Speed-Investment Game

Trades clear every $\Delta$ seconds in batch auctions. Traders may invest in speed to receive signals earlier within a batch, but orders arriving before the clearing deadline have equal priority. Model the speed race as a contest and determine how equilibrium investment varies with $\Delta$.

### 88. Predatory Trading against a Forced Liquidator

Trader 1 must liquidate $Q$ shares over $T$ periods. Trader 2 learns this and chooses a trading path to profit from temporary and permanent price impact. Both know the impact model and Trader 1 anticipates predation. Formulate the dynamic game and find a subgame-perfect or open-loop Nash equilibrium liquidation schedule.

### 89. Strategic Liquidation by Two Large Traders

Two risk-averse traders must liquidate initial inventories $Q_1,Q_2$ over a finite horizon. Their trades create linear temporary and permanent price impact. Each chooses a trading schedule to minimize expected execution cost plus inventory risk, taking the other schedule as given. Find an open-loop Nash equilibrium.

### 90. OTC Bilateral Bargaining over a Bond

A dealer and customer bargain over the price of one bond. Their private valuations and outside options differ, and delay carries cost. Model trade using Nash bargaining or alternating offers, compute the transaction price, and analyze how bargaining power and search outside options affect the spread.

### 91. Supply-Function Equilibrium

Two electricity generators simultaneously submit increasing supply functions $S_i(p)$. Demand is $D(p)=\bar D+\varepsilon-\gamma p$, where $\varepsilon$ is uncertain when bids are submitted. The market-clearing price equates total supply and demand. Find a symmetric linear supply-function equilibrium under specified cost functions.

### 92. Kreps–Scheinkman Capacity-Then-Price Game

Two firms first choose capacities simultaneously and pay capacity costs. They then compete in prices subject to those capacities, with efficient rationing. Inverse demand is linear and marginal production cost is constant. Find the subgame-perfect equilibrium and compare it with Cournot competition.

### 93. Cournot Competition with Stochastic Demand

Two firms choose quantities before observing demand shock $\varepsilon$. Price is
```math
P=a+\varepsilon-b(q_1+q_2),
```
and firms may have different information about $\varepsilon$. Find Bayesian Nash equilibrium quantities under common information and under asymmetric signals.

### 94. Stackelberg Competition under Demand Uncertainty

A leader chooses quantity before observing a demand shock. A follower observes the leader’s quantity and a private signal about demand before choosing its quantity. Formulate the Bayesian subgame-perfect equilibrium and compare the value of information for the leader and follower.

### 95. Salop Circular-City Competition

There are $N$ firms equally spaced or endogenously located on a circle of circumference one. Consumers are uniformly distributed, incur transportation cost $t$ per unit distance, and buy one unit from the lowest delivered-price firm. Find a symmetric price equilibrium and analyze free entry with fixed cost $F$.

### 96. Vertical Differentiation Game

Two firms choose product qualities $q_H\ge q_L\ge0$ and then prices. Consumers have types $\theta$ uniformly distributed on an interval and utility $\theta q-p$. Quality costs are convex. Find the subgame-perfect equilibrium qualities, prices, and market segmentation.

### 97. Hotelling Price Competition with Quadratic Transport Costs

Two firms are fixed at locations $0$ and $1$. Consumers are uniformly distributed on $[0,1]$, buy one unit, and incur quadratic transportation cost $t(x-\ell_i)^2$. Firms simultaneously set prices with common marginal cost $c$. Find the Nash equilibrium prices and market shares.

### 98. Advertising Contest

Two firms sell substitutable products and simultaneously choose advertising expenditures $a_1,a_2\ge0$. Firm $i$’s market share is
```math
\frac{a_i^\rho}{a_1^\rho+a_2^\rho},
```
and advertising has linear or convex cost. Find equilibrium advertising and identify when the contest dissipates most of the available profit.

### 99. Two-Sided Platform Pricing

Two competing platforms set prices to buyers and sellers. A buyer’s utility increases with the number of sellers on the same platform, and a seller’s utility increases with the number of buyers. Agents may single-home or multi-home. Formulate equilibrium platform prices and participation under specified network-effect parameters.

### 100. Network-Effects Technology-Adoption Game

Each of $N$ users chooses technology $A$ or $B$. User $i$’s payoff equals intrinsic value $v_{iA}$ or $v_{iB}$ plus $\alpha$ times the number of other users choosing the same technology. Find pure Nash equilibria, tipping conditions, and the effect of an early subsidy to one technology.

## VI. Stochastic Games, Optimal Stopping, Timing, and Search

### 101. Penney’s Game

Player 1 chooses a binary sequence of length three. After seeing it, Player 2 chooses a different length-three sequence. A fair coin is tossed repeatedly until one selected sequence appears as three consecutive outcomes; that player wins. Find Player 2’s optimal response to every choice of Player 1 and the value of the sequential game.

### 102. Nontransitive Dice

Construct or use a known set of dice $A,B,C$ such that $A$ beats $B$ with probability greater than $1/2$, $B$ beats $C$ with probability greater than $1/2$, and $C$ beats $A$ with probability greater than $1/2$. One player chooses a die first and the other chooses second. Find optimal strategic choices and the game value.

### 103. Largest-Integer Game

Two players simultaneously choose a positive integer. The player choosing the larger integer receives $+1$, the other receives $-1$, and a tie gives $0$. Determine whether a Nash equilibrium or minimax value exists under countably additive mixed strategies, and analyze finite truncations of the game.

### 104. Dynkin Stopping Game

An adapted stochastic process is observed by two players. Each chooses a stopping time $\tau_i$. If Player 1 stops first, the payoff is $X_{\tau_1}$; if Player 2 stops first, it is $Y_{\tau_2}$; if they stop together, it is $Z_{\tau_1}$. Formulate conditions for a value and find equilibrium stopping rules in a finite-horizon Markov example.

### 105. Competitive Secretary Problem

Two players observe a random sequence of $N$ candidates in the same order. At each candidate, each may make an irrevocable offer; ties are resolved by a stated rule. A player wins by hiring the best candidate overall. Determine equilibrium stopping strategies and winning probabilities.

### 106. Best-Choice Duel

Two players independently observe ranks arriving in random order and each has one stopping opportunity. The first player to stop on the overall best item wins; if neither does, or both stop according to a specified tie rule, payoffs are assigned accordingly. Find equilibrium stopping thresholds.

### 107. Snowball Game

Player 1 has one snowball and may throw it at any time while Player 2 runs from one point to another. If the throw hits, Player 1 wins; if it misses, Player 2 wins by completing the run. Player 2 chooses when and how to move, and the hit probability depends on distance. Formulate the zero-sum timing game and find optimal mixed strategies.

### 108. The Big Match

At each date, Player 1 chooses **Top** or **Bottom** and Player 2 chooses **Left** or **Right**. If Player 1 chooses Top, the game absorbs with payoff $1$ against Left and $0$ against Right. If Player 1 chooses Bottom, play continues with stage payoff $0$ against Left and $1$ against Right. Analyze finite-horizon, discounted, and long-run-average values.

### 109. Shapley Stochastic Game

A finite-state zero-sum game evolves as follows: in each state, players choose actions simultaneously, receive a stage payoff, and transition to a new state according to action-dependent probabilities. For a specified two-state example, write the Shapley equations and find stationary optimal strategies and the discounted value.

### 110. Red-and-Black Gambling Game

A gambler has fortune $x\in\{1,\dots,N-1\}$ and wants to reach $N$ before $0$. At each step the gambler chooses a stake $s\le\min(x,N-x)$; with probability $p$ the fortune rises by $s$, otherwise it falls by $s$. Determine optimal staking policies for favorable and unfavorable games, and interpret the problem as a stochastic control game against nature.

### 111. Princess and Monster Game

A princess and a monster move continuously inside a known region, each with bounded speed. The princess chooses a path to maximize expected capture time; the monster chooses a path to minimize it. Neither initially knows the other’s location. Determine optimal strategies or bounds for an interval, circle, or simple planar region.

### 112. Rendezvous Search Game

Two identical agents are placed at unknown locations and orientations on a line or graph. They choose movement strategies without communication and seek to minimize expected meeting time. Find optimal symmetric rendezvous strategies under a specified initial-distance distribution.

### 113. Search Game on an Interval

A hider chooses a point in $[0,1]$. A searcher starts at a given point, moves at unit speed, and finds the hider upon reaching that location. The hider wants to maximize and the searcher wants to minimize expected detection time. Find minimax hiding and search strategies.

### 114. Ambush Game on a Network

A traveler chooses a path from source $s$ to destination $t$ in a network. An ambusher simultaneously chooses one node or edge. If the chosen route passes through the ambush location, the traveler loses; otherwise the traveler succeeds. Find equilibrium mixed strategies and relate the value to network cuts or flows.

### 115. Patent Race with Poisson Breakthroughs

Two firms choose R&D intensities $e_i(t)\ge0$. Firm $i$’s breakthrough arrives at Poisson rate $\lambda_i(e_i)$, effort costs $c_i(e_i)$, and the first breakthrough earns prize $V$. Find Markov-perfect equilibrium effort policies and expected race duration.

### 116. Real-Options Preemption Game

Two firms observe a stochastic demand process $X_t$, such as geometric Brownian motion, and each may make an irreversible investment at a stopping time. The first investor gets leader value $L(X_t)$, the second follower value $F(X_t)$. Determine equilibrium investment thresholds and any mixed-strategy preemption region.

### 117. Technology-Adoption Timing Game

Two firms choose when to adopt a cost-reducing technology. Adoption cost falls over time, but the first adopter may gain a temporary competitive advantage. Write leader, follower, and simultaneous-adoption values, then determine equilibrium adoption times.

### 118. Voluntary-Disclosure Timing Game

A firm privately observes favorable or unfavorable information and chooses when, if ever, to disclose it. Investors update beliefs from both disclosure and silence. Delay may improve precision but carries a cost. Find a perfect Bayesian equilibrium disclosure policy and the market’s belief process.

### 119. Market-Entry Timing Game

Several firms choose entry times into a growing market. Earlier entry captures more market share but incurs higher fixed cost and greater demand uncertainty. Profits after entry depend on how many rivals have already entered. Find symmetric timing equilibria and conditions for preemption or delay.

### 120. Hot-Potato Passing Game

A risky asset is passed among traders over discrete dates. At each date the current holder may sell to the next trader at a negotiated or posted price, but at a random terminal date the asset becomes worthless and the current holder bears the loss. Find equilibrium trading and pricing behavior under common beliefs and finite horizons.

## VII. Combinatorial and Discrete Strategy Games

### 121. Nim

Several heaps contain positive numbers of tokens. Players alternate choosing one heap and removing any positive number of tokens from it. The player taking the last token wins. Characterize all winning positions and give an optimal strategy from any winning position.

### 122. Misère Nim

The rules are the same as Nim, except the player taking the last token loses. Characterize winning and losing positions and give an optimal strategy, including the special case in which all remaining heaps have size one.

### 123. Wythoff Nim

Two heaps contain $a$ and $b$ tokens. A move removes any positive number from one heap, or the same positive number from both heaps. The player making the last move wins. Characterize the cold positions and give a winning strategy.

### 124. Euclid’s Game

Start with two positive integers $a\ge b$. Players alternate replacing the larger number by $a-kb$ for any positive integer $k$ that leaves a nonnegative result, then reorder the pair. The player who produces zero wins. Characterize winning positions and relate the strategy to the Euclidean algorithm.

### 125. Subtraction Game

A heap starts with $n$ tokens. Players alternate removing a number of tokens from the set $S=\{1,3,4\}$. The player taking the last token wins. Determine the losing positions, prove any periodicity, and give an optimal strategy.

### 126. Fibonacci Nim

A heap contains $n$ tokens. The first player may remove any number from $1$ to $n-1$. Thereafter, a player may remove at most twice the number removed on the preceding move. The player taking the last token wins. Characterize winning moves using Zeckendorf representations.

### 127. Grundy’s Game

A move selects one heap and splits it into two unequal positive heaps. Players alternate until no move is possible; the player making the last move wins. Compute Sprague–Grundy values for small heap sizes and characterize winning sums of heaps.

### 128. Kayles

A row of $n$ bowling pins is given. A move knocks down either one pin or two adjacent pins; the remaining pins form independent rows. The player making the last move wins. Compute the Sprague–Grundy sequence and determine winning positions for sums of rows.

### 129. Dawson’s Kayles

A row of pins is given. A legal move knocks down two adjacent pins, and pins immediately adjacent to the removed pair become unavailable according to the standard Dawson’s Kayles rule. Determine the Sprague–Grundy values and any eventual periodicity.

### 130. Treblecross

Players alternate placing an $X$ in an empty cell of a one-dimensional strip. The first player to create three consecutive $X$'s wins. Determine winning positions and formulate a Sprague–Grundy decomposition after excluding cells that would end the game immediately.

### 131. Chomp

A rectangular chocolate bar is divided into squares. Players alternate choosing a square and eating that square together with every square above and to its right. The lower-left square is poisoned; the player forced to eat it loses. Prove that the first player has a winning strategy on every nontrivial rectangle and find explicit strategies for small boards.

### 132. Hex

Players alternately color empty cells of a rhombus-shaped hexagonal board. One player aims to connect the north and south sides; the other aims to connect east and west. Prove that draws are impossible, determine who has a winning strategy on an $n\times n$ board, and analyze small boards explicitly.

### 133. Bridg-It

Two players alternately add noncrossing links between neighboring points of their own color on a rectangular lattice. Each seeks to connect opposite sides assigned to them. Determine the relationship with Hex and find a winning strategy for specified board dimensions.

### 134. Shannon Switching Game

A graph has designated terminals $s,t$. The **Short** player claims edges, trying to create an $s$-$t$ path of claimed edges; the **Cut** player deletes edges, trying to disconnect $s$ from $t$. Players alternate. Determine winning positions using graph-theoretic criteria for a specified graph.

### 135. Dots and Boxes

Players alternate drawing one unclaimed edge of a grid of dots. Completing the fourth side of a box scores that box and grants another move. When all edges are drawn, the player with more boxes wins. Find optimal play on small boards and analyze chains, loops, and the controlled-value method.

### 136. Sprouts

Begin with $n$ isolated spots in the plane. A move draws a noncrossing curve joining two spots, possibly the same spot, and places a new spot on the curve; no spot may have degree greater than three. The last player able to move wins. Determine outcomes for small $n$ and prove general bounds on game length.

### 137. Domineering

Players tile a rectangular grid with dominoes. Left places vertical dominoes and Right places horizontal dominoes; occupied cells cannot be reused. A player unable to move loses. Determine the outcome class and combinatorial-game value for small rectangles.

### 138. Northcott’s Game

On each row of a chessboard there is one black and one white checker. Players alternately move one checker of their color horizontally without jumping over the opposing checker in that row. A player unable to move loses. Reduce the game to Nim and determine optimal play.

### 139. Silver Dollar Game

Several coins occupy distinct squares of a finite strip. Players alternate moving one coin any positive distance to the left without jumping over another coin. The player making the last move wins. Characterize the position as a sum of Nim heaps and find a winning move.

### 140. Sylver Coinage

Players alternately name positive integers that cannot be expressed as nonnegative integer combinations of previously named integers. The player forced to name $1$ loses. Determine winning strategies for selected opening moves and analyze positions through numerical semigroups.

## VIII. Matching, Cooperative Games, Voting, Fair Division, and Networks

### 141. Stable Marriage

There are $n$ applicants and $n$ firms, each with a strict ranking of the opposite side. A matching is stable if no unmatched applicant–firm pair prefers each other to their assigned partners. Run the deferred-acceptance algorithm, prove stability, and determine which side receives its optimal stable matching.

### 142. Hospitals–Residents Matching

Hospitals have capacities and strict rankings over residents; residents rank hospitals and being unmatched. Find a stable matching using deferred acceptance. Analyze what changes when hospitals have responsive preferences, couples submit joint preferences, or rankings contain ties.

### 143. House Allocation and Top Trading Cycles

Each agent initially owns one indivisible house and has strict preferences over all houses. Apply the top-trading-cycles algorithm, prove that the resulting allocation lies in the core, and examine whether truthful reporting is a dominant strategy.

### 144. Kidney-Exchange Cycle Packing

Patient–donor pairs form a directed compatibility graph. A directed cycle represents a feasible simultaneous exchange, and cycles may have length at most $K$. Choose vertex-disjoint cycles to maximize the number or weighted value of transplants. Formulate the optimization problem and discuss strategic reporting by transplant centers.

### 145. Assignment Game and the Core

There are buyers and sellers, with surplus $a_{ij}$ generated by matching buyer $i$ to seller $j$. Find a maximum-weight matching and characterize payoff vectors in the cooperative-game core. Relate core payoffs to dual variables of the assignment linear program.

### 146. Shapley Value: Glove Game

A coalition can produce one unit of value for each left–right glove pair it contains. There are specified numbers of owners of left and right gloves. Define the cooperative game $v(S)$ and compute each player’s Shapley value.

### 147. Airport Cost-Sharing Game

Several airlines require runways of different minimum lengths. Building a runway of length $x$ costs $C(x)$, and any coalition must pay for the longest runway needed by a member. Define the cooperative cost game and compute Shapley-value cost shares.

### 148. Bankruptcy Game

An estate $E$ is insufficient to satisfy claims $d_1,\ldots,d_n$. Model the situation as a cooperative game and compare allocation rules such as proportional division, constrained equal awards, constrained equal losses, and the Talmud rule on a specified numerical instance.

### 149. Banzhaf Power Index

A weighted voting body has quota $q$ and weights $[w_1,\ldots,w_n]$. A coalition wins when its total weight reaches $q$. Count each voter’s swing coalitions and compute normalized Banzhaf power. Compare voting power with nominal weight.

### 150. Shapley–Shubik Power Index

For a weighted voting game $[q;w_1,\ldots,w_n]$, consider all voter orderings and identify the pivotal voter in each ordering. Compute the Shapley–Shubik power index and compare it with the Banzhaf index.

### 151. Condorcet Cycle

Three voters rank three alternatives $A,B,C$ so that a majority prefers $A$ to $B$, a majority prefers $B$ to $C$, and a majority prefers $C$ to $A$. Construct such rankings, analyze agenda control under sequential pairwise voting, and identify strategic voting opportunities.

### 152. Median Voter Theorem

Voters have single-peaked preferences over a one-dimensional policy line. Two candidates simultaneously choose platforms and care only about winning. Prove or determine equilibrium platform choices and analyze what changes with probabilistic voting or policy-motivated candidates.

### 153. Strategic Voting under Plurality

A finite set of voters has strict rankings over three candidates and votes under plurality rule with a specified tie-break. Find Nash equilibria of the voting game, identify voters with profitable misreports, and compare sincere and strategic outcomes.

### 154. Gibbard–Satterthwaite Manipulation Example

Consider a deterministic social-choice rule over at least three alternatives that is onto and not dictatorial. Construct a finite preference profile at which some voter can obtain a strictly preferred outcome by misreporting. State precisely which assumptions make manipulation unavoidable.

### 155. Condorcet Jury Theorem

A group of $N$ voters chooses between a correct and incorrect alternative. Each voter independently chooses correctly with probability $p>1/2$, and majority rule is used. Compute the probability that the group is correct and analyze its limit as $N\to\infty$. Extend the problem to correlated signals.

### 156. Braess Paradox

A fixed mass of nonatomic drivers chooses routes through a network, minimizing travel time. Construct the classical four-node network in which adding a zero-time link increases every driver’s equilibrium travel time. Compute the Wardrop equilibria before and after the link is added.

### 157. Atomic Congestion Game

A finite number of players each chooses one route or resource set. The cost of a resource depends on the number of users. For a specified network, find pure Nash equilibria and construct Rosenthal’s potential function.

### 158. Pigou Network and Price of Anarchy

A unit mass of nonatomic traffic chooses between two parallel links. One link has latency $1$; the other has latency $x$, where $x$ is its flow. Compute the Wardrop equilibrium, the socially optimal routing, and the price of anarchy. Then generalize to polynomial latency functions.

### 159. Connections Model of Network Formation

Each player chooses which costly bilateral links to propose or maintain. Direct and indirect connections create benefits that decay with graph distance, while each direct link costs $c$. Characterize pairwise-stable networks as functions of the decay parameter and link cost.

### 160. Schelling Segregation Game

Agents of two types occupy sites on a grid. Each agent prefers locations where at least a fraction $\tau$ of nearby agents share their type and may move when dissatisfied. Analyze absorbing configurations, potential functions, and the emergence of segregation from mild local preferences.

### 161. Network Public-Goods Game

Players are nodes of a graph and choose efforts $e_i\ge0$. Player $i$ benefits from their own effort and the efforts of neighbors but pays a private effort cost. For a specified concave benefit function, find Nash equilibria and compare specialized and distributed provision patterns.

### 162. Vaccination / Inoculation Game

Individuals on a network choose whether to vaccinate at cost $c$. An infection starts at a random unvaccinated node and spreads through connected unvaccinated components, imposing loss $L$. Find pure Nash equilibria, the social optimum, and the price of anarchy.

### 163. Threshold Diffusion Game

Each node chooses whether to adopt a behavior. Adopting yields payoff only when at least a threshold fraction of neighbors also adopt, possibly plus an intrinsic payoff. Characterize Nash equilibria and determine the smallest seed set that triggers full adoption.

### 164. Coalition Formation and the Core

A transferable-utility game is specified by values $v(S)$ for every coalition $S$. Determine whether the core is empty, find imputations in the core when it is nonempty, and verify balancedness for a concrete three- or four-player game.

### 165. Core of an Exchange Economy

Several agents have initial endowments and utility functions over two goods. A coalition may reallocate only its members’ total endowment. Define blocking and the core, compute competitive equilibria, and compare the core with Walrasian allocations in a finite replica economy.

### 166. Stable Roommates

An even number of agents each ranks all other agents. A matching pairs agents into rooms and is stable if no unmatched pair prefers each other to their assigned roommates. Determine whether a stable matching exists for a specified preference profile and apply Irving’s algorithm.

### 167. Strategy-Proofness in Deferred Acceptance

Applicants and schools have strict preferences, and schools have capacities. Applicants propose in a deferred-acceptance mechanism. Determine whether truthful reporting is a dominant strategy for applicants and whether schools can benefit by misreporting priorities.

### 168. Borda-Count Manipulation

Voters rank $m$ candidates. Under Borda count, a candidate receives $m-1,m-2,\ldots,0$ points from each ballot. For a specified preference profile, determine the sincere winner and identify whether one voter or a coalition can change the outcome through strategic ranking.

### 169. Knaster’s Fair-Division Procedure

Several players assign monetary values to indivisible items. The items are allocated to highest valuers, and transfers are used to equalize perceived shares according to Knaster’s procedure. Carry out the procedure on a numerical instance and analyze strategic misreporting incentives.

### 170. Cut-and-Choose Cake Division

A divisible cake is valued by two players through nonatomic value measures. Player 1 cuts the cake into two pieces, and Player 2 chooses one piece. Find optimal strategies and prove proportionality. Then formulate the strategic problem when valuations are common knowledge and the cutter may exploit the chooser’s preferences.
