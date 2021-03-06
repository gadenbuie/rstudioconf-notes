rstudio::conf(“notes”, day = 2)
================

## Keynote - Explicit Direct Instruction in Programming Education @felienne

  - How to teach programming (and other things)
  - “Everyone should learn programming”
  - There is no wall between “users” and “prgrammers”
  - Skill progression demonstrated by uesrs in Scratch: Scaffid &
    Chambers
  - Sound matters: “I have a tear … in my pants” (you have to go back
    and re-read “tear” in the correct way)
  - Coding lacks “fights”, i.e. pedagogical debates
      - e.g. *phonics* vs *whole language*
      - or e.g. “The Math Wars”: memorization vs. exploration and
        problem solving
  - “Technology is covert philosphy”
  - Whiy minimal guidance does not work - Kirschner
  - The use of worked examples for problem solving - Sweller & Cooper

How to teach programming

  - Vocalize syntax
  - Explicit reading strategies
      - In reading:
          - skim pictures,
          - read first sentences,
          - preview text before reading in detail, etc.
      - In code:
          - Skim methods
          - Collapse code chunks
          - read function signatures
  - Assessment and formative feedback

Motivation leads to skill (virtuous cycle)

## Org thinking jdlong

  - To migrate analysts to R, first get them better at Excel. If R
    doesn’t work, then at least you’ll have better Excel\!
      - Name tables (great into to proramming)
      - Build incremental change around existing workflows: make it 10%
        better
      - RStudio built into Jupyter notebook server (esp. when Jupyter is
        already there)
      - `openxlsx` lets you write out named tables
  - R Cookbook
  - Everybody want’s to be a super hero, they don’t want to “learn
    coding”, they want to kick ass
  - Kathy Sierra
  - Get your users doing things they perceive as being useful as quickly
    as possible
  - Fallacies
      - Not all time is of equal value
      - Freq. of reporting now \!= freq. in future
      - All time spent doing analytics are of equal utility (some tasks
        are so awful that you just can’t even…)
      - Automatied and manual workflows are not equivalent (manual means
        more error)
  - 10% happier -\> 10% more productive -\> 10% improvement

## Dependencies

*not all dependencies are equal*

  - Number of additional dependencies
  - Time to install (see CRAN check pages)
  - Size of the package (KB - GB)
  - Difficulty of installation of dependencies (I’m looking at you
    rJava)

What to do instead?

  - more: features, bugfixes, testing, time
  - less: installation, diskspace, breakage, generality

GAB Q: How do they feel about importing tidyverse dependencies, like
purrr and dplyr GAB Q: How many package import dplyr

Goal of the package

  - pgk dev: needs to be smaller, less time to install, stability more
    important
  - data sci users: install time is cheap, they probably already have
    deps

*illusionary superiority*

<https://github.com/jimhester/itdepends>

## Magical code

  - **Zaps**
      - run a command, wave a wand, something magical happens\!
      - `janitor`, `here`, `tinytex::install_tinytex()`
  - **genies**
      - assist you in doing something, like interactive apps, or addins
  - **tongues**
      - the power of words and names: `tidyverse` and *tidy data*
      - a name that is confirmed by a definition
      - a new language that encapsulates an intuition

How does software magic work?

  - magic = power / pain

> The magic of **TOOL** is that it grants you **POWER** while saving you
> from **PAIN**.

## vctrs

<https://vctrs.r-lib.org> also
<https://vctrs.r-lib.org/articles/type-size.html>

## tidyeval

## react.js + shiny

  - <https://alex3165.github.io/react-mapbox-gl>
  - \<github.com/react-R\>

reactjs -\> htmlwidget -\> R

what is react?

  - jacavscript library
  - functional, based on components
  - has it’s own syntax: JSX or Javascript XML

Why care?

1.  You found a cool reactjs based library
2.  You want to build a cool react-based library and use it from R

React components are similar to HTML tag

reactR

  - supports inline JSX - no need to javascript build tools installation
  - contains the react htmlDependencies
  - makes it easier to create html widgets

Making an htmlwidget

  - scaffold R package with `usethis`
  - scaffold JS tool conif with `reactR`
  - build JS with `yarn`/`webpack`

Remaining work

  - stil doesn’t have a good way to send data from browser context to R
    context (not impossible, but needs to use `Shiny.onInputChange` with
    custom JS)
  - there are prototypes for this, though

RStudio thinks highly of Vue.js

## ipc

dealing with long running, computationally intensive problems
