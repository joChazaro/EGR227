# EGR227
## Worksheet 1 for Lecture 02 Stack and Queue

1.	What is Abstract Data Type (ADT)?
A specification of a type of data and the operations that can be performed on it
2.	Give some examples of ADTs.
List, array, queue, stack, sets, map
3.	In Java, ADTs are expressed as Interfaces	.

4.	(True/False) Stacks and Queues provide more complex functionality than List.
True
5.	Stacks and Queues are linear ordered structure provides below functionalities.
1)	Add	or push	: Insert an element in the data structure
2)	Remove or pop	: Deletes an element in the data structure
3)	isEmpty: Checks whether it has no element in the data structure
4)	Size	: returns how many elements in the data structure
5)	(Borderline) Peek 	: Allows you to take a look at the first (in case of Queue) or the last element (in case of Stack) without removing the element

6.	Queue vs Stack

1)	First In First Out (FIFO) is for Queue	.

2)	Last In First Out (LIFO) is for Stack	.

3)	The first element in the Queue is called front	and the last element
in the Queue is called back	.

 
4)	The first element in the Stack is called in the Stack is called top	.
7.	Instantiating an object type Queue<String>.
1)	Can you instantiate Queue type directly? No
2)	Why or why not? Because you cannot instantiate interfaces. To use an interface you write a class that implements the interfaces.
 
 Bottom and the last element 
3)	Write a code to obtain an object of Queue<String> named q.
		Queue<NAME> q = new LinkedList<NAME>();
8.	Instantiating an object type Stack<Integer>

1)	Can you instantiate Stack type directly? Yes
2)	Why or why not? Because a stack is the class and can be instantiated directly

3)	Write a code to obtain an object of Stack<Integer> named s.
Stack<Integer> s = new Stack<Integer>();
* Integer is a wrapper object for primitive int type.

9.	You are given below code. (SimpleStackQueueExercise.java)
String[] data = {"four", "score", "and", "seven", "years", "ago"}; Queue<String> q = new LinkedList<String>()	;//need to instantiate
Stack<String> s = new Stack<String>()	;//need to instantiate

//Write a code to insert each element in data to q and s
for ( String str: data	) {
q. add	(str);
s. push	(str);
}

//What is the output below for initial state of q and s? System.out.println("initial queue = " + q); four System.out.println("initial stack = " + s); four

//Below code deletes an element from q until q becomes empty
while ( !q.isEmpty()) { String str = q. remove	();
//What is the output in each iteration?
System.out.println("removing " + str + ", now queue = " + q); 
} 	
System.out.println();
removing four, now queue = [score, and, seven, years, ago]
	removing score, now queue = [and, seven, years, ago]
	removing and, now queue = [seven, years, ago]
	removing seven, now queue = [years, ago]
	removing years, now queue = [ago]
	removing ago, now queue = []



//Below code deletes an element from s until s becomes empty
while ( !s. isEmpty()) { String str = s. pop();
//What is the output in each iteration?
System.out.println("removing " + str + ", now stack = " + s);
}	
System.out.println();

removing ago, now stack = [four, score, and, seven, years]
	removing years, now stack = [four, score, and, seven]
	removing seven, now stack =[four, score, and]
	removing and, now stack =[four, score]
	removing score, now stack =[four]
removing four, now stack =[]
 
10.	You are given below code and the output for below code.

[Code]
Queue<Integer> q = makeQueueOfMultiples(6, 3); System.out.println("initial queue = " + q); System.out.println("sum = " + sum(q)); System.out.println("after sum queue = " + q); System.out.println();

[Output]
initial queue = [3, 6, 9, 12, 15, 18]
sum = 63
after sum queue = [3, 6, 9, 12, 15, 18]

[Exercise 1] Finish implementing below method
// pre : count >= 0
// post: returns a queue of count multiples of n
public static Queue<Integer>	makeQueueOfMultiples(int count, int n) { Queue<Integer> q = new LinkedList<Integer>(); 
for (int i = 1; i <= 6; i++)
     q.add(i*3);
return q;
}

[Exercise 2] Finish implementing below method
// post: returns the sum of the values in q
public static int	sum( Queue<Integer> q) {
int sum = 0;

for (int i = 0; i < q.size(); i++){
            int n = q.remove();
            sum += n;
            q.add(n);
        }
return sum;
}
 
11.	You are given below code and the output. [Code]
s = makeStackOfMultiples(6, 5); System.out.println("initial stack = " + s); System.out.println("sum = " + sum(s)); System.out.println("after sum stack = " + s); System.out.println();
[Output]
initial stack = [5, 10, 15, 20, 25, 30]
sum = 105
after sum stack = [5, 10, 15, 20, 25, 30]
[Exercise 1] Finish implementing below method
// pre : count >= 0
// post: returns a stack of count multiples of n
public static 	makeStackOfMultiples(int count, int n) {

        Stack<Integer> s = new Stack<Integer>();
        for (int i = 1; i <= count; i++){
            s.push(i * n);
        }
        return s;
}

