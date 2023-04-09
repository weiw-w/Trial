# Assignment 2

## Question 1

### Naive Solution in `O(n^2)`:
First, change the two strings into two arrays of characters and discard spaces. If the array is not the same length, return false. Else, run a for loop through the first array with a nest loop running through the second array. For each char in array 1, look for the same character in array 2 and make that index a "bridge" (so if there’s more than one occurrence of a char, they can all find the corresponding char in the array 2). If, in one iteration, can’t find the corresponding character in array 2, return false. If two strings are anagram, then the outer loop can be run without problem, so return true after the outer loop.

### Efficient solution in `O(n log(n))`: 
First, change the two strings into two arrays of characters and discard spaces. If the array is not the same length, return false. Else, use merge sort to sort the arrays. Then, run a for loop through the first array and check if the element at each index of the first array equals the one at the second one. 

### Efficient solution in `O(n)`:
First, change the two strings into characters and hash them into two hash maps. The key is the character, and the value is the number of occurrences. In detail, when hashing, if I encounter a key that already exists, I update the value by adding 1. Then, check if the two maps are equal to each other, where each key in the first map matches the keys in the second map and if their values match.

## Question 2

### Naive Solution in `O(n^2)`: 
Run through a for loop with variable i from the first index to the second last, and run through the nested loop with variable j from i+1 to the last. Check if the sum of each value of the index i and index j equals x; if it does, set the two declared variables before loops to i and j. 

### Efficient solution in `O(n)`:
First, hash the array into a map where the key is the number, and the value is a list of indices. Iterate through the map. For each iteration, find a number n that equals to x minus the key of iteration. If n equals the key of iteration and the sublist, value of the key, has a size of more than one, find the two indices from the set. If not, check if the map contains n as a key; if yes, I can find the indices of the two keys from their values. For both cases, I need to compare the found indices with the indices of the previous found pair to make sure the final pair returned is the first pair that appears on the array.

## Question 3

### Naive Solution in `O(n^2)`: 
Run a for loop with variable i through the list, and run a loop with variable j from i+1 to the last index. From each iteration in the inner loop, check if the integer at index j equals the one at index i and count the occurrences of the integer at index i. If it does, make the index j null so it won’t be counted again in the outer loop. After running the whole inner loop, for each iteration on the outer loop, check if the number occurrences is odd. If it is, return the value at index i. 

### Efficient solution in `O(n)`: 
Hash the list into a map where the key is the number, and the value is the number of occurrences. When hashing, if I encounter a key that already exists, I update the value by adding 1. Then, I iterate through the map, and find the value with the odd number of occurrences. 

### Efficient solution in `O(n)` and `constant space`: 
By using bit manipulation, I can find the number with odd occurrences. Run a for loop through the array to the second last index and declare an integer num to store the result. For the first iteration, find the XOR value of the elements at the first index and the next index and store it in num. Then, for each iteration afterward, find the XOR value of num and the element at the next index. Based on the pattern found, num should equal to the number with odd occurrences after the loop.  

## Question 4

### Naive Solution in `O(n^2)`:
Run a for loop with variable i through the list, and run a loop with variable j from i+1 to the last index. Set a variable sum to be initially the value at index i, and then add the value at index j. Check at each iteration if the sum equals to 0, and if it does, return true. If after running through the outer loop and no sum equals to 0, then return false.

### Efficient solution in `O(n)`:
First, run a for loop through the array where each element is consecutively added to a variable sum. If an element or the sum equals 0, return true. If not, we also add the sum from each iteration to an array. Then, we use a hash set to find if there is a duplicate element in the sum array; if there is, that means a section in the original array will add to 0. If not, return false.

## Question 5

### Naive Solution in `O(n^2)`:
Run a for loop with variable i through the list, and run a loop with variable j from i+1 to the last index. Declare two variables to be the two of numbers of a pair, and when run through the inner loop to find the reverse. If I find a reverse, I add the reverse and the initial pairs to a result list and index j null so it won’t be iterated again in the outer loop. 

### Efficient solution in `O(n)`:
First check if the array only has 1 or less pair; if so, I can already return an empty array. If not, hash the array into a map where the key is the element and the value is the index. This will serve as a key. Then, run through the original array again and check if each pair’s reverse exists in the map. If it does, remove the pair from the map and add the two pairs into the result array. I will also check for a special case of two pairs of identical integers, like (1,1). When I encounter the first pair of the identical integers, I check if the index saved in the map is the index of the iteration. If not, it means that there is a duplicate pair, and do the same as other reverse pairs. If it is the same, there’s no reverse, so add it. 

## Question 6

### Naive Solution in `O(n^2)`:
First, use a merge sort to sort the array to get the number of occurrences of each number. Then, I run a loop through the original array and add the first occurrence of each number to an arraylist to get the order by using the contains method for arraylist. Then, based on the order and the number of occurrences, I will add the numbers into the result array in the correct way.

### Efficient solution in `O(n)`:
Hash the array into a map where the key is the element and the value is the number of occurrences. When hashing, if I encounter a key that already exists, I update the value by adding 1. However, when hashing, I also have an array.list to keep the order of the element that is first seen (1st cluster in index 0, 2nd cluster in index 1, and so on). Then, loop through the list of order, and look for the value for each element of the cluster in the map. At last, in each iteration, add the number of elements to the result array based on the number of occurrences.

## Question 7

### Naive Solution in `O(n^2)`:
With the assumption that two different chars of the first String can’t be replaced by the same character, I will implement this way: first, check if the two strings are the same length. Else, run a for loop with variable i through the array of char of the first String, and have a char variable for the char at index i in the second string. I will also put the corresponding char variable to a hash set. If the set already has the char, then that means the two different chars in the first String want to be replaced by the same char, so return false. Then run a nested for loop with variable j through the array to find recurrence of the same char. When I find a recurrence, I check if the corresponding char in the second string is the same as the char variable. If it is, make the array[j] a bridge, so it won't be iterated again. If it isn’t, return false. In this way, check all the characters in the first String, and return true after the loops. 

### Efficient solution in `O(n)`:
With the assumption that two different chars of the first String can’t be replaced by the same character, I will implement this way: first, check if the two strings are the same length; if not, return false. Else, hash the two Strings into two maps where the key is the char and the value is a number that represents that char. For example, ACCS and AVDDSA are 1223 and 123341. Then, run through the Strings and create two arrays of their numerical versions based on the two maps. Lastly, compare the two int arrays, and if they are the same, return true.
