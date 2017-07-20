Home Assignment: The Love Geometry
==================================

Here is the Love Geometry project consisting several steps which graded independently. The necessary exercises are
[Step 1](#step-1-the-language-of-love-and-destruction) and [Step 2](#step-2-show-me-your-love) everything else is
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
1. If project has prerequisites there should be a how-to manual for installing them.
1. We want you to use Python 3.5+.

Get Ready for PEG
-----------------

Take a look at [pyPEG](https://fdik.org/pyPEG/). It's a Python parser for
[parser expression grammars](https://www.wikiwand.com/en/Parsing_expression_grammar) which is very similar to
context-free grammars you may know from the Computer Science courses.

Don't be afraid! It's not as scary as it seems (:

It may be hard to design a grammar at the first time. There is a similar library for Javascript which has a
[live editor](https://pegjs.org/online) where you can start to play with grammar definitions.

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

```python
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
parser to be implemented as a module and covered by test cases. We do not restrict you by any testing framework, pick
what you fits you best.

You should provide a description for each of your test cases.

### Completion Checklist

- [ ] PEG parser for the love story language.
- [ ] Unit tests for the parser.
- [ ] Installation and running how-to manual in the `README.md`.

### On the Meaning of Love

Here we want to disambiguate meaning of term we use in the document.
 
A *state of love*, the *love case* or the *situation of love* is the order of things described in a one sentence. We can
think about it as a snapshot of relations.

A *love story* is a sequence on love states.

Why not *story of relations*? Well, in our pocket universe loathing can be thought as just a negative form of love. 

Step 2. Show Me Your Love
-------------------------

Now let's create an ecosystem for our language.

First of all we want yo to create a simple web application (pick whatever you want but we think
[Flask](http://flask.pocoo.org/) or [aiohttp](http://aiohttp.readthedocs.io/en/stable/) will be enough) with one API
endpoint which receives a love story and responds with the parsed structure.

The next thing is to write a simple client library that talks to that endpoint and parses written love stories to their
structural representations. 

There should be a minimal error reporting with HTTP codes and error descriptions in case when client sends invalid love
statements.

We also want you to create a simple [Jupyter Notebook](http://jupyter.org/) with a piece of the code which talks to the
love story server and prints response in an easy readable way.

### Completion Checklist

- [ ] Server application that parses love stories.
- [ ] Client library that talks to that server.
- [ ] Jupyter notebook where we can play with the client and send requests to the server.
- [ ] Manual that describes how to use the start the app and the notebook.

### More Summits Ahead

Completion of this task together with the [Step 1](#step-1-the-language-of-love-and-destruction) should be enough to
pass the grading threshold.

But why stop here? There are more challenges to complete. Besides, you may have some crucial errors in your solution
you, don't see now. So, if I were you, I will take the next steps in order to get even more fun and confidence in your
results.

Step 3. Find the Cheater (optional)
-----------------------------------

This task is optional but it may be useful for later steps and also gives an important perspective on the DSL design. 

As we can see from the [Step 1](#step-1-the-language-of-love-and-destruction) the syntax does not constrains us to write
things like:

```
A loves B but A hates B.
A loves B, A loves B, A loves B.
A loves A.
```

What additional constrains should we apply to the language semantics? Define those constrains and describe them in the
`README.md`.
 
Implement the validator that checks parsed structures and shows messages in case when user writes a meaningless state of
love. You also can integrate some checks into the grammar but the parser should not swallow errors (e.g. if user does
something you consider as wrong he or she should receive an error).

It is up to you whether the semantic check has to be implemented in the parser library or at the server application.
But we want to keep an ability to receive an unchecked (original) response. And, please, [don't put the logic inside the
controller](https://www.hughgrigg.com/posts/keep-controllers-thin/).

### Completion Checklist

- [ ] Implement semantic validation on the parser or server application level.
- [ ] Keep the possibility for the pure (unchecked) run of the parser.
- [ ] Propagate errors to the client.
- [ ] Document your decisions.
- [ ] Add or update the code in the Jupyter notebook to test your solution.

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
 
The third is a high self-esteem. Have you forbidden that kind of relations at the
[Step 3](#step-3-find-the-cheater-optional)? Well then you may reconsider your decision. Or keep it. It's all up to you.

In order to complete this exercise you have to design and implement an algorithm which finds all circles in a given
sate of love.

We want you to create an API endpoint which responses with a list of such circles for a given love story, update the
client library and extend the Jupyter notebook with a new snippet of code that tests this exercise.

The algorithm itself can be implemented at the level of the parser library or as a part of the application.

Whatever you do, don't put the logic inside the controller. Just [don't](https://www.hughgrigg.com/posts/keep-controllers-thin/).

### Completion Checklist

- [ ] Implement the algorithm that searches for affection circles.
- [ ] Add the API endpoint.
- [ ] Update the client library.
- [ ] Add or update the code in the Jupyter notebook to test your solution.

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

To complete this assignment you should serve an HTML page with a form consisting a text area field for a love story and
a submit button. Once pressed we want you to render a page with love representation tables which corresponds to a
written love story.

You can use AJAX requests or reload the page with the submitted GET or POST parameters. It's completely up to you.
 
In case of a wrong input you should show corresponding errors.

To have all possible credits you also have to introduce `mutually` keyword to the love language parser.

### Completion Checklist

- [ ] Create a web page with a text area for a love story and a submit button.
- [ ] Render love representation tables for a submitted story.
- [ ] Document your solution in the `README.md`.

### Excellent Mark Checklist 

- [ ] Add `mutual` keyword to the love story language.

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

Conclusion
----------

Hope you will find this assignment interesting.

We put so much stuff here because we want you to focus on exercise you find most exciting to you.

And no matter how far you will decide to go through the assignment we would love to hear feedback from you.

Thank you and good luck! 