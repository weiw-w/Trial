# Question 8

## Solution
The main problem is creating a record of KDA values in each game played and some stats, like total KDA values, and each game’s information can be looked up. After each new game is played, the information should be updated. Since games are in chronological order, so they can be given a number (the first game is #1, and so on). Therefore, when looking up a game, the record can just retrieve the information of a game from the given number (#1 at index 0). This way, I can use Arraylist and keep it to amortized constant time, `O(1)`. It takes `O(n)` space.

## Implementation details
I will create a `Game` class with instance variables for KDA values and a `Record` class with an array list of `Games` and stats information as instance variables. The `Record` class has an `addGame` method to add `Games` to the array list and access the KDA values. The `Game` class constructor calls the `addGame` method, as a played game should be automatically added to the record. The `Record` class has methods –  `getKofG`, `getDofG`, and `getAofG` – to look up information about a specific game. There also are methods to get stats like total KDA values, highest KDA values per game, and the game number with each of the highest KDA values, and there’s a  `gamePlayed` method to use in the test cases to get the number of games played.

## Test Cases
We test the following cases:
- `Game’s` methods of getting KDA values
- Looking up information about specific games
  - If `Games` are added to the list
  - If correct information is looked up
  - If wrong arguments are searched 
- Correct stats for total KDA values
- Correct highest KDA values and correct game associated with each


# Question 9

## Solution
The main problem consists of two parts. The first part is a first-come-first-serve list of applications, where one’s name is removed after their application is reviewed. The second part is a list where a worker can search for a person based on their first name to find their home address. I will implement the first part with a queue of people and the second part with a sorted tree map of names to people’s information. The implementation of the first part is `O(n2)`, and the second part is `O(nlog(n))`. It takes `O(n)` space.

## Implementation details
For this problem, I will create a `Person` class and a `Process` class. The `Person` class has the information of the applicant’s first name, preference of evacuation, and home address. The `Process` represents the process of reviewing these applications. It has a `submit` method to add a `Person` application to the queue for part 1 and `review` and `reviewAll` to look through the applications and add them to the map for part 2. There’s a `search` method to look for the address for a person in part 2. There are also methods for test cases – `sizeFP`, `sizeSP`, `mapOrder`.

## Test Cases
- `Person’s` methods of getting information
- First part
  - If `Persons` are added to the queue
  - If they are reviewed in first-come first-serve order
  - If correct `Person` is added to the map for the second part
  - If `reviewAll` works 
- Second part
  - If the map is in alphabetical order
  - If correct address can be found

They cover the possible scenario of an empty list or wrong argument imputed. 


# Question 10

## Solution
The main problem is accepting requests to reserve rooms by their numbers. These requests are processed in an order determined by the rank of the submitter, and it is first-come first-served among the submitters with the same rank. Also, the system should be able to check the availability of a room before requesting. I will implement the main problem with a priority queue, using a heap sort, which is the most efficient with `O(nlog(n))`.

## Implementation details
I will create a `Request` class with their name, rank, and the room number that they request for. Because there is an interactive map and the “outer system” to choose for ranks, I set the preconditions of the arguments for the constructor of `Request` to be from the predetermined room number and rank. I will also create an `InnerSystem` class with a hash map of the room numbers to their availability (`O(1)`) and a priority queue of `Requests`. It has a `submit` method to add the `Request` in the priority queue, and the `Request` constructor will call the method. The `InnerSystem` has an `availability` method to check availability of the rooms and `review` to change the availability of rooms based on the `Request`. There’s also a `size` for test cases.

## Test Cases
- `Request’s` methods of getting information
- If requests are automatically submitted
- If requests are reviewed in the correct order
  - If rooms are correctly booked
