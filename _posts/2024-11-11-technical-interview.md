---
title: "An Approach to the Technical Coding Interivew"
author: "Ahad Jawaid"
date: "2024-11-03"
layout: post

thumbnail: assets/img/posts/technical-interview/programming.png
description: An overview of how approach technical coding interviews.
categories: [Interview, Programming]
giscus_comments: true
---

I recently started preparing for interviews again, and through discussions with friends, I noticed how to approach technical interviews isn't always clear. While there are many people with more experience interviewing at top companies than me, I thought I'd share my approach which has worked for me in interviews with Amazon, Goldman Sachs, Capital One, and Toyota.

Technical interviews at big tech companies, particularly those modeled after "FAANG" (Facebook, Amazon, Apple, Netflix, Google), tend to follow a specific format. Often, you're given a problem similar to a "LeetCode" esque question, with around 20 to 45 minutes to solve it. Some companies, like Meta, may even ask their applicants solving two questions within a 40 minutes interval.

### My Formula for Technical Coding Interviews

Here’s the process I typically follow during a technical interview:

{% include figure.liquid loading="eager" path="assets/img/posts/technical-interview/technical-interview.png" class="img-fluid rounded z-depth-1 w-50 mx-auto" %}

#### 1. Read the Problem

While reading the problem, I try not to go silent. Speaking out loud helps communicate my understanding to the interviewer. Here, it’s important for me to understand the relationship between the inputs and outputs. 

#### 2. Clarify Assumptions

After understanding the intial prompt, I validate my assumptions by asking the interviewer. Holding an incorrect assumption throughout the interview can lead to solving the wrong problem. Asking questions can prevent misunderstandings and allows me to validate the problem requirements directly with the interviewer.

#### 3. Identify Test Cases (Optional)

If time permits, I write a few test cases to better understand the problem. For example, for a problem like "two-sum," a test case I write might look like this:

```
array = [1, 2, 3, 4], target = 5 -> [1, 2]
```

Specifying the expected inputs and outputs clarifies my understanding, and I validate these cases are correct with the interviewer. These initial test cases also help verify my solution once it’s implemented.

#### 4. List Potential Solutions

Next, I start brainstorming solutions based on familiar patterns, such as "two-pointer" methods for arrays or hash maps for fast lookups. Initially, I might discuss a brute-force approach before working towards an optimized solution. When discussing each option, I evaluate its time and space complexity to justify my choice.

#### 5. Choose a Solution

Once I decide on the optimal solution, I confirm with the interviewer before coding. This helps ensure they agree with my approach, avoiding potential misunderstandings.

#### 6. Code the Solution

With the go-ahead, I start coding the solution, narrating my thought process to give insight into my choices. For example, I might say, “I’m using a dictionary here to achieve faster lookups, which reduces time complexity.” This part relies heavily on your implementation skills and effective communication.

#### 7. Dry Run Solution (Optional)

If there’s time, I walk through the code with my test cases, effectively "debugging" manually. I step through each line of code, tracking variable changes and outputs to ensure accuracy. For example, here’s how I might track variables:

```
array = [1, 2, 3, 4]
target = 5
i = 0
```

For recursive solutions, I also simulate the call stack, which might look like this:

```
...
fn(array=[1, 2, 3], target=5)
fn(array=[1, 2, 3, 4], target=5)
```

## Reflections on Time Management

Managing time well during technical interviews is crucial. Many candidates can solve common patterns with enough time, but the key to standing out is delivering a clear solution within the given timeframe. For optional steps like dry-running, I adjust based on how much time remains. If I'm running low, I may skip the dry run, especially if I didn't define edge cases earlier. Similarly, if I'm struggling to come up with the optimal solution, I’ll proceed with a simpler approach rather than leaving the problem unsolved.

## Preparation

To do well with this formula, I focus on three skills:

1. Learning algorithm patterns.
2. Improving implementation skills.
3. Practicing clear and interactive communication.

For the first two, practicing problems on platforms like LeetCode is useful, while mock interviews are helpful for improving verbal explanations.

I've also included some resources that helped me improve these skills:
- [Grokking the Coding Interview](https://www.designgurus.io/course/grokking-the-coding-interview): Useful for understanding main coding patterns.
- [NeetCode Practice Set](https://neetcode.io/practice): A curated set of practice problems across various patterns.
- [Blind 75 LeetCode Questions](https://leetcode.com/discuss/general-discussion/460599/blind-75-leetcode-questions): A popular list of LeetCode problems that teaches you patterns.


Thanks for reading about my approach to technical interviews. I hope this overview provides a useful perspective, and I'm happy to answer any questions you might have!
