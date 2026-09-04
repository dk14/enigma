This repo contains Enigma webapp demonstrating enumeration of all possible terminating programs (`index.html`).

Abstract machine has sum, diff and times (dynamically aka dependently bounded recursion) operations making it computationally complete.

Static termination check: DAG means terminating program.

Static memoization ensures no equivalent algorithms are enumerated.

Simplicity control (to be improved): from simplest to most complex programs, thus from simplest to most complex outputs.

> Simplicity control will employ advanced form of memoization, discovering functionally equivalent sub-graphs (forall x. f(x) = g(x)). Programs containing more recursion will be considered more simple in order to establish total order, unique in its expressive optimality. Hyper-parameter search will recursively re-use Enigma itself as generator for computationally natural orders (of parameters).
>> This way it would model high-level reasoning of humans, start with programs that are physically easier for human programmer or mathematician to write out of most fundamental operations.
>> 
>> Length of the program does not imply its simplicity directly. Length of canonical (most expressive program) as measured in amount of Enigma-variables it employs is first, but not the only parameter to order programs fundamentally.

--------

Security applications:
- this, in theory, is attack on one-time pad. **Shannon's fundamental assumption of uniformity is rejected**:
   - output, that is easiest to compute with "no-input" program that is easiest to find, has higher probability of appearance
- true random is defined as "hardest to compute from known numbers, up to security threshold"
  - for a given security threshold (e.g. minimum 100Kwh energy spent on computation) amount of resources needed to actually satisfy it is more than threshold itself and unpredictable: spending nominal amount does not guarantee the number will be unique. E.g. no planned economy can satisfy true randomness.
 
Enigma will be a reference deterministic TRNG for https://doomsdayexplorer.online defense network.

> Shannon's entropy only applicable in cases where the whole set of events under consideration is already fully computed, stored and readily accessible, as well as selection procedure, which is not the case in security. Shannon's entropy is loosely applicable to pseudo-random generation (lottery, coin-toss), which is not applicable in security: e.g. outcome of a coin-toss is predictable from initial state and distance traveled: `(init + distance) mod 2`, slight periodic change of initial state and distance gives illusion of randomness.

-------
Test cases: 

Enigma has DSL for test cases.

Additionally, `trng.html` contains typical TRNG replica, abstracting from physical parameters. 
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

In reality the function is non-monotonic, so no probability distribution applies, every new observation creates new distribution. It is only argued that under standard security assumptions, the algorithm outputs alarming statistics for secure enclaves.

If we consider physical limitations on human thinking and computation together with mathematical unpredictability of the time needed to meet given threshold, then situation becomes actually alarming, since "simplicity control" would find algorithms that naturally come first "to the mind or computer", even if they kept secret.

> Common misinterpretations warning: one with a good eye, can clearly see that distribution above is not binomial, is not Gaussian, not Bernoulli etc - it is simply non-monotonic. So we don't exploit any statistical properties. We don't play statistical gamble, we don't speculate we DON'T argue "look it's 50% right, so that if that 50% wins - it's a lot", we instead demonstrate that distribution obtained above does not and cannot fit any monotonic statistical distribution, akin to how discrete log problem does not fit any (we only consider inductive proofs valid). We show how dangerous it could be, currently on small numbers. 
>> While this is mathematically strong disproof by counterexample to assumption of uniformity, it strongly demonstrates that "one time pad security" claims are wrong. It does not, however, demonstrate full insecurity of digital security systems in place, or rather, to what extend they are insecure - this requires further improvement of Enigma.
>> 
>> It is WIP and we encourage to take current results as inspiration for future work. White-hat aspect of Doomsday Explorer Protocol additionally gives ethical assurances for experienced security researchers, since the protocol is compatible with Enigma - Enigma is NOT a doomsday device, ignorance is. Even in current PoC state, Enigma can output quite big numbers - so it is ready to integrate to the protocol if/when the project receives proper competent public attention and lifts off. 

