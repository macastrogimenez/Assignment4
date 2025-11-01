# Assignment 4
 ## Exercise 7.1
 ### 7.1.1
 Yes, this execution is sequentially consistent. The order:
 ```<q.enq(x), q.enq(y), q.deq(x)>```
 ### 7.1.2
 Its not linearizable, because before ``` q.deq(x)``` there should be ```q.enq(x)```, and in the provided configuration it is not possible, because ``` q.deq(x)``` ends before ```q.enq(x)``` begins. So the reason is that it does not satisfy the real time ordering. (Its impossible to define linearization points within each method call, which map to 
 sequential execution that satisfy the specification of the object)

 ### 7.1.3
 Yes, it is linearizable because we can provide linearization points within each method call, which map to sequential execution that satisfy the specification of the object.
 We can for example choose point at the very beggining of method ```q.enq(x)``` call, and then choose a point at the end of method ```q.deq(x)``` call (importatnt part is to choose the point that is later than the point we have chosen for enqueue). So the linearization is:
 ```<q.enq(x), q.deq(x)>```

 ### 7.1.4
 Its not linearizable, because its not sequentally consistant - There is no option to order these method calls so that program order is preserved and the execution satisfies the specification of the object. Possible options that would keep the real time ordering are:
 <q.enq(x), q.deq(y), q.enq(y)> 
 <q.enq(x), q.enq(y), q.deq(y)>
 <q.deq(y), q.enq(x), q.enq(y)>  
But because of specification of FIFO queue, none of them is correct, because x is always enqueued first, so it has to get off the queue first (before q.deq(y) is called).