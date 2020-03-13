---
title: "Lab 7 Homework"
author: "Lily Karim"
date: "2020-03-13"
output:
  html_document: 
    keep_md: yes
    theme: spacelab
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for any included code chunks to run.  

## Libraries

```r
library(tidyverse)
library(shiny)
library(shinydashboard)
```

## Data
The data for this assignment come from the [University of California Information Center](https://www.universityofcalifornia.edu/infocenter). Admissions data were collected for the years 2010-2019 for each UC campus. Admissions are broken down into three categories: applications, admits, and enrollees. The number of individuals in each category are presented by demographic.  

```r
UC_admit <- readr::read_csv("data/UC_admit.csv")
```

```
## Parsed with column specification:
## cols(
##   Campus = col_character(),
##   Academic_Yr = col_double(),
##   Category = col_character(),
##   Ethnicity = col_character(),
##   `Perc FR` = col_character(),
##   FilteredCountFR = col_double()
## )
```

**1. Use the function(s) of your choice to get an idea of the overall structure of the data frame, including its dimensions, column names, variable classes, etc. As part of this, determine if there are NA's and how they are treated.**  

```r
str(UC_admit)
```

```
## Classes 'spec_tbl_df', 'tbl_df', 'tbl' and 'data.frame':	2160 obs. of  6 variables:
##  $ Campus         : chr  "Davis" "Davis" "Davis" "Davis" ...
##  $ Academic_Yr    : num  2019 2019 2019 2019 2019 ...
##  $ Category       : chr  "Applicants" "Applicants" "Applicants" "Applicants" ...
##  $ Ethnicity      : chr  "International" "Unknown" "White" "Asian" ...
##  $ Perc FR        : chr  "21.16%" "2.51%" "18.39%" "30.76%" ...
##  $ FilteredCountFR: num  16522 1959 14360 24024 17526 ...
##  - attr(*, "spec")=
##   .. cols(
##   ..   Campus = col_character(),
##   ..   Academic_Yr = col_double(),
##   ..   Category = col_character(),
##   ..   Ethnicity = col_character(),
##   ..   `Perc FR` = col_character(),
##   ..   FilteredCountFR = col_double()
##   .. )
```

```r
UC_admit %>% 
  anyNA()
```

```
## [1] TRUE
```





**2. The president of UC has asked you to build a shiny app that shows admissions by ethnicity across all UC campuses. Your app should allow users to explore year, campus, and admit category as interactive variables. Use shiny dashboard and try to incorporate the aesthetics you have learned in ggplot to make the app neat and clean.**


```r
UC_admit <- na.omit(UC_admit)
```


```r
UC_admit %>% 
  anyNA()
```

```
## [1] FALSE
```



```r
ui <- dashboardPage(
  dashboardHeader(title = "Admissions Across the UCs"),
  dashboardSidebar(),
  dashboardBody(
  fluidRow(
  box(title = "Plots", width = 3,
  selectInput("x", "Year", choices = unique(UC_admit$Academic_Yr), selected = "2010"),
  selectInput("y", "Campus", choices = unique(UC_admit$Campus), selected = "Davis"),
  selectInput("z", "Category", choices = unique(UC_admit$Category), selected = "Applicants")
  ), # close the first box
  
  box(title = "UC Admissions", width = 7,
  plotOutput("plot", width = "600px", height = "500px")
  ) # close the second box
  ) # close the row
  ) # close the dashboard body
) # close the ui

server <- function(input, output, session) { 
  
  # the code to make the plot of iris data grouped by species
  output$plot <- renderPlot({
    UC_admit %>% 
      filter(Academic_Yr==input$x & Campus==input$y & Category==input$z) %>% 
      ggplot(aes(x = reorder(Ethnicity, FilteredCountFR), y = FilteredCountFR)) + geom_bar(stat="identity") +labs(x = "Ethnicity", y = "Number of People")+ theme_light(base_size = 10)
  })
  
  # stop the app when we close it
  session$onSessionEnded(stopApp)

  }

shinyApp(ui, server)
```

<!--html_preserve--><div style="width: 100% ; height: 400px ; text-align: center; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;" class="muted well">Shiny applications not supported in static R Markdown documents</div><!--/html_preserve-->


**3. Make alternate version of your app above by tracking enrollment at a campus over all of the represented years while allowing users to interact with campus, category, and ethnicity.**

```r
ui <- dashboardPage(
  dashboardHeader(title = "Admissions Across the UCs"),
  dashboardSidebar(),
  dashboardBody(
  fluidRow(
  box(title = "Variables", width = 3,
  selectInput("x", "Choose Campus", choices = unique(UC_admit$Campus), selected = "Davis"),
  selectInput("y", "Choose Category", choices = unique(UC_admit$Category), selected = "Applicants"),
  selectInput("z", "Choose Ethnicity", choices = unique(UC_admit$Ethnicity), selected = "International"),
  
  ), # close the first box
  box(title = "Plot ", width = 7,
  plotOutput("plot", width = "600px", height = "500px")
  ) # close the second box
  ) # close the row
  ) # close the dashboard body
) # close the ui

server <- function(input, output, session) { 
  
  # the code to make the plot of iris data grouped by species
  output$plot <- renderPlot({
    UC_admit %>% 
      filter(Campus == input$x, Category == input$y, Ethnicity == input$z) %>%
      ggplot(aes(x = Academic_Yr, y = FilteredCountFR)) + geom_bar(stat="identity") + theme_light(base_size = 10)+labs(x = "Year", y = "Admissions")
  })
  
  # stop the app when we close it
  session$onSessionEnded(stopApp)

  }

shinyApp(ui, server)
```

<!--html_preserve--><div style="width: 100% ; height: 400px ; text-align: center; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;" class="muted well">Shiny applications not supported in static R Markdown documents</div><!--/html_preserve-->

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences. 
