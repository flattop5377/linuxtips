---
layout: post
title:  "Help fix lag by assigning specific CPU cores to processes"
---

## Goals

  * Reduce SSH lag and help other processes run faster on Virtual machines.

## Reduce SSH lag

It's possible, with qemu's smp emulation, that multiple processes are competing
for the same physical cores which causes lag. In my case I have sufficient cores
and just want to reduce lag.

If the process is already running, get the Process ID and then use taskset
```
ps -uax | grep qemu
taskset <cores> -p <process id>
```

If the process isn't running, just use taskset first:
```
tasket <cores> <command line>
```

## Next Steps

I also use sar from the systat package to monitor for resource bottlenecks.
