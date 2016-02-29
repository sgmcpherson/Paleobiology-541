Lab Exercise #5

Problem Set #1
	1.	Bivalve richness= 634
	
	sum(BivalveAbundance[“Miocene”,])

	2.	Berger-Parker Index= 0.2222222

	max(BrachiopodAbundance["Pliocene",])/sum(BrachiopodAbundance["Pliocene",])

	3.	Gini-Simpson Index= 0.9784588

	ginisimposn<-function(x,interval){
	a<-sum(x[interval,])^2
	b<-x[interval,]^2
	c<-b/a
	d<-1-sum(c)
	return(d)
	}
	ginisimpson(BrachiopodAbundance,”Late Ordovician”)

	4.	Shannon’s Entropy= 5.086654
	
	Shannon<-function(x,interval){
	a<-x[interval,]
	b<-a[a!=0]
	c<-sum(b)
	d<-b/c
	e<-d*log(d)
	f<- -sum(e)
	return(f)
	}
	Shannon(BivalveAbundance,”Late Cretaceous”)

	5.	Shannon”s Entropy= 4.511875
	
	Shannon(BivalveAbundance,”Paleocene”)

	6.	percentage change= 0.8870025

	Shannon(BivalveAbundance,”Paleocene”)/Shannon(BivalveAbundance,”Late Cretaceous”)

	Between the Late Cretaceous and Paleocene periods a mass extinction event occurred, commonly called 
	the K-Pg extinction.  Thus, this would severely reduce biodiversity, given that it is estimated that nearly 
	75% of all species perished.  This does not appear to be reflected in the Shanon index. 

	7.	percentage change= 0.5628292
	
	exp(Shannon(BivalveAbundance,”Paleocene”))/exp(Shannon(BivalveAbundance,”Late Cretaceous”))

	This number appears to be an underestimated of the change between the Late Cretaceous and Paleocene 
	periods, given that it is estimated that 75% or species went extinct during this period.  However, it is 
	much closer the the previously calculated values.

Problem Set #2

	1.	=634

	specnumber(BivalveAbundance[“Miocene”,])

	2.	=0.9784588

	diversity(BrachiopodAbundance[“Late Ordovician”,],index=“simpson”)

	3.	=5.086654

	diversity(BivalveAbundance[“Late Cretaceous”,],index=“shannon”)

	4.	=4.511875

	diversity(BivalveAbundance[“Paleocene”,],index=“shannon”)

Problem Set #3

	1.	 = -0.2376513, negative

	Bivalve<-specnumber(BivalveAbundance)

	Brachiopod<-specnumber(BrachiopodAbundance)

	cor(Bivalve,Brachiopod)

	2.	= -0.2624135, negative

	(diversity(BrachiopodAbundance,index=“simpson”),diversity(BivalveAbundance,index=
	“simpson”))

	3.	The greatest drop in brachiopod richness occurred between the Lopingian and Early Triassic epochs.


Problem Set #4

	1.	=63

	SampleAbundances<-apply(BraichiopodAbundance,1,sum)

	SampleAbundances[which(SampleAbundances==min(SampleAbundances))]

	Pleistocene 
        		 63 
	
	StandardizedRichness<-apply(BrachiopodAbundance,1,subsampleIndividuals,Quota=63)

	StandardizedRichness[1:6]

	  Mississippian     Pennsylvanian  Early Ordovician Middle Ordovician 
            	42.58             34.69             38.16             46.51 
 	 Late Ordovician        Llandovery 
            	41.54             41.76 


	2.	= -0.49727

		Brachiopod<-StandardizedRBrachiopod<- StandardizedRichness1[c("Early Ordovician", "Middle Ordovician", "Late Ordovician", "Llandovery", "Wenlock", "Ludlow", "Pridoli", "Early Devonian", "Middle Devonian", "Late Devonian", "Mississippian", "Pennsylvanian", "Cisuralian", "Guadalupian", "Lopingian", "Early Triassic", "Middle Triassic", "Late Triassic", "Early Jurassic", "Middle Jurassic", "Late Jurassic", "Early Cretaceous", "Late Cretaceous", "Paleocene", "Eocene", "Oligocene", "Miocene", "Pliocene")]

	cor(Bivalve,Brachiopod)

	3.	

