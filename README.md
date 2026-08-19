This repo contains webapp demonstrating enumeration of all possible terminating programs.

Abstract machine has sum, diff and times (dynamically aka dependently bounded recursion) operation making it computationally complete.

Static termination check: DAG means terminating program.

Static memoization ensures no equivalent algorithms are enumerated.

Simplicity control (to be improved): from simplest to most complex programs, thus from simplest to most complex outputs.

--------

Security applications:
- this, in theory, is attack on one-time pad. Shannon's fundamental assumption of uniformity is rejected:
   - output, that is easiest to compute with "no-input" program that is easiest to find, has higher probability of appearance
- true random is defined as "hardest to compute from known numbers, up to security threshold"
  - for a given security threshold (e.g. minimum 100Kwh energy spent on computation) amount of resources needed to actually satisfy it is more than threshold itself and unpredictable. E.g. no planned economy can satisfy true randomness.
