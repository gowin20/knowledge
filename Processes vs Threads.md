| Processes                                               | Threads                          |
| ------------------------------------------------------- | -------------------------------- |
| Top-level container for execution (like an application) | runs within a process            |
| dedicate memory space in the OS                         | shared memory space              |
| must use Inter-Process Communication to talk (similar to networking requessts)      | lots of communication between em |
|                                                         |                                  |

Tasks and Processes are basically interchangable in the kernel, but Threads are actually pretty different!

Processes are 

Communication between processes usually uses `json.stringify`, which is limited with low performance.


## [[Processes]]
```diff
- bad communication
+ very safe
+ separate memory
```


## [[Threads]]
```diff
+ shared memory allows easy sharing, e.g. globals
- synchronization required with sharing, otherwise unpredictable behavior
```

Threads allow for [[race conditions]] which need to be handled in some way.