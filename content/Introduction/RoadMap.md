# Roadmap to the Kingdom of Computer Science

Inspired by [Karim's blog](https://www.afternerd.com/blog/learn-computer-science/), this post aims to provide an overview of skills required to become a computer scientist. 

## 1. Programming / Coding

Programming is normally the most first skill to be learned for whoever want to enter the world of computer science. Printing `Hello World` becomes the first lesson of many languages, and yes, welcome to the virtual world. Programming is not only the first step, but a significant part in your whole computer science life, because coding is the most sufficient way to communicate your high-level ideas with "stupid" machines. 

The most frequently asked question from beginners is "What language should I learn?" or "What is the perfect language to start?". Karim said in his blog:
> (The perfect language) "a) it doesn’t exist, and b) it doesn’t matter."

I recommend beginners to learn at least two languages: 1) dynamically-compiled language, such as Python, Haskell; 2) statically-compiled language, such as C, C++, Java. You may find a playground somewhere (their official websites or a coding platform) to read or try to write simple code in different languages and pick up two that most interest you. Personally speaking, I started with C++ and Python.

Language is a tool, and the goal of learning it is to help you understand concepts of computer science, which are the basics to learn other skills. Those concepts are universal and language-independent, so if you turn to learn a new language in future, you may only focus on special features of that language.

Posts about learning programming languages are categorized with "Programming Language". 

## 2. Computer Architecture and System Programming

You may start wondering why software engineers or people in CS major have to learn something about hardware or Computer Engineering. The answer is because debugging your program is much much **HARDER** than coding it and in most periods of your life, you are struggling with debugging not coding. An understanding of system architecture makes your life easier.

By learning system architecture, we know how code written in different languages finally get excuted by the CPU. That is basically how a compiler works, "translating" our code into machine code which can is readable to CPU. 

We also need an overview of how memory allocation works. You may have already encoutered and get headache of the most common error `Segmentation Error`. This is because your program is trying to access an "illegal" memory address. Illegal means that the memory address is not allocated to your program, so behaviors like read and write on that piece of memory are forbidden.

System architecture is essential for beginners to explore further advanced topics of computer science, such as operating systems, network, and distributed systems. 

Posts about system architecture are under categories "Computer Architecture" and "Operating System".

## 3. Data Structure and Algorithms

Since we have related how CPU and memory work with each line of our code, it is time to go back to programming and start to think about how to optimize the code that can improve the performance of hardwares. 

Learning about data structure gives you an idea of what basic data strcutures (e.g., `int`, `float`, `double`, `char`, `bool`) and advanced data strcutures (e.g., `list`, `map`, `stack`, `queue`, `tree`) look like,  how various data structures are stored in memory, and how to choose proper data strcuture for our program. 

Furthermore, algorithms is mostly related to "efficiency". It tell us how to efficiently find, add, or delete data, how to efficiently sort a list of number in order, and how to efficiently design a program. Here, efficiency means that we want to minimize CPU cost and memory cost while maintaining the same functionality of our program. 

After learning data structure and algorithms, you may need to design your algorithm depending on the specific goal of the program. Please keep in mind those words people always love to say:
> "Keep it simple, stupid."; and <br>
> "Make it correct, then make it fast"

You can find relevant posts under the categories of "Data Structure" and "Algorithm".

## 4. Networks

Now let's learn about a big topic -- network. This is not a new word because we all have used a browser to access the Internet just by typing in the URL. Network programmers have hidden all mechanisms beneath the application layer, or in other words, people are not aware of network topology but they can still enjoy the Internet.

As computer scientists, we are supposed to open that black box and figure out what is going on there. One of the most important concepts in networks is *protocols*. We are going to learn a bunch of protocols, such as TCP, UDP, IP, and HTTP. 

Wireless connection is a hot topic at recent years including but not limited in WiFi, Bluetooth, 4G, and even 5G. We will also learn how wireless networking can be differenct than wired networking such as Ethernet. 

By learning computer networking, we are able to understand how the world-wide Internet is established grom the ground, to know how Internet deals with errors, package loss, and congestion control, and to build HTTP client and server by `socket` programming.

Posts about networks are categorized with "Computer Networking".

## 5. Operating Systems

Operating system (OS) is the largest software which directly controls the hardware and provides APIs to other softwares. In "System Archetecture", we have learned some general concepts about how an OS works, and now we are digging into the *kernel* and get a comprehensive understanding of virtual memory, scheduling, thread and process, file system, container, and system security. 

I will mostly discuss with Linux and Linux-kernel programming. I personally recommend that if you are neither a fan of Linux nor interested in kernel programming, don't get stuck at this point and just try to memorize the most important concepts. Additionally, C programming is also highly recommended here.

Posts about operating systems can be found at category "Operating System".

## 6. Distributed Systems

Distributed systems is one of the two advanced topis in computer science, the another is Machine Learning which will be mentioned later. 

On the one hand, with the development of computer networking, the speed of Internet grows greatly. People can access a remote service faster and faster. On the other hand, the trend of pay-as-you-use is spreading widely. Here comes the concept of *cloud*. I will give an example to illustrate what cloud is. First, suppose your company are diciding where to store all client data. One option is buy many HDDs and store data locally, and another option is buy storage from cloud and store data remotely. If your company is not big, the second option is probably better because you don't pay for extra maintainance for real HDDs and you don't waste money for unused spaces. 

Distributed system is a big topic. Any system contains more than two connected *nodes* can be called a distributed system. Many nodes or hosts work together to provide services. There are four types of services: IaaS (Infrustrue-as-a-Service), PaaS (Platform-as-a-Service), SaaS (Software-as-a-Service), and BaaS (Backend-as-a-Service).

By learning this part, you will get to know basics such as failure detection, leader election, and consensus. You will also learn advanced concepts such as cloud computing, P2P systems, and distributed file systems.

Posts about distributed systems are categorized with "Distributed System".

## 7. Machine Learning & Data Science

Machine learning is a "mixture" of computer science, mathematics, and statistics, so we can also call it "Data Science" (DS). 

With the explosion of big-data, DS are more and more required and applied in many areas such as recommendation systems, computer visions, and natural language processing. The main goal of machine learning is prediction or inference. Given a set of fully, partly or none labeled data, the machine needs to "learn" some patterns the data follows such that it can classify or group future data correctly. 

A solid knowledge of programming (especially in Python or R) is required but not sufficient to make you a data scientist. An understanding of advanced math and statistics is also a requirement. The reason is that most time you can directly call the functions in library such as Python's `Scikit-Learn` to do machine learning, but you have be very clear about what the model is doing in order to select proper parameters and improve correctness.

Posts about machine learning are categorized with "Machine Learning".