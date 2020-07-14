@karthik @kbroman Leah Wang (@lwa19) and I enjoyed going through
Karl’s [report][article] and [code][repo], and reading about his
experiences trying to reproduce the results of a paper written (well
over!) 10 years ago. As you may know, we (together with @jdblischak
and @stephens999) have been developing the
[workflowr R package][workflowr-pkg] (see also
[here][workflowr-paper]) to help researchers develop more reproducible
code. Karl’s remarks (see “Lessons”) suggest that workflowr could have
prevented — or at the very least could have alleviated — several of
the difficulties he encountered; in particular, workflowr automates or
facilitiates setting the random seed, maintaining a project history
(git), generating reports (R Markdown), and better project
organization. Our comments here focus on our experiencing using Karl’s
code to reproduce his results.

First, and foremost, we were able to successfully reproduce
[Karl’s results][reproduction]. The instructions are sufficiently
detailed and easy to follow. We ran the code on the high-performance
computing cluster run by the University of Chicago’s Research
Computing Center; see
[the fork of Karl’s repository for details][repo-fork], and in
particular [our copy of the report][reproduction-copy].

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
