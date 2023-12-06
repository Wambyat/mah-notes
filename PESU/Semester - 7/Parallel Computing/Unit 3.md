# Unit 3

## CUDA

GPU has a lot more computation but a LOT LESS CACHE. 

<img title="" src="../../../images/2023-12-03-23-12-10-image.png" alt="" data-align="center" width="615">

This is the best quality I found 😭.

CUDA is Compute Unified Device Architecture. User does batch execution. <img src="../../../images/2023-12-03-23-16-03-image.png" title="" alt="" width="553"> <== this is how we launch a batch. The GPU had its own device memory. 

nvcc, also called cuda compiler, hijacks cuda specific code and converts/compiles it. It seperates device code and host code.

<img title="" src="../../../images/2023-12-03-23-18-02-image.png" alt="" data-align="center" width="426">

CUDA library ==> CUDA Runtime ==> CUDA Driver ==> Device. The application can speak to all 3 of these CUDA parts.

CUDA is SPMD Single program multiple data. A CUDA kernel is the code that is being run. A block is a group of threads running the same kernel. A group of blocks is a grid. 

Threads in a block communicate with shared memory, global memory, atomic operations and barriers. Threads in different blocks communicate ONLY with global memory.

I don't know what an "SM" is but we fit blocks into it. Probably ~~shared memory~~? It is Streaming Multiprocessor. Mini CPU core for CUDA/GPU. One optimization implemented is when an SM is not used fully we give the rest to another block.

Basic cuda code:<img src="../../../images/2023-12-03-23-30-44-image.png" title="" alt="" width="327"><img src="../../../images/2023-12-03-23-34-11-image.png" title="" alt="" width="494">

32 groups of parallel threads are executed. These are called "wraps". All threads need not executed identically. Some threads could potentially branch out. But eventually all of them sync up. 

In kernel invocation, A can be a 2D vector. B can be a 3D vector. A will be referencing  grid based. 

#### CUDA memory:

<img title="" src="../../../images/2023-12-03-23-39-51-image.png" alt="" data-align="center" width="900">

Before most of this was not cached, now everything is cached. `cudaMalloc((void**)&Md,size)` allocates in the global memory. We can also get "page-locked" memory, i.e. host memory. Shared memory is saved into "banks" <== not explained. Texture memory is not discussed. It is different from the rest. It is more focused on graphics applications.

<img src="../../../images/2023-12-03-23-51-56-image.png" title="" alt="" data-align="center">

device func can;t have address on host.

Functions executed on the device cannot have static variables or dynamic number or arguments. OLD ass versions also does not support recursion.

<img title="" src="../../../images/2023-12-04-00-00-54-image.png" alt="" data-align="center">

Pointers are resolved (global or shared) at compiler time ONLY in 1.x versions.

Matrix multiplication example :)

<img title="" src="../../../images/2023-12-04-00-07-19-image.png" alt="" width="475"><img src="../../../images/2023-12-04-00-06-04-image.png" title="" alt="" width="610">

Ways to sync threads in a block:

<img title="" src="../../../images/2023-12-04-00-08-34-image.png" alt="" width="648" data-align="center">

Last 3 are 2.x and above ONLY. We can also do sync in a wrap. 

<img title="" src="../../../images/2023-12-04-00-10-23-image.png" alt="" width="562" data-align="center">

Atomic operations are read-modify-write on one 32 or 64 bit word in global or shared memory. If target is page locked memory, the operation is not atomic from the host's perspective. CAS is Compared and Swap/Set.

nvcc has a device emulation mode. Not very good but decent enough for debugging and general use. 

There are a few code examples shown. It confused me and the prof so im not putting it.

#### Memory fences:

<img title="" src="../../../images/2023-12-04-11-20-56-image.png" alt="" data-align="center" width="774">

#### Streams

This is a "high" level thread. This is generally used to ensure concurrency. Multiple streams run at the same time, HOWEVER, stream 0 runs alone. Streams appear to be sequential to the system. If we do not specify a stream it is sent to stream 0

<img title="" src="../../../images/2023-12-04-11-32-38-image.png" alt="" data-align="center" width="650">

<img title="" src="../../../images/2023-12-04-11-34-04-image.png" alt="" data-align="center" width="660">

<img title="" src="../../../images/2023-12-04-11-36-25-image.png" alt="" data-align="center" width="670">

Scheduling is done based on the CUDA version. The version is often hardware dependent. 

for example for 1.x <img src="../../../images/2023-12-04-11-40-50-image.png" title="" alt="" width="226"><img src="../../../images/2023-12-04-11-40-05-image.png" title="" alt="" width="385">

In 2.0: <img title="" src="../../../images/2023-12-04-11-40-34-image.png" alt="" data-align="center" width="656">

##### Control flow

Conditions should be written in a way to minimize divergent wraps. So we can arrange wraps such that all threads in the wrap have the same condition flow. Avoid using syncthreads. Try to instead just write to shared memory or something in that nature. Getting data from global memory and things like that is A LOT slower, so optimize with shared/ local memory. ~~The cache line size if also LARGE in global memory so it is unoptimized in terms of fetching fragmented memory.~~ 

<img title="" src="../../../images/2023-12-04-11-53-14-image.png" alt="" data-align="center" width="729">

<img title="" src="../../../images/2023-12-04-11-54-46-image.png" alt="" data-align="center" width="723">

So if the array width is not a multiple of 16, `cudaMallocPitch()` will pad the memory. 

Check the other notes also pls.

END OF CUDA