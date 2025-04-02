# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

#### I've deduced that the median-of-three method is more likely to choose a good pivot than choosing the first element by this reasoning:

Using the probabilities for picking a pivot that we defined in lecture, if you 
were to choose the first element of a randomly ordered array, there would be a 50% 
chance you pick a "good" pivot and a 50% chance you pick a "bad" one. To find the 
probability of choosing a good pivot with the median-of-three method, we have to 
figure out the probably of getting a good pivot as the median of three randomly 
chosen elements.

There are 27 different orderings of {B, M, T} that represent the order of which we 
can choose 3 different elements. Here, I am representing the bottom 25% of elements 
as B, the middle 50% as M, and the top 25% as T. 13 of the orderings guarantee a 
median in M, and 14 orderings guarantee a median outside of M. The orderings are as 
follows:

Median in M: (MMM), (MMB), (MMT), (MBM), (MTM), (BMM), (TMM), (BMT), (TMB), (TBM),
             (BTM), (MBT), (MTB)

Median not in M: (BMB), (BBM), (TMT), (TTM), (MBB), (MTT), (BTT), (BTB), (BBT), 
                 (BBB), (TBB), (TBT), (TTB), (TTT)

From these groups, we can conclude that if you pick 2 or 3 elements from M, you have
a 100% chance to get a median in M. If you pick 1 element from M, you have a 50% 
chance to get a median in M since there are 6 orderings in the 'Median in M' category 
and 6 in the 'Median not in M' category. If you pick 0 elements from M, you have a 0% 
chance to get a median in M. We can group the orderings into simpler categories by 
representing all elements outside of the middle as X:

2 or 3 from M: (MMM), (MMX), (MXM), (XMM)
1 from M: (XXM), (XMX), (MXX)
0 from M: (XXX)

Since $\frac{4}{8}$ orderings have a 100% chance to give you a good pivot, $\frac{3}{8}$ 
orderings have a 50% chance to give you a good pivot, and $\frac{1}{8}$ orderings have a 
0% chance to give you a good pivot, we can calculate the total probability of getting a 
good pivot with this equation:

$\frac{4}{8} + ( \frac{1}{2} \cdot \frac{3}{8}) + (0 \cdot \frac{1}{8}) = \frac{11}{16}$ 

= 68.75%

So, the median-of-three method is more likely to choose a good pivot than choosing the 
first element since choosing the first element gives you a 50% chance of getting a good 
pivot, and the median-of-three method gives you a 68.75% chance.

#### Sources

Gage Hepworth told me the answer was in the high 60s.

"I certify that I have listed all sources used to complete this exercise,
including the use of any Large Language Models. All of the work is my own, except
where stated otherwise. I am aware that plagiarism carries severe penalties and
that if plagiarism is suspected, charges may be filed against me without prior
notice."
