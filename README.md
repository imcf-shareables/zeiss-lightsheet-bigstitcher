[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8019805.svg)](https://doi.org/10.5281/zenodo.8019805)

# zeiss-lightsheet-bigstitcher

## Description

This script allows to do the whole pipeline for processing and fusing tiled CZI
files coming from a Zeiss LightSheet 7 microscope.

## Requirements

The script is made in Python and requires
[Fiji](https://doi.org/10.1038/nmeth.2019) to be ran. On top of this, it
requires a specific version of the multiview-reconstruction plugin in order to
fix the LS7 reader. This has now been integrated in more recent version of the
plugin but the script hasn't yet been updated to reflect these changes.

Once activated, just drag and drop the script in the main Fiji window and click
on the RUN button.

As Fiji is operating system independant, this can be run on Windows, Mac and
Linux. No specific hardware is necessary and script should take a couple of
minutes to finish.

## Run script

### Input

The script requires the path to the first CZI produced by the microscope. A
couple of options are then available:

* reader to use: This is necessary with the modified JAR as the LS7 reader had
  to be revert engineered to work due to some metadata changes after the
  microscope upgrade
* best illumination side: See documentation
  [here](https://imagej.net/plugins/bigstitcher/select-illumination).
* fuse images: The fusion step takes a while so we added this as an optional
  step
* convert to IMS5: This only works if you have Imaris installed in `C:\Program
  Files\Bitplane`
* delete intermediate files: If activated, will only keep on disk the H5/XML and
  the IMS file, preferred unticked
* send email: Will only work inside the University of Basel network but could be
  adapted to your need

### Runtime

The script will then go through the different steps of the pipeline:

* dataset definition: needed to establish all the info about the dataset
* conversion to H5/XML: needed to speed up processing
* pairwise shift calculation: align the tiles, timepoints and illuminations
* fusion: if your images are small, will export as tiff otherwise as a new fused
  H5/XML

### Output

The script will save the resulting files next to the CZI and intermediate files
in subfolders. A .txt file will also be saved with the log of the whole
pipeline.
