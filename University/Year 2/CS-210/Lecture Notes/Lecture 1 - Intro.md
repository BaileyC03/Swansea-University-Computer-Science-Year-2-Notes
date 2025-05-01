#### What is concurrency?
- Simultaneous occurrence of events
- **Sequential task** - task running on its own, no sharing / complications
	- 1 Thread of control. (no **sharing**)
	- Easy, can just do it (if you make a mistake, program will crash)
- **Concurrent Tasks** - Multiple tasks running simultaneously
	- Multiple threads of control - concurrent software (**sharing**)
	- Tasks are competing for resources

#### INTERCONNECTED SYSTEMS:
- Multiple machines might need to share / access the same resources
- Single machine -> Shared memory interactions
- Multiple machines -> Network interactions

#### RACE CONDITION:
When an outcome depends on which thread wins the "race"
The result depends on lucky timing.
A concurrent programme is **non-deterministic**
Single lines of code are generally not **atomic**
// We must handle this problem //

#### BENEFITS OF CONCURRENT PROGRAMMING:
- Performance Gain
- Increased application throughput (avoids IO polling or waiting)
- Increased application responsiveness
- Better structure for complex programs which interact with the environment around it / controls multiple activities / handles multiple events.

#### 4 MAIN OBJECTIVES:
- Learn how to develop practical applications without interference
- To understand and analyse subtle + complex problems in concurrent systems
- To describe and reapply core algorithms and strategies to reliably solve these problems
- To recognise the link between theoretical models and their practical application

#### COMPONENTS:
- Lab (10%)
- Coursework(20%)
- Exam (70%)

#### READING LIST:
- Oracle documentation on javase concurrency
- jenkov.com java concurrency
- Concurrency State Models & Java Processing Jeff Magee
	- Maybe audiobook this? 

#### SUMMARY:
- Goal is to reason about concurrent systems which we intend to build
- Learn to use FSMs for this purpose and use the LTSA tool to analyse model driven design
- Use java to implement concurrent programmes
