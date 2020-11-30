# ART Synchronized

This repository provides an implementation of the Adaptive Radix Tree (ART) in a thread safe manner.
Two different synchronization schemes are used, Optimistic Lock Coupling and Read-Optimized-Write-Exclusion (ROWEX).

The techniques used are described in the following papers:

- ["The Adaptive Radix Tree: ARTful Indexing for Main-Memory Databases"](https://db.in.tum.de/~leis/papers/ART.pdf)
- ["The ART of Practical Synchronization": DaMoN 2016](https://dl.acm.org/citation.cfm?id=2933352)

## Required Packages
- cmake
- C++14 compiler

## Build Instructions
    mkdir build
    cd build/
    cmake ..
    make

## Execution Instructions
Run the example test with:

    ./example n 0|1|2
    
    n: number of keys
    0: sorted keys
    1: dense keys
    2: sparse keys

## License
Copyright 2015-2016 Florian Scheibner

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
