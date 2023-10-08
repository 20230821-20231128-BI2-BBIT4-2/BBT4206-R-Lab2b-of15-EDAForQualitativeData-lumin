Business Intelligence Lab Submission Markdown
================
<Specify your group name here>
<Specify the date when you submitted the lab>

- [Student Details](#student-details)
- [Setup Chunk](#setup-chunk)
- [\<Configuring Files \>](#configuring-files-)
  - [\<You Can Have a Sub-Title Here\>](#you-can-have-a-sub-title-here)
- [\<You can Provide Another Appropriate Title
  Here\>](#you-can-provide-another-appropriate-title-here)

# Student Details

|                                                   |                                                                                                                                                                                                                                                                               |     |
|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| **Student ID Numbers and Names of Group Members** | *\<list one student name, group, and ID per line; you should be between 2 and 5 members per group\>* \| \| 1. 112827 - A - Mungai Kenneth \| \| 2. 134265 - A - Emmanuel Kiptoo \| \| 3. 123324 - B - Kelly Noella Sota \| 4. ID - Group - Name \| \| 5. ID - Group - Name \| |     |
| **GitHub Classroom Group Name**                   | Lumin \|                                                                                                                                                                                                                                                                      |     |
| **Course Code**                                   | BBT4206                                                                                                                                                                                                                                                                       |     |
| **Course Name**                                   | Business Intelligence II                                                                                                                                                                                                                                                      |     |
| **Program**                                       | Bachelor of Business Information Technology                                                                                                                                                                                                                                   |     |
| **Semester Duration**                             | 21<sup>st</sup> August 2023 to 28<sup>th</sup> November 2023                                                                                                                                                                                                                  |     |

# Setup Chunk

**Note:** the following “*KnitR*” options have been set as the
defaults:  
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE, collapse = FALSE, tidy.opts = list(width.cutoff = 80), tidy = TRUE)`.

More KnitR options are documented here
<https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and
here <https://yihui.org/knitr/options/>.

**Note:** the following “*R Markdown*” options have been set as the
defaults:

> output:  
>   
> github_document:  
> toc: yes  
> toc_depth: 4  
> fig_width: 6  
> fig_height: 4  
> df_print: default  
>   
> editor_options:  
> chunk_output_type: console

# \<Configuring Files \>

``` r
## dplyr - For data manipulation ----
if (!is.element("dplyr", installed.packages()[, 1])) {
    install.packages("dplyr", dependencies = TRUE)
}
require("dplyr")
```

    ## Loading required package: dplyr

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
## ggplot2 - For data visualizations using the Grammar for Graphics package
## ----
if (!is.element("ggplot2", installed.packages()[, 1])) {
    install.packages("ggplot2", dependencies = TRUE)
}
require("ggplot2")
```

    ## Loading required package: ggplot2

``` r
## ggrepel - Additional options for the Grammar for Graphics package ----
if (!is.element("ggrepel", installed.packages()[, 1])) {
    install.packages("ggrepel", dependencies = TRUE)
}
require("ggrepel")
```

    ## Loading required package: ggrepel

``` r
## ggraph - Additional options for the Grammar for Graphics package ----
if (!is.element("ggraph", installed.packages()[, 1])) {
    install.packages("ggraph", dependencies = TRUE)
}
require("ggraph")
```

    ## Loading required package: ggraph

``` r
## tidytext - For text mining ----
if (!is.element("tidytext", installed.packages()[, 1])) {
    install.packages("tidytext", dependencies = TRUE)
}
require("tidytext")
```

    ## Loading required package: tidytext

``` r
## tidyr - To tidy messy data ----
if (!is.element("tidyr", installed.packages()[, 1])) {
    install.packages("tidyr", dependencies = TRUE)
}
require("tidyr")
```

    ## Loading required package: tidyr

``` r
## widyr - To widen, process, and re-tidy a dataset ----
if (!is.element("widyr", installed.packages()[, 1])) {
    install.packages("widyr", dependencies = TRUE)
}
require("widyr")
```

    ## Loading required package: widyr

``` r
## gridExtra - to arrange multiple grid-based plots on a page ----
if (!is.element("gridExtra", installed.packages()[, 1])) {
    install.packages("gridExtra", dependencies = TRUE)
}
require("gridExtra")
```

    ## Loading required package: gridExtra

    ## 
    ## Attaching package: 'gridExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine

``` r
## knitr - for dynamic report generation ----
if (!is.element("knitr", installed.packages()[, 1])) {
    install.packages("knitr", dependencies = TRUE)
}
require("knitr")
```

    ## Loading required package: knitr

``` r
## kableExtra - for nicely formatted output tables ----
if (!is.element("kableExtra", installed.packages()[, 1])) {
    install.packages("kableExtra", dependencies = TRUE)
}
require("kableExtra")
```

    ## Loading required package: kableExtra

    ## 
    ## Attaching package: 'kableExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     group_rows

``` r
## formattable - To create a formattable object ---- A formattable object is an
## object to which a formatting function and related attributes are attached.
if (!is.element("formattable", installed.packages()[, 1])) {
    install.packages("formattable", dependencies = TRUE)
}
require("formattable")
```

    ## Loading required package: formattable

``` r
## circlize - To create a cord diagram or visualization ---- by Gu et al.
## (2014)
if (!is.element("circlize", installed.packages()[, 1])) {
    install.packages("circlize", dependencies = TRUE)
}
require("circlize")
```

    ## Loading required package: circlize

    ## ========================================
    ## circlize version 0.4.15
    ## CRAN page: https://cran.r-project.org/package=circlize
    ## Github page: https://github.com/jokergoo/circlize
    ## Documentation: https://jokergoo.github.io/circlize_book/book/
    ## 
    ## If you use it in published research, please cite:
    ## Gu, Z. circlize implements and enhances circular visualization
    ##   in R. Bioinformatics 2014.
    ## 
    ## This message can be suppressed by:
    ##   suppressPackageStartupMessages(library(circlize))
    ## ========================================

``` r
## memery - For creating data analysis related memes ---- The memery package
## generates internet memes that optionally include a superimposed inset plot
## and other atypical features, combining the visual impact of an
## attention-grabbing meme with graphic results of data analysis.
if (!is.element("memery", installed.packages()[, 1])) {
    install.packages("memery", dependencies = TRUE)
}
require("memery")
```

    ## Loading required package: memery

    ## Loading required package: showtext

    ## Loading required package: sysfonts

    ## Loading required package: showtextdb

``` r
## magick - For image processing in R ----
if (!is.element("magick", installed.packages()[, 1])) {
    install.packages("magick", dependencies = TRUE)
}
require("magick")
```

    ## Loading required package: magick

    ## Linking to ImageMagick 6.9.11.60
    ## Enabled features: fontconfig, freetype, fftw, heic, lcms, pango, webp, x11
    ## Disabled features: cairo, ghostscript, raw, rsvg

    ## Using 8 threads

``` r
## yarrr - To create a pirate plot ----
if (!is.element("yarrr", installed.packages()[, 1])) {
    install.packages("yarrr", dependencies = TRUE)
}
```

    ## Installing package into '/home/ki3ani/R/x86_64-pc-linux-gnu-library/4.1'
    ## (as 'lib' is unspecified)

    ## also installing the dependencies 'MatrixModels', 'BayesFactor'

``` r
require("yarrr")
```

    ## Loading required package: yarrr

``` r
## radarchart - To create interactive radar charts using ChartJS ----
if (!is.element("radarchart", installed.packages()[, 1])) {
    install.packages("radarchart", dependencies = TRUE)
}
require("radarchart")
```

    ## Loading required package: radarchart

``` r
## igraph - To create ngram network diagrams ----
if (!is.element("igraph", installed.packages()[, 1])) {
    install.packages("igraph", dependencies = TRUE)
}
require("igraph")
```

    ## Loading required package: igraph

    ## 
    ## Attaching package: 'igraph'

    ## The following object is masked from 'package:circlize':
    ## 
    ##     degree

    ## The following object is masked from 'package:formattable':
    ## 
    ##     normalize

    ## The following object is masked from 'package:tidyr':
    ## 
    ##     crossing

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     as_data_frame, groups, union

    ## The following objects are masked from 'package:stats':
    ## 
    ##     decompose, spectrum

    ## The following object is masked from 'package:base':
    ## 
    ##     union

``` r
## wordcloud2 - For creating wordcloud by using 'wordcloud2.JS ----
if (!is.element("wordcloud2", installed.packages()[, 1])) {
    install.packages("wordcloud2", dependencies = TRUE)
}
require("wordcloud2")
```

    ## Loading required package: wordcloud2

``` r
## readr - Load datasets from CSV files ----
if (!is.element("readr", installed.packages()[, 1])) {
    install.packages("readr", dependencies = TRUE)
}
require("readr")
```

    ## Loading required package: readr

``` r
# STEP 2. Customize the Visualizations, Tables, and Colour Scheme ---- The
# following defines a blue-grey colour scheme for the visualizations: shades of
# blue and shades of grey
blue_grey_colours_11 <- c("#27408E", "#304FAF", "#536CB5", "#6981c7", "#8da0db",
    "#dde5ec", "#c8c9ca", "#B9BCC2", "#A7AAAF", "#888A8E", "#636569")

blue_grey_colours_6 <- c("#27408E", "#304FAF", "#536CB5", "#B9BCC2", "#A7AAAF", "#888A8E")

blue_grey_colours_4 <- c("#27408E", "#536CB5", "#B9BCC2", "#888A8E")

blue_grey_colours_2 <- c("#27408E", "#888A8E")

blue_grey_colours_1 <- c("#6981c7")

# Custom theme for visualizations
blue_grey_theme <- function() {
    theme(axis.ticks = element_line(linewidth = 1, linetype = "dashed", lineend = NULL,
        color = "#dfdede", arrow = NULL, inherit.blank = FALSE), axis.text = element_text(face = "bold",
        color = "#3f3f41", size = 12, hjust = 0.5), axis.title = element_text(face = "bold",
        color = "#3f3f41", size = 14, hjust = 0.5), plot.title = element_text(face = "bold",
        color = "#3f3f41", size = 16, hjust = 0.5), panel.grid = element_line(linewidth = 0.1,
        linetype = "dashed", lineend = NULL, color = "#dfdede", arrow = NULL, inherit.blank = FALSE),
        panel.background = element_rect(fill = "#f3eeee"), legend.title = element_text(face = "plain",
            color = "#3f3f41", size = 12, hjust = 0), legend.position = "right")
}

# Customize the text tables for consistency using HTML formatting
kable_theme <- function(dat, caption) {
    kable(dat, "html", escape = FALSE, caption = caption) %>%
        kable_styling(bootstrap_options = c("striped", "condensed", "bordered"),
            full_width = FALSE)
}

library(readr)
```

Loading the Dataset:

``` r
# STEP 3. Load the Dataset ----
student_performance_dataset <- read_csv("/home/ki3ani/BBT4206-R-Lab2b-of15-EDAForQualitativeData-lumin/markdown/performance-dataset.csv",
    col_types = cols(class_group = col_factor(levels = c("A", "B", "C")), gender = col_factor(levels = c("1",
        "0")), YOB = col_date(format = "%Y"), regret_choosing_bi = col_factor(levels = c("1",
        "0")), drop_bi_now = col_factor(levels = c("1", "0")), motivator = col_factor(levels = c("1",
        "0")), read_content_before_lecture = col_factor(levels = c("1", "2", "3",
        "4", "5")), anticipate_test_questions = col_factor(levels = c("1", "2", "3",
        "4", "5")), answer_rhetorical_questions = col_factor(levels = c("1", "2",
        "3", "4", "5")), find_terms_I_do_not_know = col_factor(levels = c("1", "2",
        "3", "4", "5")), copy_new_terms_in_reading_notebook = col_factor(levels = c("1",
        "2", "3", "4", "5")), take_quizzes_and_use_results = col_factor(levels = c("1",
        "2", "3", "4", "5")), reorganise_course_outline = col_factor(levels = c("1",
        "2", "3", "4", "5")), write_down_important_points = col_factor(levels = c("1",
        "2", "3", "4", "5")), space_out_revision = col_factor(levels = c("1", "2",
        "3", "4", "5")), studying_in_study_group = col_factor(levels = c("1", "2",
        "3", "4", "5")), schedule_appointments = col_factor(levels = c("1", "2",
        "3", "4", "5")), goal_oriented = col_factor(levels = c("1", "0")), spaced_repetition = col_factor(levels = c("1",
        "2", "3", "4")), testing_and_active_recall = col_factor(levels = c("1", "2",
        "3", "4")), interleaving = col_factor(levels = c("1", "2", "3", "4")), categorizing = col_factor(levels = c("1",
        "2", "3", "4")), retrospective_timetable = col_factor(levels = c("1", "2",
        "3", "4")), cornell_notes = col_factor(levels = c("1", "2", "3", "4")), sq3r = col_factor(levels = c("1",
        "2", "3", "4")), commute = col_factor(levels = c("1", "2", "3", "4")), study_time = col_factor(levels = c("1",
        "2", "3", "4")), repeats_since_Y1 = col_integer(), paid_tuition = col_factor(levels = c("0",
        "1")), free_tuition = col_factor(levels = c("0", "1")), extra_curricular = col_factor(levels = c("0",
        "1")), sports_extra_curricular = col_factor(levels = c("0", "1")), exercise_per_week = col_factor(levels = c("0",
        "1", "2", "3")), meditate = col_factor(levels = c("0", "1", "2", "3")), pray = col_factor(levels = c("0",
        "1", "2", "3")), internet = col_factor(levels = c("0", "1")), laptop = col_factor(levels = c("0",
        "1")), family_relationships = col_factor(levels = c("1", "2", "3", "4", "5")),
        friendships = col_factor(levels = c("1", "2", "3", "4", "5")), romantic_relationships = col_factor(levels = c("0",
            "1", "2", "3", "4")), spiritual_wellnes = col_factor(levels = c("1",
            "2", "3", "4", "5")), financial_wellness = col_factor(levels = c("1",
            "2", "3", "4", "5")), health = col_factor(levels = c("1", "2", "3", "4",
            "5")), day_out = col_factor(levels = c("0", "1", "2", "3")), night_out = col_factor(levels = c("0",
            "1", "2", "3")), alcohol_or_narcotics = col_factor(levels = c("0", "1",
            "2", "3")), mentor = col_factor(levels = c("0", "1")), mentor_meetings = col_factor(levels = c("0",
            "1", "2", "3")), `Attendance Waiver Granted: 1 = Yes, 0 = No` = col_factor(levels = c("0",
            "1")), GRADE = col_factor(levels = c("A", "B", "C", "D", "E"))), locale = locale())

View(student_performance_dataset)

# Dimensions
dim(student_performance_dataset)
```

    ## [1] 101 100

``` r
# Data Types
sapply(student_performance_dataset, class)
```

    ##                                                                                                                                                                                                                                                                                   class_group 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                        gender 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                           YOB 
    ##                                                                                                                                                                                                                                                                                        "Date" 
    ##                                                                                                                                                                                                                                                                            regret_choosing_bi 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                   drop_bi_now 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                     motivator 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                   read_content_before_lecture 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                     anticipate_test_questions 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                   answer_rhetorical_questions 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                      find_terms_I_do_not_know 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                            copy_new_terms_in_reading_notebook 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                  take_quizzes_and_use_results 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                     reorganise_course_outline 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                   write_down_important_points 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                            space_out_revision 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                       studying_in_study_group 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                         schedule_appointments 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                 goal_oriented 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                             spaced_repetition 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                     testing_and_active_recall 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                  interleaving 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                  categorizing 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                       retrospective_timetable 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                 cornell_notes 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                          sq3r 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                       commute 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                    study_time 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                              repeats_since_Y1 
    ##                                                                                                                                                                                                                                                                                     "integer" 
    ##                                                                                                                                                                                                                                                                                  paid_tuition 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                  free_tuition 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                              extra_curricular 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                       sports_extra_curricular 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                             exercise_per_week 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                      meditate 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                          pray 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                      internet 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                        laptop 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                          family_relationships 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                   friendships 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                        romantic_relationships 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                             spiritual_wellnes 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                            financial_wellness 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                        health 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                       day_out 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                     night_out 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                          alcohol_or_narcotics 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                                        mentor 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                               mentor_meetings 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                              A - 1. I am enjoying the subject 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                          A - 2. Classes start and end on time 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                               A - 3. The learning environment is participative, involves learning by doing and is group-based 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                             A - 4. The subject content is delivered according to the course outline and meets my expectations 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                           A - 5. The topics are clear and logically developed 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                             A - 6. I am developing my oral and writing skills 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                            A - 7. I am developing my reflective and critical reasoning skills 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                       A - 8. The assessment methods are assisting me to learn 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                            A - 9. I receive relevant feedback 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                             A - 10. I read the recommended readings and notes 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                   A - 11. I use the eLearning material posted 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                         B - 1. Concept 1 of 6: Principles of Business Intelligence and the DataOps Philosophy 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                             B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                     C - 2. Quizzes at the end of each concept 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                           C - 3. Lab manuals that outline the steps to follow during the labs 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                           C - 4. Required lab work submissions at the end of each lab manual that outline the activity to be done on your own 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                          C - 5. Supplementary videos to watch 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                    C - 6. Supplementary podcasts to listen to 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                          C - 7. Supplementary content to read 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                        C - 8. Lectures slides 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                            C - 9. Lecture notes on some of the lecture slides 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ## C - 10. The quality of the lectures given (quality measured by the breadth (the full span of knowledge of a subject) and depth (the extent to which specific topics are focused upon, amplified, and explored) of learning - NOT quality measured by how fun/comical/lively the lectures are) 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                              C - 11. The division of theory and practice such that most of the theory is done during the recorded online classes and most of the practice is done during the physical classes 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                      C - 12. The recordings of online classes 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                       D - 1. \nWrite two things you like about the teaching and learning in this unit so far. 
    ##                                                                                                                                                                                                                                                                                   "character" 
    ##                                                                                                                                                          D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester) 
    ##                                                                                                                                                                                                                                                                                   "character" 
    ##                                                                                                                                                                                                                                                              Average Course Evaluation Rating 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                     Average Level of Learning Attained Rating 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                             Average Pedagogical Strategy Effectiveness Rating 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                              Project: Section 1-4: (20%) x/10 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                             Project: Section 5-11: (50%) x/10 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                Project: Section 12: (30%) x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                              Project: (10%): x/30 x 100 TOTAL 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                       Quiz 1 on Concept 1 (Introduction) x/32 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                             Quiz 3 on Concept 3 (Linear) x/15 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                         Quiz 4 on Concept 4 (Non-Linear) x/22 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                       Quiz 5 on Concept 5 (Dashboarding) x/10 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                               Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                 Lab 1 - 2.c. - (Simple Linear Regression) x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                               Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                             Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                          Lab 5 - Chart JS Dashboard Setup x/5 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                      Lab Work (7%) x/25 x 100 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                        CAT 1 (8%): x/38 x 100 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                       CAT 2 (8%): x/100 x 100 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                    Attendance Waiver Granted: 1 = Yes, 0 = No 
    ##                                                                                                                                                                                                                                                                                      "factor" 
    ##                                                                                                                                                                                                                                                                        Absenteeism Percentage 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                  Coursework TOTAL: x/40 (40%) 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                              EXAM: x/60 (60%) 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                        TOTAL = Coursework TOTAL + EXAM (100%) 
    ##                                                                                                                                                                                                                                                                                     "numeric" 
    ##                                                                                                                                                                                                                                                                                         GRADE 
    ##                                                                                                                                                                                                                                                                                      "factor"

``` r
glimpse(student_performance_dataset)
```

    ## Rows: 101
    ## Columns: 100
    ## $ class_group                                                                                                                                                                                                                                                                                     <fct> …
    ## $ gender                                                                                                                                                                                                                                                                                          <fct> …
    ## $ YOB                                                                                                                                                                                                                                                                                             <date> …
    ## $ regret_choosing_bi                                                                                                                                                                                                                                                                              <fct> …
    ## $ drop_bi_now                                                                                                                                                                                                                                                                                     <fct> …
    ## $ motivator                                                                                                                                                                                                                                                                                       <fct> …
    ## $ read_content_before_lecture                                                                                                                                                                                                                                                                     <fct> …
    ## $ anticipate_test_questions                                                                                                                                                                                                                                                                       <fct> …
    ## $ answer_rhetorical_questions                                                                                                                                                                                                                                                                     <fct> …
    ## $ find_terms_I_do_not_know                                                                                                                                                                                                                                                                        <fct> …
    ## $ copy_new_terms_in_reading_notebook                                                                                                                                                                                                                                                              <fct> …
    ## $ take_quizzes_and_use_results                                                                                                                                                                                                                                                                    <fct> …
    ## $ reorganise_course_outline                                                                                                                                                                                                                                                                       <fct> …
    ## $ write_down_important_points                                                                                                                                                                                                                                                                     <fct> …
    ## $ space_out_revision                                                                                                                                                                                                                                                                              <fct> …
    ## $ studying_in_study_group                                                                                                                                                                                                                                                                         <fct> …
    ## $ schedule_appointments                                                                                                                                                                                                                                                                           <fct> …
    ## $ goal_oriented                                                                                                                                                                                                                                                                                   <fct> …
    ## $ spaced_repetition                                                                                                                                                                                                                                                                               <fct> …
    ## $ testing_and_active_recall                                                                                                                                                                                                                                                                       <fct> …
    ## $ interleaving                                                                                                                                                                                                                                                                                    <fct> …
    ## $ categorizing                                                                                                                                                                                                                                                                                    <fct> …
    ## $ retrospective_timetable                                                                                                                                                                                                                                                                         <fct> …
    ## $ cornell_notes                                                                                                                                                                                                                                                                                   <fct> …
    ## $ sq3r                                                                                                                                                                                                                                                                                            <fct> …
    ## $ commute                                                                                                                                                                                                                                                                                         <fct> …
    ## $ study_time                                                                                                                                                                                                                                                                                      <fct> …
    ## $ repeats_since_Y1                                                                                                                                                                                                                                                                                <int> …
    ## $ paid_tuition                                                                                                                                                                                                                                                                                    <fct> …
    ## $ free_tuition                                                                                                                                                                                                                                                                                    <fct> …
    ## $ extra_curricular                                                                                                                                                                                                                                                                                <fct> …
    ## $ sports_extra_curricular                                                                                                                                                                                                                                                                         <fct> …
    ## $ exercise_per_week                                                                                                                                                                                                                                                                               <fct> …
    ## $ meditate                                                                                                                                                                                                                                                                                        <fct> …
    ## $ pray                                                                                                                                                                                                                                                                                            <fct> …
    ## $ internet                                                                                                                                                                                                                                                                                        <fct> …
    ## $ laptop                                                                                                                                                                                                                                                                                          <fct> …
    ## $ family_relationships                                                                                                                                                                                                                                                                            <fct> …
    ## $ friendships                                                                                                                                                                                                                                                                                     <fct> …
    ## $ romantic_relationships                                                                                                                                                                                                                                                                          <fct> …
    ## $ spiritual_wellnes                                                                                                                                                                                                                                                                               <fct> …
    ## $ financial_wellness                                                                                                                                                                                                                                                                              <fct> …
    ## $ health                                                                                                                                                                                                                                                                                          <fct> …
    ## $ day_out                                                                                                                                                                                                                                                                                         <fct> …
    ## $ night_out                                                                                                                                                                                                                                                                                       <fct> …
    ## $ alcohol_or_narcotics                                                                                                                                                                                                                                                                            <fct> …
    ## $ mentor                                                                                                                                                                                                                                                                                          <fct> …
    ## $ mentor_meetings                                                                                                                                                                                                                                                                                 <fct> …
    ## $ `A - 1. I am enjoying the subject`                                                                                                                                                                                                                                                              <dbl> …
    ## $ `A - 2. Classes start and end on time`                                                                                                                                                                                                                                                          <dbl> …
    ## $ `A - 3. The learning environment is participative, involves learning by doing and is group-based`                                                                                                                                                                                               <dbl> …
    ## $ `A - 4. The subject content is delivered according to the course outline and meets my expectations`                                                                                                                                                                                             <dbl> …
    ## $ `A - 5. The topics are clear and logically developed`                                                                                                                                                                                                                                           <dbl> …
    ## $ `A - 6. I am developing my oral and writing skills`                                                                                                                                                                                                                                             <dbl> …
    ## $ `A - 7. I am developing my reflective and critical reasoning skills`                                                                                                                                                                                                                            <dbl> …
    ## $ `A - 8. The assessment methods are assisting me to learn`                                                                                                                                                                                                                                       <dbl> …
    ## $ `A - 9. I receive relevant feedback`                                                                                                                                                                                                                                                            <dbl> …
    ## $ `A - 10. I read the recommended readings and notes`                                                                                                                                                                                                                                             <dbl> …
    ## $ `A - 11. I use the eLearning material posted`                                                                                                                                                                                                                                                   <dbl> …
    ## $ `B - 1. Concept 1 of 6: Principles of Business Intelligence and the DataOps Philosophy`                                                                                                                                                                                                         <dbl> …
    ## $ `B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics`                                                                                                                                                                                                                             <dbl> …
    ## $ `C - 2. Quizzes at the end of each concept`                                                                                                                                                                                                                                                     <dbl> …
    ## $ `C - 3. Lab manuals that outline the steps to follow during the labs`                                                                                                                                                                                                                           <dbl> …
    ## $ `C - 4. Required lab work submissions at the end of each lab manual that outline the activity to be done on your own`                                                                                                                                                                           <dbl> …
    ## $ `C - 5. Supplementary videos to watch`                                                                                                                                                                                                                                                          <dbl> …
    ## $ `C - 6. Supplementary podcasts to listen to`                                                                                                                                                                                                                                                    <dbl> …
    ## $ `C - 7. Supplementary content to read`                                                                                                                                                                                                                                                          <dbl> …
    ## $ `C - 8. Lectures slides`                                                                                                                                                                                                                                                                        <dbl> …
    ## $ `C - 9. Lecture notes on some of the lecture slides`                                                                                                                                                                                                                                            <dbl> …
    ## $ `C - 10. The quality of the lectures given (quality measured by the breadth (the full span of knowledge of a subject) and depth (the extent to which specific topics are focused upon, amplified, and explored) of learning - NOT quality measured by how fun/comical/lively the lectures are)` <dbl> …
    ## $ `C - 11. The division of theory and practice such that most of the theory is done during the recorded online classes and most of the practice is done during the physical classes`                                                                                                              <dbl> …
    ## $ `C - 12. The recordings of online classes`                                                                                                                                                                                                                                                      <dbl> …
    ## $ `D - 1. \nWrite two things you like about the teaching and learning in this unit so far.`                                                                                                                                                                                                       <chr> …
    ## $ `D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester)`                                                                                                                                                          <chr> …
    ## $ `Average Course Evaluation Rating`                                                                                                                                                                                                                                                              <dbl> …
    ## $ `Average Level of Learning Attained Rating`                                                                                                                                                                                                                                                     <dbl> …
    ## $ `Average Pedagogical Strategy Effectiveness Rating`                                                                                                                                                                                                                                             <dbl> …
    ## $ `Project: Section 1-4: (20%) x/10`                                                                                                                                                                                                                                                              <dbl> …
    ## $ `Project: Section 5-11: (50%) x/10`                                                                                                                                                                                                                                                             <dbl> …
    ## $ `Project: Section 12: (30%) x/5`                                                                                                                                                                                                                                                                <dbl> …
    ## $ `Project: (10%): x/30 x 100 TOTAL`                                                                                                                                                                                                                                                              <dbl> …
    ## $ `Quiz 1 on Concept 1 (Introduction) x/32`                                                                                                                                                                                                                                                       <dbl> …
    ## $ `Quiz 3 on Concept 3 (Linear) x/15`                                                                                                                                                                                                                                                             <dbl> …
    ## $ `Quiz 4 on Concept 4 (Non-Linear) x/22`                                                                                                                                                                                                                                                         <dbl> …
    ## $ `Quiz 5 on Concept 5 (Dashboarding) x/10`                                                                                                                                                                                                                                                       <dbl> …
    ## $ `Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL`                                                                                                                                                                                                                                               <dbl> …
    ## $ `Lab 1 - 2.c. - (Simple Linear Regression) x/5`                                                                                                                                                                                                                                                 <dbl> …
    ## $ `Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5`                                                                                                                                                                                                                                <dbl> …
    ## $ `Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5`                                                                                                                                                                                                                               <dbl> …
    ## $ `Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5`                                                                                                                                                                                                                                             <dbl> …
    ## $ `Lab 5 - Chart JS Dashboard Setup x/5`                                                                                                                                                                                                                                                          <dbl> …
    ## $ `Lab Work (7%) x/25 x 100`                                                                                                                                                                                                                                                                      <dbl> …
    ## $ `CAT 1 (8%): x/38 x 100`                                                                                                                                                                                                                                                                        <dbl> …
    ## $ `CAT 2 (8%): x/100 x 100`                                                                                                                                                                                                                                                                       <dbl> …
    ## $ `Attendance Waiver Granted: 1 = Yes, 0 = No`                                                                                                                                                                                                                                                    <fct> …
    ## $ `Absenteeism Percentage`                                                                                                                                                                                                                                                                        <dbl> …
    ## $ `Coursework TOTAL: x/40 (40%)`                                                                                                                                                                                                                                                                  <dbl> …
    ## $ `EXAM: x/60 (60%)`                                                                                                                                                                                                                                                                              <dbl> …
    ## $ `TOTAL = Coursework TOTAL + EXAM (100%)`                                                                                                                                                                                                                                                        <dbl> …
    ## $ GRADE                                                                                                                                                                                                                                                                                           <fct> …

``` r
# Summary of each variable
summary(student_performance_dataset)
```

    ##  class_group gender      YOB             regret_choosing_bi drop_bi_now
    ##  A:23        1:58   Min.   :1998-01-01   1: 2               1: 2       
    ##  B:37        0:43   1st Qu.:2000-01-01   0:99               0:99       
    ##  C:41               Median :2001-01-01                                 
    ##                     Mean   :2000-11-25                                 
    ##                     3rd Qu.:2002-01-01                                 
    ##                     Max.   :2003-01-01                                 
    ##                                                                        
    ##  motivator read_content_before_lecture anticipate_test_questions
    ##  1:76      1:11                        1: 5                     
    ##  0:25      2:25                        2: 6                     
    ##            3:47                        3:31                     
    ##            4:14                        4:43                     
    ##            5: 4                        5:16                     
    ##                                                                 
    ##                                                                 
    ##  answer_rhetorical_questions find_terms_I_do_not_know
    ##  1: 3                        1: 6                    
    ##  2:15                        2: 2                    
    ##  3:32                        3:30                    
    ##  4:38                        4:37                    
    ##  5:13                        5:26                    
    ##                                                      
    ##                                                      
    ##  copy_new_terms_in_reading_notebook take_quizzes_and_use_results
    ##  1: 5                               1: 4                        
    ##  2:10                               2: 5                        
    ##  3:24                               3:22                        
    ##  4:37                               4:32                        
    ##  5:25                               5:38                        
    ##                                                                 
    ##                                                                 
    ##  reorganise_course_outline write_down_important_points space_out_revision
    ##  1: 7                      1: 4                        1: 8              
    ##  2:16                      2: 8                        2:17              
    ##  3:28                      3:20                        3:34              
    ##  4:32                      4:38                        4:28              
    ##  5:18                      5:31                        5:14              
    ##                                                                          
    ##                                                                          
    ##  studying_in_study_group schedule_appointments goal_oriented spaced_repetition
    ##  1:34                    1:42                  1:20          1:12             
    ##  2:21                    2:35                  0:81          2:31             
    ##  3:21                    3:16                                3:48             
    ##  4:16                    4: 5                                4:10             
    ##  5: 9                    5: 3                                                 
    ##                                                                               
    ##                                                                               
    ##  testing_and_active_recall interleaving categorizing retrospective_timetable
    ##  1: 2                      1:14         1: 6         1:17                   
    ##  2:17                      2:51         2:28         2:36                   
    ##  3:55                      3:32         3:56         3:38                   
    ##  4:27                      4: 4         4:11         4:10                   
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  cornell_notes sq3r   commute   study_time repeats_since_Y1 paid_tuition
    ##  1:19          1:18   1   :16   1   :45    Min.   : 0.00    0   :89     
    ##  2:26          2:28   2   :23   2   :39    1st Qu.: 0.00    1   :11     
    ##  3:38          3:30   3   :33   3   :12    Median : 2.00    NA's: 1     
    ##  4:18          4:25   4   :28   4   : 4    Mean   : 2.05                
    ##                       NA's: 1   NA's: 1    3rd Qu.: 3.00                
    ##                                            Max.   :10.00                
    ##                                            NA's   :1                    
    ##  free_tuition extra_curricular sports_extra_curricular exercise_per_week
    ##  0   :73      0   :47          0   :64                 0   :23          
    ##  1   :27      1   :53          1   :36                 1   :49          
    ##  NA's: 1      NA's: 1          NA's: 1                 2   :23          
    ##                                                        3   : 5          
    ##                                                        NA's: 1          
    ##                                                                         
    ##                                                                         
    ##  meditate    pray    internet   laptop    family_relationships friendships
    ##  0   :49   0   : 8   0   :13   0   :  0   1   : 0              1   : 0    
    ##  1   :35   1   :24   1   :87   1   :100   2   : 2              2   : 3    
    ##  2   : 7   2   :19   NA's: 1   NA's:  1   3   :18              3   :17    
    ##  3   : 9   3   :49                        4   :39              4   :56    
    ##  NA's: 1   NA's: 1                        5   :41              5   :24    
    ##                                           NA's: 1              NA's: 1    
    ##                                                                           
    ##  romantic_relationships spiritual_wellnes financial_wellness  health  
    ##  0   :56                1   : 1           1   :10            1   : 2  
    ##  1   : 0                2   : 8           2   :18            2   : 3  
    ##  2   : 6                3   :37           3   :41            3   :22  
    ##  3   :27                4   :33           4   :21            4   :35  
    ##  4   :11                5   :21           5   :10            5   :38  
    ##  NA's: 1                NA's: 1           NA's: 1            NA's: 1  
    ##                                                                       
    ##  day_out   night_out alcohol_or_narcotics  mentor   mentor_meetings
    ##  0   :27   0   :55   0   :68              0   :59   0   :53        
    ##  1   :67   1   :41   1   :30              1   :41   1   :29        
    ##  2   : 5   2   : 2   2   : 1              NA's: 1   2   :15        
    ##  3   : 1   3   : 2   3   : 1                        3   : 3        
    ##  NA's: 1   NA's: 1   NA's: 1                        NA's: 1        
    ##                                                                    
    ##                                                                    
    ##  A - 1. I am enjoying the subject A - 2. Classes start and end on time
    ##  Min.   :3.00                     Min.   :3.00                        
    ##  1st Qu.:4.00                     1st Qu.:4.00                        
    ##  Median :5.00                     Median :5.00                        
    ##  Mean   :4.49                     Mean   :4.68                        
    ##  3rd Qu.:5.00                     3rd Qu.:5.00                        
    ##  Max.   :5.00                     Max.   :5.00                        
    ##  NA's   :1                        NA's   :1                           
    ##  A - 3. The learning environment is participative, involves learning by doing and is group-based
    ##  Min.   :3.00                                                                                   
    ##  1st Qu.:4.00                                                                                   
    ##  Median :4.00                                                                                   
    ##  Mean   :4.35                                                                                   
    ##  3rd Qu.:5.00                                                                                   
    ##  Max.   :5.00                                                                                   
    ##  NA's   :1                                                                                      
    ##  A - 4. The subject content is delivered according to the course outline and meets my expectations
    ##  Min.   :3.00                                                                                     
    ##  1st Qu.:4.75                                                                                     
    ##  Median :5.00                                                                                     
    ##  Mean   :4.74                                                                                     
    ##  3rd Qu.:5.00                                                                                     
    ##  Max.   :5.00                                                                                     
    ##  NA's   :1                                                                                        
    ##  A - 5. The topics are clear and logically developed
    ##  Min.   :2.00                                       
    ##  1st Qu.:4.00                                       
    ##  Median :5.00                                       
    ##  Mean   :4.65                                       
    ##  3rd Qu.:5.00                                       
    ##  Max.   :5.00                                       
    ##  NA's   :1                                          
    ##  A - 6. I am developing my oral and writing skills
    ##  Min.   :1.00                                     
    ##  1st Qu.:4.00                                     
    ##  Median :4.00                                     
    ##  Mean   :4.11                                     
    ##  3rd Qu.:5.00                                     
    ##  Max.   :5.00                                     
    ##  NA's   :1                                        
    ##  A - 7. I am developing my reflective and critical reasoning skills
    ##  Min.   :2.00                                                      
    ##  1st Qu.:4.00                                                      
    ##  Median :4.00                                                      
    ##  Mean   :4.38                                                      
    ##  3rd Qu.:5.00                                                      
    ##  Max.   :5.00                                                      
    ##  NA's   :1                                                         
    ##  A - 8. The assessment methods are assisting me to learn
    ##  Min.   :1.00                                           
    ##  1st Qu.:4.00                                           
    ##  Median :5.00                                           
    ##  Mean   :4.61                                           
    ##  3rd Qu.:5.00                                           
    ##  Max.   :5.00                                           
    ##  NA's   :1                                              
    ##  A - 9. I receive relevant feedback
    ##  Min.   :3.00                      
    ##  1st Qu.:4.00                      
    ##  Median :5.00                      
    ##  Mean   :4.58                      
    ##  3rd Qu.:5.00                      
    ##  Max.   :5.00                      
    ##  NA's   :1                         
    ##  A - 10. I read the recommended readings and notes
    ##  Min.   :3.00                                     
    ##  1st Qu.:4.00                                     
    ##  Median :5.00                                     
    ##  Mean   :4.55                                     
    ##  3rd Qu.:5.00                                     
    ##  Max.   :5.00                                     
    ##  NA's   :1                                        
    ##  A - 11. I use the eLearning material posted
    ##  Min.   :3.0                                
    ##  1st Qu.:4.0                                
    ##  Median :5.0                                
    ##  Mean   :4.7                                
    ##  3rd Qu.:5.0                                
    ##  Max.   :5.0                                
    ##  NA's   :1                                  
    ##  B - 1. Concept 1 of 6: Principles of Business Intelligence and the DataOps Philosophy
    ##  Min.   :1.00                                                                         
    ##  1st Qu.:4.00                                                                         
    ##  Median :4.00                                                                         
    ##  Mean   :4.25                                                                         
    ##  3rd Qu.:5.00                                                                         
    ##  Max.   :5.00                                                                         
    ##  NA's   :1                                                                            
    ##  B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics
    ##  Min.   :2.00                                                     
    ##  1st Qu.:3.00                                                     
    ##  Median :4.00                                                     
    ##  Mean   :3.94                                                     
    ##  3rd Qu.:5.00                                                     
    ##  Max.   :5.00                                                     
    ##  NA's   :1                                                        
    ##  C - 2. Quizzes at the end of each concept
    ##  Min.   :2.00                             
    ##  1st Qu.:4.00                             
    ##  Median :5.00                             
    ##  Mean   :4.59                             
    ##  3rd Qu.:5.00                             
    ##  Max.   :5.00                             
    ##  NA's   :1                                
    ##  C - 3. Lab manuals that outline the steps to follow during the labs
    ##  Min.   :3.00                                                       
    ##  1st Qu.:4.00                                                       
    ##  Median :5.00                                                       
    ##  Mean   :4.61                                                       
    ##  3rd Qu.:5.00                                                       
    ##  Max.   :5.00                                                       
    ##  NA's   :1                                                          
    ##  C - 4. Required lab work submissions at the end of each lab manual that outline the activity to be done on your own
    ##  Min.   :3.00                                                                                                       
    ##  1st Qu.:4.00                                                                                                       
    ##  Median :5.00                                                                                                       
    ##  Mean   :4.55                                                                                                       
    ##  3rd Qu.:5.00                                                                                                       
    ##  Max.   :5.00                                                                                                       
    ##  NA's   :1                                                                                                          
    ##  C - 5. Supplementary videos to watch
    ##  Min.   :1.00                        
    ##  1st Qu.:4.00                        
    ##  Median :4.00                        
    ##  Mean   :4.19                        
    ##  3rd Qu.:5.00                        
    ##  Max.   :5.00                        
    ##  NA's   :1                           
    ##  C - 6. Supplementary podcasts to listen to
    ##  Min.   :1.00                              
    ##  1st Qu.:4.00                              
    ##  Median :4.00                              
    ##  Mean   :4.08                              
    ##  3rd Qu.:5.00                              
    ##  Max.   :5.00                              
    ##  NA's   :1                                 
    ##  C - 7. Supplementary content to read C - 8. Lectures slides
    ##  Min.   :1.00                         Min.   :2.0           
    ##  1st Qu.:4.00                         1st Qu.:4.0           
    ##  Median :4.00                         Median :5.0           
    ##  Mean   :4.17                         Mean   :4.6           
    ##  3rd Qu.:5.00                         3rd Qu.:5.0           
    ##  Max.   :5.00                         Max.   :5.0           
    ##  NA's   :1                            NA's   :1             
    ##  C - 9. Lecture notes on some of the lecture slides
    ##  Min.   :2.0                                       
    ##  1st Qu.:4.0                                       
    ##  Median :5.0                                       
    ##  Mean   :4.6                                       
    ##  3rd Qu.:5.0                                       
    ##  Max.   :5.0                                       
    ##  NA's   :1                                         
    ##  C - 10. The quality of the lectures given (quality measured by the breadth (the full span of knowledge of a subject) and depth (the extent to which specific topics are focused upon, amplified, and explored) of learning - NOT quality measured by how fun/comical/lively the lectures are)
    ##  Min.   :2.00                                                                                                                                                                                                                                                                                 
    ##  1st Qu.:4.00                                                                                                                                                                                                                                                                                 
    ##  Median :5.00                                                                                                                                                                                                                                                                                 
    ##  Mean   :4.54                                                                                                                                                                                                                                                                                 
    ##  3rd Qu.:5.00                                                                                                                                                                                                                                                                                 
    ##  Max.   :5.00                                                                                                                                                                                                                                                                                 
    ##  NA's   :1                                                                                                                                                                                                                                                                                    
    ##  C - 11. The division of theory and practice such that most of the theory is done during the recorded online classes and most of the practice is done during the physical classes
    ##  Min.   :2.00                                                                                                                                                                    
    ##  1st Qu.:4.00                                                                                                                                                                    
    ##  Median :5.00                                                                                                                                                                    
    ##  Mean   :4.49                                                                                                                                                                    
    ##  3rd Qu.:5.00                                                                                                                                                                    
    ##  Max.   :5.00                                                                                                                                                                    
    ##  NA's   :1                                                                                                                                                                       
    ##  C - 12. The recordings of online classes
    ##  Min.   :2.00                            
    ##  1st Qu.:4.00                            
    ##  Median :5.00                            
    ##  Mean   :4.33                            
    ##  3rd Qu.:5.00                            
    ##  Max.   :5.00                            
    ##  NA's   :1                               
    ##  D - 1. \nWrite two things you like about the teaching and learning in this unit so far.
    ##  Length:101                                                                             
    ##  Class :character                                                                       
    ##  Mode  :character                                                                       
    ##                                                                                         
    ##                                                                                         
    ##                                                                                         
    ##                                                                                         
    ##  D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester)
    ##  Length:101                                                                                                                          
    ##  Class :character                                                                                                                    
    ##  Mode  :character                                                                                                                    
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##  Average Course Evaluation Rating Average Level of Learning Attained Rating
    ##  Min.   :2.909                    Min.   :2.000                            
    ##  1st Qu.:4.273                    1st Qu.:3.500                            
    ##  Median :4.545                    Median :4.000                            
    ##  Mean   :4.531                    Mean   :4.095                            
    ##  3rd Qu.:4.909                    3rd Qu.:4.500                            
    ##  Max.   :5.000                    Max.   :5.000                            
    ##  NA's   :1                        NA's   :1                                
    ##  Average Pedagogical Strategy Effectiveness Rating
    ##  Min.   :3.182                                    
    ##  1st Qu.:4.068                                    
    ##  Median :4.545                                    
    ##  Mean   :4.432                                    
    ##  3rd Qu.:4.909                                    
    ##  Max.   :5.000                                    
    ##  NA's   :1                                        
    ##  Project: Section 1-4: (20%) x/10 Project: Section 5-11: (50%) x/10
    ##  Min.   : 0.000                   Min.   : 0.000                   
    ##  1st Qu.: 7.400                   1st Qu.: 6.000                   
    ##  Median : 8.500                   Median : 7.800                   
    ##  Mean   : 8.011                   Mean   : 6.582                   
    ##  3rd Qu.: 9.000                   3rd Qu.: 8.300                   
    ##  Max.   :10.000                   Max.   :10.000                   
    ##                                                                    
    ##  Project: Section 12: (30%) x/5 Project: (10%): x/30 x 100 TOTAL
    ##  Min.   :0.000                  Min.   :  0.00                  
    ##  1st Qu.:0.000                  1st Qu.: 56.00                  
    ##  Median :0.000                  Median : 66.40                  
    ##  Mean   :1.015                  Mean   : 62.39                  
    ##  3rd Qu.:1.250                  3rd Qu.: 71.60                  
    ##  Max.   :5.000                  Max.   :100.00                  
    ##  NA's   :1                                                      
    ##  Quiz 1 on Concept 1 (Introduction) x/32 Quiz 3 on Concept 3 (Linear) x/15
    ##  Min.   : 4.75                           Min.   : 3.00                    
    ##  1st Qu.:11.53                           1st Qu.: 7.00                    
    ##  Median :15.33                           Median : 9.00                    
    ##  Mean   :16.36                           Mean   : 9.53                    
    ##  3rd Qu.:19.63                           3rd Qu.:12.00                    
    ##  Max.   :31.25                           Max.   :15.00                    
    ##                                          NA's   :2                        
    ##  Quiz 4 on Concept 4 (Non-Linear) x/22 Quiz 5 on Concept 5 (Dashboarding) x/10
    ##  Min.   : 3.00                         Min.   : 0.000                         
    ##  1st Qu.:10.91                         1st Qu.: 5.000                         
    ##  Median :13.50                         Median : 6.330                         
    ##  Mean   :13.94                         Mean   : 6.367                         
    ##  3rd Qu.:17.50                         3rd Qu.: 8.000                         
    ##  Max.   :22.00                         Max.   :12.670                         
    ##  NA's   :6                             NA's   :12                             
    ##  Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL
    ##  Min.   :26.26                                  
    ##  1st Qu.:43.82                                  
    ##  Median :55.31                                  
    ##  Mean   :56.22                                  
    ##  3rd Qu.:65.16                                  
    ##  Max.   :95.25                                  
    ##                                                 
    ##  Lab 1 - 2.c. - (Simple Linear Regression) x/5
    ##  Min.   :3.000                                
    ##  1st Qu.:5.000                                
    ##  Median :5.000                                
    ##  Mean   :4.898                                
    ##  3rd Qu.:5.000                                
    ##  Max.   :5.000                                
    ##  NA's   :3                                    
    ##  Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5
    ##  Min.   :2.150                                                 
    ##  1st Qu.:3.150                                                 
    ##  Median :4.850                                                 
    ##  Mean   :4.166                                                 
    ##  3rd Qu.:5.000                                                 
    ##  Max.   :5.000                                                 
    ##  NA's   :6                                                     
    ##  Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5
    ##  Min.   :2.85                                                   
    ##  1st Qu.:4.85                                                   
    ##  Median :4.85                                                   
    ##  Mean   :4.63                                                   
    ##  3rd Qu.:4.85                                                   
    ##  Max.   :5.00                                                   
    ##  NA's   :9                                                      
    ##  Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5
    ##  Min.   :1.850                                    
    ##  1st Qu.:4.100                                    
    ##  Median :4.850                                    
    ##  Mean   :4.425                                    
    ##  3rd Qu.:5.000                                    
    ##  Max.   :5.000                                    
    ##  NA's   :18                                       
    ##  Lab 5 - Chart JS Dashboard Setup x/5 Lab Work (7%) x/25 x 100
    ##  Min.   :0.000                        Min.   : 17.80          
    ##  1st Qu.:0.000                        1st Qu.: 70.80          
    ##  Median :5.000                        Median : 80.00          
    ##  Mean   :3.404                        Mean   : 79.72          
    ##  3rd Qu.:5.000                        3rd Qu.: 97.20          
    ##  Max.   :5.000                        Max.   :100.00          
    ##                                                               
    ##  CAT 1 (8%): x/38 x 100 CAT 2 (8%): x/100 x 100
    ##  Min.   :32.89          Min.   :  0.00         
    ##  1st Qu.:59.21          1st Qu.: 51.00         
    ##  Median :69.73          Median : 63.50         
    ##  Mean   :69.39          Mean   : 62.13         
    ##  3rd Qu.:82.89          3rd Qu.: 81.75         
    ##  Max.   :97.36          Max.   :100.00         
    ##  NA's   :4              NA's   :31             
    ##  Attendance Waiver Granted: 1 = Yes, 0 = No Absenteeism Percentage
    ##  0:96                                       Min.   : 0.00         
    ##  1: 5                                       1st Qu.: 7.41         
    ##                                             Median :14.81         
    ##                                             Mean   :15.42         
    ##                                             3rd Qu.:22.22         
    ##                                             Max.   :51.85         
    ##                                                                   
    ##  Coursework TOTAL: x/40 (40%) EXAM: x/60 (60%)
    ##  Min.   : 7.47                Min.   : 5.00   
    ##  1st Qu.:20.44                1st Qu.:26.00   
    ##  Median :24.58                Median :34.00   
    ##  Mean   :24.53                Mean   :33.94   
    ##  3rd Qu.:29.31                3rd Qu.:42.00   
    ##  Max.   :35.08                Max.   :56.00   
    ##                               NA's   :4       
    ##  TOTAL = Coursework TOTAL + EXAM (100%) GRADE 
    ##  Min.   : 7.47                          A:23  
    ##  1st Qu.:45.54                          B:25  
    ##  Median :58.69                          C:22  
    ##  Mean   :57.12                          D:25  
    ##  3rd Qu.:68.83                          E: 6  
    ##  Max.   :87.72                                
    ## 

``` r
library(readr)
```

## \<You Can Have a Sub-Title Here\>

``` r
# Fill this with other R related code that will be executed when the R markdown
# file is rendered using knitR
library(readr)
```

# \<You can Provide Another Appropriate Title Here\>

Describe the code chunk here:

``` r
# Fill this with R related code that will be executed when the R markdown file
# is rendered using knitR
library(readr)
```

**etc.** as per the lab submission requirements.
