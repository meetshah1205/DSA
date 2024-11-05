# Time complexity

It is the relation between the input size and Running time of an algorithm.

## For example

If we write just the main() function and add 1 print statement to it:

```java
public class Main {
    public static void main(String[] args){
        System.out.println("This is a print statement");
    }
}
```

It won't take much time as it is just 1 operation, and 1 operation can happen in like less than a millisecond in our modern day computer.

But of we add 2 print statements:

```java
public class Main {
    public static void main(String[] args){
        System.out.println("This is a print statement");
        System.out.println("This is another print statement");
    }
}
```

Its time complexity is

$$
2 \times \text{time complexity of the first one}
$$

Like if we take input of a variable n and run a for loop that goes from 0 to n and prints "hello".

So something like this:

```java
for (int i = 0; i < n; i++){
    System.out.println("Hello");
}
```

So let's assume it takes 1 second to print "hello" once (even though its a dramatic increase in the time then what it should really be), but we're printing "hello" n times, so that

$$
1 \ \text{second} \times n \ \text{times}
$$

## Time complexity can be

### linear

Like if we increase n by 10, run time also increases by 10.

### quadratic

Like if we increse n by 2 times, so

$$
n \times 2
$$

our runtime increases by 4 times, so

$$
\text{run }\text{time} \times 4
$$

### cubic

Like if we increment n by 2 times, so

$$
n \times 2
$$

our run time increases by 8 times, so

$$
\text{run } \text{time} \times 8(\text{because } 8 \text{ is }  2^3)
$$

#### Similarly they be

- log
- square root
- And many more

### Good code

is something that increases the minimum amount of operations with the input size

## Example

1. Lets take this code into account:

```java
public static void main(String args[]){
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();

    for (int i = 0; i<n; i++){
        System.out.println("Hello");
    }
}
```

Here the

$$
\text{input size} \propto \text{run time}
$$

Means as input increases, the time complexity also increases.

So hence it is a linear relation.

$$ \text{Hence proved} $$

## Types of time complexities

- Best case
- Average case
- Worst case

So let's say

Search for 1 in the following array

1. Best case

```
numbers: {1, 2, 3, 4, 5, 6}
```

Here it started the 0th index, and numbers[0] is 1, so it checks if 1 == 1 which is true so it stops and returns 1.

This was best case scenario.

2. Average case

But now let's change the numbers:

```
numbers: {2, 4, 1, 3, 6, 5}
```

Now if our algorithm needs to find 1, it will go by order, so

- `numbers[0]` is 2, and $2 \neq 1$. So false and proceed
- `numbers[1]` is 4, and $3 \neq 1$. So false and proceed
- `numbers[2]` is 1, and $1 = 1$. So true and not proceed and return the answer.

So in other words,

We can divide all the possible cases by n to find the average time complexity,

So

$$
\frac{1 + 2 + 3 + 4 + 5 + 6} n
$$

Because

- Best case 1 is, it at numbers[0]
- Best case 2 is, it is at numbers[1]
- And so on

<br>
<br>

Or

$$
\frac{1 + 2 \text{ .... } n} n
$$

Or

$$
\frac{n(n+1)} {2 \times n}
$$

Or

$$
\frac{n+1}2
$$

So this was average case, which was also linear. So

$$
\text{time complexity } \propto n
$$

3. Worst case

```
numbers: {6, 5, 4, 3, 2, 1}
```

Here 1 is at last.

Here n = 5 but what if

$$
n = 10^5
$$

So we will have to take $10^5$ steps to get to 1.

So here as well

$$
\text{time complexity } \propto n
$$

## Better way of representation

- We can write best case as:

$$
    \Omega(1)
$$

A.K.A Omega of 1.

- We can write average case as:

$$
\Theta \left( \frac{n(n + 1)}{2} \right)
$$

A.K.A Theta of 1.

- We can write worst case as:

$$
\mathcal{O}(n)
$$

A.K.A Big O of 1

#### NOTICE

Whenever we are in interviews or competetive coding we always take worst case time complexity, so Big O. Why you may ask. Because we want to measure the worst and the longest time the allgoritm can take.

### More examples

1.

```java
public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    int n = scanner.nextInt();

    for (int i = 0; i<n; i++){
        for (int j = 0; j<n; j++){
            System.out.println("Hello");
        }
    }
}
```

So if `n=5` then the outer loop will run for 0, 1, 2, 3, 4 but the inner loop for each iteration of th eouter loop, so when `i=0`, th inner loop will run for 0, 1, 2, 3, 4; When `i=1`, the inner loop will run for 0, 1, 2, 3, 4; and so on.

So for each iteration, the inner loop runs `n` times.

So what was the times that outer loop iterated, $n$. And the inner loop also ran for `n` times each iteration. So the time complexity was:

$$
n \times n
$$

Or

$$
n^2
$$

So the total time complexity turns out to be $\mathcal{O}(n^2)$

2.

```java
public static void main(String args[]) {
    Scanner scanner = new Scanner(System.in);
    int n = scanner.nextInt();
    int m = scanner.nextInt();

    for(int i = 0; i<n; i++){
        for(int j=0; j<m; j++){
            System.out.println("Hello");
        }
    }
}
```

The outer loop runs `n` times and the inner loop runs `m` times.

Here the worst case time complexity is $\mathcal{O}(n \times m)$ or $\mathcal{O}(nm)$.

3.

```java
public static void main(String args[]) {
    Scanner scanner = new Scanner(System.in);
    int n = scanner.nextInt();
    int m = scanner.nextInt();

    for(int i = 0; i<n; i++){
        System.out.println("Hello");
    }

    for(int j=0; j<m; j++){
        System.out.println("Hello");
    }
}
```

The first loop runs `n` times and the second loop runs `m` times. So our time complexity is $\mathcal{O}(n + m)$.

But if let's say $n = 10^6$ and $m = 3$ , So the time complexity will move more toward $n$, hence it becomes $\mathcal{O}(n)$.

4.

Compare the following time complexities:

- n
- $n^2$
- $n^3$

Lets try a smaller input:
$n=1$

- So $\mathcal{O}(n)$ is just 1 operation
- $n^2$ is just 1 operation.
- $n^3$ is just 1 operation.

So it constant no matter what.

Similarly, if $n=2$,

- $\mathcal{O}(n)$ is 2
- But $n^2$ is 4 operations.
- And $n^3$ is 8 operations.

OR $n=3$,

- $\mathcal{O}(n) = 3 \text{ operations.}$
- $\mathcal{O}(n^2) = 9 \text{ operations.}$
- $\mathcal{O}(n^3) = 27 \text{ operations.}$

This is still small, lets tak $n=10^5$

- $\mathcal{O}(n) = 10^5 \text{ operations}$
- $\mathcal{O}(n^2) = 10^10 \text{ operations}$
- $\mathcal{O}(n^3) = 10^15 \text{ operations}$

Now this difference is _*huge*_.

Now this was just time complexity, but 1 more factor is...

# Space complexity

It is the measure of the space the code takes in memory.

It depends on

- The number of variables

If we take the following code:

```java
public static void main(String args[]) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();

    for (int i = 0; i < n; i++) {
        System.out.println("Hello");
    }
}
```

We can visualize our memory:
![alt text](image.png)

## In arrays the input size actually affects the memory.