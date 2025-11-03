# Assignment 4

## Exercise 9

### Exercise 9.3.1 and 9.3.2

The test results are saved on PerformanceTestCountPrimesThreads.txt in the in /exercise09 folder.

Best measured time ~1.33 ms at 4 threads and degrading after ~4–8 threads, with clear slowdown when threadCount reaches 30–32 (oversubscription + contention). My laptop is aarch64 macOS with 10 cores. It has a mix of "performance" (P) and "efficiency" (E) cores (8P+2E) so the 10 reported cores are not identical.

Since I have few tabs open in VSC it is possible that there are only 4 high‑performance cores fully available, therefore, this may explain why we see peak throughput around that number rather than the full 10. When threadCount exceeds the number of fast hardware contexts (or when threads outnumber available hardware), the OS must time-slice threads. This increases context-switch overhead and cache miss rate (as Peter S. explained during his lecture in the Applied Algorithms course), hurting throughput.

The fact that many thread counts between 2..29 show similar good results (256 iterations) suggests moderate scaling up to some point - maybe as a consequence of the extra cost of creating and running yet another Thread; the sudden worsening above ~28–30 threads is likely a consequence of context switching.

The presence of 256 vs 128 counts is the benchmark deciding how many iterations it needs to reach its timing threshold, and it flips as measured throughput changes.

### Exercise 9.4.2

Occurences of ipsum: 1430

### Exercise 9.4.3

WordSearch 6314141.1 ns (runtime)   31749.71 (standard deviation)   64(iterations)

### Exercise 9.4.5

The test results are saved on PerformanceTestTimeSearch.txt in the in /exercise09 folder.

I measured the sequential run at about 6.31 ms and saw the parallel version drop to roughly 2.17 ms (about 3x speedup); Mark7’s iteration count changed from 64 to 128 for the faster runs because the harness adapts to reach its timing threshold. This shows the per-line string processing dominates the cost, so splitting the lines across threads yields real speedup and the shared counter does not seem to bottleneck the workload here — hence good scaling up toward the machine’s ~10 logical processors.

That contrasts with the benchmark on exercise 9.3, where counter contention and the difference performance of the cores seems to have pushed the optimum down to a few threads. Also, at no point does the Parallel counter reach running times anywhere close to those of the Sequential execution - unlike in exercise 9.3.
