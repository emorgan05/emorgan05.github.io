---
layout: post
title:      "An Algorithm Challenge"
date:       2018-04-26 15:09:00 +0000
permalink:  an_algorithm_challenge
---


This week I was given the opportunity to complete an algorithm challenge. It was timed and as I got to the last question, I ran out of time to fully complete it. After the test ended it kept rolling around in my mind, and I figured out how to make it work. 

## The Challenge:

I’m going to give you the basics, but just know that as with most algorithm challenges, it was phrased in a complicated and technical way. 

You are given an array of numbers. Your job is to create a function that sorts the array so that all even numbers are at the beginning of the array and all odd numbers are at the end of the array. But to sort it, you need to swap an odd with an even and make as few swaps as possible. Your return value needs to be the number of moves that you make to sort the array. 

## Examples:

Given the ```array [4, 5, 2, 7]```

You want to move the 2 into array[1] and the 5 to array[2]. That’s 1 move and sorts your array properly. 
Your return value will be 1.

Given the ```array [3, 8, 20, 16, 7, 9]```

You want to move the 3 to the end, but in as few moves as possible. So if you swap the 3 with the 8, it’s going to take too many moves to get it to the end of the array. It’s better if you swap the 3 with the 16 and your array is sorted in 1 move. 
Return value = 1.

## My First Solution:

My first solution finished in time, but it only solved 2 of the 3 tests. Here’s the way I was thinking about it:

1. Loop through the array
2. Find the first odd number
3. Swap it with the next even number (whether that is the next number in line or the 3rd)
4. Use a counter to track the number of moves and add 1 each time you swap
5. Continue with the loop
6. Return the counter

Here’s the actual code:

```
function moves(a) {
  let move = 0;

  for(let i = 0; i < a.length; i++) {
    if(a[i] % 2 !== 0) {
      let j = i + 1;
      while (j < a.length) {
        if(a[j] % 2 === 0) {
          let x = a[i];
          let y = a[j];
          a[i] = y;
          a[j] = x;
          move += 1;
          break;
        } else {
          j += 1;
        }
      }
    }
  }
  return move;
}
```

It worked great for an array like the first example [4, 5, 2, 7].
That looped through, swapped 5 and 2, and finished, returning 1. 

It continued to sort properly, even for more involved arrays, but the problem was that it was not choosing the simplest number of moves. 

For example, ```array = [4, 13, 10, 21, 20]```

The simplest swap is 13 and 20. That is one move that will make the array [4, 20, 10, 21, 13] and it’s properly sorted for this problem. (Side note: there is no need for the even or odd numbers to be in any order, they just need to be in an even and odd section). 

I knew what my code was doing instead of the simplest swap. 
1. First it swapped the 13 and the 10, giving [4, 10, 13, 21, 20]
2. Then it swapped the 13 and the 20, giving [4, 10, 20, 21, 13]
3. It gets to the sorted array, but it took 2 moves instead of 1. 

## Refactoring: 

With the failing test, I went back to my code. I was hoping that I could refactor it to make it work in the few minutes I had left. 

Unfortunately, I pretty quickly realized that this was not a simple refactor and that instead, I would have to rethink my entire approach to the problem. Thinking about finding the odd number and swapping it with the next even wasn’t going to give me the simplest number of moves. And there wasn’t a way to make it work. 

So I started rethinking my entire approach to the problem. What did I really need to know in order to solve the challenge?

I got two steps into a new approach and ran out of time. 

But I kept going with it and solved the problem. 

## The New Approach:

It took a few gears creakily groaning in my brain to shift from my initial thought of find the odd and swap it with the next even. The first thing that I realized was I needed to know exactly how many even numbers were in this array and how many odd numbers were in this array. Then I would know what I was dealing with. 

Then it suddenly struck me that I didn’t have to actually swap the numbers. 
<iframe src="https://giphy.com/embed/3ohzdWXG2y5Q61Vi2Q" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/geekandsundry-reaction-3ohzdWXG2y5Q61Vi2Q">via GIPHY</a></p>

**So here’s the new approach:**

1. Loop through the array and count the number of even numbers and the number of odd numbers
2. Loop through the array again, but stop at the even numbers (essentially treat the even number as the limit of an evens array)
3. If there are any odd numbers in that section, add 1 to the move counter
4. Return the move counter

Ok, so my thinking there is, if I know the total number of evens in the array is 4, then array[0] - array[3] will have to be even. If there is an odd number at array[1], it has to move. So that’s one move. If there are odd numbers at array[1], array[2], and array[3], then they all have to move, so 3 moves. 

**And here’s the code:**

```
function moves(a) {
  let move = 0;
  let evens = 0;
  let odds = 0;

  for(let i = 0; i < a.length; i++) {
    if(a[i] % 2 === 0) {
      evens += 1;
    } else {
      odds += 1;
    }
  }

  for(let j = 0; j < evens; j++) {
    if(a[j] % 2 !== 0) {
      move += 1;
    }
  }
  return move;
}
```

And that tricky test that didn’t pass, the one where array = [4, 13, 10, 21, 20]. Now it passes with one move.

