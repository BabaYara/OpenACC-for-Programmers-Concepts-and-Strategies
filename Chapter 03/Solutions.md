Compiled and run on a laptop with a GTX 1060 GPU. Saw a 100% reduction in speed from the serial version after the initial acceleration. 

Turns out you need to target GPUs with compute capability 6.0 to see the level of speed up reported in the book. I ended up with a code that run at 1.9 seconds compared to the serial version that was running at around 19 seconds on my system. 
