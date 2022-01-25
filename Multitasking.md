#async #os

Back in ye olden days of computing, PCs only had a single process that could only run one thing at a time. Things had to stop so that other things could execute, nothing went in parallel

First came **Cooperative Multitasking**: the ability for apps to `yield` within their code, which pauses and lets another app run.
```diff
- user applications actually have to call `yield` in their code, and if they don't then it would be a mess 
```
- This is why Windows systems based on DOS (and mac up through OS9) frequently crash and freeze our operating system, that's why you can drag windows around and they would cover your entire screen w/ copies of themselves

New system: **Preemptive Multitasking**: the ability for the OS to pause any application at any given time, save the state, and load another system in its place
- OS handles everything : introduced in Windows NT-4
- Some systems still use this today

Switch to Multithreading: to understand difference, see [[Processes vs Threads]]

Most current system: **Symmetric Multi Threading (SMT)**: harnessess multiple cores for better performance
- Exactly the same as **Hyperthreading**
- Runs 