[Exercise 2] Finish implementing below method
// post: returns the sum of the values in s
public static 	sum(Stack<Integer> s) {
int sum = 0;
        Queue<Integer> q = new LinkedList<>();
        while(!s.isEmpty()){
            int n = s.pop();
            sum += n;
            q.add(n);
        }
        // create new queue for auxiliary storage
        queueToStack(q, s);
        stackToQueue(s, q);
        queueToStack(q, s);

return sum;
}
 
12.	You are given below code and the output for below code.

[Code]
System.out.println("current queue = " + q); Stack<Integer> s = new Stack<Integer>(); queueToStack(q, s);
System.out.println("after queueToStack:"); System.out.println("	queue = " + q); System.out.println("	stack = " + s); System.out.println();

[Output]
current queue = [3, 6, 9, 12, 15, 18] after queueToStack:
queue = []
stack = [3, 6, 9, 12, 15, 18]

[Exercise] Finish implementing below method
// post: Values from q moved to s
//	(added in queue order, front to back);
//	q is empty
public static 	queueToStack(Queue<Integer> q, Stack<Integer> s) {
while (!q.isEmpty()) {
		int n = q.remove();
            s.push(n);
}
}
 
13.	You are given below code and the output. [Code]
System.out.println("current queue = " + q);
System.out.println("current stack = " + s); stackToQueue(s, q); System.out.println("after stackToQueue:"); System.out.println("	stack = " + s); System.out.println("	queue = " + q);

[Output]
current queue = []
current stack = [5, 10, 15, 20, 25, 30] after stackToQueue:
stack = []
queue = [30, 25, 20, 15, 10, 5]

[Exercise]
// post: Values from s moved to q
//	(added in stack order, top to bottom);
//	s is empty
public static void stackToQueue(Stack<Integer> s, Queue<Integer> q) {
        while(!s.isEmpty()){
            int n = s.pop();
            q.add(n);
}
 
Additional Exercise Questions

* Be prepare for the hard Stack/Queue questions in our first midterm


1.	Using your IntelliJ, create a new project. Download code from BB called ReverseFile.java and place it under /src. Also download input.txt and place it under root (the parent of /src). Implement the main method, where it should print all words in input.txt in reverse order. Then prints them out again in order but all UPPERCASE. (You may use stackToQueue or QueueToStack method as the helper methods). Take screenshots of 1) your code and 2) the output and include them in a Word doc and submit to BB. The output should also show that words data structure containing the words in order after you print out them in UPPERCASE.
import java.io.File; 
import java.io.FileNotFoundException; 
import java.util.LinkedList; 
import java.util.Scanner; 
import java.util.Stack; 

/* Contributors: Matt N, Johana C, True S */ 
public class ReverseFileFinished { 
public ReverseFileFinished() { 
} 
public static void main(String[] args) 
throws FileNotFoundException {
Stack<String> words = new Stack(); 
Scanner input = new Scanner(new File("input.txt")); while(input.hasNext()) {
 String word = input.next(); 
words.push(word); } 

LinkedList q = new LinkedList(); 

while(!words.isEmpty()) { 
System.out.println((String)words.peek()); 
q.add((String)words.pop()); 
} 
while(!q.isEmpty()) {
System.out.println(((String)q.peek()).toUpperCase()); 
words.push((String)q.remove()); 
} 

while(!words.isEmpty()) { 
q.add((String)words.pop()); 
} 
while(!q.isEmpty()) {
 words.push((String)q.remove()); 
} 
} 
}
2.	Write a method splitStack that takes a stack of integers as a parameter and splits it into negatives and non-negatives. The numbers in the stack should be rearranged so that all the negatives appear on the bottom of the stack and all the non-negatives appear on the top. In other words, if after this method is called you were to pop numbers off the stack, you would first get all the nonnegative numbers and then get all the negative numbers. It does not matter what order the numbers appear in as long as all the negatives appear lower in the stack than all the non-negatives. You may use a single queue as auxiliary storage. Write your code in the back and submit this page.

import java.util.LinkedList;
import java.util.Queue; 
import java.util.Stack; 
/* Contributors: Matt N, Johana C, True S */ 

public class splitStack { 
	public splitStack() { 
} 
public static void splitStack(Stack<Integer> S) { 
	Queue<Integer> q = new LinkedList(); 
	int numNegatives; 
	
	for(numNegatives = 0; !S.isEmpty(); q.add((Integer)S.pop())) { 
		if ((Integer)S.peek() < 0) { ++numNegatives; } 
	} 
	while(numNegatives > 0) { 
		if ((Integer)q.peek() < 0) { 
			S.push((Integer)q.remove()); --numNegatives; 
		} 
		else { 
			q.add((Integer)q.remove()); 
			} 
		} 
	while(!q.isEmpty()) { 
		S.push((Integer)q.remove()); 
	} 
	System.out.println(S); 
} 
public static void main(String[] args) { 
	Stack<Integer> Test = new Stack(); 
	Test.push(5); 
	Test.push(8); 
	Test.push(-17); 
	Test.push(-13); 
	splitStack(Test); 
} 
}
