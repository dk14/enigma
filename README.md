This repo contains Enigma webapp demonstrating enumeration of all possible terminating programs (`index.html`).

Abstract machine has sum, diff and times (dynamically aka dependently bounded recursion) operations making it computationally complete.

Static termination check: DAG means terminating program.

Static memoization ensures no equivalent algorithms are enumerated.

Simplicity control (to be improved): from simplest to most complex programs, thus from simplest to most complex outputs.

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


