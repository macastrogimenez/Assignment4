# Exercise 9.2

OS: Mac OS X; 26.0.1; aarch64
JVM: Homebrew; 17.0.16
CPU: null; 10 "cores"

non-volatile inc 0.5 ns 0.03 536870912
volatile inc 1.7 ns 0.01 268435456

OS: Mac OS X; 26.0.1; aarch64
JVM: Homebrew; 17.0.16
CPU: null; 10 "cores"

non-volatile inc 0.5 ns 0.02 536870912
volatile inc 1.7 ns 0.05 268435456

OS: Mac OS X; 26.0.1; aarch64
JVM: Homebrew; 17.0.16
CPU: null; 10 "cores"

non-volatile inc 0.5 ns 0.00 536870912
volatile inc 1.7 ns 0.01 268435456

Are they plausible?
Yes. Volatile is 3.4x slower because it forces memory synchronization on every write,
preventing CPU caching and compiler optimizations.
Non-volatile variables can be cached in registers and heavily optimized by the JIT compiler.

Any surprises?
Only 3.4x slower, whereas on x86 architectures volatile is typically 10-20x slower.
Extremely fast, both operations complete in under 2ns
