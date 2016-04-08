# Lab #6

> well done! 18/20

## Problem Set #1

	1.	> dim(DataPBDB)-dim(MacroPBDB)
	[1] 25153    13

	2.	Given that Macrostrat’s coverage is currently limited to only North America, occurrences outside of this continent is not counted, resulting in the lost data. 

## Problem Set #2

	1.	
	> OrderRichness<-specnumber(OrderMatrix)
	> sortOrderRichness<-sort(OrderRichness)
	> CandidateUnits<-names(tail(sortOrderRichness,n=10))
	> CandidateUnits
 		[1] "Forteau Fm"       "Parker Slate"     "Snowy Range Fm"  
 		[4] "Weymouth Fm"      "Langston Fm"      "Wheeler Shale"   
 		[7] "Marjum Limestone" "Stephen Fm"       "Kinzers Fm"      
		[10] "Chancellor"   

	2.	> GenusFrequencies<-apply(GenusMatrix,2,sum)
	3.	> GenusFrequenciesBarplot<-table(GenusFrequencies)
		> barplot(GenusFrequenciesBarplot)
	4.	hollow curve
	5.	> RareGenera<-which(GenusFrequencies<=2)
		> RareGenera<-GenusFrequencies[RareGenera]

## Problem Set #3

	1.	
		> CandidateMatrix<-GenusMatrix[c(CandidateUnits),]
		> PercentShared
    	 	 Forteau Fm     Parker Slate   Snowy Range Fm      Weymouth Fm 
      	 	0.5652174        0.2812500        0.1951220        0.6764706 
    	 	Langston Fm    Wheeler Shale Marjum Limestone       Stephen Fm 
     	  	0.1632653        0.2307692        0.3559322        0.3055556 
    	  	Kinzers Fm       Chancellor 
    	   	0.2586207        0.5714286 

	2.	Based off of this data, I believe that Forteau Fm, Wymouth Fm, Majum Limestone and Chancellor are the most likely to qualify for Lagerstatten because they contain the highest percentages of rare genera. 

	3.	The Marjum Limestone is a geological formation in Utah that dates back to the Cambrian period.  It is most known for it’s preservation of soft-bodied tissue, trilobites and other shelly fossils. 
	
> This is a good guess, but the Chancellor is the best choice. It contains the Burgess Shale -2 Points.
	
