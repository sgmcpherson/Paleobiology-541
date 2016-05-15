Lab #13

Problem Set #1 
	1.	> ncol(OrdovicianMatrix)
	[1] 211
	> ncol(SilurianMatrix)
	[1] 423
	The results of 211 and 423 are both measures of gamma biodiversity in the Ordovician and Silurian, 
	respectively.
	2.	> mean(specnumber(OrdovicianMatrix))
		[1] 26.60526
		> mean(specnumber(SilurianMatrix))
		[1] 42.79167
	These average biodiversities are both measures of alpha diversities. 
	3.	> ncol(OrdovicianMatrix)-mean(specnumber(OrdovicianMatrix))
	[1] 184.3947
	> ncol(SilurianMatrix)-mean(specnumber(SilurianMatrix))
	[1] 380.2083
	These results represent the beta biodiversity. 
	4.	Alpha increases by 16.1, beta by 195.9, and gamma by 212; therefore all diversity measures increase through the Ordovician to the Silurian. 
	5.	> AlphaOrdovician<-mean(specnumber(OrdovicianMatrix))/211
		> AlphaOrdovician
		[1] 0.1260913
	> AlphaSilurian<-mean(specnumber(SilurianMatrix))/423
	> AlphaSilurian
	[1] 0.1011623
	> BetaOrdovician<-184.3947/211
	> BetaOrdovician
	[1] 0.8739085
	> BetaSilurian<-380.2083/423
	> BetaSilurian
	[1] 0.8988376
	Both the alpha and beta values still increase throughout the Ordovician and Silurian when measured as 
	percentages.  However, the increases are significantly smaller. The lower Silurian alpha percentage 
	could suggest that it is more cosmopolitan, as opposed to the Ordovician period, because alpha values 
	suggest that genera are more abundant but they’re less widespread.  This does not match what we 
	learned in class.
	6.	Percentages don’t portray the degree of difference between the original values.

