But a Whimper
=============

Here is the Lego Land project consisting several steps which graded independently. The necessary exercises are only a
steps [1](#step-1-describe), [2](#step-2-plan-your-attack) and [3a](#step-3a-case-sensitive)/[3b](#step-3b-cucumber-time).

In optional [Step 4](#step-4-a-clockwork-cucumber-optional) you can try yourself as an automation testing engineer. This
is a star-type of assignment. We do not expect you to finish it but we will love to work with a person who can see
outside of the box of his/ner competency and specialisation.

By completing each step of this home assignment you proof that you have some valuable feature. So, it's ok to not to
complete all of them.

Technical requirements
----------------------

Pay attention to the following requirements. They are simple but necessary for your success.

1. The solution SHOULD come in a form of a bundle (`*.tgz` or `*.zip`).
1. The name of the bundle should be `whimper-<your full name>-v<version number>`. The version number starts from `1`.
   We accept multiple versions of the assignment. The final grade will be calculated for the latest version of your
   assignment.
1. All textual parts of the assignment should be presented in a single PDF document.
1. The title of the document should consist the assignment name, your full name and the version of the assignment.
1. If you will complete programming assignment then there should be a `README.md` in the root of your assignment with
   the guide to start your solution.
1. All texts should be written in English.
1. You SHOULD not present this solution publicly. This will cause an immediate and inexcusable failure (:

Meet Noisli
-----------

[Noisli](https://www.noisli.com/) is the nice and simple site we will use in our test assignment. It helps to organize
user's sound environment. Explore it before staring to work on the assignment. 

Step 1. Describe
----------------

Write a short but complete description of the Noisli project. Try to focus on the most important parts of the project.
Describe what the application gives to the user. Avoid marketing stereotypes and promotion. More facts, less sentiments.   


Step 2. Plan your Attack
------------------------

Here we want you to write a [test plan](https://en.wikipedia.org/wiki/Test_plan) for the Noisli project. Take
[IEEE 829-2008](http://ieeexplore.ieee.org/document/4578383/) as a template. Try to fill as much parts as possible. For
those paragraphs you will decide not to fill give a clear explanation why it is not relevant.

Step 3a. Case Sensitive
-----------------------

Write test scenarios for main functionality of Noisly application. Organise your scenarios in suites. Prioritize your
tests.

You can skip this step if you want to use [Cucumber](https://cucumber.io/docs/reference) you can skip this task and
proceed to [Step 3b](#step-3b-cucumber-time).

Step 3b. Cucumber Time
----------------------

Write test scenarios for main functionality of Noisly application using [Cucumber](https://cucumber.io/docs/reference).
Organise your scenarios in feature suits each in a separate file.

Add a short contents for Cucumber feature files in your PDF file or `README.md`. Prioritize your tests in that list.

Step 4. A Clockwork Cucumber (optional)
---------------------------------------

Only for those who accomplished [Step 3b](#step-3b-cucumber-time).

Use your favorite tool to convert Cucumber into automated tests. You can use anything you think is appropriate here. It
is possible to automate only a most important subset of your Cucumber scenarios to pass this task.

Obvious suggestions:
* [Cucumber.js](https://github.com/cucumber/cucumber-js) — Javascript
* [Letuce](http://lettuce.it/) — Python
* [Cucumber for Rails](https://github.com/cucumber/cucumber-rails) — Ruby on Rails (still implies overhead in a form of
  Rails app) 

Ensure that `README.md` contains all installation and run instructions for your tests.
