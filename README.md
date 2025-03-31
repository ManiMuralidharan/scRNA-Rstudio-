This R script performs single-cell RNA sequencing (scRNA-seq) data processing using the Seurat package. It loads 10X Genomics data, creates Seurat objects, calculates mitochondrial and ribosomal percentages, and provides a cell and gene count summary. Here's a step-by-step guide on how to use it:

1. Install Required R Packages:

Open R or RStudio.
Run the following code to install the necessary packages:
Code snippet

install.packages(c("Seurat", "ggplot2", "dplyr", "SingleR", "celldex"))
2. Prepare Your Data:

This script expects your 10X Genomics data to be organized in a specific directory structure.
You should have a main data directory (e.g., "data ScRNA").
Inside the data directory, you should have subdirectories for each sample (e.g., "BP_iso", "BP_PD_1", "BS_iso", "BS_PD_1").
Each sample subdirectory should contain the following files:
barcodes.tsv (or barcodes.tsv.gz)
features.tsv (or features.tsv.gz)
matrix.mtx (or matrix.mtx.gz)
Ensure your data is in this structure.
3. Set the Data Directory:

Manual Setting (For RStudio Testing):
If you're testing the script in RStudio, modify the data_dir variable in the "MANUAL SETTINGS" section to point to your data directory. For example:
Code snippet

data_dir <- "C:/path/to/your/data/ScRNA" # Replace with your actual path
Command-Line Arguments (For Production Use):
If you want to run the script from the command line, you'll provide the data directory as the first argument.
Example of command line usage.
Bash

Rscript your_script_name.R /path/to/your/data/ScRNA 0.8 0.3 0.3
The numbers are optional arguments that are the cluster resolution, min_pct and logfc_threshold.
4. Run the Script:

In RStudio:
Open the R script in RStudio.
Modify the data_dir variable as needed.
Run the script.
From the Command Line:
Open your terminal or command prompt.
Navigate to the directory containing your R script.
Run the command:
Bash

Rscript your_script_name.R /path/to/your/data/ScRNA
Replace your_script_name.R with the actual name of your script and /path/to/your/data/ScRNA with the path to your data directory.
5. Script Execution and Output:

The script will:
Load the required R libraries.
Verify that the data directories and required files exist.
Load the 10X Genomics data for each sample.
Create Seurat objects for each sample.
Calculate mitochondrial and ribosomal percentages.
Rename cells with sample-specific prefixes.
Print a summary of cell and gene counts for each sample.
Save the cell and gene count summary to a CSV file named cell_gene_counts_summary.csv in your data directory.
Stop the script execution, allowing you to review the cell counts.
Review Cell Counts:
Carefully examine the cell and gene count summary printed in the R console.
If the cell counts are too low for any sample, investigate the issue and correct the data.
6. Continue Processing (After Review):

If the cell counts are satisfactory, remove or comment out the stop("✅ Cell counts have been displayed. Review the output before proceeding.") line from the script.
Then run the script again.
The script will continue with the rest of the single cell analysis.
Important Notes:

File Paths: Double-check that all file paths are correct.
Data Structure: Ensure your data is organized as described in step 2.
Error Handling: The script includes error handling to catch common issues. Pay attention to any error messages.
Memory Usage: scRNA-seq data processing can be memory-intensive. Ensure your computer has sufficient RAM.
Customization: You can customize the script by modifying the mitochondrial and ribosomal gene patterns (mt_pattern and rb_pattern) and adding further processing steps.
This guide should help you run the R script successfully.
