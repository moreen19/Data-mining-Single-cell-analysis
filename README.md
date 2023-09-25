# Data-mining-Single-cell-analysis

## Single cell Analysis of human kidney tumours

In this project i do a single cell analysis of human kidney tumor cells using Seurat.

**Preprocessing data**
In this section i considered the quality and type of cells that i would be including in the analysis and also carried out normalization of the data.

for example checking the quality and type of cells
I plotted box plots of the Genes detected/nfeature_RNA and Number of UMIs/nCount_RNA in order to find out if there are any that are below the recommended/desirable minimum values.

![image](https://github.com/moreen19/Data-mining-Single-cell-analysis/assets/97608840/8af83910-81af-46be-806b-342abee84b28)

The histogram below of RNA feature counts also shows that the values are within the desired range.

![image](https://github.com/moreen19/Data-mining-Single-cell-analysis/assets/97608840/be10157a-3f16-4922-ba63-52e17b1d7903)

**Normalizing the data**
I used the LogNormalize function to normalize the data.This allows for accurate comparisons of gene expressions across samples.I preferred to use Lognormalize because i had created a Seurat object and not a singlecellExperiment object and also because Seurat lognormalize calculates highly variable genes and focuses these for future downstream analysis.

**Dimension Reduction and clustering**
NMF was my chosen method for dimension reduction since single cell count data is strictly non negative and thus non negative matrix factorization would be the best method to use.Dimension reduction is done to embed each cell’s high-dimensional expression profile into a low-dimensional representation to facilitate visualization and clustering.

below is a UMAP showing the various cell clusters in the data set.

![image](https://github.com/moreen19/Data-mining-Single-cell-analysis/assets/97608840/eaab30ec-be3e-4857-8c6e-2baefef1373c)

**Visualizing cell maker genes for each cluster**

To indentify cell maker genes for each cluster i chose scran’s FindAllMakers because it finds the gene makers for each cluster compared to all other remaining cells.

I only wanted the positive markers so i set only.pos to TRUE and used the default settings for the logfc.threshold which is used to limit the genes to be tested based on logscale difference between two groups of cells.

![image](https://github.com/moreen19/Data-mining-Single-cell-analysis/assets/97608840/c6dfda61-e1a8-4726-afd1-992257064626)

Another type of plot that might aid in understanding more about the data is a metadataplot.In this case showing the representation of cell_type per factor.

![image](https://github.com/moreen19/Data-mining-Single-cell-analysis/assets/97608840/d12260a5-fa9e-48a1-a727-ae741c8a0d4c)

## Conclusions

The packages available for single cell analysis like Seurat and Singlet do a good job in helping to analyze cells and create visualizations though some are not compatible with all types of data sets for example singleR that has cell references in celldex that are not compatible to all type of data sets.

Though the NMF produced better results it took a while to run and carryout the dimension reduction while PCA was much faster.

From the plots and visualizations i learnt that the different clusters in the cells are not only due to cell type but there are also other factors that some of the cells share in common like for example my data dealt with kidney tissue so all the cells though different are from the same type of tissue.







