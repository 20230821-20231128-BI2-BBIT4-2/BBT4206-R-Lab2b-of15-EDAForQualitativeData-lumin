# Business Intelligence Lab Submission Markdown

<Specify your group name here> <Specify the date when you submitted the lab>

-   [Student Details](#student-details)
-   [Setup Chunk](#setup-chunk)
-   [Course Evaluation Rating per Group and per Gender](#course-evaluation-rating-per-group-and-per-gender)
-   [Word Count](#word-count)
    -   [Word Count per gender](#word-count-per-gender)
    -   [Top words for Group B students](#top-words-for-group-b-students)
    -   [Top 10 words for female students](#top-10-words-for-female-students)
-   [Word Cloud](#word-cloud)
    -   [Word Cloud for Evaluation Likes](#word-cloud-for-evaluation-likes)
    -   [Word Cloud for Evaluation Wishes](#word-cloud-for-evaluation-wishes)
-   [TF-IDF Score](#tf-idf-score)
    -   [TF-IDF Score per Group](#tf-idf-score-per-group)
    -   [TF-IDF Score per Gender (Wishes)](#tf-idf-score-per-gender-wishes)

# Student Details {#student-details}

+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **Student ID Numbers and Names of Group Members** | *\<list one student name, group, and ID per line; you should be between 2 and 5 members per group\>* |
|                                                   |                                                                                                      |
|                                                   | 1.  123324 - B - Kelly Noella Sota                                                                   |
|                                                   |                                                                                                      |
|                                                   | 2.  Kenneth Kimathi                                                                                  |
|                                                   |                                                                                                      |
|                                                   | 3.  ID - Group - Name                                                                                |
|                                                   |                                                                                                      |
|                                                   | 4.  ID - Group - Name                                                                                |
|                                                   |                                                                                                      |
|                                                   | 5.  ID - Group - Name                                                                                |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **GitHub Classroom Group Name**                   |                                                                                                      |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **Course Code**                                   | BBT4206                                                                                              |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **Course Name**                                   | Business Intelligence II                                                                             |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **Program**                                       | Bachelor of Business Information Technology                                                          |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+
| **Semester Duration**                             | 21^st^ August 2023 to 28^th^ November 2023                                                           |
+---------------------------------------------------+------------------------------------------------------------------------------------------------------+

# Setup Chunk {#setup-chunk}

**Note:** the following "*KnitR*" options have been set as the defaults:\
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE, collapse = FALSE, tidy.opts = list(width.cutoff = 80), tidy = TRUE)`.

More KnitR options are documented here <https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and here <https://yihui.org/knitr/options/>.

**Note:** the following "*R Markdown*" options have been set as the defaults:

> output:
>
> github_document:\
> toc: yes\
> toc_depth: 4\
> fig_width: 6\
> fig_height: 4\
> df_print: default
>
> editor_options:\
> chunk_output_type: console

These snippets are designed to generate visualizations for course evaluation data, specifically focusing on evaluation likes, wishes, and other related aspects(gender, class group).

``` r
## dplyr - For data manipulation ----
if (!is.element("dplyr", installed.packages()[, 1])) {
    install.packages("dplyr", dependencies = TRUE)
}
require("dplyr")
```

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
```

``` r
## ggplot2 - For data visualizations using the Grammar for Graphics package
## ----
if (!is.element("ggplot2", installed.packages()[, 1])) {
    install.packages("ggplot2", dependencies = TRUE)
}
require("ggplot2")
```

```         
## Loading required package: ggplot2
```

``` r
## ggrepel - Additional options for the Grammar for Graphics package ----
if (!is.element("ggrepel", installed.packages()[, 1])) {
    install.packages("ggrepel", dependencies = TRUE)
}
require("ggrepel")
```

```         
## Loading required package: ggrepel
```

``` r
## ggraph - Additional options for the Grammar for Graphics package ----
if (!is.element("ggraph", installed.packages()[, 1])) {
    install.packages("ggraph", dependencies = TRUE)
}
require("ggraph")
```

```         
## Loading required package: ggraph
```

``` r
## tidytext - For text mining ----
if (!is.element("tidytext", installed.packages()[, 1])) {
    install.packages("tidytext", dependencies = TRUE)
}
require("tidytext")
```

```         
## Loading required package: tidytext
```

``` r
## tidyr - To tidy messy data ----
if (!is.element("tidyr", installed.packages()[, 1])) {
    install.packages("tidyr", dependencies = TRUE)
}
require("tidyr")
```

```         
## Loading required package: tidyr
```

``` r
## widyr - To widen, process, and re-tidy a dataset ----
if (!is.element("widyr", installed.packages()[, 1])) {
    install.packages("widyr", dependencies = TRUE)
}
require("widyr")
```

```         
## Loading required package: widyr
```

``` r
## gridExtra - to arrange multiple grid-based plots on a page ----
if (!is.element("gridExtra", installed.packages()[, 1])) {
    install.packages("gridExtra", dependencies = TRUE)
}
require("gridExtra")
```

```         
## Loading required package: gridExtra

## 
## Attaching package: 'gridExtra'

## The following object is masked from 'package:dplyr':
## 
##     combine
```

``` r
## knitr - for dynamic report generation ----
if (!is.element("knitr", installed.packages()[, 1])) {
    install.packages("knitr", dependencies = TRUE)
}
require("knitr")
```

```         
## Loading required package: knitr
```

``` r
## kableExtra - for nicely formatted output tables ----
if (!is.element("kableExtra", installed.packages()[, 1])) {
    install.packages("kableExtra", dependencies = TRUE)
}
require("kableExtra")
```

```         
## Loading required package: kableExtra

## 
## Attaching package: 'kableExtra'

## The following object is masked from 'package:dplyr':
## 
##     group_rows
```

``` r
## formattable - To create a formattable object ---- A formattable object is an
## object to which a formatting function and related attributes are attached.
if (!is.element("formattable", installed.packages()[, 1])) {
    install.packages("formattable", dependencies = TRUE)
}
require("formattable")
```

```         
## Loading required package: formattable
```

``` r
## circlize - To create a cord diagram or visualization ---- by Gu et al.
## (2014)
if (!is.element("circlize", installed.packages()[, 1])) {
    install.packages("circlize", dependencies = TRUE)
}
require("circlize")
```

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
```

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

```         
## Loading required package: memery

## Loading required package: showtext

## Loading required package: sysfonts

## Loading required package: showtextdb
```

``` r
## magick - For image processing in R ----
if (!is.element("magick", installed.packages()[, 1])) {
    install.packages("magick", dependencies = TRUE)
}
require("magick")
```

```         
## Loading required package: magick

## Linking to ImageMagick 6.9.12.96
## Enabled features: cairo, freetype, fftw, ghostscript, heic, lcms, pango, raw, rsvg, webp
## Disabled features: fontconfig, x11
```

``` r
## yarrr - To create a pirate plot ----
if (!is.element("yarrr", installed.packages()[, 1])) {
    install.packages("yarrr", dependencies = TRUE)
}
require("yarrr")
```

```         
## Loading required package: yarrr

## Loading required package: jpeg

## Loading required package: BayesFactor

## Loading required package: coda

## Loading required package: Matrix

## 
## Attaching package: 'Matrix'

## The following objects are masked from 'package:tidyr':
## 
##     expand, pack, unpack

## ************
## Welcome to BayesFactor 0.9.12-4.5. If you have questions, please contact Richard Morey (richarddmorey@gmail.com).
## 
## Type BFManual() to open the manual.
## ************

## yarrr v0.1.5. Citation info at citation('yarrr'). Package guide at yarrr.guide()

## Email me at Nathaniel.D.Phillips.is@gmail.com

## 
## Attaching package: 'yarrr'

## The following object is masked from 'package:ggplot2':
## 
##     diamonds
```

``` r
## radarchart - To create interactive radar charts using ChartJS ----
if (!is.element("radarchart", installed.packages()[, 1])) {
    install.packages("radarchart", dependencies = TRUE)
}
require("radarchart")
```

```         
## Loading required package: radarchart
```

``` r
## igraph - To create ngram network diagrams ----
if (!is.element("igraph", installed.packages()[, 1])) {
    install.packages("igraph", dependencies = TRUE)
}
require("igraph")
```

```         
## Loading required package: igraph

## 
## Attaching package: 'igraph'

## The following object is masked from 'package:BayesFactor':
## 
##     compare

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
```

``` r
## wordcloud2 - For creating wordcloud by using 'wordcloud2.JS ----
if (!is.element("wordcloud2", installed.packages()[, 1])) {
    install.packages("wordcloud2", dependencies = TRUE)
}
require("wordcloud2")
```

```         
## Loading required package: wordcloud2
```

``` r
## readr - Load datasets from CSV files ----
if (!is.element("readr", installed.packages()[, 1])) {
    install.packages("readr", dependencies = TRUE)
}
require("readr")
```

```         
## Loading required package: readr
```

``` r
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
```

# Course Evaluation Rating per Group and per Gender {#course-evaluation-rating-per-group-and-per-gender}

This snippet creates a decorated tabular output to display average course evaluation ratings per class group and gender.

``` r
student_performance_dataset <-
  read_csv("data/20230412-20230719-BI1-BBIT4-1-StudentPerformanceDataset.CSV",
           col_types =
             cols(
               class_group = col_factor(levels = c("A", "B", "C")),
               gender = col_factor(levels = c("1", "0")),
               YOB = col_date(format = "%Y"),
               regret_choosing_bi = col_factor(levels = c("1", "0")),
               drop_bi_now = col_factor(levels = c("1", "0")),
               motivator = col_factor(levels = c("1", "0")),
               read_content_before_lecture =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               anticipate_test_questions =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               answer_rhetorical_questions =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               find_terms_I_do_not_know =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               copy_new_terms_in_reading_notebook =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               take_quizzes_and_use_results =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               reorganise_course_outline =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               write_down_important_points =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               space_out_revision =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               studying_in_study_group =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               schedule_appointments =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               goal_oriented = col_factor(levels = c("1", "0")),
               spaced_repetition =
                 col_factor(levels = c("1", "2", "3", "4")),
               testing_and_active_recall =
                 col_factor(levels = c("1", "2", "3", "4")),
               interleaving = col_factor(levels = c("1", "2", "3", "4")),
               categorizing = col_factor(levels = c("1", "2", "3", "4")),
               retrospective_timetable =
                 col_factor(levels = c("1", "2", "3", "4")),
               cornell_notes = col_factor(levels = c("1", "2", "3", "4")),
               sq3r = col_factor(levels = c("1", "2", "3", "4")),
               commute = col_factor(levels = c("1", "2", "3", "4")),
               study_time = col_factor(levels = c("1", "2", "3", "4")),
               repeats_since_Y1 = col_integer(),
               paid_tuition = col_factor(levels = c("0", "1")),
               free_tuition = col_factor(levels = c("0", "1")),
               extra_curricular = col_factor(levels = c("0", "1")),
               sports_extra_curricular = col_factor(levels = c("0", "1")),
               exercise_per_week = col_factor(levels = c("0", "1", "2", "3")),
               meditate = col_factor(levels = c("0", "1", "2", "3")),
               pray = col_factor(levels = c("0", "1", "2", "3")),
               internet = col_factor(levels = c("0", "1")),
               laptop = col_factor(levels = c("0", "1")),
               family_relationships =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               friendships = col_factor(levels = c("1", "2", "3", "4", "5")),
               romantic_relationships =
                 col_factor(levels = c("0", "1", "2", "3", "4")),
               spiritual_wellnes =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               financial_wellness =
                 col_factor(levels = c("1", "2", "3", "4", "5")),
               health = col_factor(levels = c("1", "2", "3", "4", "5")),
               day_out = col_factor(levels = c("0", "1", "2", "3")),
               night_out = col_factor(levels = c("0", "1", "2", "3")),
               alcohol_or_narcotics =
                 col_factor(levels = c("0", "1", "2", "3")),
               mentor = col_factor(levels = c("0", "1")),
               mentor_meetings = col_factor(levels = c("0", "1", "2", "3")),
               `Attendance Waiver Granted: 1 = Yes, 0 = No` =
                 col_factor(levels = c("0", "1")),
               GRADE = col_factor(levels = c("A", "B", "C", "D", "E"))),
           locale = locale())

evaluation_per_group_per_gender <- student_performance_dataset %>% # nolint
  mutate(`Student's Gender` =
           ifelse(gender == 1, "Male", "Female")) %>%
  select(class_group, gender,
         `Student's Gender`, `Average Course Evaluation Rating`) %>%
  filter(!is.na(`Average Course Evaluation Rating`)) %>%
  group_by(class_group, `Student's Gender`) %>%
  summarise(average_evaluation_rating =
              mean(`Average Course Evaluation Rating`)) %>%
  arrange(desc(average_evaluation_rating), .by_group = TRUE)
```

```         
## `summarise()` has grouped output by 'class_group'. You can override using the
## `.groups` argument.
```

``` r
evaluation_per_group_per_gender %>%
  rename(`Class Group` = class_group) %>%
  rename(`Average Course Evaluation Rating` = average_evaluation_rating) %>%
  select(`Class Group`, `Student's Gender`,
         `Average Course Evaluation Rating`) %>%
  mutate(`Average Course Evaluation Rating` =
           color_tile("#B9BCC2", "#536CB5")
           (`Average Course Evaluation Rating`)) %>%
  kable("html", escape = FALSE, align = "c",
        caption = "Course Evaluation Rating per Group and per Gender") %>%
  kable_styling(bootstrap_options =
                  c("striped", "condensed", "bordered"),
                full_width = FALSE)
```

+-------------+-------------------+----------------------------------+
| Class Group | Student\'s Gender | Average Course Evaluation Rating |
+:===========:+:=================:+:================================:+
| A           | Female            | 4.618190                         |
+-------------+-------------------+----------------------------------+
| A           | Male              | 4.573423                         |
+-------------+-------------------+----------------------------------+
| B           | Female            | 4.573431                         |
+-------------+-------------------+----------------------------------+
| B           | Male              | 4.569174                         |
+-------------+-------------------+----------------------------------+
| C           | Female            | 4.636370                         |
+-------------+-------------------+----------------------------------+
| C           | Male              | 4.294362                         |
+-------------+-------------------+----------------------------------+

: Course Evaluation Rating per Group and per Gender

This snippet generates a bar chart to visualize average course evaluation ratings per class group and gender.

``` r
evaluation_per_group_per_gender %>%
    ggplot() + geom_bar(aes(x = class_group, y = average_evaluation_rating, fill = `Student's Gender`),
    stat = "identity", position = "dodge") + expand_limits(y = 0) + blue_grey_theme() +
    scale_fill_manual(values = blue_grey_colours_2) + ggtitle("Course Evaluation Rating per Group and per Gender") +
    labs(x = "Class Group", y = "Average Rating")
```

![](Lab2b-Submission-Markdown_files/figure-gfm/Third%20Code%20Chunk-1.png)<!-- -->

# Word Count {#word-count}

## Word Count per gender {#word-count-per-gender}

The following snippet displays the number of significant words in evaluation likes per gender in a tabular format

``` r
evaluation_likes_and_wishes <- student_performance_dataset %>%
  mutate(`Student's Gender` =
           ifelse(gender == 1, "Male", "Female")) %>%
  rename(`Class Group` = class_group) %>%
  rename(Likes = `D - 1. Write two things you like about the teaching and learning in this unit so far.`) %>% # nolint
  rename(Wishes = `D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester)`) %>% # nolint
  select(`Class Group`,
         `Student's Gender`, `Average Course Evaluation Rating`,
         Likes, Wishes) %>%
  filter(!is.na(`Average Course Evaluation Rating`)) %>%
  arrange(`Class Group`)

undesirable_words <- c("wow", "lol", "none", "na")

evaluation_likes_filtered <- evaluation_likes_and_wishes %>% # nolint
  unnest_tokens(word, Likes) %>%
  anti_join(stop_words, by = c("word")) %>%
  distinct() %>%
  filter(!word %in% undesirable_words) %>%
  filter(nchar(word) > 3) %>%
  rename(`Likes (tokenized)` = word) %>%
  select(-Wishes)
word_count_per_gender_likes <- evaluation_likes_filtered %>%
  group_by(`Student's Gender`) %>%
  summarise(num_words = n()) %>%
  arrange(desc(num_words))
  
word_count_per_gender_likes %>%
  mutate(num_words = color_bar("lightblue")(num_words)) %>%
  rename(`Number of Words` = num_words) %>%
  kable("html", escape = FALSE, align = "c",
        caption = "Number of Significant Words in Evaluation Likes 
                   per Gender: Minus contractions, special characters, 
                   stopwords, short words, and censored words.") %>%
  kable_styling(bootstrap_options =
                  c("striped", "condensed", "bordered"),
                full_width = FALSE)
```

+-------------------+-----------------+
| Student\'s Gender | Number of Words |
+:=================:+:===============:+
| Male              | 265             |
+-------------------+-----------------+
| Female            | 214             |
+-------------------+-----------------+

: Number of Significant Words in Evaluation Likes per Gender: Minus contractions, special characters, stopwords, short words, and censored words.

The following snippet displays the number of significant words in evaluation wishes per gender in a tabular format

``` r
evaluation_likes_and_wishes <- student_performance_dataset %>%
  mutate(`Student's Gender` =
           ifelse(gender == 1, "Male", "Female")) %>%
  rename(`Class Group` = class_group) %>%
  rename(Likes = `D - 1. Write two things you like about the teaching and learning in this unit so far.`) %>% # nolint
  rename(Wishes = `D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester)`) %>% # nolint
  select(`Class Group`,
         `Student's Gender`, `Average Course Evaluation Rating`,
         Likes, Wishes) %>%
  filter(!is.na(`Average Course Evaluation Rating`)) %>%
  arrange(`Class Group`)

undesirable_words <- c("wow", "lol", "none", "na")

evaluation_wishes_filtered <- evaluation_likes_and_wishes %>% # nolint
  unnest_tokens(word, Wishes) %>%
  anti_join(stop_words, by = c("word")) %>%
  distinct() %>%
  filter(!word %in% undesirable_words) %>%
  filter(nchar(word) > 3) %>%
  rename(`Wishes (tokenized)` = word) %>%
  select(-Likes)

word_count_per_gender_wishes <- evaluation_wishes_filtered %>%
  group_by(`Student's Gender`) %>%
  summarise(num_words = n()) %>%
  arrange(desc(num_words))

 word_count_per_gender_wishes %>%
  mutate(num_words = color_bar("lightblue")(num_words)) %>%
  rename(`Number of Words` = num_words) %>%
  kable("html", escape = FALSE, align = "c",
        caption = "Number of Significant Words in Evaluation Wishes 
                   per Gender: Minus contractions, special characters, 
                   stopwords, short words, and censored words.") %>%
  kable_styling(bootstrap_options =
                  c("striped", "condensed", "bordered"),
                full_width = FALSE)
```

+-------------------+-----------------+
| Student\'s Gender | Number of Words |
+:=================:+:===============:+
| Male              | 149             |
+-------------------+-----------------+
| Female            | 109             |
+-------------------+-----------------+

: Number of Significant Words in Evaluation Wishes per Gender: Minus contractions, special characters, stopwords, short words, and censored words.

## Top words for Group B students {#top-words-for-group-b-students}

Displays the most frequently used words in course evaluation likes for students in group B.

``` r
evaluation_likes_filtered %>%
    select(`Class Group`, `Student's Gender`, `Average Course Evaluation Rating`,
        `Likes (tokenized)`) %>%
    filter(`Class Group` == "B") %>%
    count(`Likes (tokenized)`, sort = TRUE) %>%
    top_n(9) %>%
    mutate(`Likes (tokenized)` = reorder(`Likes (tokenized)`, n)) %>%
    ggplot() + geom_col(aes(`Likes (tokenized)`, n), fill = blue_grey_colours_1) +
    blue_grey_theme() + xlab("Word in Course Evaluation") + ylab("Number of Times Used (Term Frequency)") +
    ggtitle("Most Frequently Used Words in Course Evaluation Likes for Group B
          Students") +
    coord_flip()
```

```         
## Selecting by n
```

![](Lab2b-Submission-Markdown_files/figure-gfm/Your%20Sixth%20Code%20Chunk-1.png)<!-- -->

## Top 10 words for female students {#top-10-words-for-female-students}

Generates a bar chart showing the most frequently used words in course evaluation wishes by female students

``` r
evaluation_wishes_filtered %>%
    select(`Class Group`, `Student's Gender`, `Average Course Evaluation Rating`,
        `Wishes (tokenized)`) %>%
    filter(`Student's Gender` == "Female") %>%
    count(`Wishes (tokenized)`, sort = TRUE) %>%
    top_n(9) %>%
    mutate(`Wishes (tokenized)` = reorder(`Wishes (tokenized)`, n)) %>%
    ggplot() + geom_col(aes(`Wishes (tokenized)`, n), fill = blue_grey_colours_1) +
    blue_grey_theme() + xlab("Word in Course Evaluation") + ylab("Number of Times Used (Term Frequency)") +
    ggtitle("Most Frequently Used Words in Course Evaluation Wishes for Female
          Students") +
    coord_flip()
```

```         
## Selecting by n
```

![](Lab2b-Submission-Markdown_files/figure-gfm/Seventh%20Code%20Chunk-1.png)<!-- -->

# Word Cloud {#word-cloud}

## Word Cloud for Evaluation Likes {#word-cloud-for-evaluation-likes}

This code generates a word cloud visualization for evaluation likes, highlighting the most frequently used words.

``` r
evaluation_likes_filtered_cloud <- evaluation_likes_filtered %>% # nolint
  count(`Likes (tokenized)`, sort = TRUE)

wordcloud2(evaluation_likes_filtered_cloud, size = .5)
```

```         
## PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.
```

::: {#htmlwidget-8f03afe8fae93a328221 .wordcloud2 .html-widget .html-fill-item-overflow-hidden .html-fill-item style="width:576px;height:384px;"}
:::

```{=html}
<script type="application/json" data-for="htmlwidget-8f03afe8fae93a328221">{"x":{"word":["lecturer","concepts","understand","labs","notes","content","understanding","unit","explained","practical","teaching","detailed","easy","topic","explains","quizzes","business","class","delivery","interactive","makes","questions","teacher","developed","helpful","learn","learning","manner","manuals","method","topics","understood","classes","concept","delivered","easier","lecture","lectures","real","slides","students","understandable","world","comprehensive","concerns","data","depth","engaging","enjoy","examples","helping","helps","knowledge","learnt","lecturer's","lessons","material","mode","project","provided","quizes","read","reading","relevant","resources","start","student","taught","time","accommodating","activities","actual","advance","ahead","algorithms","amount","analogies","answered","answers","applicationsthe","applied","arranged","aspect","aspects","assessment","assignment","assignments","assist","assistance","benefits","broad","broadly","businesses","calendar","career","carry","cats","check","chronological","churn","communcation","complex","confirms","constant","contents","conveyed","covers","create","customer","deep","description","efficient","encourage","encourages","engage","enhances","enjoyable","ensure","ensures","entry","environment","excellent","exciting","expanded","expect","explain","explanation","explanations","extra","extremely","fascinating","feedback","fine","fluent","focus","focuses","follow","gauge","google","gradual","guides","guiding","hand","hands","hard","highly","honest","hundle","including","incoming","indulging","ineractive","information","informative","informing","inhtegrating","insights","intelligence","intergation","intuitive","it’s","labeled","lecurer","lend","market","meetings","moves","multiple","nice","noteslabs","online","opportunity","organization","organized","outline","outlined","pace","participation","passionate","path","people","perceived","planning","positive","practicality","prediction","prepare","prior","prsented","punctuality","purposes","quick","quiz","quizz","recordings","references","related","responding","responses","revise","revision","rush","saves","scenarios","scope","sectioned","sessions","sets","simple","solve","spreadsheet","structured","systematic","takes","talk","teaches","technological","testing","theory","ties","understadable","valid","versed","video","wise","written"],"freq":[21,14,14,13,13,11,11,10,9,9,8,7,7,7,6,6,5,5,5,5,5,5,5,4,4,4,4,4,4,4,4,4,3,3,3,3,3,3,3,3,3,3,3,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],"fontFamily":"Segoe UI","fontWeight":"bold","color":"random-dark","minSize":0,"weightFactor":4.285714285714286,"backgroundColor":"white","gridSize":0,"minRotation":-0.7853981633974483,"maxRotation":0.7853981633974483,"shuffle":true,"rotateRatio":0.4,"shape":"circle","ellipticity":0.65,"figBase64":null,"hover":null},"evals":[],"jsHooks":{"render":[{"code":"function(el,x){\n                        console.log(123);\n                        if(!iii){\n                          window.location.reload();\n                          iii = False;\n\n                        }\n  }","data":null}]}}</script>
```
## Word Cloud for Evaluation Wishes {#word-cloud-for-evaluation-wishes}

This code generates a word cloud visualization for evaluation wishes, highlighting the most frequently used words.

``` r
evaluation_wishes_filtered_cloud <- evaluation_wishes_filtered %>% # nolint
  count(`Wishes (tokenized)`, sort = TRUE)

wordcloud2(evaluation_wishes_filtered_cloud, size = .5)
```

::: {#htmlwidget-adedf404a0879131efe6 .wordcloud2 .html-widget .html-fill-item-overflow-hidden .html-fill-item style="width:576px;height:384px;"}
:::

```{=html}
<script type="application/json" data-for="htmlwidget-adedf404a0879131efe6">{"x":{"word":["slides","concepts","class","labs","learning","lecturer","notes","physical","quizzes","recommend","understanding","cats","classes","explanation","recommendation","teaching","understand","videos","assignments","complex","content","enjoying","explain","improve","interactive","lecture","louder","motivation","online","practical","quiz","read","reduce","review","short","speak","stuck","students","unit","watch","activities","algorithm","allowed","amount","applied","assess","assistance","audibly","based","choices","clarification","colours","comment","compete","complaints","complete","concept","coursework","cover","cumbersome","delivered","descouraged","develop","devide","diagrams","difficult","discouraging","disscussions","easier","efficient","elabotration","emphasis","encourage","engagement","engaging","enhance","evaluation","exam","examples","experience","extremely","fast","fewer","fine","flexibility","flows","flying","follow","formed","giving","hard","illustrations","include","incorporate","increased","involvement","kindly","lengthy","lessons","limit","lively","makes","managable","manuals","material","materials","mentally","mode","models","moment","multiple","netflix","nice","operations","optimum","papers","pass","people","perfect","perfectooo","performing","physically","practice","precise","previous","price","process","project","provide","python","questions","quiizzes","quizes","reading","recall","recomendations","recommendable","recommendatios","remember","revision","satisfied","scary","scored","semester","separate","sessions","shorter","simpler","slide","sliders","specifically","start","step","strict","student","submissions","subtopics","summarised","supplementary","task","terms","theory","time","tiresome","topics","tricky","variation","vocal","voice","week","worded","wordy","writing","youtube"],"freq":[10,8,6,5,5,5,4,4,4,4,4,3,3,3,3,3,3,3,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],"fontFamily":"Segoe UI","fontWeight":"bold","color":"random-dark","minSize":0,"weightFactor":9,"backgroundColor":"white","gridSize":0,"minRotation":-0.7853981633974483,"maxRotation":0.7853981633974483,"shuffle":true,"rotateRatio":0.4,"shape":"circle","ellipticity":0.65,"figBase64":null,"hover":null},"evals":[],"jsHooks":{"render":[{"code":"function(el,x){\n                        console.log(123);\n                        if(!iii){\n                          window.location.reload();\n                          iii = False;\n\n                        }\n  }","data":null}]}}</script>
```
# TF-IDF Score {#tf-idf-score}

## TF-IDF Score per Group {#tf-idf-score-per-group}

Calculates and visualizes the TF-IDF (Term Frequency-Inverse Document Frequency) scores for important words in evaluation likes, grouped by class group.

``` r
popular_tfidf_words_likes <- evaluation_wishes_filtered %>% # nolint
  unnest_tokens(word, `Wishes (tokenized)`) %>%
  distinct() %>%
  filter(!word %in% undesirable_words) %>%
  filter(nchar(word) > 3) %>%
  rename(`Wishes (tokenized)` = word) %>%
  select(`Class Group`, `Student's Gender`,
         `Average Course Evaluation Rating`, `Wishes (tokenized)`) %>%
  count(`Class Group`, `Wishes (tokenized)`, sort = TRUE) %>%
  ungroup() %>%
  bind_tf_idf(`Wishes (tokenized)`, `Class Group`, n)

head(popular_tfidf_words_likes)
```

```         
## # A tibble: 6 × 6
##   `Class Group` `Wishes (tokenized)`     n     tf   idf  tf_idf
##   <fct>         <chr>                <int>  <dbl> <dbl>   <dbl>
## 1 C             slides                   8 0.0602 0     0      
## 2 B             class                    4 0.0471 0.405 0.0191 
## 3 C             concepts                 4 0.0301 0     0      
## 4 B             concepts                 3 0.0353 0     0      
## 5 C             learning                 3 0.0226 0     0      
## 6 C             notes                    3 0.0226 0.405 0.00915
```

``` r
top_popular_tfidf_words <- popular_tfidf_words_likes %>%
  arrange(desc(tf_idf)) %>%
  mutate(`Wishes (tokenized)` =
           factor(`Wishes (tokenized)`,
                  levels = rev(unique(`Wishes (tokenized)`)))) %>%
  group_by(`Class Group`) %>%
  slice(seq_len(10)) %>%
  ungroup() %>%
  arrange(`Class Group`, tf_idf) %>%
  mutate(row = row_number())

top_popular_tfidf_words %>%
  ggplot(aes(x = row, tf_idf, fill = `Class Group`)) +
  geom_col(fill = blue_grey_colours_1) +
  blue_grey_theme() +
  labs(x = "Word in Course Evaluation", y = "TF-IDF Score") +
  ggtitle("Important Words using TF-IDF by Chart Level") +
  ggtitle("Most Important Words by TF-IDF Score in Course Evaluation Wishes per 
      Class Group") +
  facet_wrap(~`Class Group`, scales = "free") +
  scale_x_continuous(
                     breaks = top_popular_tfidf_words$row,
                     labels = top_popular_tfidf_words$`Wishes (tokenized)`) +
  coord_flip()
```

![](Lab2b-Submission-Markdown_files/figure-gfm/Tenth%20Code%20Chunck-1.png)<!-- -->

## TF-IDF Score per Gender (Wishes) {#tf-idf-score-per-gender-wishes}

Calculates and visualizes TF-IDF scores for important words in evaluation wishes, grouped by gender.

``` r
popular_tfidf_words_gender_wishes <- evaluation_wishes_filtered %>% # nolint
  unnest_tokens(word, `Wishes (tokenized)`) %>%
  distinct() %>%
  filter(!word %in% undesirable_words) %>%
  filter(nchar(word) > 3) %>%
  rename(`Wishes (tokenized)` = word) %>%
  select(`Class Group`, `Student's Gender`,
         `Average Course Evaluation Rating`, `Wishes (tokenized)`) %>%
  count(`Student's Gender`, `Wishes (tokenized)`, sort = TRUE) %>%
  ungroup() %>%
  bind_tf_idf(`Wishes (tokenized)`, `Student's Gender`, n)

head(popular_tfidf_words_gender_wishes)
```

```         
## # A tibble: 6 × 6
##   `Student's Gender` `Wishes (tokenized)`     n     tf   idf tf_idf
##   <chr>              <chr>                <int>  <dbl> <dbl>  <dbl>
## 1 Male               class                    6 0.0411 0.693 0.0285
## 2 Male               slides                   6 0.0411 0     0     
## 3 Female             concepts                 5 0.0459 0     0     
## 4 Female             slides                   4 0.0367 0     0     
## 5 Female             labs                     3 0.0275 0     0     
## 6 Female             notes                    3 0.0275 0     0
```

``` r
top_popular_tfidf_words <- popular_tfidf_words_gender_wishes %>%
  arrange(desc(tf_idf)) %>%
  mutate(`Wishes (tokenized)` =
           factor(`Wishes (tokenized)`,
                  levels = rev(unique(`Wishes (tokenized)`)))) %>%
  group_by(`Student's Gender`) %>%
  slice(seq_len(10)) %>%
  ungroup() %>%
  arrange(`Student's Gender`, tf_idf) %>%
  mutate(row = row_number())

top_popular_tfidf_words %>%
  ggplot(aes(x = row, tf_idf, fill = `Student's Gender`)) +
  geom_col(fill = blue_grey_colours_1) +
  blue_grey_theme() +
  labs(x = "Word in Course Evaluation", y = "TF-IDF Score") +
  ggtitle("Important Words using TF-IDF by Chart Level") +
  ggtitle("Most Important Words by TF-IDF Score in Course Evaluation Wishes per 
      Class Group") +
  facet_wrap(~`Student's Gender`, scales = "free") +
  scale_x_continuous(
                     breaks = top_popular_tfidf_words$row,
                     labels = top_popular_tfidf_words$`Wishes (tokenized)`) +
  coord_flip()
```

![](Lab2b-Submission-Markdown_files/figure-gfm/Eleventh%20Code%20Chunck-1.png)<!-- -->
