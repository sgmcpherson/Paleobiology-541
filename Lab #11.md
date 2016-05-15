Lab #11 

Problem Set #1
	1.	>TriassicUnits<-read.csv("https://macrostrat.org/api/units?interval_name=Triassic&format=csv&response=long")
	2.	>str(TriassicUnits)
	838 Triassic Units
	3.	>TriassicUnits[1:10,]
	Of the 10 units observed, the rocks are primarily igneous and metamorphic; sedimentary rock would be 
	better for fossil preservation, therefore these 10 units aren’t as relevant. 
	4.	The column “b_age” signifies the starting age of each unit while “t_age” denotes the ending age.
	5.	All 10 units range through the Triassic with some of them ending in the Cretaceous period. 

Problem Set #2
	1.	>TriassicUnits <- read.csv("https://macrostrat.org/api/units?interval_name=Triassic&format=csv&lith_class=sedimentary")
	2.	Triassic<-TriassicUnits[which(TriassicUnits[,"b_age"]<=251 & TriassicUnits[,"t_age"]>=201),]
	3.	>CretaceousUnits <- read.csv("https://macrostrat.org/api/units?interval_name=Cretaceous&format=csv&lith_class=sedimentary")
	>Cretaceous<-CretaceousUnits[which(CretaceousUnits[,"b_age"]<=145 & 
	CretaceousUnits[,"t_age"]>=66),]

	>JurassicUnits <- read.csv("https://macrostrat.org/api/units?	
	interval_name=Jurassic&format=csv&lith_class=sedimentary")
	>Jurassic<-JurassicUnits[which(JurassicUnits[,"b_age"]<=198 & 
	JurassicUnits[,"t_age"]>=146),]

	>PermianUnits <- read.csv("https://macrostrat.org/api/units?
	interval_name=Permian&format=csv&lith_class=sedimentary")
	>Permian<-PermianUnits[which(PermianUnits[,"b_age"]<=299 & 
	PermianUnits[,"t_age"]>=252),]

	>CarboniferousUnits <- read.csv("https://macrostrat.org/api/units?
	interval_name=Carboniferous&format=csv&lith_class=sedimentary")
	>Carboniferous<-CarboniferousUnits[which(CarboniferousUnits[,"b_age"]<=359 & 
	CarboniferousUnits[,"t_age"]>=300),]

	>DevonianUnits <- read.csv("https://macrostrat.org/api/units?
	interval_name=Devonian&format=csv&lith_class=sedimentary")
	>Devonian<-DevonianUnits[which(DevonianUnits[,"b_age"]<=419 & 
	DevonianUnits[,"t_age"]>=360),]

	>SilurianUnits <- read.csv("https://macrostrat.org/api/units?
	interval_name=Silurian&format=csv&lith_class=sedimentary")
	>Silurian<-SilurianUnits[which(SilurianUnits[,"b_age"]<=443 & SilurianUnits[,"t_age"]>=420),]

	>OrdovicianUnits <- read.csv("https://macrostrat.org/api/units?
	interval_name=Ordovician&format=csv&lith_class=sedimentary")
	>Ordovician<-OrdovicianUnits[which(OrdovicianUnits[,"b_age"]<=485 & 
	OrdovicianUnits[,"t_age"]>=444),]
	4.	>UnitFreqs<-c(nrow(Cretaceous),nrow(Jurassic),nrow(Triassic), nrow(Permian),nrow(Carboniferous),nrow(Devonian), nrow(Silurian),nrow(Ordovician))
	>UnitFreqs
	[1] 4588  881  497  903 2913 1900  969 1923
	5.	UnitFreqsNoTriassic<-c(nrow(Cretaceous),nrow(Jurassic),nrow(Permian),nrow(Carboniferous),nrow(Devonian),nrow(Silurian),nrow(Ordovician))
	>mean(UnitFreqsNoTriassic)
	[1] 2002.429
	>sd(UnitFreqsNoTriassic)
	[1] 1366.48
	>nrow(Triassic)
	[1] 497
	>(2002.429-497)/1366.48
	[1] 1.101684

	The number of Triassic Units is ~1.101684 below the mean. 
	6.	No, because it is less than two standard deviations away from the mean, meaning it wouldn’t have a lower number of units compared to other periods.
	7.	Even while considering both the Jurassic and Triassic periods as outliners both of the means still only fall one standard deviation below the mean.

	> SansTriassic&Jurassic<-
	c(nrow(Cretaceous),nrow(Permian),nrow(Carboniferous),nrow(Devonian),nrow(Silurian),
	nrow(Ordovician))
	>mean(SansTriassic&Jurassic)
	[1] 2199.333
	>sd(NoTJ)
	[1] 1383.85
	>nrow(Triassic)
	[1] 497
	>nrow(Jurassic)
	[1] 821

Problem Set #3
	1.	> URL <- "https://macrostrat.org/api/columns?format=geojson_bare&project_id=1"
	> GotURL<-getURL(URL)
	> NAMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
	> plot(NAMap)
	2.	URLIA<-"https://macrostrat.org/api/columns?format=geojson_bare&age_top=242&age_bottom=252.2&project_id=1"
	> GotURLIA<-getURL(URLIA)
	> NAMap<-readOGR(GotURLIA,"OGRGeoJSON",verbose=FALSE)
	> plot(NAMap,col="#B051A5",add=TRUE)
	3.	> IAAnimals<-downloadPBDB("Animalia",StartInterval="Induan",StopInterval="Anisian")
	> points(IAAnimals[,"lng"],IAAnimals[,"lat"],pch=20,col="blue")
	4.	> plot(NAMap)
		> URL<-"https://macrostrat.org/api/columns?format=geojson_bare&age_top=251&age_bottom=260&project_id=1"
		> GotURL<-getURL(URL)
		> NALopMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
		> plot(NALopMap,col="#FBA794",add=TRUE)
	5.	> LopAnimals<-downloadPBDB("Animalia",StartInterval="Lopingian",StopInterval="Lopingian")
		> points(LopAnimals[,"lng"],LopAnimals[,"lat"],pch=20)
	6.	The areal extent of North American sedimentary units across the P/T boundary appear to be very similar; in other words they occurred in approximately the same amount of area.  However, based on the plotted fossils, there does appear to be a substantial drop in the percentage of sedimentary units with reported fossils in them across the P/T.  Overall, I don’t think that there is sufficient evidence to accept either of these hypotheses; the P/T appear to both be well sampled, therefore there is enough data to reject the hypotheses. 



