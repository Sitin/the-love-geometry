Lego Land
=========

Here is the Lego Land project consisting several steps which graded independently. The necessary exercises is only a
[Step 3](#step-3-lego-land), everything else is optional.

Steps [1](#step-1-warmup-blocks-optional) and [2](#step-2-warmup-rectangle-optional) are warmup exercises. You feel to
skip them if you are sure in your ability to complete [Step 3](#step-3-lego-land).

In [Step 4](#salus-per-aquam-optional) you can try yourself and create an SPA. This is a star-type of assignment. We do
not expect you to finish it but we will love to work with a person who can see outside of the box of his competency and
specialisation.

By completing each step of this home assignment you proof that you have some valuable feature. So, it's ok to not to
complete all of them.

Technical requirements
----------------------

Pay attention to the following requirements. They are simple but necessary for your success.

1. The solution SHOULD come in a form of a code bundle (`*.tgz` or `*.zip`).
1. The name of the bundle should be `love-geometry-<your full name>-v<version number>`. The version number starts from
   `1`. We accept multiple versions of the assignment. The final grade will be calculated for the latest version of your
   assignment.
1. You SHOULD not present this solution publicly. This will cause an immediate and inexcusable failure (:
1. Each exercise should be implemented on a separate page. You can use shared CSS and Javascript if you will.
1. All pages include a heading with your full name at the top. Also your full name should be the first thing at the page
title.

Step 1. Warmup Blocks (Optional)
--------------------------------

Create a responsive markup for 3 blocks: A, B and C. Each of 200px width.

When the blocks can be displayed in one line the order should be ABC:

|     |   200px  |   200px  |   200px  |     |
|-----|----------|----------|----------|-----|
|     |     A    |     B    |     C    |     |

When only 2 blocks can fit in one line the order should be ACB:

|     |   200px  |   200px  |     |
|-----|----------|----------|-----|
|     |     A    |     C    |     |
|     |     B    |          |     |

Finally, when there is space only for a one block the order is CAB:

|     |   200px  |     |
|-----|----------|-----|
|     |     C    |     |
|     |     A    |     |
|     |     B    |     |

Step 2. Warmup Rectangle (Optional)
-----------------------------------

Create responsive markup for the following 4 blocks. Preserve the order listed below.

Here is how they should be positioned when there is enough space to display all 3 columns: 

|     |   200px  |   200px  |   200px  |     |
|-----|----------|----------|----------|-----|
|     |     A    |          |          |     |
|     |     B    |     C    |     D    |     |

But if they do non fit into 3 columns they should transform into one-column layout:

|     |   200px  |     |
|-----|----------|-----|
|     |     A    |     |
|     |     C    |     |
|     |     D    |     |
|     |     B    |     |

Step 3. Lego Land
-----------------

Here is the `legolize` function which creates an HTML string with `count` of divs each having a class randomly selected
from the `classes` list:

```javascript 1.8
function legolize(count, classes) {
  function randomClasses(count, classes) {
    let xs = [];
    for (let i = 0; i < count; i++) {
      xs[i] = classes[Math.floor(Math.random() * classes.length)];
    }
    
    return xs;
  }
  
  return randomClasses(count, classes).map(x => '<div class="' + x + '">&nbsp;</div>');
}
```

Your task is to:

1. Create a page filled with at least 64 of blocks with at least 3 random classes.
1. The size of block is 64x64 pixels.
1. Block with different class should have a different background color.
1. You should use [floating](https://www.w3schools.com/cssref/pr_class_float.asp) positioning model for blocks. E.g.
   there should be as much blocks on the line as it fits to a screen. 
1. 3 consequent blocks of the same class on the one line should be displayed with the special background.

The last task is the most tricky one and requires some explanation. The one line condition means that the following
blocks should keep their class background:

|     |   64px   |    64px  |    64px  |     |
|-----|----------|----------|----------|-----|
|     |     A    |     B    |     B    |     |
|     |     B    |     A    |     A    |     |
|     |     B    |     A    |          |     |

But if we make a screen wider then 3 B's may come in a one line:

|     |   64px   |    64px  |    64px  |    64px  |     |
|-----|----------|----------|----------|----------|-----|
|     |     A    |   **B**  |   **B**  |   **B**  |     |
|     |     A    |     A    |     B    |     A    |     |

And thus the special background should be applied to them.

Salus Per Aquam (optional)
--------------------------

Put the whole your assignment into a single page application using React or Angular 2+ or any other framework. In this
case different steps should be on different tabs or routes.

Remember about title format described in [technical requirements](#technical-requirements).

Completion of this assignment isn't necessary but gives you a big plus.