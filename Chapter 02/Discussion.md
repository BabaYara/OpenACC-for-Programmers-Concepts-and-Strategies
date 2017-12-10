### Soltuions

## 1. 
Sequential version of the program compiled and run on an intel 7th gen laptop CPU with no acceleration takes about 0.0099 seconds to complete.

Sequential version run on the GPU with "!$acc loop seq" directive takes about 0.0181 seconds to complete.
 
The version that uses the parrallel directive without adding a clause runs the same program on all avaiable GPU SMs and so runs slower. Takes around 0.4683 seconds to finish.

The version with the ```!$acc parallel``` directive plus the clause ```loop``` takes about as long as the version with the no loop clause. 

I think the purpose of problem one is to show that you can run the same program on one GPU thread or a dozen and see no speed up if it is not correctly parallised. 


