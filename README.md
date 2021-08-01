# 2DFenwickTrees
Overview:

Let us consider the following, 
Let, f be some reversible function and A be an array of integers of length N.
Then, a Fenwick tree is a data structure which:
1. ...calculates the value of function f in the given range [l,r] (i.e. f(Al,Al+1,…,Ar)) in O(logn) time;
2. ...updates the value of an element of A in O(logn) time;
3. ...requires O(N) memory, or in other words, exactly the same memory required for A;
4. ...is easy to use and code, especially, in the case of multidimensional arrays.
The most common application of Fenwick tree is calculating the sum of a range i.e,
f(A1,A2,…,Ak)=A1+A2+⋯+Ak.

Using a BIT, we expanded upon this application across a dimension to utilize it for retrieval operations.

We have used this data structure to complete operations on the sub matrix, and its efficiency and time complexity have been discussed.



Let us understand the terminology behind these terms:

A Fenwick Tree (Binary Indexed Tree, or BIT) is a fairly common data structure.
1. BITs are used to efficiently answer certain types of range queries, on ranges from a root to some distant node. 
2. They also allow quick updates on individual data points.
3. A BIT can perform both of these operations in O(log N) time, and takes O(N) memory
4. BITs take advantage of the fact that ranges can be broken down into other ranges, and combined quickly. 
5. Adding the numbers 1 through 4 to the numbers 5 through 8 is the same as adding the numbers 1 through 8. 
6. Basically, if we can pre calculate the range query for a certain subset of ranges, we can quickly combine them to answer any [1,x] range query.
The binary number system helps us here. Every number N can be represented in log N digits in binary. 


Data Structure Used:

We used a structure to define the queries as it gives us the ability to define Cartesian coordinates used to locate the start and end point of the locations of the matrix.

The structure takes 4 integers as variables which represent the Cartesian coordinates. This data structure seemed most apt to use due our application of querying in multiple test cases. 
This allows us the dynamic allocation of memory to objects upon static declaration of variables within the main() function.

The actual BIT/Fenwick Tree is represented using a 2 dimensional array of MxN order where each element represents another BIT of the elements entered so far. This 2D BIT is then expanded upon and cut up into multiple divisions to be operated upon.

Question: Can we answer sub-matrix sum queries efficiently using Binary Indexed Tree?

We know that to answer range sum queries on a 1-D array efficiently, binary indexed tree (or Fenwick Tree) is the best choice (even better than segment tree due to less memory requirements and a little faster than segment tree).
Hence, the answer is yes. This is possible using a 2D BIT which is nothing but an array of 1D BIT.

Question: Could we perform both the query and update operations in O(log n) time?

One efficient solution is to use Segment Tree that performs both operations in O(log n) time.
An alternative solution is our BIT, which also achieves O(log n) time complexity for both operations. Compared with Segment Tree, Binary Indexed Tree requires less space and is easier to implement.

Time Analysis:

Both updateBIT(x, y, val) function and getSum(x, y) function takes O(log(NM)) time.
Building the 2D BIT takes O(NM log(NM)).
Since in each of the queries we are calling getSum(x, y) function so answering all the Q queries takes O(Q *log(NM)) time.

Space complexity: 
O(NM) to store the 2D BIT/Fenwick Tree and Auxiliary Array
Hence the overall time complexity of the program is O((NM+Q).log(NM)) where,

N = maximum X co-ordinate of the whole matrix.

M = maximum Y co-ordinate of the whole matrix.

Q = Number of queries


Limitations and further enhancements:

The limitations of this data structure can be defined as follows:
1.	It cannot be used to calculate the maximum or minimum within a specified range.
2.	Each query on Binary Indexed Tree takes constant or logarithmic time. However, BITs and the Auxiliary Matrix require linear memory space. This problem is only furthered with the addition of another row and column to calculate sub operations
3.	The data structure when expanded upon to “N” dimensions increments the time complexity by an exponential factor.

This data structure can be further enhanced by the following measures:
1.	The code currently handles all known cases for a 2-dimensional BIT. However the logic described in the algorithm still holds true for any number of dimensions. Hence, the code could be expanded across dimensions.
2.	The space requirement can be additionally optimized by lazily allocating BIT cells, while in the same time losing only logarithmic factor in the running time.


