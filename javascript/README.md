Home Assignment: The Love Geometry
==================================

Here is the Love Geometry project consisting several steps which graded independently. The necessary exercises are
[Step 1](#step-1-the-language-of-love-and-destruction) and [Step 2](#step-2-show-me-your-love), everything else is
optional.

By completing each step of this home assignment you proof that you have some valuable feature. So, it's ok to not to
complete all of them.

But note that poor implementation of necessary steps won't give you enough grade. Which means that working on some
optional stuff may be a wise decision. 

You also may jump over some exercises but since later stages depends on their predecessors you should do it in a smart
way. What does it mean? That you should somehow mock the incomplete functionality: either by some code stubs or by the
bold design solution. Feel free to embrace your imagination.

Technical Requirements
----------------------

Pay attention to the following requirements. They are simple but necessary for your success.

1. The solution SHOULD come in a form of a code bundle (`*.tgz` or `*.zip`) or from the private GitHub repository (you
can request GitHub account which should be invited to).
1. You SHOULD not present this solution publicly. This will cause an immediate and inexcusable failure (:
1. There should be an OBVIOUS way to run the project described in the `README.md` provided in the root of the
repository/bundle. All command line steps should be described as if you are talking to a person without programming
skills.
1. If project has prerequisites (Node.js, NPM, Angular CLI et c.) there should be a how-to manual for installing them.
1. You can dockerize your application if you want. It will give you a few extra credits.  

Get Ready for PEG
-----------------

Take a look at [PEGjs parser](https://pegjs.org/) it's a Javascript parser for
[parser expression grammars](https://www.wikiwand.com/en/Parsing_expression_grammar) which is very similar to
context-free grammars you may know from the Computer Science courses.

Don't be afraid! It's not as scary as it seems (:

There is a nice [intro](https://coderwall.com/p/316gba/beginning-parsers-with-peg-js) you can look trough.

Step 0. Pick Your Favorite Tool
-------------------------------

The project should come in a form of a single page web application. You are free to use any framework you want but we
encourage you to use Angular 4 or React (+ something).

Note that we do care about design and usability but this assignment tests your engineering skills. So, the UI/UX should
help you to better express your solution and us to better asses them.

We think that all exercises may be implemented as evolution of one page. Still you free to ad several sections. But in
that case don't forget about navigation.

Step 1. The Language of Love and Destruction
--------------------------------------------

Let's say we have a toy language that describes relations between people:

```
A loves B but B hates A.
A hates B, A loves D while B loves C and D hates A.
A loves B, B loves A and B loves D.
A loves B but B hates A
D loves B and C loves A.
```

Each sentence here represents a state of the evolving love story.

Note that there are **multiline** sentences (like the last one)!
 
We want to write a parser for this language that for each line returns a structure of relations of people mentioned in
it. Such structure can be (but not necessary) like the following:

```javascript
[
  {
    'A': { 'loves': ['B'] },
    'B': { 'hates': ['A'] }
  },
  {
    'A': { 'hates': ['B'], 'loves': ['D'] },
    'B': { 'loves': ['C'] },
    'D': { 'hates': 'A' }
  }
]
```

As you can see it represents the first two lines of the story above.

We do not give you a formal definition of this language. Instead we want you to design grammar sufficient to grasp its
spirit.

For this part of the assignment the sufficient representation does not require any user interface. Instead we want the
parser to be implemented as a module and covered by test cases. We do not restrict you by any testing framework since
Node.js has built in `assert` module which may be sufficient if you are not experience with testing.

You should provide a description for each of your test cases.

### On the Meaning of Love

Here we want to disambiguate meaning of term we use in the document.
 
A *state of love*, the *love case* or the *situation of love* is the order of things described in a one sentence. We can
think about it as a snapshot of relations.

A *love story* is a sequence on love states.

Why not *story of relations*? Well, in our pocket universe loathing can be thought as just a negative form of love. 

Step 2. Show Me Your Love
-------------------------

The exercise will be completed when there will be a text area input for a love story and the text field with the
corresponding javascript structure. You should parse the stories automatically each time when user changes the text
(this is usually called "live edit").

There should be a minimal error reporting in case when user enters invalid love statements.

You can use code highlights like [Code Mirror](https://codemirror.net/) if you want. I've used the one in my one of my
[pet projects](http://takorogo.github.io/#/) when I was in love with graph databases and DSLs.

This is a major task and if fully completed together with the Step 1. it should be enough to pass the grading threshold.

But why stop here? There are more challenges to complete. Besides, you may have some crucial errors in your solution
you, don't see now. So, if I were you, I will take the next steps in order to get even more fun and confidence in your
results.

Step 3. Find the Cheater (optional)
-----------------------------------

This task is optional but it may be useful for later steps and also gives an important perspective on the DSL design. 

As we can see from the step 1. the syntax does not constrains us to write things like:

```
A loves B but A hates B.
A loves B, A loves B, A loves B.
A loves A.
```

What additional constrains should we apply to the language semantics? Define those constrains and describe them (either
at the `README.md` or inside your SPA).
 
Implement the validator that checks parsed structures and shows messages in case when user writes a meaningless state of
love. You also can integrate some checks into the grammar but the parser should not swallow errors (e.g. if user does
something you consider as wrong he or she should receive an error).

Step 4. Circles of Affection (optional)
---------------------------------------

Sometimes we have a state of love with circles of feeling of some type. E.g.:

```
A loves B, B loves C and C loves A.
A hates B while B hates A.
A loves A.
```

In the first sentence we have a traditional love triangle.

The second one is a mutual loathing.
 
The third is a high self-esteem. Have you forbidden that kind of relations at the Step 3? Well then you may reconsider
your decision. Or keep it. It's all up to you.

Now. In order to complete this exercise you have to design and implement an algorithm which finds all circles in a given
sate of love.

We want you to create a block at the page where you will list such circles for the given love story (in addition to
the area with listed structures from the Step 2).

Step 5. The Matrix of Love (optional)
-------------------------------------

Now let's have some fan!

How about to create a table representation for a given state of love?

Let's say we have the following situation:

```
Lyubomir loves Ron, Ron hates Lubomyr
Vasya hates Alice, Alice hates Vasya
Ulices loves Alice, Alice loves Ulices
Mary loves Vasya
Ulises hates Theodoric.
```

In this case the table should looks like:

|          | Ron | Alice | Mary | Theodoric |
|----------|:---:|:-----:|:----:|:---------:|
| Vasya    |     |   -   |  ?/+ |           |
| Lyubomir | +/- |       |      |    -/?    |
| Ulises   |     |   +   |      |           | 

Now, the table is good but the textual description is ugly.
 
What if we'll add a special keyword to describe mutual affection? So, the description will be:

```
Lyubomir loves Ron, Ron hates Lubomyr
Vasya mutually hates Alice
Ulices mutually loves Alice
Mary loves Vasya
Ulises hates Theodoric.
```

Much better!

To complete this assignment you should create a component which renders such table according to the currently described
structures. Which means there may be several such tables at the page since one story may consist several states. 

To have all possible credits you also have to introduce `mutually` keyword to the love language parser. 

### The Love Matrix Behaviour
 
In order to disambiguate how table should work let me add some examples.

Consider if in addition to the existing text we will add:
 
```
...
Ulises mutually loves Mike
...
```
It means we have to add a new column, e.g.:

|          | Ron | Alice | Mary | Theodoric | Mike |
|----------|:---:|:-----:|:----:|:---------:|:----:|
| Vasya    |     |   -   |  ?/+ |           |      |
| Lyubomir | +/- |       |      |    -/?    |      |
| Ulises   |     |   +   |      |           | +    |


Now, if we will strip `Mary loves Vasya` from the text resulting to:

```
Lyubomir loves Ron, Ron hates Lubomyr
Vasya mutually hates Alice
Ulices mutually loves Alice
Ulises mutually loves Mike
Ulises hates Theodoric.
```

There will be no more Mary, so, we have to remove the empty “Mary” column:

|          | Ron | Alice | Theodoric | Mike |
|----------|:---:|:-----:|:---------:|:----:|
| Vasya    |     |   -   |           |      |
| Lyubomir | +/- |       |    -/?    |      |
| Ulises   |     |   +   |           |  +   |

Step 6. The End of Love (optional)
----------------------------------

Write end-to-end tests for all completed steps.

We will evaluate the grade for this exercise looking not only to the number of test cases but also on their
completeness. It is always better to get more with less efforts.

You can use any reasonable testing solution you want (we prefer Selenium and Chrome webdriver). Note that the tests
should run on our environment and you have to include installation manual for all the tools you use. 

Conclusion
----------

Hope you will find this assignment interesting.

We put so much stuff here because we want you to focus on exercise you find most exciting to you.

And no matter how far you will decide to go through the assignment we would love to hear feedback from you.

Thank you and good luck! 