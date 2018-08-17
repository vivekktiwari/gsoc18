# Google Summer of Code 2018: Animint2
Project Summary Report


##### Organization: [R Project for Statistical Computing](https://github.com/rstats-gsoc)

##### Student: [Vivek Kumar](https://github.com/vivekktiwari)

##### Mentors: [Toby Dylan Hocking](https://github.com/tdhock) and [Faizan Khan](https://github.com/faizan-khan-iit)

------------------------------------

### Abstract
`animint2` is a R package that allows you to create interactive and animated multi-layer, multi-plot data visualizations using the `ggplot2` syntax. The package uses the D3.js JavaScript library for rendering. It helps to discover and understand patterns in large multi-variate datasets. The aim of the project was to document, render, debug the already exsiting `animint2` which is the latest version of `animint`.

------------------------------------

### Introduction
The initial motive behind the GSoC project was to translate Animint Designer Manual to support the new `animint2` syntax, and create additional chapters to further document `animint2` usage. The objective was to compile a designer manual for `animint2` package that will outline different functions, resolve issues and guide the user through the package. So far there was no proper equivalent documentation for `animint2`. The `ggplot2` dependency has been a major issue over time for `animint2` as the package depends on it. Further work done by past contributors reduced the dependency which resulted in two separate packages; `ggplot2Animint` and `animint2`. `ggplot2Animint` is `animint2` specific fork of the `ggplot2` package to support the changes needed which were not accepted earlier. As we moved long in the project, motive changed to continue the work on `animint2` done by fellow contributors and make package ready for CRAN submissions.

------------------------------------

### First Evaluation
During the first evaluation, major work involved cleaning the `animint2` code and documentation for making it ready for CRAN submission (animint2 issue [#12](https://github.com/tdhock/animint2/issues/12)). This included removing the outdated package version, declaring global variables, parameters and basic documentation. As we moved forward, it was decided to clean the `ggplot2Animint` code and internals first. It was planned to submit both packages separately for CRAN. The further work on cleaning `ggplot2Animint` was done on [`cran` branch of Faizan Khan's repo of forked ggplot2](https://github.com/faizan-khan-iit/ggplot2/tree/cran).

------------------------------------

### Second Evaluation
After cleaning `ggplot2Animint` code for CRAN submission, we started testing the package with other R packages including `ggplot2` which resulted in failed testcases (Issue [#4](https://github.com/faizan-khan-iit/ggplot2/issues/4)). The possible solution suggested was to merge the `ggplot2Animint` and `animint2` so that we can have a better understanding of error and changes done in `ggplot2Animint` which also resulted in failed testcases in `animint2` was well. Merging the code had the added advantage of submitting only a single package to CRAN. The second evaluation period was spent on merging both the packages into one to remove the dependency. The complete work on merging was done in [`merge` branch of `animint2`](https://github.com/tdhock/animint2/tree/merge). 


------------------------------------

### Final Evaluation
After merging both the packages, main task was to make sure `animint2` and `ggplot2` work together in same environment. For this purpose, I started working on renaming all the `ggplot2` functions imported from `ggplot2Animint`. `ggplot2` contains more than 500+ functions which were renamed to avoid nameclash so that both functions work independently. Renaming the functions have also resulted in new syntax and functions mentioned below:


```
# Older syntax
geom_point(aes(xVar, yVar), 
  clickSelects="clickVar", 
  showSelected=c("showVar1", "showVar2", selector.name="selector.value"))

# New syntax
a_geom_point(a_aes(xVar, yVar),
  clickSelects="clickVar",
  showSelected=c("showVar1", "showVar2", selector.name="selector.value"))

```
There are still a few internal functions left to be renamed which are hard to find and are being used through same name in the environment by both packages (`ggplot2` and `animint2`).

------------------------------------

### Link to commits
The links to all the commits are given below:

1. [ggplot2Animint cran ready code with renamed functions](https://github.com/faizan-khan-iit/ggplot2/pull/7/commits)
2. [Merged Code of ggplot2Animint and animint2](https://github.com/tdhock/animint2/pull/23/commits)
3. [animint2 code with new renamed functions](https://github.com/tdhock/animint2/pull/25/commits)
4. [dataset documentation for animint2](https://github.com/tdhock/animint2/pull/14)

------------------------------------

### Future Work
The end goal involves further renaming of few internal functions imported from `ggplot2` code, documentation of `animint2` functions, making `animint2` ready for CRAN submission and finally submitting `animint2` to CRAN.

