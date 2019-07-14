---
title: "Coding Standards"
# author: 'Ernestynne Walsh'
# date: '2019'
knit: (function(inputFile, encoding) { 
      out_dir <- "output";
      rmarkdown::render(inputFile,
                        encoding=encoding, 
                        output_file=file.path("..", out_dir, "coding-standards.html")) })
output:
  html_document:
    css: ../assets/nc.css
    keep_md: yes
    self_contained: yes
    toc: true
    toc_float: 
      collapsed: false
  
---


---

<!--img src="logo.svg" style="position:absolute;top:0px;right:0px;" /-->



## Coding Standards

This is the set of standards that Nicholson Consulting work should follow to create consistent and easy to maintain code. Most of our work is done in R so the coding standards provide more examples to reflect that.

### Style Guides
This is a well documented area already. For R we follow the [tidyverse](https://style.tidyverse.org/) style guide. 

Use the `formatR`to tidy up some of the [aesthetics](https://yihui.name/formatR) of your code

```r
library(lintr)

#tidy up a whole directory
formatR::tidy_dir(getwd())
```

The `lintr` package to confirm that you conform to the tidyverse standards.


```r
library(lintr)
lint("file.R")
```

For C\# we use [Microsoft's coding conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)

For PHP we use the [PRS-2 Coding Style Guideline](https://www.php-fig.org/psr/psr-2/)

All other languages we use follow [Google Style Guides](http://google.github.io/styleguide/)

### Good Coding Standards
Often data science teams are working on the deliver quickly vs deliver something that is maintainable dilemma. Delivering something that is maintainable allows you to work more quickly in the future because you can recycle work and the code is written in such a way that it is easy to troubleshoot if something breaks down the track.

Our standards are made to align with our SDLC. Code that is written by Nicholson Consulting is:

* modular and can be reused again
* is version controlled
* well documented
* has been tested
* and is efficiently written

More about how this is achieved is detailed below.

### Version Control
All code should be versioned. Nicholson Consulting has its own [GitHub](https://github.com/nicholson-consulting) account. All repositories should be private to begin with and once written permission is obtained from the Technical Lead and the client they can be made public.

We created the Social Investment Agency [Version Control Standards](https://nz-social-investment-agency.github.io/sia_analytical_processes/output/git_version_control.html) so this is a great place to learn more about Git and version control.

We can also arrange specific training through Catalyst IT if you need it. Contact our People Experience Lead

In some situations the client may have their own version control system which we will use. Depending on the who owns the IP we may also sign the final version out and place it in a **private repository** with permission of the client.

### Documentation
This is also covered in many style guides but given the importance of reusable and maintainable code it warrants its own section

#### In Repository Documentation
All our GitHub repos should have a `README.md` file in the top level. This is the first place a person will go looking for instructions on what the repository should do. It should include as a minimum:

* The purpose of the repository
* Installation instructions including any dependencies (if applicable)
* Authors
* The license (GNU GPLv3 for code and CC-BY-SA for content by default with MIT and CC-BY respectively in some special cases). Talk to the Technical Lead if you are unsure which license you should apply
* Acknowledgements

An example of the README for this repo can be found [here](https://github.com/nicholson-consulting/coding-standards/blob/master/README.md).

#### In Code Documentation
##### Headers
Headers should contain some basic information An example is shown below


```r
#################################################################################
# DESCRIPTION: Examples of how to write R code that runs on CAS
#
# INPUT: NA
#
# OUTPUT: NA
#
# AUTHOR: EW
#
# DEPENDENCIES: 
# swat package must be installed
# authinfo file must contain credentials to connect to the server
# D:\Workshop\HOW\data\cas_crash.csv must exist
#
# NOTES:
# code is versioned and publicly available so the credentials have been ommited
# you will need to specify the server name and port number prior to running this
#
# HISTORY:
# 13 Apr 2019 EW updated after testing on image
# 12 Feb 2019 EW v1
#################################################################################
```

Ideally, this example should have Roxygen comments in it. More info below.

##### Roxygen
Use Roxygen to automatically generate the documentation. An example of Roxygen comments is shown below. 


```r
#' Nicholson Consulting brand fill colours
#'
#' This is a function for adding fill to ggplot that aligns with NC brand colours kikorangi (blue scale), kowhai (yellow scale), kiwkiwi (gray scale),
#' makiwikiwi (light gray scale) or whero (red scale)
#' @keywords plot ggplot fill 
#' @usage 
#' nc.plot.fill.core()
#' nc.plot.fill.kikorangi()
#' nc.plot.fill.kowhai()
#' nc.plot.fill.kiwikiwi()
#' nc.plot.fill.makiwkikiwi()
#' nc.plot.fill.whero()
#' @export
#' @examples
#' library(ggplot2)
#' library(ncrpackage)
#'
#' ggplot(mtcars, aes(mpg, wt, colour = as.factor(cyl))) +
#' geom_point() +
#' ggtitle("Fuel economy data)") +
#' nc.plot.theme() +
#' nc.plot.fill.core()
```
The `*.Rd`, and `NAMESPACE` files can then be built using `devtools::document()` or `roxygen2::roxygenize()`

For more informaton on how to use Roxygen see [here](http://r-pkgs.had.co.nz/man.html) 

##### Comments
Comments in the code should be information and explain why you are doing something not what you are doing. 

Large sections can be sectioned off by using a series of \# symbols


```r
#################################################################################
# New section
#################################################################################
```


### Testing
*Coming Soon*

### Package Creation
*Coming Soon*

### Performance
*Coming Soon*





