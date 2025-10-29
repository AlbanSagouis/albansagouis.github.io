---
title: "Saving all available metadata in exif slots"
draft: true
date: 2024-05-26T20:15:30-04:00
categories:
  - blog
tags:
  - photography
  - weekend-project
  - experience
  - R
  - package
image: /assets/images/saving-shot-metadata.png
---

JSON DATA


### The workflow

#### Installation

You can install the development version of nossaflex from
[GitHub][nossaflex_package] with:

``` r
#| eval:false
install.packages("devtools")
devtools::install_github("AlbanSagouis/nossaflex")
```

#### Example

This is a basic example which shows you how to solve a common problem:

``` r
library(nossaflex)
files <- c("Pictures/2024/01 02 Winter in Berlin/DSC_001034",
           "Pictures/2024/01 02 Winter in Berlin/DSC_001035",
           "Pictures/2024/01 02 Winter in Berlin/DSC_001036")
filenames <- reading_nossaflex(path = "path_to_the_filenames.txt") # provided by the `analog` app
renaming_nossaflex(filenames = filenames, files = files)
```

Additionally you may want to safely save the shots metadata inside the
scans:

``` r
metadata <- reading_nossaflex(path = "path_to_the_filenames.txt") |>  # provided by the `analog` app
     parsing_nossaflex()
editing_exif(files, metadata)
```

#### Related work

The package relies heavily on the great
[`exiftoolr`][exiftoolr] package by
@JoshOBrien which itself depends on the great
[`exiftool`][exiftool] software by Phil Harvey.

Finally, [jExifToolGUI][jexiftoolgui] also
offers exif editing and with a Graphical Interface, nice.


[nossaflex_website]:  https://nossaflex.io/the-system
[nossaflex_youtube]:  https://www.youtube.com/@NOSSAFLEX
[nossaflex_package]:  https://github.com/albansagouis/nossaflex
[exiftoolr]:          https://github.com/JoshOBrien/exiftoolr/
[exiftool]:           https://exiftool.org/
[jexiftoolgui]:       https://github.com/hvdwolf/jExifToolGUI
