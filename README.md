# DSA-Assignment-1
PROBLEM: 1
----------
APPROACH:
The task is to implement a singly circular linked list that contains CPU processes. Each process has an execution time. Once the process has been executed, it is marked as ‘complete’ and removed from the list. In each cycle the remaining time of each process is decremented until it reaches 0. There is an additional implementation that deals with a process being added in between a cycle. Now that I have explained my understanding of the problem, here are the steps I have taken to reach the end goal.
1.	Firstly, I created a class named ‘Process’. This class basically represents a node of a singly circular linked list. The class contains a default and a parameterized constructor for ease. The class has the attributes:
‘string process_id’,   ‘int execution_time’, ‘int remaining_time’, ‘Process *next’ .
The first 3 attributes are self-explanatory. ‘Process *next’ basically stores the address of the next node (process) in the linked list.
2.	Next, I created functions ‘add_to_empty’ and ‘add_to_end’. These are used to add nodes (processes) to the linked list. The ‘add_to_empty’ function basically adds the first process in the list whereas the other function adds other incoming processes. I have added every new process right at the end of the list.
3.	Next, there is a ‘delete_a_node’ function. The purpose of this function is to remove a process from the list once its remaining time is finished. This function finds the process to be deleted first and then updates the tail of the linked list.
4.	Then I created a ‘print_list’ function. This function only prints the details of the linked list after every cycle. I have printed the initial stage in the main function. This function starts printing from cycle 1.
5.	After creating all these functions, I then moved to the main function. In the main, I firstly hard coded the CPU time for each cycle. I then proceeded to make a circular linked list by calling the previously defined functions and printing the initial state according to the format of the sample output in the problem. Next, it was time to implement the logic of decrementing the ‘remaining_time’ after each cycle. I created a pointer ‘ptr’ that points to the first process in the list. Then I initialized a variable ‘cycle’ that keeps track of the number of cycles. The while loop is where all the logic is being implemented. I used my while loop to iterate through the list, decrement the ‘remaining_time’ by CPU time. If it becomes 0, call the ‘delete_a_node’ function to remove the node from the list. I also added a new process in the list in cycle 3. The cycle number increments after each iteration.

ASSUMPTIONS:
I have assumed the following:
1.	 The ‘TIME_PER_CYCLE’ (CPU time) remains fixed i.e 3 in each cycle.
2.	A new process is added in cycle
3.	At least one process exists in the circular linked list at the beginning (i.e., the system starts with three predefined processes).
4.	In each cycle, the process's remaining time is reduced by ‘TIME_PER_CYCLE’, but it cannot drop below zero.
Publicly accessible GitHub link:

CHALLENGES FACED:
1.	Creating the ‘delete_a_node’ function was challenging because of the nature of the list i.e Circular. I had to make sure that the circular list stayed intact after deleting a node.
2.	Managing new processes dynamically while the system is already running was also difficult because I had to ensure the new process is added without disrupting ongoing cycles.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

PROBLEM: 2
----------
APPROACH:
What I perceived from this problem is that I am supposed to generate a 309 digit random number, split the number into multiple parts and store it in a linked list. Then, I am supposed to apply an algorithm to check if the number as a whole is prime or not. The test is performed on the entire number, not just pieces of the number stored in the linked list. I am also supposed to print out some prime numbers less than the 309 digit number. The approach I have used for this problem can be divided in the steps below:
1.	Firstly, I created a ‘Node’ class which has the attributes ‘string data’ and ‘Node* next’. The first attribute stored part of the 309 digit number as a string while the next pointer basically stores the address of the next node in the list.
2.	Then I created a ‘add_node_to_end’ function that adds a new node to the end of the linked list.
3.	After that, I created a ‘print_data’ function whose job is to print the linked list (This function is not used in the output. I only created this to test the working of my code hence it is commented out of the program).
4.	I then created another function ‘create_linked_list’ that basically extracts 20 digits from the 309 digit number and adds it to a node in the list. I made 15 nodes containing 20 digits and 1 node containing 9 digits of the larger 309 digit number.
5.	Next, I created the ‘generate_random_number’ function. This function is basically generating my big 309 digit number. I used time as the seed because I wanted to generate a different number every time I run the program. I put the range of 1 to 9 on my first digit because I didn’t want a 0 as the first digit. Then I used a for loop to store my number as a string.
6.	I then created a ‘concatenate_number’ function that basically traverses the list and concatenates all the strings stored in the nodes.
7.	The ‘miller_rabin’ and ‘mod_exp’ implement the Miller-Rabin primality algorithm.
8.	I also created a ‘find_small_primes’ method  to find prime numbers less than 100.
9.	In the main function, the respective functions are called. Firstly a random number is generated, stored in a list, concatenated, and then the algorithm is applied on the number. I also deleted the memory of the linked list to prevent memory leaks. I used a small number (17) to check if my logic was working fine.

ASSUMPTIONS:
I have assumed the following:
1.	The number is supposed to be random and changing in each run.
2.	The smaller primes are supposed to be printed up till a specified value (in this case 100)
3.	The Rabin-Miller algorithm is to be applied on the entire number, not parts of the number that are stored in the linked list

CHALLENGES FACED:
1.	My greatest challenge was to figure out which approach would be best to check primality, deterministic or probabilistic. After a lot of research, I ended up choosing the Rabin-Miller Algorithm which is probabilistic. I reached this outcome after reading various articles and youTube videos:
https://www.youtube.com/watch?v=8i0UnX7Snkc&t=245s 
https://en.wikipedia.org/wiki/Primality_test
https://www.cs.cornell.edu/courses/cs4820/2019sp/handouts/MillerRabin.pdf
2.	My second challenge was to figure out a way to store the 309 digit number. I considered unsigned long long but then I found out it wasn’t suitable as it only functions with 20 or less digits hence my only option was using the GMP Library.
3.	After deciding the type, I got stuck on setting up my VS Code environment after downloading MYSYS2. It was very time consuming to finally get the program running after installation.

