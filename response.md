@karthik @kbroman Leah Wang (@lwa19) and I enjoyed going through
Karl’s [report][article] and [code][repo], and reading about his
experiences trying to reproduce the results of a paper written (well
over!) 10 years ago. As you may know, we (together with @jdblischak
and @stephens999) have been developing the
[workflowr R package][workflowr-pkg] (see also
[the paper][workflowr-paper]) to help researchers develop more
reproducible code. Karl’s remarks at the end of his article
("Lessons") suggest that workflowr could have prevented --- or, at the
very least, could have alleviated --- several of these difficulties;
in particular, workflowr facilitiates, or automates, setting the
random seed, maintaining a project history (with git), generating
reports (with R Markdown), and better project organization. Our
comments here focus on our experiences using Karl’s code to reproduce
his results.

First, and foremost, we were able to successfully reproduce
[Karl’s results][reproduction]. The instructions are sufficiently
detailed and easy to follow; in particular, it was helpful to have a
single R Markdown file giving a start-to-finish set of steps for
generating the results. We ran the code on the high-performance
computing cluster run by the University of Chicago’s Research
Computing Center; see [Leah's fork of Karl’s repository][repo-fork]
for details, and in particular
[Leah's reproduction of the report][reproduction-copy]. The only issue
was that there was some knitr-specific syntax in the code chunks,
e.g., `<<run_sept02_mcmc>>`, that gave RStudio some trouble depending
on how the code was run. For compatibility it would be best to avoid
such syntax. The remaining comments are some areas where we found the
code difficult to follow, with some small suggestions for improvement
(say, for the 50-year Reproducibility Challenge):

+ Changing the working directory multiple times during the analysis
  makes it hard to keep track of the file paths, which files are being
  loaded, and where files are being saved to, certainly when the code
  is being run interactively; it would be better to have a single
  working directory throughout, and define all the file paths relative
  to that directory.

+ In the "table4" code chunk was rather headspinning in the way that
  the code was modified on the fly; it seems that this could have been
  handdled more elegantly by defining a variable, e.g., `cutoff <-
  75`, and using that instead of hardcoded values. 

+ Instead of clearing the workspace with `rm(list = ls())`, it may
  have been better to split the analysis into multiple R Markdown
  files that are listed in a "master" R Markdown file.

+ Since the MCMC step takes a some time to run, it would be helpful to
  give a warning, and some sense of how long it should take to run.

+ There is some bookkeeping at the beginning---moving and renaming files---and perhaps it would have been better to commit these changes..

+ All the code and results are saved to a single folder,
  `Paper_ReScience2020/reproduction/R`. This is what we see:

    ```
    circlefig.R
    figs4paper.R
    nov02_analysis.R
    nov02_data.RData
    nov02_prepareData.R
    nov02_results.RData
    prob_essential.ps
    sept02_analysis.R
    sept02_data.RData
    sept02_prepareData.R
    sept02_results.RData
    ```

  It would have been helpful to create folders such as "code", "data"
  and "output" to distinguish the inputs from the outputs.

Please assign most of the credit for this review to Leah Wang
(@lwa19). She worked through Karl’s [report][reproduction], reproduced
his results and provided most of the feedback on the code.

[article]: https://kbroman.org/Paper_ReScience2020/article/article.pdf
[repo]: https://github.com/kbroman/Paper_ReScience2020
[repo-fork]: https://github.com/lwa19/Paper_ReScience2020
[reproduction]: https://kbroman.org/Paper_ReScience2020/reproduction/reproduction.html
[reproduction-copy]: https://lwa19.github.io/Paper_ReScience2020/reproduction/reproduction.html
[workflowr-pkg]: https://cran.r-project.org/package=workflowr
[workflowr-paper]: https://doi.org/10.12688/f1000research.20843.1
