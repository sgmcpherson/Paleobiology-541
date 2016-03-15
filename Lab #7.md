Lab #7 

Problem Set #1

	1.	max_ma: returns only records whose temporal locality is at least ____ years old, in Ma
	min_ma: returns only records whose temporal locality is at most ____ years old, in Ma

	2.	> tapply(DataPBDB[,"max_ma"],DataPBDB[,"genus"],max)
                	

	3.	>tapply(DataPBDB[,”min_ma”],DataPBDB[,“genus”],min)

	4.	> MaxOccur<-sort(table(DataPBDB[,"genus"]))
	> dim(MaxOccur)
	[1] 1018
	> MaxOccur[1018]
	Anadara 
   		1916 

	5.	> Anadara<-subset(DataPBDB,genus="Anadara")
		> max(Anadara[,"max_ma"])
		[1] 66
		> min(Anadara[,"min_ma"])
		[1] 0

Problem Set #2

	1.	mean(sample(Lucina[,“paleolng”]),replace=TRUE))
	
	Taking the mean of the sample “paleolng” from the column Lucina, where via replace=TRUE, numbers 
	can be repeated more than once

	2.	plot(density(ResampledMeans))
	
	Yes, the graph looks approximately Gaussian; the mean is relatively in the middle and the distribution is 
	pretty symmetrical. 

	3.	> mean(ResampledMeans)
		[1] 24.16227
		> OriginalMean
		[1] 24.1997

	Yes, the means are similar.

	4.	sort(ResampledMeans,decreasing=FALSE)

	5.	> quantile(sort(ResampledMeans),c(0.025,0.975))
    	2.5%    97.5% 
	21.82094 26.28630 

	6.	This means that 95% of the data falls within the 2.5 and 97.5 percentiles. 

Problem Set #3

	1.	Given the values, it is likely that Lucina is still alive because the estimated extinction is between the present and the future. 

	2.	> estimateExtinction(Dallarca[,"min_ma"],0.95)
		Earliest   Latest 
 		2.58800 -3.88749 

	3.	Since the Pliocene Epoch ended approximately 2.58 Ma, it is possible that Dallarca is still extant because this time interval falls within this range. 
 
	4.	I believe that we should trust the pure reading of the fossil record because the dating for the estimated extinction of Dallarca lines up with the end of the Pliocene period and no earlier fossils have been found; practically speaking, based on levels of deposition and stratigraphy, younger fossils should be relatively easier to find.

Problem Set #4

	1.	It is unlikely that fossil specimens would be equally, randomly distributed throughout stratigraphical layers.

	2.	It is also unlikely that fossil specimens would be randomly distributed throughout all geographical areas.  For example, certain specimens cannot tolerate extreme environments, therefore the likelihood of them being located in such an area would be low.

Problem Set #5

	1.	> dim(DataPBDB)
		[1] 67618    26
		> dim(ExtantData)
		[1] 59097    26

	67,618-59,097=8,521

	2.	> length(unique(DataPBDB[,"genus"]))
		[1] 1018
		> length(unique(ExtantData[,"genus"]))
		[1] 532

	532/1018=0.522933 -> 52.3% extant today

	3.	> tapply(ExtantData[,"max_ma"],ExtantData[,"genus"],max)

	> tapply(ExtantData[,"min_ma"],ExtantData[,"genus"],min)

	4.	tapply(ExtanctData[,“min_ma”],ExtantData[,“genus”],min)!=0

	5.	> Scrobicularia<-subset(DataPBDB,DataPBDB[,"genus"]=="Scrobicularia")
		> estimateExtinction(Scrobicularia[,"min_ma"],0.95)
 		Earliest    Latest 
  		0.01170 -34.70966

	> Meiocardia<-subset(DataPBDB,DataPBDB[,"genus"]=="Meiocardia")
	> estimateExtinction(Meiocardia[,"min_ma"],0.95)
 	Earliest    Latest 
 	0.011700 -5.329574 

	> Dimya<-subset(DataPBDB,DataPBDB[,"genus"]=="Dimya")
	> estimateExtinction(Dimya[,"min_ma"],0.95)
 	Earliest    Latest 
 	0.781000 -2.054688 

	> Digitaria<-subset(DataPBDB,DataPBDB[,"genus"]=="Digitaria")
	> estimateExtinction(Digitaria[,"min_ma"],0.95)
 	Earliest    Latest 
 	0.781000 -3.761154 

	> Cuspidaria<-subset(DataPBDB,DataPBDB[,"genus"]=="Cuspidaria")
	> estimateExtinction(Cuspidaria[,"min_ma"],0.95)
	 Earliest    Latest 
	2.5880000 0.7771965

	> Arctica<-subset(DataPBDB,DataPBDB[,"genus"]=="Arctica")
	> estimateExtinction(Arctica[,"min_ma"],0.95)
 	Earliest    Latest 
 	0.011700 -1.799104 

	> Aloides<-subset(DataPBDB,DataPBDB[,"genus"]=="Aloides")
	> estimateExtinction(Aloides[,"min_ma"],0.95)
	Earliest   Latest 
   	5.333     -Inf 

	> Kurtiella<-subset(DataPBDB,DataPBDB[,"genus"]=="Kurtiella")
	> estimateExtinction(Kurtiella[,"min_ma"],0.95)
 	Earliest    Latest 
 	 0.01170 -34.70966 

	> Gouldia<-subset(DataPBDB,DataPBDB[,"genus"]=="Gouldia")
	> estimateExtinction(Gouldia[,"min_ma"],0.95)
	Earliest    Latest 
	 0.011700 -2.047386 

	> Acrosterigma<-subset(DataPBDB,DataPBDB[,"genus"]=="Acrosterigma")
	> estimateExtinction(Acrosterigma[,"min_ma"],0.95)
 	Earliest    Latest 
 	0.011700 -3.481128 
	
	Given the data, only Cuspidaria is extinct while it is possible that the rest could still be alive 	today; therefore, 90% may be extant. 


