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
