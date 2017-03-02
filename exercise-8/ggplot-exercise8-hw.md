    housing <- read.csv("Rgraphics/dataSets/landdata-states.csv")
    head(housing[1:5])

    ##   State region    Date Home.Value Structure.Cost
    ## 1    AK   West 2010.25     224952         160599
    ## 2    AK   West 2010.50     225511         160252
    ## 3    AK   West 2009.75     225820         163791
    ## 4    AK   West 2010.00     224994         161787
    ## 5    AK   West 2008.00     234590         155400
    ## 6    AK   West 2008.25     233714         157458

    hist(housing$Home.Value) 

    library(ggplot2)

![](ggplot-exercise8-hw_files/figure-markdown_strict/unnamed-chunk-1-1.png)

    ggplot(housing, aes(x = Home.Value)) +
      geom_histogram()

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](ggplot-exercise8-hw_files/figure-markdown_strict/unnamed-chunk-1-2.png)

    # colored scatter plot
    plot(Home.Value ~ Date,
         data=subset(housing, State == "MA"))
    points(Home.Value ~ Date, col="red",
           data=subset(housing, State == "TX"))
    legend(1975, 400000,
           c("MA", "TX"), title="State",
           col=c("black", "red"),
           pch=c(1, 1))

![](ggplot-exercise8-hw_files/figure-markdown_strict/unnamed-chunk-1-3.png)

    #ggplot colored scatterplot
    ggplot(subset(housing, State %in% c("MA", "TX")),
           aes(x=Date,
               y=Home.Value,
               color=State))+
      geom_point()

![](ggplot-exercise8-hw_files/figure-markdown_strict/unnamed-chunk-1-4.png)
