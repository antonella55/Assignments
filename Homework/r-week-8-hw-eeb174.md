Exploring Data Frames
=====================

    cats <- read.csv(file = "feline-data.csv")
    age <- c(2,3,5,12)
    cats

    ##     coat weight likes_string
    ## 1 calico    2.1            1
    ## 2  black    5.0            0
    ## 3  tabby    3.2            1

    age <- c(4,5,8)
    cats <- cbind(cats, age)
    cats

    ##     coat weight likes_string age
    ## 1 calico    2.1            1   4
    ## 2  black    5.0            0   5
    ## 3  tabby    3.2            1   8

    newRow <- list("tortoiseshell", 3.3, TRUE, 9)
    cats <- rbind(cats, newRow)

    ## Warning in `[<-.factor`(`*tmp*`, ri, value = "tortoiseshell"): invalid
    ## factor level, NA generated

    levels(cats$coat)

    ## [1] "black"  "calico" "tabby"

    levels(cats$coat) <- c(levels(cats$coat), 'tortoiseshell')
    cats <- rbind(cats, list("tortoiseshell", 3.3, TRUE, 9))

    str(cats)

    ## 'data.frame':    5 obs. of  4 variables:
    ##  $ coat        : Factor w/ 4 levels "black","calico",..: 2 1 3 NA 4
    ##  $ weight      : num  2.1 5 3.2 3.3 3.3
    ##  $ likes_string: int  1 0 1 1 1
    ##  $ age         : num  4 5 8 9 9

    cats$coat <- as.character(cats$coat)
    str(cats)

    ## 'data.frame':    5 obs. of  4 variables:
    ##  $ coat        : chr  "calico" "black" "tabby" NA ...
    ##  $ weight      : num  2.1 5 3.2 3.3 3.3
    ##  $ likes_string: int  1 0 1 1 1
    ##  $ age         : num  4 5 8 9 9

    cats[-4,]

    ##            coat weight likes_string age
    ## 1        calico    2.1            1   4
    ## 2         black    5.0            0   5
    ## 3         tabby    3.2            1   8
    ## 5 tortoiseshell    3.3            1   9

    cats

    ##            coat weight likes_string age
    ## 1        calico    2.1            1   4
    ## 2         black    5.0            0   5
    ## 3         tabby    3.2            1   8
    ## 4          <NA>    3.3            1   9
    ## 5 tortoiseshell    3.3            1   9

    na.omit(cats)

    ##            coat weight likes_string age
    ## 1        calico    2.1            1   4
    ## 2         black    5.0            0   5
    ## 3         tabby    3.2            1   8
    ## 5 tortoiseshell    3.3            1   9

    cats <- na.omit(cats)

    cats <- rbind(cats, cats)
    cats

    ##             coat weight likes_string age
    ## 1         calico    2.1            1   4
    ## 2          black    5.0            0   5
    ## 3          tabby    3.2            1   8
    ## 5  tortoiseshell    3.3            1   9
    ## 11        calico    2.1            1   4
    ## 21         black    5.0            0   5
    ## 31         tabby    3.2            1   8
    ## 51 tortoiseshell    3.3            1   9

    rownames(cats) <- NULL
    cats

    ##            coat weight likes_string age
    ## 1        calico    2.1            1   4
    ## 2         black    5.0            0   5
    ## 3         tabby    3.2            1   8
    ## 4 tortoiseshell    3.3            1   9
    ## 5        calico    2.1            1   4
    ## 6         black    5.0            0   5
    ## 7         tabby    3.2            1   8
    ## 8 tortoiseshell    3.3            1   9

Challenge 1
-----------

    df <- data.frame(id = c('a', 'b', 'c'),
                     x = 1:3,
                     y = c(TRUE, TRUE, FALSE),
                     stringsAsFactors = FALSE)

    df <- data.frame(first = c('Antonella'),
                     last = c('Gonzalez'),
                     lucky_number = c(8),
                     stringsAsFactors = FALSE)
    df <- rbind(df, list('Marie', 'Curie', 238) )
    df <- cbind(df, coffeetime = c(TRUE,TRUE))
    df

    ##       first     last lucky_number coffeetime
    ## 1 Antonella Gonzalez            8       TRUE
    ## 2     Marie    Curie          238       TRUE

Challenge 2
-----------

    #download.file("https://raw.githubusercontent.com/swcarpentry/r-novice-gapminder/gh-pages/_episodes_rmd/data/gapminder-FiveYearData.csv", destfile = "data/gapminder-FiveYearData.csv")
    gapminder <- read.csv(file = "data/gapminder-FiveYearData.csv")

    #source(file = "scripts/load-gapminder.R")

Subsetting Data
===============

    x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
    names(x) <- c('a', 'b', 'c', 'd', 'e')
    x

    ##   a   b   c   d   e 
    ## 5.4 6.2 7.1 4.8 7.5

    x[1]

    ##   a 
    ## 5.4

    x[4]

    ##   d 
    ## 4.8

    x[c(1, 3)]

    ##   a   c 
    ## 5.4 7.1

    x[1:4]

    ##   a   b   c   d 
    ## 5.4 6.2 7.1 4.8

    1:4

    ## [1] 1 2 3 4

    c(1, 2, 3, 4)

    ## [1] 1 2 3 4

    x[c(1,1,3)]

    ##   a   a   c 
    ## 5.4 5.4 7.1

    x[6]

    ## <NA> 
    ##   NA

    x[0]

    ## named numeric(0)

    x[-2]

    ##   a   c   d   e 
    ## 5.4 7.1 4.8 7.5

    x[c(-1, -5)]  # or x[-c(1,5)]

    ##   b   c   d 
    ## 6.2 7.1 4.8

Challenge 1
-----------

    x[2:4]

    ##   b   c   d 
    ## 6.2 7.1 4.8

    x[-c(1,5)]

    ##   b   c   d 
    ## 6.2 7.1 4.8

    x[c("b", "c", "d")]

    ##   b   c   d 
    ## 6.2 7.1 4.8

    x[-which(names(x) == "a")]

    ##   b   c   d   e 
    ## 6.2 7.1 4.8 7.5

    names(x) == "a"

    ## [1]  TRUE FALSE FALSE FALSE FALSE

    x[-which(names(x) %in% c("a", "c"))]

    ##   b   d   e 
    ## 6.2 4.8 7.5

Challenge 2
-----------

    x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
    names(x) <- c('a', 'b', 'c', 'd', 'e')
    print(x)

    ##   a   b   c   d   e 
    ## 5.4 6.2 7.1 4.8 7.5

    x[-which(names(x) == "g")]

    ## named numeric(0)

    # A and C
