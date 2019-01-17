rstudio::conf(“notes”, “day 1”)
================

## Keynote

### ❤️ Code

## Shiny

Cranwhales

  - \<cran-logs.rstudio.com\>
  - Shiny is good for:
      - data updated periodically
      - large computation at startup
      - possible option to drill down into lower levels

production is: “real users, with real consequences if things go wrong”.

  - keep it up
  - keep it safe
  - keep it correct
  - keep it snappy

Organizational challenges

  - IT & management tend to be skeptical
      - IT is conservative
      - Skeptical (rightly so?) of data scientists creating production
        software
      - Skeptical of new technology
  - Engineering depts might be bias against R

Testing shiny apps for produciton

  - shinyloadtest: is it slow?
  - profvis: see what makes it slow
  - optimize:
      - Move all the work out of Shiny and do not duplicate across users
      - Make code faster
          - Avoid text connections
          - avoid bad for loops
      - Use caching (sometimes)
      - Use async if nothing else works
  - repeat

`shinyloadtest`

1.  Deploy
2.  Record normal session
3.  Play back session concurrently using `shinyloadtest::shinycannon`
4.  Go back to R and view load testing

Use `feather` for fast loading of data (blog: feather vs rds)

*Shiny in Production* - Kelly O’Briant - <http://bit.ly/shiny-prod-book>

speakerdeck.com/jcheng

-----

## Shiny in production

1.  commit to repo
2.  jenkins to build the image
3.  marathon (off-brand kubernetes)
4.  mesos (deploy environment)

`plumber` doesn’t support HTTPS? needed to add an APACHE layer in front
of plumber to enable HTTPS. `sodium` for encryption

Enterprise web services with neuralnets using R and tensorflow

## R in production

@sellorm

the barriers to using R in organizations are cultural

two paths for getting r into organizations

  - the path of “magic”: a shiny app or something like that drives
    high-level decisions (shiny)
  - the other path is technical
      - data science isn’t software engineering and that’s fine
      - the rigor of data science lies in code and methodological
        correctness
      - but software engineering has more requirements and continues
        much further beyond
          - CI/CD, staging servers, automated testing, security, dev
            ops, release management, containers, etc.