# Replication Package 
This is where you can find code and data to replicate the main figures and tables in the paper "What We Teach About Race and Gender: Representation in Images and Text of Children's Books" which is published in the Quarterly Journal of Economics.

## Requirements
You will need to download both R and RStudio to run these scripts. We use R version 4.3.0 (2023-04-21) and RStudio version 2023.03.0+386.  
The script `code\requirements.txt` contains information on all the `.R` packages (and which versions) we use for this analysis. These packages will automatically be loaded in the beginning of each script which outputs a table or figure. Please open this script and make sure all the listed packages are installed before running any code. 

## Code 
This folder contains the code we use to make each main figure and table (with the exception of Figure II which was made using a graphics editor).
In particular, this folder contains:
  - One `.R` script for each figure and table. For example:
    - `figure_I.R` outputs three `.png` files: `figure_I_a.png`, `figure_I_b.png`, and `figure_I_c.png`
    - `table_I.R` outputs one `.txt` file: `table_I.txt`
  - `graph_themes.R` contains code which sets the ggplot theme and customizes colors, shapes, etc for the figures in our paper. This script will automatically run at the beginning of any script that outputs a figure.
  - `requirements.txt` contains code to load the required packages. This script will automatically run at the beginning of any script that outputs a figure or table.
  - `run_all_scripts.R` will run all the scripts and output all figures and tables.

## Data
We do not store the data on github. You can download the data here.
The specific files you will need include:
  - `book_purchase_data.Rdata`
  - `cces_data.Rdata`
  - `census_data.Rdata`
  - `library_data.Rdata`
  - `representation_data.Rdata`
  - `search_interest_data.Rdata`  
The data should also contain a folder called `supplemental` which contains the `.png` files that we use as background gradient in figures 4a, 5a, 5b, and 5c.  
There is also one censored file (`censored_data/book_purchase_level_data.Rdata`) that we were not allowed to share which contains data on children's book purchases and purchaser demographics. 
We use these data to construct table II, table III, table Vb, table VI, and figure Ib. More information on the variables contained in this data can be found in the data folder.
