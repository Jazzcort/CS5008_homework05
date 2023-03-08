# Sort Analysis Data

## Results Table
Make sure to go out to at least 100,000 (more are welcome), and you have 10 different values (more welcome). You are welcome to go farther, but given 100,000 can take about 20 seconds using a selection sort on a fast desktop computer, and 200,000 took 77 seconds, you start having to wait much longer the more 0s you add. However, to build a clearer line, you will want more data points, and you will find merge and quick are able to handle higher numbers easier (but at a cost you will explore below). 

You are free to write a script to run the program and build your table (then copy that table built into the markdown). If you do that, please include the script into the repo.  Note: merge sort is going to be completed in the workshop for Module 06. You can start on it now, but welcome to wait.

### Table
| N | Bubble | Selection | Insertion | Merge | Quick |
| :-- | :--: | :--: | :--: | :--: | :--: |
| 10 | 0.000004 | 0.000003 | 0.000002 | 0.000003 | 0.000011 |
| 100 | 0.000135 | 0.000034 | 0.000027 | 0.000026 | 0.000027 |
| 1000 | 0.008786 | 0.003030 | 0.002470 | 0.000270 | 0.000400 |
| 10000 | 0.520124 | 0.155717 | 0.154295 | 0.004643 | 0.003826|
| 100000 | 49.470302 | 11.716587 | 11.615933 | 0.034069 | 0.030414 |
| 200000 | 198.304594 | 46.135009 | 45.996568 | 0.061316 | 0.057048 |



## BigO Analysis  / Questions

### 1. Build a line chart
Build a line chart using your favorite program. Your X axis will be N increasing, and your Y access will be the numbers for each type of sort. This will create something similar to the graph in the instructions, though it won't be as smooth.

Include the image in your markdown. As a reminder, you save the image in your repo, and use [image markdown].

<img src="https://github.com/Jazzcort/CS5008_homework05/blob/main/chart.png" width="600" height="420"> <br>

The line of Insertion Sort is overlapping with the line of Selection Sort. Also, the line of Merge Sort is overlapping with the line of Quick Sort.


### 2. Convinced?
Given the direction of the line chart, are you "convinced" of the complexity of each of the sorts? Why or why not?

In the chart, we can observe that Bubble, Selection, and Insertion Sort shows the $O(n^{2})$ curve. For the Merge and Quick sort, it's hard to observe the Time Complexity from the chart, but as we can see, it's much faster than the first three sort algorithms we introduced above. So, I'm pretty convinced to this result. 


### 3. Big O
Build another table that presents the best, worst, and average case for Bubble, Selection, Insertion, Merge, and Quick. You are free to use resources for this, but please reference them if you do. 

|  | Bubble | Selection | Insertion | Merge | Quick |
| :-- | :--: | :--: | :--: | :--: | :--: |
| Best Case | $O(n)$ | $O(n^{2})$ | $O(n)$ | $O(n\log(n))$ | $O(n\log(n))$ |
| Worst Case | $O(n^{2})$ | $O(n^{2})$ | $O(n^{2})$ | $O(n\log(n))$ | $O(n^{2})$ |
| Average Case | $O(n^{2})$ | $O(n^{2})$ | $O(n^2)$ | $O(n\log(n))$ | $O(n\log(n))$ |

The Bubble Sort introduceed in the class video doesn't check if at least a swap is done in the second for-loop. So, even if the given array is already sorted, this version of Bubble Sort still run through the whole array. Therefore, the best case time complexity is still $O(n^{2})$

#### 3.2 Worst Case
Provide example of arrays that generate _worst_ case for Bubble, Selection, Insertion, Merge Sorts

For Selestion Sort, whether the input array is presorted or not, we always need to search the rest of the array entirely for the minimum. Therefore, we have to do same amount of comparisons no matter what kind of case we have. It's meaningless to discuss about the worst and best case for Selection Sort.

It's same for Merge sort. Different cases would not affect the Time Complexity of it so I'm not going to discuss about the worst and best case for Merge Sort as well.

The worst case for the rest of the sorting algorithm would be a sorted array in descending order.

For example: 9, 8, 7, 6, 5, 4, 3, 2, 1

If we use Bubble Sort to sort this array, in the second for-loop, we have to swap every two elements since the first element is always bigger than the second element in a descending array.

If we use Insertion Sort, we have to compare the "i"th element from "i - 1"th to the 1st element for every insertion since the elements with bigger index number is smaller than the elements with smaller index number in a descending array.

For Merge Sort, we have to c

#### 3.3 Best Case
Provide example of arrays that generate _best_ case for Bubble, Selection, Insertion, Merge Sorts 

As what I mentioned above, we're not going to discuss the best case for Selection and Merge Sort.

The best case for Bubble and Insertion Sort would be a sorted array in accending order.

For example: 1, 2, 3, 4, 5, 6, 7, 8, 9

