---
title: "APMD can now read JSON exports too"
date: 2024-05-26T20:15:30-04:00
categories:
  - photography
  - weekend-project
  - experience
  - R
  - package
image: /assets/images/saving-shot-metadata.png
---

A quick follow-up to [saving the camera settings of a shot in the exif data
of the scans][previous-post].

That post covered the original `Analog` workflow: the app hands you a list
of NOSSAFLEX-encoded filenames, you rename your scans to match, and `APMD`
reads the shutter speed, aperture, focal length and exposure straight out of
the filenames before writing them to exif.

Since then I picked up a couple more logging apps, and neither of them
exports a NOSSAFLEX filename list — they export a JSON file instead, one
record per shot. So `APMD` needed a second way in: `parsing_json()` reads
that JSON directly and extracts the same metadata, no renaming step
required.

``` r
metadata <- parsing_json(path = "path_to_the_export.json") # exported by the `Analog` app
editing_exif(files, metadata)
```

Same result as before, one step shorter. If you're on `Frames`, there's a
matching `parsing_frames()` for its own JSON export.

Same install, same [`exiftoolr`][exiftoolr]/[`exiftool`][exiftool] underneath
— see the [previous post][previous-post] for the full setup.

[previous-post]: /posts/photography/2024-02-25-saving-shot-metadata/
[exiftoolr]:          https://github.com/JoshOBrien/exiftoolr/
[exiftool]:           https://exiftool.org/
