# 2024-spa-summary

This repository contains code and data required to render summary documents (in both `.html` and `.pdf` formats) of South Pacific albacore (SPA) catch within the Western and Central Pacific Fisheries Commission ([WCPFC](https://www.wcpfc.int/)) convention area. Catch summaries are provided for all participating Members, Participating Territories and Cooperating Non-Members (CCMs) with longline and troll catch of SPA per the most recent [WCPFC Yearbook data](https://www.wcpfc.int/statistical-bulletins). Catch summaries are placed in the context of a proposed Conservation and Management Measure (CMM) on a management procedure (MP) for SPA ([public proposal](https://meetings.wcpfc.int/node/24363)). 

Note that the data set used, [`YB_data_2023/XLS_SouthWCPFC.csv`](https://www.wcpfc.int/doc/annual-catch-estimates-2022-data-files), is the 2023 version of the [WCPFC Tuna Fishery Yearbook - Annual Catch Estimates](https://www.wcpfc.int/statistical-bulletins). The file `YB_data_2023/spa-ll-eez.csv` contains data transcribed from [SC20-SA-IP-07](https://meetings.wcpfc.int/node/23046) Table 6, and the file `YB_data_2023/ccm-dat.csv` containing CCM abbreviations was created for this repository.

Only the `.qmd` file needs to be edited in order to make changes to the summary documents.

## Set-up R environment

Users should [clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) this repository on their local machine.

### Using base R

Users should open up an R terminal ([version 4.4.0](https://cloud.r-project.org/)) and change the working directory to the directory that they cloned the repository into:
```
setwd("path/to/2024-spa-summary/")
```
Next they should source the [`.Rprofile`](https://github.com/N-DucharmeBarth-NOAA/2024-spa-summary/blob/main/.Rprofile):
```
source(".Rprofile")
```
This should prompt the `renv` package to bootstrap itself. [`renv`](https://rstudio.github.io/renv/index.html) is used for R package management to ensure a consistent work environment is set-up by recording package version information in a lock-file, [`renv.lock`](https://github.com/N-DucharmeBarth-NOAA/2024-spa-summary/blob/main/renv.lock). Follow the in terminal prompts to install all packages. This should take a few minutes as there are a number of packages to load. If `renv` does not bootstrap automatically then run:
```
renv::restore()
```

### Using an integrated development environment (IDE)

Users using an integrated development environment (IDE) such as [Visual Studio Code](https://code.visualstudio.com/download) can configure set-up with R version 4.4.0 (set-up instructions [here](https://github.com/REditorSupport/vscode-R)). In order to configure Visual Studio Code to work with `renv` the user should follow the configuration steps located [here](https://github.com/REditorSupport/vscode-R/wiki/Working-with-renv-enabled-projects). Once Visual Studio Code has been configured properly, open the `2024-WCPFC21-analysis` folder using Visual Studio Code. [Opening an R terminal](https://code.visualstudio.com/docs/languages/r#_running-r-code) should prompt the `renv` package to bootstrap itself as described above. If `renv` does not bootstrap automatically then run:

```
renv::restore()
```
If using an alternative IDE such as [Rstudio](https://posit.co/download/rstudio-desktop/) the R environment set-up will be very similar to the process described for Visual Studio Code.

## Rendering

The `wcpfc-ca-spa-catch-summaries.html` and `wcpfc-ca-spa-catch-summaries.pdf` summary files are produced by rendering the `wcpfc-ca-spa-catch-summaries.qmd` file using [Quarto](https://quarto.org/docs/get-started/). In this case, [Quarto version 1.6.37](https://quarto.org/docs/download/) was used.

Open a terminal window in the project directory to render the Quarto document (`.qmd` file), from the command line using:

```
quarto render wcpfc-ca-spa-catch-summaries.qmd
```

This *should* work without error. If not, it is possible that a [TinyTeX](https://yihui.org/tinytex/) distribution may need to be installed and this can be done using [R](https://yihui.org/tinytex/#for-r-users) via the [tinytex](https://yihui.org/tinytex/r/) package. 

## Github Disclaimer

This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an ‘as is’ basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.
