# Computer Science Questions

#### What is Runtime Complexity ?


It describes the performance of an algorithm. (How much more processing power/time is required to run your algorithm if we double the inputs)

- Constant Time ```1``` No matter how many elements we're working with, the algorithm/operation will take the same amount of time

- Logarithmic Time ``` log(n)``` You have this if doubling the number of elements you are iterating over doesn't double the amount of work. Always assume that searching operations are log(n)

- Linear Time ``` n ``` Iterating through all elements in a collection of data. If you see a for loop spanning from '0' to 'array.length' you probably have 'n', or linear runtime

- Quasilinear Time ``` n * log(n) ``` You have this if doubling the number of elements you are iterating over doesn't double the amount of work. Always assume that any sorting operation is n * log(n)

- Quadratic Time ``` n ^ 2 ``` Every element in a collection has to be compared to every other element. 'The handshake problem'

- Exponential Time ``` 2 ^ n ``` If you add a single element to a collection, the processing power required doubles


#### How can you identify runtime complexity?

- Iterating with a simple for loop through a single collection probably ```O(n)```
- Iterating through half a collection, still ```O(n)```. There are no constants in runtime.
- Iterating through two different collections with separate for loops ```O(n+m)```
- Two nested for loops iterating over the same collection ```O(n^2)```
- Two nested loops iterating over different collections ```O(n*m)```
- Sorting ```O(n*log(n))```
- Searching a sorted array ```O(log(n))```

#### What is Big 'O' Notation ?

It's a way of writing out runtime complexity

- ```O(n)``` Linear
- ```O(1)``` Constant
- ```O(n^2)``` Quadratic
