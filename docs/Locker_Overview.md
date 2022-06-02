# Overview

The Locker module allows any CMST holder to earn variable interest on their principal by locking their CMST into the Locker vault in the Harbor Protocol. Users aren’t required to deposit a minimum amount of CMST to earn the interest from the vault and they can withdraw any or all of their CMST from the vault at any time.

Locker Stability Rate ( LSR) is the term used to define the interest rate applied in the Locker module. This interest rate is also compounded per block ( just like the stability fee) and added back per block to the principal in the user’s locker. This sum now becomes the principal for the next block. To estimate the calculations easily, LSR should be calculated annually as per the equation and example below. The calculation of the interest earned per block is computed with the Rewards module.
