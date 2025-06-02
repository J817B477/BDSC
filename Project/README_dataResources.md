### source_data (data downloaded, untarred, unzipped in notebook or using web interface )
1. `betaValue_txtFiles`
    * folder containing all of the beta_value files that can be downloaded from each NCBI GEO sample (GSM) page, accessed from the [GSE146917](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE146917) page.
    * all files represent a single sample which were concatenated into a dataframe stored as `output_txtFiles/betaValue_txtFiles.csv`
    * generated with `betaValue_matrixBuild.ipynb`

1. `GEO_sample_metadata.csv`
    * contains sample level metadata for `GSE146917`
    * important attributes include:
        * "averageage:ch1"
        * "averagebodymassindex:ch1"
        * "dnamage:ch1"
        * "huntingtondiseasestatus:ch1"
        * "sentrix.id:ch1"
        * (might not be fully updated exhaustive list)
    * generated with `GEO_SampleMeta_build_R.ipynb`

1. `GPL13534-11288_platformManifest.txt`
    * contains metadata specifically for the Illumina HumanMethylation450 BeadChip array design (ie., the physical/functional beadchip)
    * in addition to other relevant information, includes associated genes for each CpG site
    * this manifest was collected to map methylation metadata to the numeric matrix contained in the `beta_values.csv`, facilitating analyses like differential methylation studies and in our case methylation clustering analysis
    * the data merger was carried out with `betaValue_matrixBuild.ipynb` 

1. `GSE146917_RAW.tar`
    * includes a large set of archived files curated by or produced from the study
    * can be unpacked so that the individual files within it can be extracted and uncompressed
    * `StudyAugmented_platformManifest.csv`formerly known as `methylation.csv` was extracted from it

1. `StudyAugmented_platformManifest.csv`
    * is a very poorly formatted csv including manifest data as well as unarticulated computational analysis data
    * it can't be read into a program as is but can be opened in excel and parts can be extracted via copy/paste

### Output Data (data built by notebooks)
1. `beta_values.csv`
    * provides [noob-normalized](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-014-0503-2#:~:text=We%20have%20found%20(see%20below,to%20a%20specific%20statistical%20model.)) beta_values that reflect overall intensity measures for CpG sites
    * was the original output of `betaValue_matrix_build`
    * was used to create `meta_beta_values.csv`

1. `meta_beta_values.csv`
    * adds metadata to the df from `beta_values.csv`
    * purpose is to use matadata attributes to filter out non-ideal CpG site objects to support clustering
    

    

