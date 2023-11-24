# parallel-algorithms
A collection of practical work performed in the process of studying the topic "Parallel Algorithms"

## ➕ Matrix addition
In this work, the execution time of adding two matrices of size N * M was compared in 3 ways:
1) One process for each operation: reading, matrix addition, writing the result;
2) One thread for each operation: reading, matrix addition, writing the result;
3) One thread for each operation: reading and writing the result. Multiple threads for matrix addition.

The following conclusions were obtained during the study:
1) The sizes of the matrices have a great influence on the execution time of the program;
2) The characteristics of the computing system also greatly influence the execution time of the program;
3) Increasing the number of threads does not always lead to faster task execution. It is necessary to find the optimal number of threads for a task of a certain complexity, otherwise most of the time will be spent on initializing these threads than on their work.

To run the program, enter the following commands:
```
// Matrix generator
make generator
./generate-matrices.out <number of rows> <number of columns>
```
```
// Processes
make process
./process.out <number of rows> <number of columns>
```
```
// Thread
make thread
./thread.out <number of rows> <number of columns>
```
```
// Threads
make threads
./threads.out <number of rows> <number of columns> <number of threads>
```

Directory: `./matrix-addition`

## 🔄 Producer-consumer problem
This program solves the producer-consumer problem in the field of matrix addition. 3 buffers are created: a storage of the first matrices, a storage of the second matrices, and a storage of the sum of the first and second matrices.
Also, as in the previous work, matrix addition is possible using multiple threads.

To run the program, enter the following commands:
```
make
./a.out <number of rows> <number of columns> <number of threads> <number of iterations>
```

Directory: `./producer-consumer`

### Compare-and-Swap
The previous program was rewritten using CAS. Performs similar actions.

To run the program, enter the following commands:
```
cmake .
./a.out <number of rows> <number of columns> <number of gen & add threads> <number of threads for one matrix> <number of iterations>
```

Therefore, if N gen & add threads and M iterations are introduced, the result will be N*M matrices (each thread performs M iterations).

Directory: `./compare-and-swap`
