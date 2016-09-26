# Workflow for data analysis (Greg)

Greg's notes on how data moves from collection, to the filesystem, then
through the data analysis process.

**See also:** [[General programming|comp_programming]] page.

## Filesystem

* **`~/data/`** - on its own partition, regularly backed up
  *  **`current/`**  - contains directories, organized by project, storing metadata, initial field/lab measurements (usually in spreadsheet form), reports, papers in progress, etc. Each project directory may also contain a **`data_analysis`** directory storing data analysis functions and scripts, symlinks to the project's **rawdata** directory, and any other processed data needed for data analysis. **THIS DIRECTORY MUST HAVE VERSIONING**
    *  **project_1/**
      * Lab and field spreadsheets...
      * Maps of plot locations, etc
      * Documentation files for dataloggers, etc
      * Papers in progress
      * **data_analysis/**
        * **symlink to ../rawdata/project_1/**
        * **m/**
          * matlab scripts and functions
        * **py/**
          * python scripts and functions
        * **processed_data/**
          * textfiles with (for example) data exported from spreadsheets in parent directory, data from processing scripts, plot locations converted to UTM (from map), etc.
    *  **project_2/**
      * ...
      * **data_analysis/**
        * **symlink to ../rawdata/project_2/**
        * **m/**
        * ...
  * **`*`archive/`*`** - same as above but for projects that are completed/not maintained
    *  **oldproject_1/**
  * **`rawdata`**  - contains directories for each project, typically storing raw data downloads, datalogger files, or data that has been minimally processed from the initial measurements. This data is usually large in size, is suitable for sharing among many projects, or comprises some contextual information not directly measured in the current project (environmental monitoring data for example).
    * **project_1/**
      * textfile1 (long-term climate measurments from a nearby weather station)
      * textfile2 (datalogger .dat file)
    * **project_2/**
      * ...

## General Workflow

This refers to current projects, each of which is stored in a
***data/current/projectname/*** directory.

### Data collected in the field or lab

- In general, this data must be transcribed from field sheets, downloaded from instruments, formatted, etc, and this is most often done using spreadsheets or text files. 
  - Some formatting, editing, or summary creation of textfiles can be done with `[`shell`
`scripts`](procedures:shellscripts)`, `[`procedures:awk`](procedures:awk)`, etc, but be sure to document and save the scripts in the appropriate **projectname/data_analysis/** directory.
- Processed data can be exported as a textfile to the **projectname/data_analysis/processed_data/** directory, or put in the rawdata/ directory (if it fits criteria above).
- Data is then processed and analyzed with python, matlab, or other scripts located in the **projectname/data_analysis/** directory
- This analysis generates outputs(datafiles, figures) that can be stored in **projectname/data_analysis/processed_data/** for further use in analysis, or in the **projectname/** directory, the wiki, or elsewhere for interpretation, publication, etc.`

The generalized workflow looks like this:
-----------------------------------------

 **Field/Lab measurements** => projectname/ => **Process
        to text** => (**QC/data munging** =>)
        projectname/processed\_data/ => **Analysis with
        matlab/python/r (calculation, summary data, plots)** =>
        projectname/processed\_data/ (OR projectname/, papers, wiki,
        reports, etc for finished products)

### Data from elsewhere

- Often this is downloaded as text data (ie, from SNOTEL, etc) in (hopefully) quality-checked form. However some munging may be necessary to trim, format, or otherwise make the data easier to use 
  - Probably use `[`shell`
`scripts`](procedures:shellscripts)`, `[`procedures:awk`](procedures:awk)`, etc, and again, be sure to document and save the scripts in the appropriate **projectname/data_analysis** directory.
- Data can then be directly placed in the **~/data/rawdata/projectname/** directory
- Follow steps 3 & 4, as above.`

The generalized workflow looks like this:
-----------------------------------------

 **Download data** => (**QC/Data munging** =>)
        rawdata/projectname/ => **Analysis with matlab/python/r
        (calculation, summary data, plots)** =>
        /projectname/data\_analysis/processed\_data (OR /projectname/,
        wiki, paper, etc for finished products)

## Coding and version control

### Code pieces

In terms of actual pieces of code, there are generally several types
that recur in each project.

- a loading function
- a data cleaning function
- the function(s) that actually do the analysis (calculating, transforming, selecting data)
- the script(s) that produce reports or plots using the analysis functions above`

In practice, this means that in each data analysis project folder, there
will be (at least) one version of each of these types of functions.
Depending on the language in use and the maturity of the project, there
may be many function files and reporting/plotting scripts. See more
discussion of about these types of issues
[here](http://stackoverflow.com/a/1434424),
[here](http://stackoverflow.com/q/1266279),
[here](http://stackoverflow.com/q/2295389) and
[here](http://stackoverflow.com/q/2295389)

### Versioning

Within each project folder in **data/data\_analysis** there is a
versioning repository (.hg or .git). These repositories are initialized
early in the development of the project and commits are made to the
repository when substantial changes are made to the codebase. For
example, if a new plotting script is written one day, it should be added
and committed to the repository. If a function is changed to use a
different equation or constant, the change should be committed.
Branching is also possible for testing new analyses or generating
publication subsets of the analysis, and these branches can later be
merged into the main, or kept separate. In most cases, data is not
versioned, it is stored in the rawdata directory and changes to that
directory are logged in a README file.

Versioning is currently done with
[mercurial](procedures:mercurial), but
[git](procedures:git) has a page here too.
