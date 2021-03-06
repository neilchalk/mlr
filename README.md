# Machine Learning in R <img src="man/figures/logo_navbar.png" align="right" />

[![Build Status](https://travis-ci.org/mlr-org/mlr.svg?branch=master)](https://travis-ci.org/mlr-org/mlr)
[![Build status](https://ci.appveyor.com/api/projects/status/8predl48o55f2do2/branch/master?svg=true)](https://ci.appveyor.com/project/pat-s/mlr/branch/master)
[![CRAN Status Badge](http://www.r-pkg.org/badges/version/mlr)](https://CRAN.R-project.org/package=mlr)
[![CRAN Downloads](http://cranlogs.r-pkg.org/badges/mlr)](https://cran.rstudio.com/web/packages/mlr/index.html)
[![StackOverflow](https://img.shields.io/badge/stackoverflow-mlr-blue.svg)](https://stackoverflow.com/questions/tagged/mlr)

* [CRAN release site](https://CRAN.R-project.org/package=mlr)
* Detailed Tutorial: [Online as HTML](https://mlr-org.github.io/mlr/)
* [mlr cheatsheet](https://github.com/mlr-org/mlr/blob/master/addon/cheatsheet/MlrCheatsheet.pdf)

* Install the development version

```R
devtools::install_github("mlr-org/mlr")
```

* [Further installation instructions](https://github.com/rdatsci/PackagesInfo/wiki/Installation-Information)
* [Ask a question about mlr on Stackoverflow](https://stackoverflow.com/questions/tagged/mlr)
* [We are on Slack](https://mlr-org.slack.com/) (Request invitation: code{at}jakob-r.de)
* [We have a blog on mlr](https://mlr-blog.netlify.com/)
* A list of possible enhancements to mlr is available on the [wiki](https://github.com/mlr-org/mlr/wiki/Developer-Instructions#list-of-possible-enhancements-to-mlr) - contributors welcome!
* We are in the top 20 of the most starred R packages on Github, as reported by [metacran](http://www.r-pkg.org/starred).

# mlr - How to Cite and Citing Publications

Please cite our [JMLR paper](http://jmlr.org/papers/v17/15-066.html) [[bibtex](http://www.jmlr.org/papers/v17/15-066.bib)].

Some parts of the package were created as part of other publications.
If you use these parts, please cite the relevant work appropriately.
An overview of all mlr related publications can be found [here](http://mlr-org.github.io/mlr/articles/mlr_publications.html).

A list of publications that cite mlr can be found in the [wiki](https://github.com/mlr-org/mlr/wiki/Misc#publications-that-use-mlr).

# Introduction

R does not define a standardized interface for all its machine learning algorithms.
Therefore, for any non-trivial experiments, you need to write lengthy, tedious and error-prone wrappers to call the different algorithms and unify their respective output.

Additionally you need to implement infrastructure to resample your models, optimize hyperparameters, select features, cope with pre- and post-processing of data and compare models in a statistically meaningful way.
As this becomes computationally expensive, you might want to parallelize your experiments as well. This often forces users to make crummy trade-offs in their experiments due to time constraints or lacking expert programming skills.

**mlr** provides this infrastructure so that you can focus on your experiments!
The framework provides supervised methods like classification, regression and survival analysis along with their corresponding evaluation and optimization methods, as well as unsupervised methods like clustering.
It is written in a way that you can extend it yourself or deviate from the implemented convenience methods and construct your own complex experiments or algorithms.

Furthermore, the package is nicely connected to the [**OpenML**](https://github.com/openml/openml-r) R package and its [online platform](https://www.openml.org/), which aims at supporting collaborative machine learning online and allows to easily share datasets as well as machine learning tasks, algorithms and experiments in order to support reproducible research.

# Features

* Clear S3 interface to R classification, regression, clustering and survival analysis methods
* Possibility to fit, predict, evaluate and resample models
* Easy extension mechanism through S3 inheritance
* Abstract description of learners and tasks by properties
* Parameter system for learners to encode data types and constraints
* Many convenience methods and generic building blocks for your machine learning experiments
* Resampling methods like bootstrapping, cross-validation and subsampling
* Extensive visualizations for e.g. ROC curves, predictions and partial predictions
* Benchmarking of learners for multiple data sets
* Easy hyperparameter tuning using different optimization strategies, including potent configurators like iterated F-racing (irace) or sequential model-based optimization
* Variable selection with filters and wrappers
* Nested resampling of models with tuning and feature selection
* Cost-sensitive learning, threshold tuning and imbalance correction
* Wrapper mechanism to extend learner functionality in complex and custom ways
* Combine different processing steps to a complex data mining chain that can be jointly optimized
* OpenML connector for the Open Machine Learning server
* Extension points to integrate your own stuff
* Parallelization is built-in
* Unit-testing
* Detailed tutorial

# News

Changes of the packages can be accessed in the [NEWS file](https://mlr-org.github.io/mlr/news/index.html) shipped with the package.

# Get in Touch

Please use the issue tracker for problems, questions and feature requests.
Don't email in most cases, as we forget these mails.

We also do not hate beginners and it is perfectly valid to mark an issue as "Question".
However, simple usage questions are better suited at [Stackoverflow using the 'mlr' tag](https://stackoverflow.com/questions/tagged/mlr).

Please don't forget that all of us work in academia and put a lot of work into this project, simply because we like it, not because we are specifically paid for it.

We also welcome pull requests or new developers.
Just make sure that you have a glance at our [**mlr** coding guidelines](https://github.com/mlr-org/mlr/wiki/Developer-Instructions#mlr-coding-guidelines) before.

# mlr-tutorial

With the start of v2.13 we switched from [mkdocs](https://github.com/mkdocs/mkdocs) to [pkgdown](https://github.com/r-lib/pkgdown).
All source files are now located in this repo under `vignettes/`.

**Modification of a tutorial section**:

If you want to modify/add a tutorial section, please follow these steps:

1. Open the respective source file, e.g. `task.Rmd`.
2. Follow the style guide while editing:
     - Reference `mlr` functions as <function()>, e.g. `makeLearner()`.
     - Reference external functions as <package::function()>, e.g. `kernlab::ksvm()`.
     - Reference other tutorial pages with `<name_of_vignette>.html`, e.g. `[bagging](bagging.html)`.
     - Always start a new sentence with a new line.
     - If you want to insert a paragraph, skip one line.
     - Always insert *exactly one* empty line *before and after* a code chunk, header, figure or a table.
     - Referencing images is a bit tricky since we need to ensure that they look good in both the HTML and PDF version.
       Put your image into `vignettes/tutorial/devel/pdf/img/` and see the examples in [resampling.Rmd](https://github.com/mlr-org/mlr/blob/master/vignettes/resampling.Rmd), [nested_resampling.Rmd](https://github.com/mlr-org/mlr/blob/master/vignettes/nested_resampling.Rmd) or [handling_of_spatial_data.Rmd](https://github.com/mlr-org/mlr/blob/master/vignettes/handling_of_spatial_data.Rmd).
3. Make sure that the `.Rmd` file is working on its own, i.e. compile it as a single file (preferably using `build_article("<vignette-name>")`) and see if everything works.
   Put required packages in the setup chunk at the beginning of the tutorial.

**Rendering the tutorial locally**:

If you want to view the complete `pkgdown` site locally, run `pkgdown::build_site(lazy = TRUE)`.
You don't have to render the complete site every time you change one tutorial.
The `lazy = TRUE` argument ensures that only pages are rebuilt that have changed.
Also, if you have built the whole site once, you can just build the vignettes again by using `build_articles(lazy = TRUE)`.
More specific, if you are working on one vignette, you can run `build_article("<vignette-name>")`.
You do not need to pass the `.Rmd` extension when using `build_article()`.

Important: Do not commit any file in `docs/` as the rendering will be done by Travis!

**Adding a new section**:

Edit `_pkgdown.yml` and add the new section at the appropriate place.

**Issues and Pull Requests**:

If you want to open an issue or pull request that is related to `mlr-tutorial`, label it with `tutorial` and mention [jakob-r](https://github.com/jakob-r) or [pat-s](https://github.com/pat-s) if you need help.
