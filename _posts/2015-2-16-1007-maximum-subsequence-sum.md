---
layout: post
title: 1007 Maximum Subsequence Sum
tags: Date-Struct
---

## 题目

Given a sequence of K integers { N1, N2, ..., NK }. A continuous subsequence is defined to be { Ni, Ni+1, ..., Nj } where 1 <= i <= j <= K. The Maximum Subsequence is the continuous subsequence which has the largest sum of its elements. For example, given sequence { -2, 11, -4, 13, -5, -2 }, its maximum subsequence is { 11, -4, 13 } with the largest sum being 20.

Now you are supposed to find the largest sum, together with the first and the last numbers of the maximum subsequence.

### Input Specification:

Each input file contains one test case. Each case occupies two lines. The first line contains a positive integer K (<= 10000). The second line contains K numbers, separated by a space.

### Output Specification:

For each test case, output in one line the largest sum, together with the first and the last numbers of the maximum subsequence. The numbers must be separated by one space, but there must be no extra space at the end of a line. In case that the maximum subsequence is not unique, output the one with the smallest indices i and j (as shown by the sample case). If all the K numbers are negative, then its maximum sum is defined to be 0, and you are supposed to output the first and the last numbers of the whole sequence.
Sample Input:

10

-10 1 2 3 4 -5 -23 3 7 -21

### Sample Output:

10 1 4

## AC 代码

{% highlight C linenos %}

#include <stdio.h>
#define MaxNumber 10000

void MaxSubeqSum(int List[], int N)
{
  int ThisSum, MaxSum;
  int i;
  int left = 0, right;
  int old_left = -1;
  int neg = 1, zer = 1;

  ThisSum = MaxSum = 0;

  for (i = 0; i < N; i++)
  {
    ThisSum += List[i];
    
    if (List[i] > 0) neg = 0;
    else if (List[i] == 0) zer = 0;

    if (ThisSum > MaxSum)
    {
      MaxSum = ThisSum;
      right  = i;
      left   = old_left + 1;
    }
    else if (ThisSum < 0)
    {
      ThisSum  = 0;
      old_left = i;
    }
  }

  if (neg == 1)
    if (zer == 1) 
     printf("%d %d %d\n", MaxSum, List[0], List[N-1]);
    else printf("%d %d %d\n", MaxSum, 0, 0);
  else
    printf("%d %d %d\n", MaxSum, List[left], List[right]);

  return ;

}

int main()
{
  int List[MaxNumber];
  int i, n;

  scanf("%d", &n);
  
  if (n > MaxNumber) return -1;
  
  for (i = 0; i < n; i++)
  {
    scanf("%d", &List[i]);
  }

  MaxSubeqSum(List, n);

  return 0;

}

{% endhighlight %}