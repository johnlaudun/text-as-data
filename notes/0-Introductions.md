## Introductions 

In the first two weeks we make all the usual introductions: course and participants (all of us in the room). We then begin the first of many considerations of what it means to quantify qualitative things like words from a very “big picture” point of view, if only to remind ourselves that for every insight, there is a blindness. The good news is that there are many questions to ask, and many ways to ask them. We finish with getting ready to do begin our analytical journey. 



### 0.1 Course Overview

All the usual things: syllabus review and course overview. instructor introduction, some participant introduction/polling.



### 0.2. Ethical Considerations 

There are all sorts of considerations of the ethical implications for data, not the least of which is Cathy O’Neil’s _Weapons of Math Destruction_. The readings for this period are fairly short, seven pages here and six pages there, but they come at the topic from very different angles. Enjoy the contract and come prepared to talk about your response (and how that connects you to a particular kind of audience).

* [Data Feminism][]: Download the introduction and read it. Our discussion will focus on the last section, entitled “Data and Power” (11-17).
* [Intelligence Community Directives][]: download *ICD 203: Analytic Standards* and read it. Our discussion will focus on D.6.3.e.(1-9).

If these kinds of larger considerations pique your curiosity, there are a number of books now out. I like Erica Thompson’s _Escape from Model Land_ and Brandeis Hill Marshall’s _Data Conscience_. There is also *A Primer on Powerful Numbers: Selected Readings in the Social Study of Publc Data and Official Numbers*, which is available from [Data & Society](https://datasociety.net/library/a-primer-on-powerful-numbers-selected-readings-in-the-social-study-of-public-data-and-official-numbers/). 

**Note**: We will read Bender et al’s “On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? 🦜” ([Bender et al 2021][]) later this semester when we get to transformers and large language models.

[Data Feminism]: https://direct.mit.edu/books/oa-monograph/4660/Data-Feminism

[Intelligence Community Directives]: https://www.dni.gov/index.php/what-we-do/ic-related-menus/ic-related-links/intelligence-community-directives

[Bender et al 2021]: https://dl.acm.org/doi/10.1145/3442188.3445922



### 0.3. Analytics Unplugged

Can we compute a short story by hand? Our considerations include: summarization, named entities, (and with a little computing) term frequencies.**Action(s)**: In groups, create a meaningful visualization of text based on a quantification of your choosing.
**Follow-Up**: ["The Zipf Mystery"][]

["The Zipf Mystery"]: https://www.youtube.com/watch?v=fCn8zs912OE



### 0.4 Our Base of Operations

One of the difficulties in any collaboration, whether it's two people or many more, is making sure everyone is working with the same versions of the software and various libraries. To that end, this semester we will all use Mini Conda. 

Some of you may have heard of, and even used, Mini Conda's larger cousin, Anaconda. Anaconda is great as a one stop shop, especially if you are new to data science, but Mini Conda allows you much more control of what gets installed while also being incredibly easy to use. And, perhaps just as importantly, it makes setting up a virtual environment painless. And I mean painless, which means you can set up a coding environment for this class and not have it mess with libraries in use elsewhere. It's as simple as `conda activate`. 

#### Getting up and running with `conda`

1. **Install Mini Coda**: go to its documents site: https://docs.conda.io/en/latest/. Click on the *Getting Started* panel, which will walk you through the [installation](https://docs.conda.io/projects/conda/en/stable/user-guide/install/index.html) process. The easiest way seems to be to download an installer and run it. (CLI gurus feel free to go that route.)
2. After you have installed Miniconda — and make sure it’s Miniconda and not its bigger sibling Anaconda — **open up your shell** / terminal. You should now see a conda environment in front of your shell prompt. It will look something like this:

```bash
(base) Developer/text-as-data %
```

*The `(base)` at the far left of my prompt signifies that I’m in the base conda environment. The rest is the prompt for my particular setup: all my code is in the Developer directory of my home director and the repo/directory for this course is `text-as-data`, and then my preferred posix prompt, the percent sign.*

3. **Create a virtual environment** for this course. (I use 370 because shorter is better, but you can do whatever you like.) Specify that it use Python 3.11. (Conda will have installed 3.12 into its `(base)`, but not all the libraries we will be using are 3.12-ready.)

```bash
conda create --name 370 python=3.11
```

4. Activate your new environment.

```bash
conda activate 370
```

 Your command prompt will have changed and will now look like this: `(370) %`. 

5. Install the things. (Okay, really we’re installing Python modules or libraries, but it’s more fun to write “install the things.”) Installation is as easy as `conda install` and then the name of the module. The modules are: `jupyter`, `nltk`, and, if you want to, `pandas`. Any of these commands will also install dependencies, or modules upon which these modules rely. If your connection is fast, these should zip by. 
6. *Optional*: **Set 370 as your default** environment (unless you like typing `conda activate 370` every time you log into your shell). This is not something you can do within `conda` sadly: you’re going to have to edit your `.bashprofile` or `.zshrc` or wherever the Windows power shell stores things like PATH and other stuff that runs when its starts up. For POSIX people editing one of the files listed above, just add `conda activate 370` somewhere. (I tend to put it at the end.)

If, after you have installed Jupyter, you need a little help getting started, take a look at Codecademy's instructions on setting up Mini Conda (for both Windows and Mac) and installing Jupyter: 

https://www.codecademy.com/article/setting-up-jupyter-notebook 

If you want to have a look into the future, take a look at the first chapter in the NLTK book: 

https://www.nltk.org/book/ch01.html. 
