# Launching Parallel Kernels

The execution configuration allows programmers to specify details about launching the kernel to run in parallel on multiple GPU threads. More precisely, the execution configuration allows programmers to specifiy how many groups of threads (called thread blocks) and how many threads they would like each thread block to contain. The syntax for this is:

```
<<<NUMBER_OF_BLOCKS, NUMBER_OF_THREADS_PER_BLOCK>>>
```

The kernel code is executed by every thread in every thread block configured when the kernel is launched. The image below corresponds to `<<<1, 5>>>`:

![thread-block](https://miro.medium.com/max/1118/1*e_FAITzOXSearSZYNWnmKQ.png)


## CPU Code

```c
#include <stdio.h>

void firstParallel()
{
  printf("This should be running in parallel.\n");
}

int main()
{
  firstParallel();
}
```

## Exercise: GPU implementation

```
# rewrite the CPU code above so that is runs on a GPU
```

Run your GPU code with different values of `NUMBER_OF_BLOCKS` and `NUMBER_OF_THREADS_PER_BLOCK` to see how the execution configuration works.

```
$ cd 06a_first_parallel
$ vim first_parallel.cu   # edit this file (use a text editor of your choice)
$ nvcc -o first_parallel first_parallel.cu
$ sbatch job.slurm
```

One possible solution to this exercise is [here](solution.cu).