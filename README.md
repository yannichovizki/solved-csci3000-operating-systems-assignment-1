Download Link: https://assignmentchef.com/product/solved-csci3000-operating-systems-assignment-1
<br>
The goal of this homework is to get you familiar with system calls related to processes in the UNIX operating system. You will write a program that uses multiple processes to compute the sum of a set of (small) positive integers. This is a very strange method of computing the sum of a set of numbers, but we will use it to learn about processes. There are two kinds of processes for this assignment:




<ul>

 <li>A set of “<strong>worker</strong>” processes. Each worker process gets two small integers as command line parameters (they will be available in its <em>argv</em>), computes their sum and returns the result using <strong><em>exit</em></strong> system call. So, for every sum a worker process is created.</li>

 <li>A “<strong>coordinator</strong>” process. It is responsible for creating the “worker” processes, and coordinating the computation. Note that all the computation is done by the “worker” processes. All the numbers to be added are provided in the command line for the coordinator process.</li>

</ul>




Note that the coordinator may have to create multiple sets of processes. For example, if there are 8 numbers, the coordinator will first create 4 workers and get the results from them. At this point there are 4 numbers, and it creates 2 workers. Finally one worker is created to compute the overall sum. To make it simpler, if the number of integers to add is odd, the coordinator adds a 0 to the list of numbers. Note that this may happen at any step during the computation.




Use the thin clients in Room No. 208 or the PCs in Room No. 207 or your own computer to get onto xlogin.cs.ecu.edu and work on your programming assignments. The <em>xlogin</em> server runs SUSE LINUX. Remember that you first need to go through VPN (Virtual Private Network) to remotely connect to xlogin.cs.ecu.edu. After going through VPN, you need to use either <em>ssh</em>, <em>putty</em> or <em>NX</em> clients to remotely login.




Create a subdirectory called <strong><em>cs3000</em></strong> in your <strong><em>home</em></strong> directory. Create a subdirectory called <strong><em>assign1</em></strong> in your <strong><em>cs3000</em></strong> directory. Use that subdirectory to store all the files concerning this assignment and nothing else. You need to follow these general guidelines for all your future assignments as well. Name the two source files <em>worker.c</em> and <em>coordinator.c</em>. The code for worker process should be compiled separately and its executable be called <strong><em>worker</em></strong>. It should also be possible to execute the “<strong><em>worker</em></strong>” program as a standalone program. The executable for the coordinator process should be called coordinator. So, to compute the sum of the numbers 1 . . . 7, the command line would look something like:

<strong>coordinator</strong> 1 2 3 4 5 6 7




Since the results are passed around by <em>exit</em> keep the numbers small (single digit). Note that this is not a good way for communication between processes. Each worker process should print its <strong>process id</strong>, its <strong>operands</strong> and their <strong>sum</strong>. Each time the coordinator gets a result from a worker, it must print the <em>pid</em> of the worker, and the result received from that worker. If you are not using <em>makefile</em>, please include the name of the compiler you are using and any special options needed as comments (along with other traditional comments) at the beginning of your source code.




<strong>System Calls </strong>In order to do this assignment, you should get familiar with several system calls. The important ones are <strong><em>fork</em></strong>, <strong><em>execlp</em></strong>, <strong><em>exit</em></strong>, and <strong><em>wait</em></strong> system calls. You will also need <strong><em>getpid</em></strong> and <strong><em>perror</em></strong> system calls. You can find more information on them in the reference books mentioned in the class. You can also find information about them directly from the system by using the manual pages.





