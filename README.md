# parallel-algorithms
A collection of practical work performed in the process of studying the topic "Parallel Algorithms"

## ➕ Matrix addition
In this work, the execution time of adding two matrices of size N * M was compared in 3 ways:
1) One process for each operation: reading, matrix addition, writing the result;
2) One thread for each operation: reading, matrix addition, writing the result;
3) One thread for each operation: reading and writing the result. Several threads for matrix addition.

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

