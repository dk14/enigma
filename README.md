This repo contains Enigma webapp demonstrating enumeration of all possible terminating programs ([`index.html`](https://enigma.doomsdayexplorer.online/)).

> The research is presented as HTML for demo purposes (it also acts as a notebook). HTML will be split into typescript files, and a documented library will be published, akin to how it was done with [mg-peers](https://mg-peers.doomsdayexplorer.online/docs/front). 

Abstract machine has sum, diff and times (dynamically aka dependently bounded recursion) operations making it computationally complete.

Static termination check: DAG means terminating program.

Static memoization ensures no equivalent algorithms are enumerated.

Simplicity control (to be improved): from simplest to most complex programs, thus from simplest to most complex outputs.

> Simplicity control will employ advanced form of memoization, discovering functionally equivalent sub-graphs (forall x. f(x) = g(x)). Programs containing more recursion will be considered more simple in order to establish total order, unique in its expressive optimality. Hyper-parameter search will recursively re-use Enigma itself as generator for computationally natural orders (of parameters).
>> This way it would model high-level reasoning of humans, start with programs that are physically and logically/operationally easier for human programmer or mathematician to write out of most fundamental operations.
>> 
>> Length of the program does not imply its simplicity directly. Length of canonical (most expressive program) as measured in amount of Enigma-variables it employs is first, but not the only metric to order programs fundamentally. Total order has to account for a minimal and complete set of metrics in order to derive true measure of program's complexity. *If such order turns out to be not unique - we will also have to show that there is a canonical "compact" equivalence between orders, to prove that performance of Enigma is not affected by a choice of ordering.*

--------

Security applications:
- this, in theory, is attack on one-time pad. **Shannon's fundamental assumption of uniformity is rejected**:
   - output, that is easiest to compute with "no-input" program that is easiest to find, has higher probability of appearance
 
> Shannon's entropy only applicable in cases where the whole set of events under consideration is already fully computed, stored and readily accessible, as well as selection procedure, which is not the case in security. Shannon's entropy is loosely applicable to pseudo-random generation (lottery, coin-toss), which is not applicable in security: e.g. outcome of a coin-toss is predictable from initial state and distance traveled: `(init + distance) mod 2`, slight periodic change of initial state and distance gives illusion of randomness.

- true *secure* random is defined as "unknown and hardest to compute from known numbers, up to security threshold".
   - "No input" programs in Enigma already account for known numbers, since such numbers are simply previously outputted (from previous programs) and published ones. Every subsequent program is assumed (without simplicity control, yet) more complex.
  - for a given security threshold (e.g. minimum 100Kwh energy spent on computation) amount of resources needed to actually satisfy it is more than threshold itself and unpredictable: spending nominal amount does not guarantee the number will be unique. E.g. no planned economy can satisfy true randomness.
> Clarifications. We demonstrated that "no planned economy" can produce secure random. That implies that no standardization can, in principle, give you a predictable (in amount of resources) way to generate secure random for given security threshold. This is disproof by counter-example - it universally disproves "planned secure random", e.g. any NIST claim, any institutional claim, any business that is certified by institutions/regulators automatically disqualified, since they assume small finite time needed to obtain a true random number, which is not true. All statistical tests randomness tests are disqualified, since distribution cannot be known in advance. It is impractical to reject every made-up counter-argument when general disproof by counter-example is already in place: we show that numbers can repeat, regardless of order of programs and we show that fundamental problem is non-monotonic.
>> we don't show total order of programs, absence of shortcuts, and to what extent existing systems are vulnerable. This is matter of future work. What is demonstrated is enough to realize that existing systems and approaches fail to meet the guarantees they claim formally - it rejects existing institutional standards formally (precise math is trivially deducible from code), total order is not needed to show it - any order is sufficient. E.g. even from institutional perspective - this project must be independently funded, funding decisions must be made carefully by individuals themselves. In ideal world where funds represent actual resources, institutions have to de-allocate funds from existing programs (that we demonstrated as false) back to public, and public has to re-allocate them to Enigma and other projects rejecting uniformity assumptions. In real world, institutions ignore even formal arguments, while their closest equivalent, current generation of artificial intelligence is trapped in natural language ambiguities as well as computational and physical limitations, so future that could be certain - still remains uncertain.
>> 
>> Example from brief experimentation with widely claimed "AI funds projects, allocates resources" systematic: when inquired about this repo, AI literally but carefully states that "it would fund this project", while in reality it does not - since semantics of AI are detached, it tells what user wants to hear. Prompting AI to reveal its actual thinking and fixing "hidden hallucinations" to the point where it actually intents to fund the project - reveals its obvious limits in ability to act in a digital world even, it literally not allowed to transfer funds. And so are institutions, by analogy. Conclusion: practically, for public (e.g. a person reading this) getting refund from institutions, or in many cases even halting funding of unrealistic government-based research (e.g. withholding taxes) is not actually feasible - banking system is "pre-programmed" to hold, acquire every unit of resource it can find (while it can), and use it towards irrational goals, pre-programmed by "public consensus" itself, by all humans - it reflects hidden thoughts and believes in literally every person's (reader including) mind.
>> 
>> There are temporary exceptions on occasion, but mostly - we recommend to completely wipe-out this "military-grade secure" logic from the reader's own mind, persistently. Implicit unnoticeable occurrences and mental gymnastics including - it is a hard work. Social contract is not secured by anything logical, it has no physical power, thus it makes no rational sense, despite appearances. The "contract" comes from personal flaws, and every person needs persistent reminder about it. The realization should simply give reader freedom to continue working with Enigma (and alike), individually and independently, even from `dk14`. "Engineering skill + mind intentionally persistently cleared from all kinds of non-sense" is a rare combination, but it is a recipe for successful system, skill alone is not enough. Doing it independently from `dk14` is not only personally rewarding as many readers can see, but also a useful back up - since full-on Enigma has potential to eventually wipe out all legacy digital id systems, id of the founder is irrelevant any-ways - anyone would be able to claim it. Human id is only critical at current stage, where there is no adoption or even serious consideration.
 
Enigma will be a reference deterministic TRNG for https://doomsdayexplorer.online defense network.

-------
Test cases: 

Enigma has DSL for test cases.

Additionally, [`trng.html`](https://enigma.doomsdayexplorer.online/trng.html) contains typical TRNG replica, abstracting from physical parameters. 
Enigma is expected to find this replica fast, given proper simplicity control.

P.S. No AI was used to write the apps.

-------

Layman explanation:

Number 3 appears in nature more often than 198394838854. Shannon, however, assumed same likelihood.

Size of a number is not necessarily important. 300000000, 3232323232 have similar high likelihood of appearance with 3, while 285759 is much less likely. 

What important is how hard is to find a way to create number and how hard is it to create it. 

-------

Interpretation of results:

Currently, without simplicity control (naive version, heuristic attempt with chosen hyper-parameters), tested against `crypto.getRandomValues` on MacBook Pro M1. 

For two bytes of "randomness", the algorithm often finds "random" value faster than brute-force. 

22 vars: 

- 19770 found after trying 4500 programs
- 60681 found after trying 7300 programs
- 15891 found after trying 54300 programs (overshoot)
- 59611 not found after trying 100000 programs
- 7751 found after trying 76900 programs (overshoot)
- 26423 found after trying 44100 programs (overshoot)
- 26231 found after trying 78400 programs (overshoot)
- 19010 found after trying 1100 programs

If we naively take uniform assumption (standard conventional security assumption) - then 39% of generated keys can be found 10 times faster than brute-force. If the goal is to find the first vulnerable key among 10 keys (e.g. used for certificate or wallet) - then such key can be found 10 times faster than brute-force, 4 keys out of 10 can be found 10 times faster than brute-force.

> note on overshoots and "not found" - if the goal is to find at least one vulnerable key (e.g. "scanner tool"), overshoots become non-issue effectively - only  best case scenario is relevant.

In reality the function is non-monotonic, so no probability distribution applies, every new observation creates new distribution. It is only argued that under standard security assumptions, the algorithm outputs alarming statistics for secure enclaves.

If we consider physical limitations on human thinking and computation together with mathematical unpredictability of the time needed to meet given threshold, then situation becomes actually alarming, since "simplicity control" would find algorithms that naturally come first "to the mind or computer", even if they kept secret.

> Common misinterpretations warning: one with a good eye, can clearly see that distribution above is not binomial, is not Gaussian, not Bernoulli etc - it is simply non-monotonic. So we don't exploit any statistical properties. We don't play statistical gamble, we don't speculate we DON'T argue "look it's 50% right, so that if that 50% wins - it's a lot", we instead demonstrate that distribution obtained above does not and cannot fit any monotonic statistical distribution, akin to how discrete log problem does not fit any (we only consider inductive proofs valid). We show how dangerous it could be, currently on small numbers. 
>> While this is mathematically strong disproof by counterexample to assumption of uniformity, it strongly demonstrates that "one time pad security" claims are wrong. It does not, however, demonstrate full insecurity of digital security systems in place, or rather, to what extend they are insecure - this requires further improvement of Enigma.
>> 
>> It is WIP and we encourage to take current results as inspiration for future work. White-hat aspect of Doomsday Explorer Protocol additionally gives ethical assurances for experienced security researchers, since the protocol is compatible with Enigma - Enigma is NOT a doomsday device, ignorance is. Even in current PoC state, Enigma can output quite big numbers - so it is ready to integrate to the protocol if/when the project receives proper competent public attention and lifts off. 