Problem Set #2
	1.	> LatePermian <- downloadPBDB("Animalia", StartInterval="Guadalupian", StopInterval="Lopingian")
	> LatePermian <- cleanRank(LatePermian, "genus")
	> LatePermian <- constrainAges(LatePermian, Epochs)
	> LatePermian <- macrostratMatch(LatePermian)
	> PermianMatrix <- presenceMatrix(LatePermian, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> PermianMatrix <- cullMatrix(PermianMatrix, 2, 10)
	> EarlyTriassic <- downloadPBDB("Animalia", StartInterval="Induan", StopInterval="Ladinian")
	> EarlyTriassic <- cleanRank(EarlyTriassic, "genus")
	> EarlyTriassic <- constrainAges(EarlyTriassic, Epochs)
	> EarlyTriassic <- macrostratMatch(EarlyTriassic)
	> TriassicMatrix <- presenceMatrix(EarlyTriassic, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> TriassicMatrix <- cullMatrix(TriassicMatrix, 2, 10)
	> LateCretaceous <- downloadPBDB("Animalia", StartInterval="Santonian", 	
	> StopInterval="Maastrichtian")
	> LateCretaceous <- cleanRank(LateCretaceous, "genus")
	> LateCretaceous <- constrainAges(LateCretaceous, Epochs)
	> LateCretaceous <- macrostratMatch(LateCretaceous)
	> CretaceousMatrix <- presenceMatrix(LateCretaceous, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> CretaceousMatrix <- cullMatrix(CretaceousMatrix, 2, 10)
	> EarlyPaleogene <- downloadPBDB("Animalia", StartInterval="Danian", StopInterval="Lutetian")
	> EarlyPaleogene <- cleanRank(EarlyPaleogene, "genus")
	> EarlyPaleogene <- constrainAges(EarlyPaleogene, Epochs)
	> EarlyPaleogene <- macrostratMatch(EarlyPaleogene)
	> PaleogeneMatrix <- presenceMatrix(EarlyPaleogene, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> PaleogeneMatrix <- cullMatrix(PaleogeneMatrix, 2, 10)
	2.	> mean(specnumber(PermianMatrix))
	[1] 57.63636
	> ncol(PermianMatrix)-mean(specnumber(PermianMatrix))
	[1] 253.3636
	> ncol(PermianMatrix)
	[1] 311
	> mean(specnumber(TriassicMatrix))
	[1] 35.15385
	> ncol(TriassicMatrix)-mean(specnumber(TriassicMatrix))
	[1] 122.8462
	> ncol(TriassicMatrix)
	[1] 158
	> mean(specnumber(CretaceousMatrix))
	[1] 57.96875
	> ncol(CretaceousMatrix)-mean(specnumber(CretaceousMatrix))
	[1] 717.0312
	> ncol(CretaceousMatrix)
	[1] 775
	> mean(specnumber(PaleogeneMatrix))
	[1] 52.85
	> ncol(PaleogeneMatrix)-mean(specnumber(PaleogeneMatrix))
	[1] 978.15
	> ncol(PaleogeneMatrix)
	[1] 1031
	3.	> mean(specnumber(PermianMatrix))/ncol(PermianMatrix)
	[1] 0.1853259
	> 253.3636/ncol(PermianMatrix)
	[1] 0.8146741
	> mean(specnumber(TriassicMatrix))/ncol(TriassicMatrix)
	[1] 0.2224927
	> 122.8462/ncol(TriassicMatrix)
	[1] 0.7775073
	> mean(specnumber(CretaceousMatrix))/ncol(CretaceousMatrix)
	[1] 0.07479839
	> 717.0312/ncol(CretaceousMatrix)
	[1] 0.9252016
	> mean(specnumber(PaleogeneMatrix))/ncol(PaleogeneMatrix)
	[1] 0.05126091
	> 978.15/ncol(PaleogeneMatrix)
	[1] 0.9487391
	4.	Alpha biodiversity decreases after each extinction event when not measured as a percentage. 
	5.	Alpha biodiversity increases until the end of the Permian extinction and then begins to decrease in the Late Cretaceous. 

Problem Set #3
	1.	> LateOrdovician <- downloadPBDB("Animalia", "Sandbian", "Hirnantian")
	> LateOrdovician <- cleanRank(LateOrdovician, "genus")
	> LateOrdovician <- constrainAges(LateOrdovician, Epochs)
	> LateOrdovician <- macrostratMatch(LateOrdovician)
	> OrdovicianMatrix <- abundanceMatrix(LateOrdovician, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> EarlySilurian <- downloadPBDB("Animalia", "Llandovery", "Wenlock")
	> EarlySilurian <- cleanRank(EarlySilurian, "genus")
	> EarlySilurian <- constrainAges(EarlySilurian, Epochs)
	> EarlySilurian <- macrostratMatch(EarlySilurian)
	> SilurianMatrix <- abundanceMatrix(EarlySilurian, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> PermianMatrix <- abundanceMatrix(LatePermian, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> TriassicMatrix <- abundanceMatrix(EarlyTriassic, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> CretaceousMatrix <- abundanceMatrix(LateCretaceous, SampleDefinition="unit_name", 
	TaxonRank="genus")
	> PaleogeneMatrix <- abundanceMatrix(EarlyPaleogene, SampleDefinition="unit_name", 
	TaxonRank="genus")
	2.	> exp(mean(diversity(OrdovicianMatrix, index="shannon")))
	[1] 10.96187
	> exp(diversity(colSums(OrdovicianMatrix), index="shannon"))-exp(mean(diversity(OrdovicianMatrix, 
	index="shannon")))
	[1] 89.55187
	> exp(diversity(colSums(OrdovicianMatrix), index="shannon"))
	[1] 100.5137
	> exp(mean(diversity(SilurianMatrix, index="shannon")))
	[1] 10.89307
	> exp(diversity(colSums(SilurianMatrix), index="shannon"))-exp(mean(diversity(SilurianMatrix, 
	index="shannon")))
	[1] 262.4305
	> exp(diversity(colSums(SilurianMatrix), index="shannon"))
	[1] 273.3235
	> exp(mean(diversity(PermianMatrix, index="shannon")))
	[1] 9.318572
	> exp(diversity(colSums(PermianMatrix), index="shannon"))-exp(mean(diversity(PermianMatrix, 
	index="shannon")))
	[1] 200.7583
	> exp(diversity(colSums(PermianMatrix), index="shannon"))
	[1] 210.0769
	> exp(mean(diversity(TriassicMatrix, index="shannon")))
	[1] 9.198214
	> exp(diversity(colSums(TriassicMatrix), index="shannon"))-exp(mean(diversity(TriassicMatrix, 
	index="shannon")))
	[1] 195.2891
	> exp(diversity(colSums(TriassicMatrix), index="shannon"))
	[1] 204.4873
	> exp(mean(diversity(CretaceousMatrix, index="shannon")))
	[1] 7.69611
	> exp(diversity(colSums(CretaceousMatrix), index="shannon"))-exp(mean(diversity(CretaceousMatrix, 
	index="shannon")))
	[1] 370.605
	> exp(diversity(colSums(CretaceousMatrix), index="shannon"))
	[1] 378.3011
	> exp(mean(diversity(PaleogeneMatrix, index="shannon")))
	[1] 13.97237
	> exp(diversity(colSums(PaleogeneMatrix), index="shannon"))-exp(mean(diversity(PaleogeneMatrix, 	
	index="shannon")))
	[1] 503.1029
	> exp(diversity(colSums(PaleogeneMatrix), index="shannon"))
	[1] 517.0753
	3.	> exp(mean(diversity(OrdovicianMatrix, index="shannon")))/exp(diversity(colSums(OrdovicianMatrix), index="shannon"))
	[1] 0.1090584
	> (exp(diversity(colSums(OrdovicianMatrix), index="shannon"))-
	exp(mean(diversity(OrdovicianMatrix, index="shannon"))))/exp(diversity(colSums(OrdovicianMatrix), 
	index="shannon"))
	[1] 0.8909416
	> exp(mean(diversity(SilurianMatrix, index="shannon")))/exp(diversity(colSums(SilurianMatrix), 
	index="shannon"))
	[1] 0.03985414
	> (exp(diversity(colSums(SilurianMatrix), index="shannon"))-exp(mean(diversity(SilurianMatrix, 
	index="shannon"))))/exp(diversity(colSums(SilurianMatrix), index="shannon"))
	[1] 0.9601459
	> exp(mean(diversity(PermianMatrix, index="shannon")))/exp(diversity(colSums(PermianMatrix), 
	index="shannon"))
	[1] 0.04435791
	> (exp(diversity(colSums(PermianMatrix), index="shannon"))-exp(mean(diversity(PermianMatrix, 
	index="shannon"))))/exp(diversity(colSums(PermianMatrix), index="shannon"))
	[1] 0.9556421
	> exp(mean(diversity(TriassicMatrix, index="shannon")))/exp(diversity(colSums(TriassicMatrix), 
	index="shannon"))
	[1] 0.04498184
	> (exp(diversity(colSums(TriassicMatrix), index="shannon"))-exp(mean(diversity(TriassicMatrix, 
	index="shannon"))))/exp(diversity(colSums(TriassicMatrix), index="shannon"))
	[1] 0.9550182
	> exp(mean(diversity(CretaceousMatrix, index="shannon")))/exp(diversity(colSums(CretaceousMatrix), 
	index="shannon"))
	[1] 0.02034387
	> (exp(diversity(colSums(CretaceousMatrix), index="shannon"))-exp(mean(diversity(CretaceousMatrix, 
	index="shannon"))))/exp(diversity(colSums(CretaceousMatrix), index="shannon"))
	[1] 0.9796561
	> exp(mean(diversity(PaleogeneMatrix, index="shannon")))/exp(diversity(colSums(PaleogeneMatrix), 
	index="shannon"))
	[1] 0.02702192
	> (exp(diversity(colSums(PaleogeneMatrix), index="shannon"))-exp(mean(diversity(PaleogeneMatrix, 
	index="shannon"))))/exp(diversity(colSums(PaleogeneMatrix), index="shannon"))
	[1] 0.9729781
	4.	Alpha diversity decreases after the End Odovician and the End Permian, but increases after the End Cretaceous. 
	5.	Alpha diversity increases after the End Permain and End Cretaceous extinctions, but decreases at the end of the Ordovician. 

Problem Set #3
	1.	As a general rule, it appears that beta diversity appears to neither increase or decrease after mass extinction events. 

