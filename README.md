Word chains are a simple game often found in the games and puzzles section of
newspapers. The aim of the game is to get from one word to another by changing
one letter of the word each time. Each change of letter must result in a legal
intermediate word. For example, we can change LEAD into GOLD through the
following steps:

LEAD → LOAD → GOAD → GOLD

Using Java, create an automated solver method that accepts the start and end words
and prints a list of steps required to do the transform. There’s a dictionary of legal
words to use in your solver in this zip file. You can assume the dictionary will be in
the same directory as your executable. Start and end words should be the same
length as each other.


--------- My comments on solution.

The word chain game can produce many solutions - the above says that there is one possible chain of steps (intermediate
words) which can lead from one word to another. This in general is not true - the soluton set can be many possible
chains of words. Actually there is no evaluation which solution might be better than other - longer or shorter?

Restriction on length of input and output words is important, as it limits the possible chain set a lot.

There is no comment on uppercase/lowercase letters, but we can assume that there is no difference between 'Table', 'TABLE' or
'TaBlE'.

The websters dictionary will be loaded at the beginning of the execution, and automata will search for possible solutions
using it heavily.
The most important operation is to retrieve all possible n+1 steps is to get result that:
1) does not exist in already found set of words (all previous steps)
2) do differ by one letter
3) exists within the dictionary (obviously).

The first aproach to this solution is an recursive generator of all solutions which should work according to following
algorithm:

1) start with SetOfWords = {inputWord},
2) retrieve all possible next steps from dictionary - say N * nextStep (different step values),
3) if the set of next steps is empty - there is no more solutions,
3) for all next steps create SetOfWords = {inputWord, nextStep},
4) if nextStep is equal outputWord then return this as a solution
5) otherwise go to #2

This naturally sounds like recursive generator.

-------- My last comment on solution
I'm really suprised how much time this search takes. It takes minutes to report some chains of words. I did some obvious
optimisation on dictionary, limiting the dictionary to be searched to only words of given length, but still this program
takes a lot and reporting of all possible solutions - and will take much time.
The next step for optimise I guess would be limiting the length of the word chain to some limit - but this will result
in reporting not all of possible combinations. After some consideration I have added this possibility to do some research
on the complexity of this problem.

For "load" to "gold":
- only one 3 word solution
- 8 solutions for 4 word chain
- 69 solutions on 5 word chain

So we can see that the amount of solutions increases a lot!

This problem is even more interesting when removing the limit of word length fix - this will mean that from one word to
another we can go by adding or removing, not only changing chars.

I like this problem a lot and enjoyed to solve it! :)