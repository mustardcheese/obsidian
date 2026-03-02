What does locking enforce?
- Enables exclusivity of access over critical sections

Data Race:
Two unordered accesses to the same location in memory, where at least one is a write

What does "unordered" mean?
- Locks DO add some kind of order
- We can't exactly specify which thing happens when BUT some kind of order between threads is achieved with locks

**Locks enable dynamic ordering**
- We can determine some partial order after a lock hits
- Reduces the space of possibilities

### Weak Ordering (Relaxed Consistencies)
- Hardware, compiler can reorder reads and writes so long as it is still correct from the executing thread's perspective
- Weak ordering doesn't concern with correctness across threads
- fill in

Locks acquire and release happen in a partial order
- Acquire -> all subsequent reads/writes in the current thread happen **after**
- Release -> all preceding reads/writes in the current thread happen **before**

### Race Conditions

take the photos from the slides
data race: things try to read and write

slides slides slides (it all makes sense just put in photos)
- partial order means the correct r/w of t1 and t2, but it could be swapped
- fully ordered me there's exactly one globally visible sequence

It works because in the semantics of acquire, there's an edge representing a 'happen-before' relation between acquire and the actually executable code
There is also a 'happen-before' relation between the threads of executions
It is then mathematically provable that one green block happens before/after another because of the transitivity of the happen-before relation
- partial order means it exists twice (SLIDES!)
we can mathematically prove the correctness of the programs

## Producer Consumer
Keep track of:
- safety -- thread safe?
- liveness -- deadlock?
- efficiency -- efficient?
Correctness First -> Efficiency second
- Overlock if necessary, but efficiency later

Producer:
- Adds elements to a queue
Consumer:
- As long as there are elements, remove them
- If there are no elements, **wait** for the next element
Concept: waiting
- Notion of waiting can't be done just by the mutex alone
Goal:
- Computationally efficient waiting primitive
- Ordering primitive (P -> C)
```
Produce(int v){
	lock(lk);
	
	q.push();
	
	unlock(lk);
	
Consume(){
	lock(lk);
	
	v = q.pop();
	
	unlock(lk);
	return v;
}
```

**Because mutexes only guarantee partial order, we might run consume (bad) before produce is done**
- Safety -- bad
- Liveness -- fine
- Efficiency -- bad


```
Produce(int v){
	lock(lk);
	
	q.push();
	
	unlock(lk);
	
Consume(){
	lock(lk);
	
	if(!q.empty()){
		v = q.pop();
	}
	
	unlock(lk);
	return v;
}
```
- Safety -- fine, checks
- Liveness -- fine, no deadlocks
- Efficiency -- bad, either inside or outside consume, we'll have to keep checking if the queue is empty, causing a busywait and reducing efficiency
### Conditional Variables

```
Produce(int v){
	lock(lk);
	
	q.push();
	
	unlock(lk);
	
Consume(){
	lock(lk);
	
	if(!q.empty()){
		cv.wait(lk);
	}
	v = q.pop()
	
	unlock(lk);
	return v;
}
```
- Safety -- fine
- Liveness -- bad, there's no signal to free the cv so deadlocks
- Efficiency -- fine, no more busywaiting

```
Produce(int v){
	lock(lk);
	
	q.push();
	cv.signal();
	
	unlock(lk);
	
Consume(){
	lock(lk);
	
	if(!q.empty()){
		cv.wait(lk);
	}
	v = q.pop()
	
	unlock(lk);
	return v;
}
```
- Safety -- bad, spurious wakeup
- Liveness -- fine, no deadlocks
- Efficiency -- fine, no busywaiting

But what about multiple consumers?
- While one consumer is grabbing the lock after the signal, another consumer might snipe it
- The check happens, one pop, two pop, and causes a safety violation

```
Produce(int v){
	lock(lk);
	
	q.push();
	cv.signal();
	
	unlock(lk);
	
Consume(){
	lock(lk);
	
	while(!q.empty()){
		cv.wait(lk);
	}
	v = q.pop()
	
	unlock(lk);
	return v;
}
```
- Safety -- fine, eliminated spurious wakeups
- Liveness -- fine, no deadlocks
- Efficiency -- fine, no busywaiting

### Signal Ordering
son im crine fill in the rest of the lecture before i shit myself this dude teaches too fucking slow swear