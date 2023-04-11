## CoinChange 

### Description 
The Coin Change problem is a classic algorithmic problem in computer science and mathematics. It involves finding the minimum number of coins needed to make change for a given amount of money, using a given set of coin denominations. This asks an existence question of whether or not we can give a change amount using the coins we have. On the other hand, it's also an optimization problem so that among all combinational possibilities that meet the criteria, we must choose the one using the minimum amount of coins.

### Decision Tree
Let's take a look at an exmaple of how complex this problem can get. 

Consider if we want to create the value of 32 cents, in which we abide by US currency values {1, 5, 10, 25} cents. We are restricted to only using each coin only once.

At every level, we must consider the question: "Do we include 25 cents or not?", in decreasing order of the coins available. This question opens two node paths of either yes or no? 

![Decision Tree](https://user-images.githubusercontent.com/94495024/231309197-4f5e1e2c-97ec-4084-ac6c-b2cf4e9c5a60.jpg)

As you can see, this gets really complicated _really fast_. There is a total of 2^4 leaf nodes created each corresponding to a different subset of decisions taken. While it seems like we could go on forever, our base case indicates that whenever there are no more coins to choose from, or we reach a negative amount, we terminate.

## Discussion
By reading the graph, it becomes clear here that the most important question to figure out here is whether to include the 25 cents or not. If 25 cents is included in our solution (32 - 25 = 7 coins remaining), then the problem cannot be solved. 

7 - 10 = -3 X <br />
7 - 5 = 2 <br />
 ~ 2 - 1 = 1 X <br />
7 - 1 = 6 X <br />

No good. We can only use each coin once and there are still coins remaining.

If 25 cents is not included in our solution (32 coins remaining), then the problem also cannot be solved.
<br />
32 - 10 = 22 <br />
 ~ 22 - 5 = 17 <br />
    -> 17 - 1 = 16 X <br />
. . . 

Also, no good. There are even more coins remaining than before! 

Therefore, this problem cannot be solved to create a value of 32. However, if we wanted to create a value of 31, we could!
<br />
31 - 25 = 6 <br />
 ~ 6 - 10 = -4 X <br />
 ~ 6 - 5 = 1 <br />
    -> 1 - 1 = 0 <br />
   
Having to chose each coin only once can be pretty frustrating! That's why my solution includes an UnlimitedCoinChange function where each coin can be used for an unlimited number of times. With that function, creating 32 could be done by including 25 cents and using 1 cent twice. The solution would be {25, 5, 1, 1} in order to create the amount of 32 coins!

### Areas for Improvement 
One way to improve this project is by including a dyanmmic programming approach. As opposed to our greedy algorithm, this can be done either through memoization or tabulation. The problem could be broken down into smaller subproblems and their solutions stored in a table to avoid redundant calculations.



