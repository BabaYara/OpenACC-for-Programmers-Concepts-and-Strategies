## Question 1
Basically including a gang or worker loop in a vector loop can lead to the parallisation of loops with dependent data structures and we do not want that.
There is also the issue of efficiency. A vector loop is best used as the inner most loop and a gang loop as the outter most.

## Quesion 2
One would generally consider the statement as meaning "the order of operation not being important". There are a few counter examples that prove the point (I should come back to them at one point in time)

## Question 3
Same problem as before. There are a few involved counter examples that show that this statement need not be true. 

## Queestion 4
