### Soltuions

## 1. 
Sequential version of the program compiled and run on an intel 7th gen laptop CPU with no acceleration takes about 0.0099 seconds to complete.

Sequential version run on the GPU with "!$acc loop seq" directive takes about 0.0181 seconds to complete.
 
The version that uses the parrallel directive without adding a clause runs the same program on all avaiable GPU SMs and so runs slower. Takes around 0.4683 seconds to finish.

The version with the ```!$acc parallel``` directive plus the clause ```loop``` takes about as long as the version with the no loop clause. 

I think the purpose of problem one is to show that you can run the same program on one GPU thread or a dozen and see no speed up if it is not correctly parallised. 

## 2

I first compile and run the program on the CPU without any acceleration directives. passing_count has 10,000 as its last element as we would exect. Redo the execrise with the acceleration directives and now passing_count has a random value between 1-10,000 because GPU threads update this address space in paralllel. Which means we are not guarranted the sequential update required to arrive at last passing_count = 10,000. 

My implementation of the parallel GPU version of the problem did not confirm my prior. The compiler seems smart enough to take out passing_count and loop that of the code sequentially leading to no weird behaviour but you cannot guarrantee this correction all the time.

## 3
The code in the book takes about 0.3669 seconds to complete and this is down to not using as much of the hardware as possible. We are only parallelising the main outerloop. We can speed up things by using the collapse clause to collpase the whole nested loop construct into a single loop which parallelises across all available hardware/nodes. This implementation takes about 0.3607 seconds. 
