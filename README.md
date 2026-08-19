This repo contains Enigma webapp demonstrating enumeration of all possible terminating programs (`index.html`).

Abstract machine has sum, diff and times (dynamically aka dependently bounded recursion) operations making it computationally complete.

Static termination check: DAG means terminating program.

Static memoization ensures no equivalent algorithms are enumerated.

Simplicity control (to be improved): from simplest to most complex programs, thus from simplest to most complex outputs.

--------

Security applications:
- this, in theory, is attack on one-time pad. Shannon's fundamental assumption of uniformity is rejected:
   - output, that is easiest to compute with "no-input" program that is easiest to find, has higher probability of appearance
- true random is defined as "hardest to compute from known numbers, up to security threshold"
  - for a given security threshold (e.g. minimum 100Kwh energy spent on computation) amount of resources needed to actually satisfy it is more than threshold itself and unpredictable. E.g. no planned economy can satisfy true randomness.
 
Enigma will be a reference deterministic TRNG for https://doomsdayexplorer.online defense network.

-------
Test cases: 

Enigma has DSL for test cases.

Additionally, `trng.html` contains typical TRNG replica, abstracting from physical parameters. 
Enigma is expected to find this replica fast, given proper simplicity control.

P.S. No AI was used to write the apps.