If we apply Bubble to this array, in the second for-loop of this algorithm, we don't have to do any swaps at all. In this case, we reduce the runtime of swapping elements from the total runtime. In addition, if we add a boolean variable in the first for-loop to check if there are any swaps happening or nothing at all in the second for-loop, we can optimize the Time Complexity to $O(n)$ for the best case.

For the Insertion Sort, we only need to compare "i"th element with "i - 1"th element for every insertion because "i"th element is always bigger than "i - 1"th element in a ascending array. In this case, the Time Complexity is reduced to $O(n)$ 


#### 3.4 Memory Considerations
Order the various sorts based on which take up the most memory when sorting to the least memory. You may have to research this, and include the mathematical notation. 

Merge > Quick > Bubble = Selection = Insertion

| Merge | Quick | Bubble |Selection | Insertion |
| :--: | :--: | :--: | :--: | :--: |
| $O(n)$ | $O(log(n))$ | $O(1)$ | $O(1)$ | $O(1)$ | 

For Merge Sort, because we need a auxiliary array with the same size as the original array to store the sorted subarrays temporarily, the Space Complexity would be $O(n)$

For Quick Sort, if we unfortunately choose bad pivot every time, the Space Complexity would be $O(n)$ as n recursive calls will be made. However, in average, the Space Complexity would be $O(log(n))$.

For the rest of the sorting algorithm, we're not using any extra memories, so the Space Complexity would be $O(1)$


### 4. Growth of Functions
Give the following values, place them correctly into *six* categories. Use the bullets, and feel free to cut and paste the full LatexMath we used to generate them.  

$n^2$  
$n!$  
$n\log_2n$  
$5n^2+5n$  
$10000$  
$3n$    
$100$  
$2^n$  
$100n$  
$2^{(n-1)}$
#### Categories
* $O(n!)$: $n!$
* $O(2^{n})$: $2^n$, $2^{(n-1)}$
* $O(n^2)$: $n^2$, $5n^2+5n$
* $O(n\log(n))$: $n\log_2n$
* $O(n)$: $3n$, $100n$
* $O(1)$: $100$, $10000$

### 5. Growth of Function Language

Pair the following terms with the correct function in the table. 
* Constant, Logarithmic, Linear, Quadratic, Cubic, Exponential, Factorial

| Big $O$     |  Name  |
| ------      | ------ |
| $O(n^3)$    |  Cubic |
| $O(1)$      | Constant |
| $O(n)$      | Linear |
| $O(\log_2n)$ | Logarithmic |
| $O(n^2)$    | Quadratic |
| $O(n!)$     | Factorial |
| $O(2^n)$    | Exponential |



### 6. Stable vs Unstable
Look up stability as it refers to sorting. In your own words, describe one sort that is stable and one sort that isn't stable 

Merge sort is a stable sort algorithm, because when we're merging two sorted subarrays, if the value from left subarray is equal to the value from right subarray, the element in the left subarray is always placed first. Therefore, the order of identical elements to each other always remains unchanged.

Selection sort is unstable sort algorithm, becuse the order of identical elements to each other might change.
For emample:

```text
       "a" "b"
Step 1: 2   2   1

           "b" "a"
Step 2: 1   2   2

           "b" "a"
Step 3: 1   2   2
```

Therefore, Selection Sort is unstable.

### 6.2 When stability is needed?
Explain in your own words a case in which you will want a stable algorithm over an unstable. Include an example. 

We choose a stable algorithm over an unstable algorithm when we want to sort a data which already has some order to it and we want to keep that order after we apply the sort algorithm. For example, when we are going to sort a list of students which is already sorted by their name alphabetically by their grades, and we want to keep the sorted order of the names after we apply the sort algorithm to sort the list by grade. In this situation, we would choose stable sort algorithm.

### 7. Gold Thief

You are planning a heist to steal a rare coin that weighs 1.0001 ounces. The problem is that the rare coin was mixed with a bunch of counter fit coins. You know the counter fit coins only weight 1.0000 ounce each. There are in total 250 coins.  You have a simple balance scale where the coins can be weighed against each other. Hint: don't think about all the coins at once, but how you can break it up into even(ish) piles. 

#### 7.1 Algorithm
Describe an algorithm that will help you find the coin. We encourage you to use pseudo-code, but not required.

Divide the coins into two piles, and weigh them. Choose the heavier pile and repeat the same process. At the end, the heavier one in the last two coins is the rare coin.

#### 7.2 Time Complexity
What is the average time complexity of your algorithm? 

The algorithm is ultilzing the concept of binary search to find the coin, so the average time complexity would be $O(log(n))$

### Reference
Woltmann, S. (2022, July 19). Insertion sort - algorithm, source code, Time Complexity. HappyCoders.eu. Retrieved March 4, 2023, from https://www.happycoders.eu/algorithms/insertion-sort/ 



<!-- links moved to bottom for easier reading in plain text (btw, this a comment that doesn't show in the webpage generated-->
[image markdown]: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images