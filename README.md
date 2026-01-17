# Study Case_OmicsLite_Week 3
## Vaccine HIV
### Tools: GEO, GEO2R, R (R/Rstudio), GO (g:profiler), KEGG 
This is a project based learning (PBL) in OmicsLite about exploration explanation from one journal about HIV case in patient DF, DHF and ND
### Notes: DF = Dengue Fever; DHF = Dengue Hemorrhagic Fever; ND: Non-Dengue (normal)

## Step-by-Step GEO / GEO2R
1. Check the journal, we gonna explor (today about HIV Vaccine)
2. Check the access for GEO2R (sometimes few datasets can't be explor the dataset public, so we can't running in the R)
3. After that, check dataset (GSE18090), go to the website GEO2R analysis
4. In GEO2R analysis website, we can filter rows and then naming, DF and DHF as a "Patient" and ND as a "Normal"
5. Check the option analysis in taskbar (in below)
6. Choose the "Options", Usually in deafult have choosed the options. But, apply "Submitter supplied" in category platform (Because NCBI generated maybe there are some changes in datasets) and choose "yes" to apply limma.
<img width="1764" height="541" alt="image" src="https://github.com/user-attachments/assets/031a9105-07a1-46ad-94bb-e399d739c3ff" />
7. Running data ("Reanalyze")
8. then, you can choose better visualizations, such as heatmap plot and Venn diagram, for DEG (Differential Expression Gene)
9. Choose the "Download the table", the output will become "tsv"
10. As a challenge, you can convert the extension data .tsv become .csv, then convert from data in Ms.Excel or you can use SQL database. But in easier way, you can use the ChatGPT, for filtering the upregulated and downregulated 20 sample gene in datasets (with prompt)
11. After getting, the 20 downregulated DEGs and 20 upregulated DEGs, you can copy the "Symbol Gene". In usually, the symbol genes have two or more symbol genes with limiter "//", you can use the ChatGPT with prompt "Please, filtering the symbol "//" in the data 20 DEGs downregulated and upregulated, after that, make the data into vertical"

## Step-by-Step GO (Gene Ontology)
1. Visit the GO (website g:Profiler or DAVID)
2. Insert the list gene after filtering and make vertical data (form ChatGPT)
3. Run the analysis
4. Visit the GO-BP, GO-MP, GO-CC. Find the  "Innate immmune response", "Inflammatory response", "Response to virus", "Apoptotic process" etc.
5. Explor the other analysis to make the conculsion.

## Step-by-Step KEGG Pathway
1. Identification pathway the result from enrichment.
2. Visit the KEGG Mapper (Search organism _Homo sapiens_)
3. Insert the DEGs (one by one), such as at the first insert downregulated DEG then analysis, after that insert upregulated DEG
4. Analysis the output ( “Toll-like receptor signaling pathway – 5 genes hit”, “Cytokine-cytokine receptor interaction – 7 genes hit”, “Apoptosis – 3️ genes hit”), combine with the results from GO.

## Step-by-Step Interpretation
1. Insert the visualization data from GEO2R (R/Rstudio)
2. Insert the lists data, such as GO-BP, GO-MP, GO-CC.
3. Insert the pathway gene data visualization.
4. Make the conclusion wtih the data visualization

You can explor the other datasets, have fun to do the analysis from your data, make the workflow :)
