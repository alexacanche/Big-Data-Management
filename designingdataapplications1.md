# Designing Data-Intensive Applications
 
## Chapter 1: Reliable, Scalable, and Maintainable Applications

### 1.  Exaplain each of the three component software systems must contain: 
- **Reliability:** Performing the correct function at the desired level of performance even in the face of adversity.
- **Scalability:** As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with that growth.
- **Maintainability:** Over time, many different people will work on the system (engineering and operations, both maintaining current behavior and adapting the system to new use
cases), and they should all be able to work on it productively.

### 2. Think of a software example and describe it for each point of the expectations of reliability in software
(answers may vary)
**GITHUB**
- Performs the function that the user expected. (upload a file)
- Tolerates user mistakes or using the software in unexpected ways. (selects files with the same name as the one that are already in the repository)
- Performs good enough under the expected load and data volume. (charges fast even though the file is heavy)
- Prevents any unauthorized access and abuse. (trying to edit the file of someone else without forking)

### 3. Write other three other tools that can help increase the fault-tolerance like the netflix chaos monkey.
(answers may vary)
Gremlin, pumba, chaos toolkit, simian army, powerfulSeal, litmus, etc.

### 4. Write an example of hardware, software and human errors (different from the book).
(answers may vary)
- **Hardware:** power grid has a blackout
- **Software:** a software bug that causes every instance of an application server to crash when given a particular bad input
- **Human:** no restrictions about inputs, for example, no letters while filling a phone number form.

### 5. Describe with your own words inn scalabilty, what is load.
(answers may vary)
Load can be described with a few numbers which we call load parameters. The best choice of parameters depends on the architecture of your system: it may be requests per second to a web server, the ratio of reads to writes in a database, the number of simultaneously active users in a chat room, the hit rate on a cache, or something else. Perhaps the average case is what matters for you, or perhaps your bottleneck is dominated by a small number of extreme cases.

### 6. Why is the median a better statistical metric han the mean to calculate performance in software?  
The mean is not a very good metric if you want to know your “typical” response time, because it doesn’t tell you how many users actually experienced that delay.
Usually it is better to use percentiles. If you take your list of response times and sort it from fastest to slowest, then the median is the halfway point: for example, if your median response time is 200 ms, that means half your requests return in less than 200 ms, and half your requests take longer than that. This makes the median a good metric if you want to know how long users typically have to wait: half of user requests are served in less than the median response time, and the other half take longer than the median.

### 7. Let's imagine you've have created a web page that currently has a small bunch of viewers but then an influencer talks about your web page and then, out of nowhere you start to get a lots of views, what system would you use? elastic system or scaled manually?
Elastic system, since you don't now when the people is going the mention of the influencer, you could have time when there a lots of people accesing your web page as well when a small quantity, therefore using elastic system would detect this and automatically add computing resources. 

### 8. In maintenance, what is operability and why is it important?
Operability makes it easy for operations teams to keep the system running smoothly. and a quote from the book could state its importance “good operations can often work around the limitations of bad (or incomplete) software, but good software cannot run reliably with bad operations.”

### 9. Why SQL is an example of abstraction?
SQL is an abstraction that hides complex on-disk and in-memory data structures, concurrent requests from other clients, and inconsistencies after crashes. Of course, when programming in a high-level language, we are still using machine code; we are just not using it directly, because the programming language abstraction saves us from having to think about it.

### 10. According to the text, Agile community has developed technical tools such as test-driven development (TDD), describe TDD.
“Test-driven development” refers to a style of programming in which three activities are tightly interwoven: coding, testing (in the form of writing unit tests) and design (in the form of refactoring).

It can be succinctly described by the following set of rules:
- Write a “single” unit test describing an aspect of the program
- Run the test, which should fail because the program lacks that feature
- Write “just enough” code, the simplest possible, to make the test pass
- “Refactor” the code until it conforms to the simplicity criteria
- Repeat, “accumulating” unit tests over time

