# Dynamic Value Challenges for CTFd

It's becoming commonplace in CTF to see challenges whose point values decrease
after each solve.

This CTFd plugin creates a dynamic challenge type which implements this
behavior. Each dynamic challenge starts with an initial point value and then
each solve will decrease the value of the challenge until a minimum point value.
Within CTFd you are free to mix and match regular and dynamic challenges.

The current implementation requires the challenge to keep track of three values:

 * Initial - The original point valuation
 * Decay - The amount of solves before the challenge will be at the minimum
 * Minimum - The lowest possible point valuation

The value decay logic is implemented with the following math:

```
ceil(initial - (initial * log(x=solve_count, base=decay)))
```

If the number generated is lower than the minimum, the minimum is chosen
instead.

# Installation

1. Clone this repository to `CTFd/plugins`. It is important that the folder is
named `DynamicValueChallenge` so CTFd can serve the files in the `assets`
directory.