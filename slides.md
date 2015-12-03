% Software Carpentry in Computational Science
% Adapted from [Scientific Computing for Numerical Mathematicians Lecture](https://github.com/ahmadia/lectures-scientific-computing-advice) by Aron Ahmadia

# Introduction

There are a plethora of best practices available to help you scientifically compute.
It is likely that you will only be able to afford a limited amount of time learning a subset of them.
The purpose of this lecture is to help orient you on the path to writing software as part of your research by:

* introducing the most important practices of software construction
    + and relating them to your role as a `data scientist`
* making specific recommendations for
    + selecting tools that you should be using
    + and practices that you should be following

# The 8 Essential Practices

[Best Practices for Scientific Computing](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745)

1. Write Programs for People, Not Computers
2. Let the Computer Do the Work
3. Make Incremental Changes
4. Don't Repeat Yourself (or Others)
5. Plan for Mistakes
6. Design Flexibly for Performance, Build Accessibly for Correctness
7. Document Design and Purpose, Not Mechanics
8. Collaborate



# 1. Write Programs For People, Not Computers


* A program should not require its readers to hold more than a handful of facts in memory at once.
* Make names consistent, distinctive, and meaningful.
* Make code style and formatting consistent.
* [Python Enhancement Proposal 8: Style Guide](https://www.python.org/dev/peps/pep-0008/)
    + 4 spaces for indentation
    + `_single_leading_underscore` for private variables
    + Classes should be named as `CapWords`
    + Functions should named as `separated_by_underscores`
    + Constants should be named as `ALLCAPS`
    + `a+= b` may not work in all interpreters
    + Use `if isinstance(` instead of `if type(`


# 2. Let the Computer Do the Work


* Make the computer repeat tasks.
* Save recent commands in a file for re-use.
* Use a build tool to automate workflows.

# 3. Make Incremental Changes.


* Work in small steps with frequent feedback and course correction.
* Use a version control system.
* Put everything that has been created manually in version control.

# Organize with Wikis

* Similar to a lab notebook
* organize your personal notes
* organize your shared notes
* Wiki tools
    + gollum, gitit, instiki
    + Can run privately on your desktop/notebook
    + Allow inclusion of equations, images, code
* Alternatives
    + Google Docs
    + Evernote
    + Don't generally have equation or code support

# Use Version Control for Checkpointing and Collaboration

* use *local* version control software to checkpoint personal code development
    + checkpointing your work encourages wild ideas and late-night coding sessions
    + you can easily restore back in the morning if it was a bad idea
    + no server or central database required (Git)
* use **distributed version control** to collaborate with others
* I advocate *Git*, but you may be stuck with whatever your group uses
    + though check out git-svn for using Git to collaborate with an svn repository, it's awesome!

# 4. Don't Repeat Yourself (or Others)


* Every piece of data must have a single authoritative representation in the system.
* Modularize code rather than copying and pasting.
* Re-use code instead of rewriting it.

# Automate common actions by saving simple blocks of code into **scripts**

* A script is a set of commands organized into a single file
* Sometimes it takes a few arguments, but more often there are just some parameters at the top of the file to modify
* The script is the base unit of scientific programming, you should be comfortable writing these whenever you want to save or otherwise document or repeat your actions
* Use scripts to explore new ideas, they are easy to write and throw away
* **Don't repeat commands into your REPL, save them to a script**

# Refactor commonly used blocks of code into **functions**

* Eventually, you will find that your scripts have a lot of repeated code, or that you are spending a lot of time adjusting parameters at the top of the file
* Refactor out repeated code into **function calls** in your scripts and implement the **function** either in the same file or a separate one
* Be comfortable with the calling and return syntax of your programming language environment, whether it is BASH or Python
* **Don't repeat code in scripts, refactor them to functions**

# Group commonly used functions into **libraries**

* If you can imagine a task there may already be a package/module/library
    + `conda` makes it really easy try new packages
* If you are unlucky enough to have to write a lot of software functions for your work, you might want to consider designing and releasing a library so that others do not have to share your misfortune
    + Make your own `conda` recipes



# 5. Plan for Mistakes


* Add assertions to programs to check their operation.
    + Packages like Numpy and Pandas provide helpful assertion functions
    + Many times they are tiny functions to test just one operation
* Use an off-the-shelf unit testing library.
    + `nosetests` or `py.test` make automated test running easy.
* Turn bugs into test cases.
    + Don't just fix it and forget it.
* Use a symbolic debugger.

# Verify and Validate your Code

* **verification** - is your code correctly written?
* **validation** - do your computations accurately model the physical phenomena in question?
* Test frameworks help you verify your code, but validation is usually a manual process
    + although it is desirable to write regression tests that verify previously validated results hold true when the code has been modified!
* Use the **method of manufactured solutions** to verify correctness of code
* use **comparisons to experiment** to validate code
* use **comparisons to similar software** as an additional check

# 6. Document design and purpose, not mechanics.


* Document interfaces and reasons, not implementations.
    + Comments should explain *why* and *how*
* Refactor code in preference to explaining how it works.
    + Clear, readable code is its own explanation
* Embed the documentation for a piece of software in that software.
    + **Always write `docstrings`!**
    + Several tools read `docstrings` to generate formatted API documentation

# Principles of documentation

* Save every bit of code you use for generating publishable/reportable results
* Document and comment your code for yourself as if you will need to understand it in 6 months
    + use `README` files liberally
    + as well as file-level, function-level, and inline documentation
    + **Always write `docstrings`!**
* If any piece of code is too complex to easily describe, consider refactoring it

# 7. Design flexibly for performance, build accessibly for correctness

* Better algorithms beat better architectures
* Write code in the highest-level language possible.
  + Python is significantly more portable and readable than C/C++
  + Python allows seamless *deployment* of applications
* Use a profiler to identify bottlenecks.

# Be fluent in multiple languages
You speak multiple languages when interacting with a computer.  Choosing to use a new tool, library, or language can be similar to learning a new language:

+ There is a high initial startup cost as you learn vocabulary, grammar, and idioms
+ You will learn faster by observing and working with others who are more skilled than you
+ But once you have gained some fluency, you will find yourself capable of new things!

# Use domain specific languages and libraries to increase your expressivity

* Aim for languages and tools that allow you to express your models simply.
* Minimize the coupling to external libraries so it is easier to upgrade, replace, or remove them.

# Use REPL Environments for Development

**REPL (read-eval-print-loop)** environments tighten the coupling between the code you write and the results you see, increasing productivity.

|REPL                          |              non-REPL |
:----------------|:----------------------|
| IPython and Python    |                   C/C++ |
| Julia                            |                  Fortran  |
| Interactive Sessions   |                      Batch Systems |


# Collaborate


* Use pre-merge code reviews.
  + GitHub-style *pull requests*
* Use pair programming when bringing someone new up to speed and when
tackling particularly tricky problems.
* Use an issue tracking tool.


# Python Roadmap

1. Organize work from IPython console or notebook into a script
    + Add simple argument parsing with `sys.argv`
    + `git init` , `git add`, `git commit`
2. Refactor into module units
    + Make functions
    + Add `docstrings`
    + Add `if __name__ == '__main__':`
3. Make the module *importable* as a py file
    + Don't rely on the global namespace
    + Clearly define arguments and returns for functions
    + Consider making classes
    + Add more docstrings

# Python Roadmap

4. Begin writing tests
    + Functions beginning with test\_
    + Use testing methods from Numpy and Pandas
    + Use `assert` to check the state of returns
5. Organize the module into a package
    + Use `PackageName/package/package.py` directory structure
    + Add `__init__.py`
    + Add `__main__.py` if your package has a CLI
    + Even more `docstrings`
    + Many more tests
6. Installing the package
    + Write a `setup.py` script
    + Write a `conda` recipe
    + Upload to anaconda.org

# Closing Thoughts

# Reduce Complexity

* Endeavor to use languages and libraries that reduce the complexity of your work
* It is worth installing a complicated or expensive software tool if your computations are naturally expressed with it
* Always look for opportunities to write **less** code
    + you will have to do less initial work (sometimes)
    + you will introduce less bugs
    + your code will be easier to understand and maintain
* When writing software, try to keep individual functions short, single-purpose, and avoid excessive nesting

# Aim for reproducibility
* The goals of non-review scientific publications are to:
    + Describe a new result or approach
    + Convince others of its usefulness
* The **reproducibility** of your publication will greatly benefit both of these goals

# References and Further Reading

# Books

# Pragmatic Programmer, The: From Journeyman to Master
Andrew Hunt and David Thomas

ISBN 978-0132119177

*Describes the important principles and practices of being an effective programmer, instead of teaching a specific language or technique*

# Code Complete Second Edition
Steve McConnell

ISBN 978-0735619678

*Focuses on principles of software construction, with attention to skills, testing, and design.*

# Verification and Validation in Scientific Computing
William L. Oberkampf and Christopher J. Roy

ISBN 978-0521113601

*Focuses on verification and validation of numerical solutions to models described by systems of partial differential and integral equations.*

# Research Literature

# Programming Languages for Scientiﬁc Computing
Matthew G. Knepley

Preprint: http://arxiv.org/pdf/1209.1711.pdf

*Gives an overview of modern programming languages and techniques such as code generation, templates, and mixed-language designs. This is a preprint, so expect some rough spots.*

# Two Solitudes
Greg Wilson

Slides: http://www.slideshare.net/gvwilson/two-solitudes

*Describes Greg's journey as a scientist and leader for the Software Carpentry project, provides some insight into the differences between industry and academics.*

# Best Practices for Scientific Computing
D. A. Aruliah, C. Titus Brown, Neil P. Chue Hong, Matt Davis, Richard T. Guy, Steven H. D. Haddock, Katy Huff, Ian Mitchell, Mark Plumbley, Ben Waugh, Ethan P. White, Greg Wilson, Paul Wilson

Preprint: http://arxiv.org/abs/1210.0530

*Good summary paper of many fundamental practices for working with and developing scientific software.*

# Web References

# What Every Computer Scientist Should Know About Floating-Point Arithmetic
David Golberg

Web article: http://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html

*Introduction to the IEEE floating-point standard, its implications, and many of the common pitfalls when using floating-point numbers in scientific computing*

# The Research Software Engineer
Rob Baxter, Neil Chue Hong, Dirk Gorissen, James Hetherington, and Ilian Todorov

Web article: http://dirkgorissen.com/2012/09/13/the-research-software-engineer

*Discussion of the current challenges to scientific software engineering as a profession.*

# Science Code Manifesto

http://sciencecodemanifesto.org

*Publicly signed commitment to clear licensing and curation of software associated with research publications.*

# US Army Engineer Research and Development Center

http://www.erdc.usace.army.mil/

*Innovative solutions for a safer world.*

