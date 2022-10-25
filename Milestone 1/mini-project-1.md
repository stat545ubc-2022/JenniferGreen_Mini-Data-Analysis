Mini Data-Analysis Deliverable 1
================

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.5 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.0      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

3.  Make a repository in the <https://github.com/stat545ubc-2022>
    Organization. You will be working with this repository for the
    entire data analysis project. You can either make it public, or make
    it private and add the TA’s and Lucy as collaborators. A link to
    help you create a private repository is available on the
    \#collaborative-project Slack channel.

# Instructions

## For Both Milestones

- Each milestone is worth 45 points. The number of points allocated to
  each task will be annotated within each deliverable. Tasks that are
  more challenging will often be allocated more points.

- 10 points will be allocated to the reproducibility, cleanliness, and
  coherence of the overall analysis. While the two milestones will be
  submitted as independent deliverables, the analysis itself is a
  continuum - think of it as two chapters to a story. Each chapter, or
  in this case, portion of your analysis, should be easily followed
  through by someone unfamiliar with the content.
  [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
  is a good resource for what constitutes “good code”. Learning good
  coding practices early in your career will save you hassle later on!

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 45 points: 43 for your analysis, 1
point for having your Milestone 1 document knit error-free, and 1 point
for tagging your release on Github.

# Learning Objectives

By the end of this milestone, you should:

- Become familiar with your dataset of choosing
- Select 4 questions that you would like to answer with your data
- Generate a reproducible and clear report using R Markdown
- Become familiar with manipulating and summarizing your data in tibbles
  using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset (10 points)

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

- *apt_buildings*: Acquired courtesy of The City of Toronto’s Open Data
  Portal. It currently has 3455 rows and 37 columns.

- *building_permits*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 20680 rows and 14 columns.

- *cancer_sample*: Acquired courtesy of UCI Machine Learning Repository.
  It currently has 569 rows and 32 columns.

- *flow_sample*: Acquired courtesy of The Government of Canada’s
  Historical Hydrometric Database. It currently has 218 rows and 7
  columns.

- *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 10032 rows and 22 columns.

- *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
  rows and 21 columns.

- *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

- We hope that this project will serve as practice for carrying our your
  own *independent* data analysis. Remember to comment your code, be
  explicit about what you are doing, and write notes in this markdown
  document when you feel that context is required. As you advance in the
  project, prompts and hints to do this will be diminished - it’ll be up
  to you!

- Before choosing a dataset, you should always keep in mind **your
  goal**, or in other ways, *what you wish to achieve with this data*.
  This mini data-analysis project focuses on *data wrangling*,
  *tidying*, and *visualization*. In short, it’s a way for you to get
  your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 Out of the 7 datasets available in the `datateachr` package, choose
**4** that appeal to you based on their description. Write your choices
below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

1: *vancouver_trees* 2: *flow_sample* 3: *apt_buildings* 4:
*building_permits*

<!----------------------------------------------------------------------------->

1.2 One way to narrowing down your selection is to *explore* the
datasets. Use your knowledge of dplyr to find out at least *3*
attributes about each of these datasets (an attribute is something such
as number of rows, variables, class type…). The goal here is to have an
idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

Below, I will begin to explore 4 datasets to see what the data looks
like in order to choose which I would like to work with.

``` r
# Exploring the *vancouver_trees* dataset
glimpse(vancouver_trees)
```

    ## Rows: 146,611
    ## Columns: 20
    ## $ tree_id            <dbl> 149556, 149563, 149579, 149590, 149604, 149616, 149…
    ## $ civic_number       <dbl> 494, 450, 4994, 858, 5032, 585, 4909, 4925, 4969, 7…
    ## $ std_street         <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ genus_name         <chr> "ULMUS", "ZELKOVA", "STYRAX", "FRAXINUS", "ACER", "…
    ## $ species_name       <chr> "AMERICANA", "SERRATA", "JAPONICA", "AMERICANA", "C…
    ## $ cultivar_name      <chr> "BRANDON", NA, NA, "AUTUMN APPLAUSE", NA, "CHANTICL…
    ## $ common_name        <chr> "BRANDON ELM", "JAPANESE ZELKOVA", "JAPANESE SNOWBE…
    ## $ assigned           <chr> "N", "N", "N", "Y", "N", "N", "N", "N", "N", "N", "…
    ## $ root_barrier       <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N", "N", "…
    ## $ plant_area         <chr> "N", "N", "4", "4", "4", "B", "6", "6", "3", "3", "…
    ## $ on_street_block    <dbl> 400, 400, 4900, 800, 5000, 500, 4900, 4900, 4900, 7…
    ## $ on_street          <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ neighbourhood_name <chr> "MARPOLE", "MARPOLE", "KENSINGTON-CEDAR COTTAGE", "…
    ## $ street_side_name   <chr> "EVEN", "EVEN", "EVEN", "EVEN", "EVEN", "ODD", "ODD…
    ## $ height_range_id    <dbl> 2, 4, 3, 4, 2, 2, 3, 3, 2, 2, 2, 5, 3, 2, 2, 2, 2, …
    ## $ diameter           <dbl> 10.00, 10.00, 4.00, 18.00, 9.00, 5.00, 15.00, 14.00…
    ## $ curb               <chr> "N", "N", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "…
    ## $ date_planted       <date> 1999-01-13, 1996-05-31, 1993-11-22, 1996-04-29, 19…
    ## $ longitude          <dbl> -123.1161, -123.1147, -123.0846, -123.0870, -123.08…
    ## $ latitude           <dbl> 49.21776, 49.21776, 49.23938, 49.23469, 49.23894, 4…

``` r
dim(vancouver_trees)
```

    ## [1] 146611     20

``` r
class(vancouver_trees)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#Exploring the *flow_sample* dataset
glimpse(flow_sample)
```

    ## Rows: 218
    ## Columns: 7
    ## $ station_id   <chr> "05BB001", "05BB001", "05BB001", "05BB001", "05BB001", "0…
    ## $ year         <dbl> 1909, 1910, 1911, 1912, 1913, 1914, 1915, 1916, 1917, 191…
    ## $ extreme_type <chr> "maximum", "maximum", "maximum", "maximum", "maximum", "m…
    ## $ month        <dbl> 7, 6, 6, 8, 6, 6, 6, 6, 6, 6, 6, 7, 6, 6, 6, 7, 5, 7, 6, …
    ## $ day          <dbl> 7, 12, 14, 25, 11, 18, 27, 20, 17, 15, 22, 3, 9, 5, 14, 5…
    ## $ flow         <dbl> 314, 230, 264, 174, 232, 214, 236, 309, 174, 345, 185, 24…
    ## $ sym          <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…

``` r
dim(flow_sample)
```

    ## [1] 218   7

``` r
class(flow_sample)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#Exploring the *apt_buildings* dataset
glimpse(apt_buildings)
```

    ## Rows: 3,455
    ## Columns: 37
    ## $ id                               <dbl> 10359, 10360, 10361, 10362, 10363, 10…
    ## $ air_conditioning                 <chr> "NONE", "NONE", "NONE", "NONE", "NONE…
    ## $ amenities                        <chr> "Outdoor rec facilities", "Outdoor po…
    ## $ balconies                        <chr> "YES", "YES", "YES", "YES", "NO", "NO…
    ## $ barrier_free_accessibilty_entr   <chr> "YES", "NO", "NO", "YES", "NO", "NO",…
    ## $ bike_parking                     <chr> "0 indoor parking spots and 10 outdoo…
    ## $ exterior_fire_escape             <chr> "NO", "NO", "NO", "YES", "NO", NA, "N…
    ## $ fire_alarm                       <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ garbage_chutes                   <chr> "YES", "YES", "NO", "NO", "NO", "NO",…
    ## $ heating_type                     <chr> "HOT WATER", "HOT WATER", "HOT WATER"…
    ## $ intercom                         <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ laundry_room                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ locker_or_storage_room           <chr> "NO", "YES", "YES", "YES", "NO", "YES…
    ## $ no_of_elevators                  <dbl> 3, 3, 0, 1, 0, 0, 0, 2, 4, 2, 0, 2, 2…
    ## $ parking_type                     <chr> "Underground Garage , Garage accessib…
    ## $ pets_allowed                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ prop_management_company_name     <chr> NA, "SCHICKEDANZ BROS. PROPERTIES", N…
    ## $ property_type                    <chr> "PRIVATE", "PRIVATE", "PRIVATE", "PRI…
    ## $ rsn                              <dbl> 4154812, 4154815, 4155295, 4155309, 4…
    ## $ separate_gas_meters              <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ separate_hydro_meters            <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ separate_water_meters            <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ site_address                     <chr> "65  FOREST MANOR RD", "70  CLIPPER R…
    ## $ sprinkler_system                 <chr> "YES", "YES", "NO", "YES", "NO", "NO"…
    ## $ visitor_parking                  <chr> "PAID", "FREE", "UNAVAILABLE", "UNAVA…
    ## $ ward                             <chr> "17", "17", "03", "03", "02", "02", "…
    ## $ window_type                      <chr> "DOUBLE PANE", "DOUBLE PANE", "DOUBLE…
    ## $ year_built                       <dbl> 1967, 1970, 1927, 1959, 1943, 1952, 1…
    ## $ year_registered                  <dbl> 2017, 2017, 2017, 2017, 2017, NA, 201…
    ## $ no_of_storeys                    <dbl> 17, 14, 4, 5, 4, 4, 4, 7, 32, 4, 4, 7…
    ## $ emergency_power                  <chr> "NO", "YES", "NO", "NO", "NO", "NO", …
    ## $ `non-smoking_building`           <chr> "YES", "NO", "YES", "YES", "YES", "NO…
    ## $ no_of_units                      <dbl> 218, 206, 34, 42, 25, 34, 14, 105, 57…
    ## $ no_of_accessible_parking_spaces  <dbl> 8, 10, 20, 42, 12, 0, 5, 1, 1, 6, 12,…
    ## $ facilities_available             <chr> "Recycling bins", "Green Bin / Organi…
    ## $ cooling_room                     <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ no_barrier_free_accessible_units <dbl> 2, 0, 0, 42, 0, NA, 14, 0, 0, 1, 25, …

``` r
dim(apt_buildings)
```

    ## [1] 3455   37

``` r
class(apt_buildings)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#Exploring the *building_permits* data set 
glimpse(building_permits)
```

    ## Rows: 20,680
    ## Columns: 14
    ## $ permit_number               <chr> "BP-2016-02248", "BU468090", "DB-2016-0445…
    ## $ issue_date                  <date> 2017-02-01, 2017-02-01, 2017-02-01, 2017-…
    ## $ project_value               <dbl> 0, 0, 35000, 15000, 181178, 0, 15000, 0, 6…
    ## $ type_of_work                <chr> "Salvage and Abatement", "New Building", "…
    ## $ address                     <chr> "4378 W 9TH AVENUE, Vancouver, BC V6R 2C7"…
    ## $ project_description         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ building_contractor         <chr> NA, NA, NA, "Mercury Contracting Ltd", "08…
    ## $ building_contractor_address <chr> NA, NA, NA, "88 W PENDER ST  \r\nUnit 2069…
    ## $ applicant                   <chr> "Raffaele & Associates DBA: Raffaele and A…
    ## $ applicant_address           <chr> "2642 East Hastings\r\nVancouver, BC  V5K …
    ## $ property_use                <chr> "Dwelling Uses", "Dwelling Uses", "Dwellin…
    ## $ specific_use_category       <chr> "One-Family Dwelling", "Multiple Dwelling"…
    ## $ year                        <dbl> 2017, 2017, 2017, 2017, 2017, 2017, 2017, …
    ## $ bi_id                       <dbl> 524, 535, 539, 541, 543, 546, 547, 548, 54…

``` r
dim(building_permits)
```

    ## [1] 20680    14

``` r
class(building_permits)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

<!----------------------------------------------------------------------------->

1.3 Now that you’ve explored the 4 datasets that you were initially most
interested in, let’s narrow it down to 2. What lead you to choose these
2? Briefly explain your choices below, and feel free to include any code
in your explanation.

<!-------------------------- Start your work below ---------------------------->

I have narrowed down my datasets to *apt_buildings* and
*vancouver_trees*. Although *apt_buildings* has many columns, they are
all easy to understand what the variables are. The few that I do not
know, including “rsn” seem to not be important enough for answering my
possible research questions and can be filtered out. As for
*vancouver_trees*, I am interested in environmental data for my thesis
research so I may end up having similar variables in my thesis analysis
work. However, this data set involves some complicated variables that I
wouldn’t know how to work with, including latitude and longitude.
Further, this data set seems to more be a recorded account of where each
tree is located for residential purposes versus for environmental
conservation work, which makes me slightly less interested in it.
<!----------------------------------------------------------------------------->

1.4 Time for the final decision! Going back to the beginning, it’s
important to have an *end goal* in mind. For example, if I had chosen
the `titanic` dataset for my project, I might’ve wanted to explore the
relationship between survival and other variables. Try to think of 1
research question that you would want to answer with each dataset. Note
them down below, and make your final choice based on what seems more
interesting to you!

<!-------------------------- Start your work below ---------------------------->

For the *apt_buildings* I could answer if private versus TCHC/Social
Housing allows for pets or has better amenity options For the
*vancouver_trees* I could answer if the species correlates with the
height and diameter of the trees

Based on these two possible research questions, I will choose
*vancouver_trees* as that is a more interesting to me!
<!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate.
Remember, marks will be awarded for completion of the 4 tasks, but 10
points of the whole project are allocated to a reproducible and clean
analysis. If you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset (15 points)

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 Complete *4 out of the following 8 exercises* to dive deeper into
your data. All datasets are different and therefore, not all of these
tasks may make sense for your data - which is why you should only answer
*4*. Use *dplyr* and *ggplot*.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 For each of the 4 exercises that you complete, provide a *brief
explanation* of why you chose that exercise in relation to your data (in
other words, why does it make sense to do that?), and sufficient
comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

*Making a new tibble*

I will first make a new tibble with a subset of the data I am interested
in by selecting the columns I will want to use. I will then assign these
selections to a new data set name. I have chosen to do this step as I do
not find every column relevant to my possible interests. Selecting for
only the column I’m interested in makes the data set easier to work
with.

``` r
#Assigning and making the new tibble
van_trees2 <-
(vancouver_trees %>% 
   select(tree_id, genus_name, species_name, common_name, neighbourhood_name, height_range_id, diameter, date_planted, longitude, latitude))

#Show the new tibble
head(van_trees2)
```

    ## # A tibble: 6 × 10
    ##   tree_id genus_name specie…¹ commo…² neigh…³ heigh…⁴ diame…⁵ date_pla…⁶ longi…⁷
    ##     <dbl> <chr>      <chr>    <chr>   <chr>     <dbl>   <dbl> <date>       <dbl>
    ## 1  149556 ULMUS      AMERICA… BRANDO… MARPOLE       2      10 1999-01-13   -123.
    ## 2  149563 ZELKOVA    SERRATA  JAPANE… MARPOLE       4      10 1996-05-31   -123.
    ## 3  149579 STYRAX     JAPONICA JAPANE… KENSIN…       3       4 1993-11-22   -123.
    ## 4  149590 FRAXINUS   AMERICA… AUTUMN… KENSIN…       4      18 1996-04-29   -123.
    ## 5  149604 ACER       CAMPEST… HEDGE … KENSIN…       2       9 1993-12-17   -123.
    ## 6  149616 PYRUS      CALLERY… CHANTI… MARPOLE       2       5 NA           -123.
    ## # … with 1 more variable: latitude <dbl>, and abbreviated variable names
    ## #   ¹​species_name, ²​common_name, ³​neighbourhood_name, ⁴​height_range_id,
    ## #   ⁵​diameter, ⁶​date_planted, ⁷​longitude

This simplified our table from 20 columns to 10, which will make it
easier to work with.

*Investigating Missing Values*

Now, I would like to know about the missing value information in my data
set, specifically, which columns have the most NA values, as this could
affect my analysis. Below, I use tidyr functions to find the missing
values (na’s) across all the columns and then plotted this information.

``` r
#Collecting the missing values per variable
missing_values <- van_trees2 %>% summarise(across(everything(), ~sum(is.na(.))))
#Plotting the missing values per variable
missing_values %>% pivot_longer(cols=everything()) %>%
  ggplot(aes(x=name, y=value))+
  geom_col()+
  theme(axis.text.x = element_text(angle = 90, hjust=1))+
  xlab("Variable")+
  ylab("# of missing values (NAs)")+
  ggtitle("Number of Missing Values per Variable in *van_trees2*")+
  geom_text(aes(label=value), nudge_y = 3000)
```

![](mini-project-1_files/figure-gfm/Missing%20Values%20per%20Variable-1.png)<!-- -->

This plot shows us that the variable “date_planted”, representing when
the trees were planted, is disproportionately missing values, which
means we may want to exclude this variable from the analysis, or at
least be aware of this fact when doing the analysis. Further, it makes
sense to me that the latitude and longitude variables were missing the
same amount of values as those are linked variables.

*Exploring the Relationship Between 2 Variables*

Next, I was curious what relationships I could start to see between the
variables. I know that older trees have larger diameters than their
younger counter parts. I wanted to see if this pattern exists in planted
residential trees by comparing the date planted and the diameter on a
line graph.

``` r
# Looking for date_planted and diameter correlation
van_trees2 %>% ggplot(mapping=aes(x = date_planted, y = diameter), na.rm = FALSE) + 
  geom_line() + 
  ylab("Diameter (DBH in inches)") + 
  xlab("Date Planted") +
  ggtitle("Date Planted vs Diameter")
```

    ## Warning: Removed 76548 row(s) containing missing values (geom_path).

![](mini-project-1_files/figure-gfm/Date%20Planted%20vs%20Diameter-1.png)<!-- -->
There is no clear pattern here. However, we can see some obvious
outliers in the diameter data, which may be interesting to look at later
on. Further, we can also see some small gaps in time without trees being
planted, including around 2010. However, this could be due to the
missing values in dates_planted.

*Plotting the Distribution of a Numeric Variable*

Additionally, as I start to think about what I can do with this data, I
wondered if certain neighborhoods have significantly more trees planted
there than others. Although I don’t have data readily available on the
wealth of these neighborhoods, it could be interesting to see if there
is a link between trees in the neighborhood and cost of living. Let’s
look at which neighborhoods have the most trees. I will do this by
grouping by the neighborhood_name variable and summarizing by the number
of trees. I will then create a bar graph to better visualize this.

``` r
#Number of trees per neighbourhood in Vancouver
Neighbourhood <- van_trees2 %>% group_by(neighbourhood_name) %>% summarise(trees =n())

#Creating a bar graph of trees per neighborhood
Neighbourhood %>% 
  ggplot(mapping=aes(x = neighbourhood_name, y = trees), na.rm = FALSE) + 
  geom_bar(stat='identity') + 
  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  ggtitle("Trees Planted per Neighbourhood") +
  xlab("Neighbourhood in Vancouver") +
  ylab("# of Trees Planted")
```

![](mini-project-1_files/figure-gfm/Trees%20Planter%20per%20Neighbourhood-1.png)<!-- -->
By plotting this distribution, I found that Renfrew-Collingwood,
Hastings-Sunrise, and Kensington-Cedar Cottage have had the most amount
of trees planted since 1990. These numbers per neighborhood may,
however, fluctuate over time. Further, there could be reasons for these
neighborhoods having more trees planted in them, including the size of
the neighborhood, lack of trees already being there, etc.

<!----------------------------------------------------------------------------->

# Task 3: Write your research questions (5 points)

So far, you have chosen a dataset and gotten familiar with it through
exploring the data. Now it’s time to figure out 4 research questions
that you would like to answer with your data! Write the 4 questions and
any additional comments at the end of this deliverable. These questions
are not necessarily set in stone - TAs will review them and give you
feedback; therefore, you may choose to pursue them as they are for the
rest of the project, or make modifications!

<!--- *****START HERE***** --->

1)  How have the number of trees planted in each neighborhood changed
    over time?
2)  Are certain types of trees planted in some neighborhoods versus
    others?
3)  How has species planted changed over time?
4)  How does tree size vary across neighborhoods?
    <!----------------------------------------------------------------------------->

# Task 4: Process and summarize your data (13 points)

From Task 2, you should have an idea of the basic structure of your
dataset (e.g. number of rows and columns, class types, etc.). Here, we
will start investigating your data more in-depth using various data
manipulation functions.

### 1.1 (10 points)

Now, for each of your four research questions, choose one task from
options 1-4 (summarizing), and one other task from 4-8 (graphing). You
should have 2 tasks done for each research question (8 total). Make sure
it makes sense to do them! (e.g. don’t use a numerical variables for a
task that needs a categorical variable.). Comment on why each task helps
(or doesn’t!) answer the corresponding research question.

Ensure that the output of each operation is printed!

**Summarizing:**

1.  Compute the *range*, *mean*, and *two other summary statistics* of
    **one numerical variable** across the groups of **one categorical
    variable** from your data.
2.  Compute the number of observations for at least one of your
    categorical variables. Do not use the function `table()`!
3.  Create a categorical variable with 3 or more groups from an existing
    numerical variable. You can use this new variable in the other
    tasks! *An example: age in years into “child, teen, adult, senior”.*
4.  Based on two categorical variables, calculate two summary statistics
    of your choosing.

**Graphing:**

5.  Create a graph out of summarized variables that has at least two
    geom layers.
6.  Create a graph of your choosing, make one of the axes logarithmic,
    and format the axes labels so that they are “pretty” or easier to
    read.
7.  Make a graph where it makes sense to customize the alpha
    transparency.
8.  Create 3 histograms out of summarized variables, with each histogram
    having different sized bins. Pick the “best” one and explain why it
    is the best.

Make sure it’s clear what research question you are doing each operation
for!

<!------------------------- Start your work below ----------------------------->

I will now look through each of my proposed research questions and start
to summarize and graph the related information.

**1) How have the number of trees planted in each neighborhood changed
over time?**

``` r
#Creating a categorical variable with 3 or more groups from an existing numerical variable

#Making a vector of dates
dates <- van_trees2$date_planted
#Extracting the year from dates as a new vector
year <- as.numeric(format(dates,'%Y'))

#Adding this vector into *van_trees2*
van_trees2$year_planted <- year
```

Creating this new variable was very helpful for my research question on
trees planted over time as I made knowing just the year the trees were
each planted accessible. This way I can look at trees per year.

``` r
#Creating a graph out of summarized variables that has at least two geom layers.

#I first need to count how many rows there are per year as this tells us how many trees were planted in each year
trees_per_year <- van_trees2 %>% count(year_planted)

#I then can create a bar graph of trees planted per year
ggplot(trees_per_year, aes(x=year_planted, y =n)) + 
  geom_col() +
  geom_text(aes(label=n), nudge_y = 100, size=2) + 
  ylim(0,4000) +
  xlab("Year") +
  ylab("Number of Trees Planted") +
  ggtitle("Number of Trees Planted Per Year in Vancouver") 
```

    ## Warning: Removed 1 rows containing missing values (position_stack).

    ## Warning: Removed 1 rows containing missing values (geom_text).

![](mini-project-1_files/figure-gfm/Trees%20Planted%20Per%20Year-1.png)<!-- -->

Creating a clear bar chart of year vs number of trees planted helped me
clealry visualzie which years had the most trees planted. I can see that
the graph is almost in a bell curve shape.

**2) Are certain types of trees planted in some neighborhoods versus
others?**

``` r
#Computing the number of observations for at least one of my variables. Specifically, how many different tree species have been planted in each neighborhood
species_per_neighbourhood <- 
  van_trees2 %>%
  group_by(neighbourhood_name) %>%
  summarize(species = n_distinct(common_name))

head(species_per_neighbourhood)
```

    ## # A tibble: 6 × 2
    ##   neighbourhood_name species
    ##   <chr>                <int>
    ## 1 ARBUTUS-RIDGE          260
    ## 2 DOWNTOWN               168
    ## 3 DUNBAR-SOUTHLANDS      364
    ## 4 FAIRVIEW               223
    ## 5 GRANDVIEW-WOODLAND     310
    ## 6 HASTINGS-SUNRISE       347

Above, I calculated the number of species (by common_name) in each
neighbourhood in Vancouver. This is very useful for my research question
of looking at which trees are planted in which neighborhoods.

``` r
#Creating a graph out of summarized variables that has at least two geom layers.

ggplot(species_per_neighbourhood, aes(x=neighbourhood_name, y = species)) + 
 geom_col() +  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  geom_text(aes(label= species), nudge_y = 10, size=3)  +
  xlab("Vancouver Neighbourhood") +
  ylab("# of different tree species") +
  ggtitle("The number of tree species planted in each Vancouver neighbourhood") 
```

![](mini-project-1_files/figure-gfm/Tree%20Species%20per%20Neighborhood-1.png)<!-- -->
This graphic helped me visualize the diversity of trees per Vancouver
neighbourhood, and showed me that there isn’t a huge difference between
neighbourhoods. However, it is interesting to see that Downtown has the
least. I would later like to look at what the most popular tree type in
downtown is.

**3) How has species planted changed over time? **

``` r
#Computing the number of observations for at least one of my categorical variables. Specifically, per year, how many different species were planted. 
species_per_year <- 
  van_trees2 %>%
  group_by(year_planted) %>%
  summarize(species = n_distinct(common_name))

head(species_per_year)
```

    ## # A tibble: 6 × 2
    ##   year_planted species
    ##          <dbl>   <int>
    ## 1         1989      10
    ## 2         1990      41
    ## 3         1991      36
    ## 4         1992      59
    ## 5         1993      73
    ## 6         1994      80

This shows if some years accounted for biodiversity more than other
years. While it does not tell us which were the most popular per year,
this is a good start.

``` r
#Creating a graph out of summarized variables that has at least two geom layers.

ggplot(species_per_year, aes(x=year_planted, y = species))+
  geom_col() +  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  geom_text(aes(label= species), nudge_y = 5, size=2.5)  +
  ylim(0,170) +
  xlab("Year") +
  ylab("# of different tree species") +
  ggtitle("The number of tree species planted per year in Vancouver ") 
```

    ## Warning: Removed 1 rows containing missing values (position_stack).

    ## Warning: Removed 1 rows containing missing values (geom_text).

![](mini-project-1_files/figure-gfm/Tree%20Species%20per%20Year-1.png)<!-- -->
This graph helps us visualize which years planted the most diverse
trees. It is interesting to see that the diversity in tree species
planted increased steadily over time since the start of planting on
record until the late 1990s. I am not seeing many other interesting
patterns here. It’s important to keep in mind, however, that this isn’t
answering the entirety of the proposed research question.

**4) How does tree size vary across neighborhoods?**

``` r
#Based on two categorical variables, I will calculate two summary statistics
#First I will look at a summary of diameter
mean(van_trees2$diameter)
```

    ## [1] 11.49016

``` r
range(van_trees2$diameter)
```

    ## [1]   0 435

``` r
#Next I will look at a summary of height_range_id (a category to denote height)
mean(van_trees2$height_range_id)
```

    ## [1] 2.626965

``` r
range(van_trees2$height_range_id)
```

    ## [1]  0 10

This shows me the kinds of numbers I will be working with for this
research question but it doesn’t get me very far in answering my
question.

``` r
#Making a graph with customized alpha transparency.
ggplot(van_trees2, aes(x=height_range_id, y=diameter)) +
 geom_point(aes(color = neighbourhood_name),
            size = 1,
            alpha = 0.8) 
```

![](mini-project-1_files/figure-gfm/Height%20Range%20ID%20vs%20Diameter%20per%20Neighborhood-1.png)<!-- -->
This graph was not very useful for my research question as it is unclear
with too many data points stacked on top of each other. This is due to
trees being grouped into 10 height_range_id categories in the original
data set. Perhaps then, I will only look at diameter when looking at
size.

<!----------------------------------------------------------------------------->

### 1.2 (3 points)

Based on the operations that you’ve completed, how much closer are you
to answering your research questions? Think about what aspects of your
research questions remain unclear. Can your research questions be
refined, now that you’ve investigated your data a bit more? Which
research questions are yielding interesting results?

<!-------------------------- Start your work below ---------------------------->

For my first research question, I answered how the number of trees
planted has changed over time in Vancouver but did not yet account for
each neighbourhood. Here, I was able to get pretty close to answering my
research question. For my second research question, I answered how many
different species have been planted in each neighbourhood, but have not
yet looked at the specific types of trees that are most popular in each
neighbourhood. This is an interesting question to me as it looks at
biodiversity per area. For my third research question, I was looking at
how many different species were planted each year as this could tell us
biodiversity planning over time. Again, I did not look at which species
were most popular per year yet, but I did get a sense of overall
biodiversity in species per year. For my fourth research question, I
only scratched the surface for looking at tree size differences
throughout the different neighbourhoods in Vancouver. I could refine
this question to only look at one size variable (height or diameter).
<!----------------------------------------------------------------------------->

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
