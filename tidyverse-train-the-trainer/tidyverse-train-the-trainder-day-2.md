Tidyverse Train the Trainer
================
Day 2
1/16/2019

## Notes

  - [Make it Stick: Science of Succesful
    Learning](https://www.amazon.com/Make-Stick-Science-Successful-Learning/dp/0674729013)
  - Teaching `readr` later in the day gives a buffer section. It’s
    someting that can be dropped as a “self-contained” unit, or if on
    time can be explained. Several people in the class discussed that it
    can be distracting to show people how to import data because they
    take off from there.
  - Instead, starting off by writing code can be an excellent
    introduction. copy/paste, run code, then start modifying the code.
    Gets students “coding” immediately.

## Workshop Outlines

1.  Two Day Workshop

<!-- end list -->

  - Day 1
      - Import & Intro
      - Visualize
      - Transform Part 1
      - Transform Part 2 and Output
  - Day 2
      - Review (import %\>% transform %\>% visualize)
      - Tidy
      - Scripts, workflow
      - Project

## Mental Models

  - Tidy data
      - Bento box
      - pick and choose lunch menu

## Serparate and Separate Rows

  - building on the idea of “tidy” data: one unit of observation per
    cell
  - sometimes cells are overflowing with data, imagine an oveflowing
    cupboard
  - what you want in the end are groups of like things: cups in one
    place, plates in another
  - `separate()` and `separate_row()` are like adding cupboards or
    adding shelves
  - You use `separate()` when you need new cupboard (move plates out of
    the cup cupboard), `separate_row()` when you need more shelves
    (unstack cups)
  - Both functions have the same form…
  - by default the separation operates on anything that isn’t a letter
    or number
  - but you can change this as well

## ADEPT

  - Analogy
  - Diagram
  - Example
  - Plain english
  - Technical definition

## Excercises

  - Start building exercises early in the preparation process
  - Put together useful data sets
  - scaffolding: choose a level of difficulty that matches the learner’s
    progress
      - reading code that’s disorganized and comment on reason

## My `tidyr` learning example

`tidyr` is part of the
    tidyverse

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.1.0     ✔ purrr   0.2.5
    ## ✔ tibble  2.0.1     ✔ dplyr   0.7.8
    ## ✔ tidyr   0.8.2     ✔ stringr 1.3.1
    ## ✔ readr   1.3.1     ✔ forcats 0.3.0

    ## ── Conflicts ────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

Run this code chunk below. (Don’t look inside, just run it.)

``` r
starswars <- 
  starwars %>% 
  mutate(
    hair_eyes = paste(hair_color, eye_color, sep = ";"), 
    films = map_chr(films, paste, collapse = ";")
  ) %>% 
  filter(!is.na(hair_color)) %>% 
  select(1, hair_eyes, films) %>% 
  slice(1:5)
```

You now have a table called `starswars`

``` r
starswars
```

    ## # A tibble: 5 x 3
    ##   name          hair_eyes     films                                        
    ##   <chr>         <chr>         <chr>                                        
    ## 1 Luke Skywalk… blond;blue    Revenge of the Sith;Return of the Jedi;The E…
    ## 2 Darth Vader   none;yellow   Revenge of the Sith;Return of the Jedi;The E…
    ## 3 Leia Organa   brown;brown   Revenge of the Sith;Return of the Jedi;The E…
    ## 4 Owen Lars     brown, grey;… Attack of the Clones;Revenge of the Sith;A N…
    ## 5 Beru Whitesu… brown;blue    Attack of the Clones;Revenge of the Sith;A N…

Notice that both `hair_eyes` and `films` are “overflowing”. The
`hair_eyes` column contains two separate concetps: hair color and eye
color. The `films` column contains multiple films in a single cell.

``` r
<separate>(data, <column>, <?into>, sep = "<separator>")
```

``` r
separate_rows(starswars, films, sep = ";")
```

    ## # A tibble: 20 x 3
    ##    name               hair_eyes        films                  
    ##    <chr>              <chr>            <chr>                  
    ##  1 Luke Skywalker     blond;blue       Revenge of the Sith    
    ##  2 Luke Skywalker     blond;blue       Return of the Jedi     
    ##  3 Luke Skywalker     blond;blue       The Empire Strikes Back
    ##  4 Luke Skywalker     blond;blue       A New Hope             
    ##  5 Luke Skywalker     blond;blue       The Force Awakens      
    ##  6 Darth Vader        none;yellow      Revenge of the Sith    
    ##  7 Darth Vader        none;yellow      Return of the Jedi     
    ##  8 Darth Vader        none;yellow      The Empire Strikes Back
    ##  9 Darth Vader        none;yellow      A New Hope             
    ## 10 Leia Organa        brown;brown      Revenge of the Sith    
    ## 11 Leia Organa        brown;brown      Return of the Jedi     
    ## 12 Leia Organa        brown;brown      The Empire Strikes Back
    ## 13 Leia Organa        brown;brown      A New Hope             
    ## 14 Leia Organa        brown;brown      The Force Awakens      
    ## 15 Owen Lars          brown, grey;blue Attack of the Clones   
    ## 16 Owen Lars          brown, grey;blue Revenge of the Sith    
    ## 17 Owen Lars          brown, grey;blue A New Hope             
    ## 18 Beru Whitesun lars brown;blue       Attack of the Clones   
    ## 19 Beru Whitesun lars brown;blue       Revenge of the Sith    
    ## 20 Beru Whitesun lars brown;blue       A New Hope

``` r
separate(starswars, hair_eyes, into = c("hair", "eyes"), sep = ";")
```

    ## # A tibble: 5 x 4
    ##   name          hair      eyes  films                                      
    ##   <chr>         <chr>     <chr> <chr>                                      
    ## 1 Luke Skywalk… blond     blue  Revenge of the Sith;Return of the Jedi;The…
    ## 2 Darth Vader   none      yell… Revenge of the Sith;Return of the Jedi;The…
    ## 3 Leia Organa   brown     brown Revenge of the Sith;Return of the Jedi;The…
    ## 4 Owen Lars     brown, g… blue  Attack of the Clones;Revenge of the Sith;A…
    ## 5 Beru Whitesu… brown     blue  Attack of the Clones;Revenge of the Sith;A…

Change the name of the columns where hair color and eye color were
stored to `hair_color` and `eye_color`.

Re-unite hair color and eye color, separated by `/` instead of `,`.

``` r
starswars %>% 
  separate(hair_eyes, into = c("hair", "eyes"), sep = ";") %>% 
  unite(hair_eyes, hair, eyes, sep = "/")
```

    ## # A tibble: 5 x 3
    ##   name          hair_eyes     films                                        
    ##   <chr>         <chr>         <chr>                                        
    ## 1 Luke Skywalk… blond/blue    Revenge of the Sith;Return of the Jedi;The E…
    ## 2 Darth Vader   none/yellow   Revenge of the Sith;Return of the Jedi;The E…
    ## 3 Leia Organa   brown/brown   Revenge of the Sith;Return of the Jedi;The E…
    ## 4 Owen Lars     brown, grey/… Attack of the Clones;Revenge of the Sith;A N…
    ## 5 Beru Whitesu… brown/blue    Attack of the Clones;Revenge of the Sith;A N…
