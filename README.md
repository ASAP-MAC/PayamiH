# 01-31-2025

This major rebumping of the reports includes the following changes:
	
	* Added "Future directions" chapter to reports for all 3 datasets

	* Added `stool_travel_time` as covariate only to NGRC and UAB, to account for
	  the time these samples have been in room temperature

After these modifications, I was asked to analyses of approach 1 with `CLR` transformed traits. 
To do that, I will branch the repository.

This note is specific to the CLR branch.
I apply CLR to data at the **Q1** stage. However, Q2 and Q3 further subset data, which could 
prove problematic? we should discuss.

# 01-27-2025

After multiple iterations, we are now going for the following 3 research questions:

	* Q1 - Is there interaction between SNP variant dosage and PD status (case or control) on cluster abundance?
	
	* Q2 - is SNP VAF associated with cluster abundance in PD?

	* Q3 - is SNP VAF associated with cluster abundance in Controls?

These questions are addressed in all 3 datasets and results are stored in project1_microGenPD/output_{DoD,NGRC,UAB}/Q...

Files in there are numbered as 1: interaction model, 2: linDA regression, 3: gene set enrichment analysis.	

# 12-13-2024

We found interesting $PD \times genetics$ signals in PD and healthy people with the DoD dadaset, but also stumbled upon samples unexpectedly missing. We will first concentrate on reconciling these missing data
And then re-running our analyses. 

Additionally, I renamed Wallen data to DoD as named in the group. 

# 11-15-2024

After new discussions with Haydeh, we agreed on an analysis strategy to first look at the top markers that she has selected for the disease in the MedRxiv pre-print, following the Nature Communications publication in 2022. 
The strategy is to:
	
	- remove participants that had stool collected with swabs
	- Group abundances of bacteria for each cluster
	- sum their abundances
	- transform abundances
	- take genetic variants found associated with PD in HLA and SNCA (19 in Wallen)
	- Test additive effect using Dosages
	- Adjust p-values by number of variants and bacteria tested (Bonferroni)

The model should look like the following (one per bacterial cluster and per variant)

$$
cluster_x \sim Age + scaled(seq.Depth) + PD \times variant_i
$$

Then we extract the effect of variants on bacterial clusters, and that will be regardless of the disease.

Sensitivity analysis may include repeating the same analysis on healthy controls with the following model

$$
cluster \sim Age + scaled(seq.Depth) + variant_i
$$

# 11-01-2024

We outlined the first project, aimed at building on the results by Zachary Wallen in the [Nat.Comm. 2022](https://doi.org/10.1038/s41467-022-34667-x).
The first analysis is to **take the taxa that were mostly associated with PD and test their association with variants most strongly associated with PD as found in the GWAS catalog**. At a later stage, we should discuss potentially different trends in PD separately from health controls.
