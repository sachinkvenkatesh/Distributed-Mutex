# Distributed-Mutex
Implementation of Raymond's algorithm - tree based distributed mutual exclusion algorithm

A token based mutual exclusion algorithm - here a spanning tree of the nodes/systems in the network is contructed and a token is passed along the tree nodes. The node that has the token can enter critical section

## Implementation
CSEnter() and CSLeave() are the services that has been provided for the application.
The application is blocked on requesting to enter critical section. Once the node gets the token, the system can enter critical section. On completion of critical section the applicaiton calls csLeave().
A queue is maintained at each node to keep track of its adjacent tree-node requests. On leaving the critical section, the system/node checks the queue - if it has any requests pending, the token is passed to a node at the top of the queue.

## Testing
To test the critical section, all nodes on entering critical section a file-write operation is performed. If there is any critical section overlap, based on the time-stamp(assuming that all the clocks are synchronized) of the critical sections it can be determined.

## Variants
1. Greedy - Critical section request of its own (node) is given preference
2. Non-Greedy - Critical Section request based on the request made irrespestive of the node.

## Experimental Evaluation
 Message Complexity, Response time and Throughput were measured on varying -
 1. n : number of requests made by each node
 2. d : inter-request delay 
 3. c : critical section time
 
 Results are in report.txt
