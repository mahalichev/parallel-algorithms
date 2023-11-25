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

### ➡️ Compare-and-Swap
The previous program was rewritten using CAS. Performs similar actions.

To run the program, enter the following commands:
```
cmake .
./a.out <number of rows> <number of columns> <number of gen & add threads> <number of threads for one matrix> <number of iterations>
```

Therefore, if N gen & add threads and M iterations are introduced, the result will be N*M matrices (each thread performs M iterations).

Directory: `./compare-and-swap`

## ✖️ Matrix multiplication
This program allows you to compare the speed of performing matrix multiplication using the usual method and the Strassen "fast" multiplication algorithm.
During the work, it was discovered that matrix multiplication using the Strassen algorithm is faster than parallel multiplication, which becomes especially noticeable for large matrix sizes.

The reason for reducing the multiplication time is to reduce the complexity of performing this operation from $O(n^3)$ to $O(n^{2.81})$.

To run the program, enter the following commands:
```
cmake .

// Parallel multiplication
./a.out d <first matrix rows number> <first matrix columns number> <second matrix columns number> <number of gen & add threads> <number of threads for one matrix> <number of iterations>

// Strassen algorithm (depth - maximum recursion depth)
./a.out s <first matrix rows number> <first matrix columns number> <second matrix columns number> <depth> <number of gen & add threads> <number of threads for one matrix> <number of iterations>
```

Directory: `./matrix-multiplication`

## 🎨 Mandelbrot set
This program implements the calculation of the Mandelbrot fractal in OpenCL, where each execution thread executes the kernel code located in the Mandelbrot.cl file,
thereby determining the color of the pixel for which this execution thread is responsible.
When comparing the execution time of calculations on the processor and on the GPU, it was revealed that the program runs much faster on the GPU due to the presence of a larger number of computing cores.

To run the program, enter the following commands:
```
cmake .
./a.out <width> <height> <iterations> <scale> <offset X> <offset Y>
```

Directory: `./mandelbrot`

![image](https://github.com/mahalichev/parallel-algorithms/assets/54910038/3829b538-a959-43d4-a7f9-fc367d5ff3c2)
