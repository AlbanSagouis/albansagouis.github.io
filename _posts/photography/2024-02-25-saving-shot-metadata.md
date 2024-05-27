---
title: "Saving the camera settings of a shot in the exif data of the scans"
date: 2024-02-25T20:15:30-04:00
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

For decades (centuries?) photographers have been writing their camera settings for each shot on a
notebook to learn and train their eye, to organise their shots or because they are data-freaks.
Today, you could still make notes by hand or use a dedicated smartphone app or you could be the
proud owner of a more modern film camera that saves the shot data on a memory card.

Once the film developed, by yourself or a lab, and scanned, by yourself or a lab, the scans you get
do not have the information of the original shots. These data are on paper, on a smartphone or on a memory card.
I downloaded the `Analog` app for my smartphone, because it is free, does not collect user data,
it's lightweight and I loved the design, and I began saving the settings for each shot. Data was accumulating
but I was not seeing how to get it out yet.

A digital camera would take the picture and save the settings inside the `jpg` or `tiff` files
in exif data. I want the same thing for my scans!

And how to get these data in the exif fields of the scans? Well surprisingly, it's not as straightforward as
you (I) would expect. At first I did not find anything satisfying and discussing with the developers behind
`Analog` made it clear that it was not a straightforward task for them either. We talked about workflow.

The team were encouraging amateur and professional photographers to rename their
files, well their scans, following this convention to save the settings of
each shot. Then they developed `Analog` which of course allows users to save Shutter speed,
Aperture, the lens' focal length and exposure correction. At the end of the
roll, the data is extracted and the user receives a list of name files by email:

> Test roll_NO01_SS50_A2.8_FL50_EX0
> Test roll_NO02_SS50_A2.8_FL50_EX0
> Test roll_NO03_SS125_A4_FL50_EX0
> Test roll_NO04_SS125_A4_FL50_EX0

They hand-rename the scans or use a renaming software. OK.
but this does not go _inside_ the files, a file name is not an ideal way
of storing data even when using the standardised convention they created:
NOSSAFLEX

> It’s as easy as the name – NOSSAFLEX has all of the information in the
> title.
>
> NO = Number  
> SS = Shutter Speed  
> A = Aperture  
> FL = Focal Length  
> EX = Exposure

I could not find a way to automatically save the data on my phone to the exif slots of my scans...

So I decided to create an R package to do it! An exciting weekend project and certainly
an article for the blog!

Since I was already using the `Analog` app, I had to follow its data structure.

### Here is the README of my package

This package relies on a file naming convention for, essentially analog,
photography. Photographs taken on film, then developed, then scanned are lacking
important metadata or if they have, it's from the scanning device, not the
original camera.
The nossaflex package takes NOSSAFLEX structured file names
and can 1) batch rename corresponding pictures and 2) edit their exif data
to add information such as focal length, shutter speed, aperture.
This allow a photographer to take notes on the `Analog` app while shooting
pictures, export nossaflex compatible file names and use R to rename scans
and edit their exif metadata with corresponding shot information.

The nossaflex package is the entry of the NOSSAFLEX file naming
convention into the R universe to help scientific, professional or
amateur photographers to name their picture files consistently and
informatively.

When taking a picture with an analog camera, data such as aperture,
shutter speed or focal length are not automatically saved the way they
are in a digital camera. Many photographers write down these precious
metadata in a notebook, we want to help them improve their workflow and
data quality.

#### What is NOSSAFLEX?

Here is an explanation from the creators:

> It’s as easy as the name – NOSSAFLEX has all of the information in the
> title.
>
> NO = Number  
> SS = Shutter Speed  
> A = Aperture  
> FL = Focal Length  
> EX = Exposure

NOSSAFLEX file names looks like this: `NO03_SS250_A8_FL80_EX0.jpg` or
this: `NO34_SS30_A2.8_FL35_EX+1.tiff`!

Learn more on their \[website\]{<https://nossaflex.io/the-system>} or on
their \[Youtube channel\]{<https://www.youtube.com/@NOSSAFLEX>}.

#### The package

Here are the two main functions in the package:

- `renaming_nossaflex` batch-renames picture files from uninformative
  `DSC_00345.jpg` to information-rich NOSSAFLEX name based on data
  provided by the user, see {analog} section:
  `NO03_SS250_A8_FL80_EX0.jpg`.
- `editing_exif` batch-saves the metadata of the pictures into the exif
  slots of the scan files (jpg, tiff, etc).

#### Analog or an other app

#### The workflow

#### Installation

You can install the development version of nossaflex from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
# devtools::install_github("AlbanSagouis/nossaflex")
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
`exiftoolr`{<https://github.com/JoshOBrien/exiftoolr/>} package by
@JoshOBrien which itself depends on the great
`exiftool`{<https://exiftool.org/>} software by Phil Harvey.  
Finally, jExifToolGUI{<https://github.com/hvdwolf/jExifToolGUI>} also
offers exif editing and with a Graphical Interface, nice.
