Lab #12

Problem Set #1
	1.	> TriassicSynapsids<-downloadPBDB("Synapsida",StartInterval="Anisian",StopInterval="Rhaetian")
	> TriassicSynapsids<-cleanRank(TriassicSynapsids,"genus")
	> TriassicDiapsids<-downloadPBDB("Diapsida",StartInterval="Anisian",StopInterval="Rhaetian")
	> TriassicDiapsids<-cleanRank(TriassicDiapsids,"genus")
	> JurassicDiapsids<-downloadPBDB("Diapsida",StartInterval="Jurassic",StopInterval="Neogene")
	> JurassicDiapsids<cleanRank(JurassicDiapsids,"genus")
	> JurassicDiapsids<-cleanRank(JurassicDiapsids,"genus")
	> JurassicSynapsids<-downloadPBDB("Synapsida",StartInterval="Jurassic",StopInterval="Neogene")
	> JurassicSynapsids<-cleanRank(JurassicSynapsids,"genus")
	2.	> TriassicDiapsids<-length(unique(TriassicDiapsids[,"genus"]))
		> TriassicDiapsids
		[1] 389
		> TriassicSynapsids<-length(unique(TriassicSynapsids[,"genus"]))
		> TriassicSynapsids
		[1] 116
	3.	> DiapsidSurvivors<-intersect(TriassicDiapsids,unique(JurassicDiapsids[,"genus"]))
		> length(DiapsidSurvivors)
		[1] 37
		> DiapsidVictims<-setdiff(TriassicDiapsids,unique(JurassicDiapsids[,“genus”]))
	> length(DiapsidVictims)
	[1] 352
	> SynapsidSurvivors<-intersect(TriassicSynapsids,unique(JurassicSynapsids[,“genus”]))
	> length(SynapidSurvivors
	[1] 9
	>SynapsidVictims<-setdiff(TriassicSynapsids,unique(JurassicSynapsids[,“genus”]))
	> length(SynapsidVictims)
	[1] 107
	4.	> SOdds<-(length(SynapsidSurvivors)/length(JurassicSynapsids))/(length(SynapsidVictims)/length(JurrassicSynapsids))
	> DOdds<-(length(DiapsidSurvivors)/length(JurassicDiapsids))/(length(DiapsidVictims)/	length(JurassicDiapsids))
	> OddsRatio<-DOdds/SOdds
	> log(OddsRatio)
	[1] 0.222891
	5.	StandardError <- sqrt(1/length(SynapsidSurvivors) + 1/length(SynapsidVictims) + 1/length(DiapsidSurvivors) + 1/length(DiapsidVictims))
	UpperLimit <- log(OddsRatio) + (1.96*StandardError)
	UpperLimit
	[1] 0.9828172
	LowerLimit <- log(OddsRatio) - (1.96*StandardError)
	LowerLimit
	[1] -0.5370353
	Given that the lower limit of our confidence interval is negative, we cannot conclude that Diapsids had a 
	statistically significant advantage in survival over Synapsids throughout T/J transition. 


Problem Set #2
	1.	> Triassic <- downloadPBDB(c("Diapsida", "Synapsida"), "Anisian", "Rhaetian")
	> Triassic <- cleanRank(Triassic, "genus")
	> Jurassic<- downloadPBDB(c("Diapsida", "Synapsida"), "Jurassic", "Neogene")
	> Jurassic <- cleanRank(Jurassic, "genus")
	2.	> MeanTriassicLat<-tapply(Triassic[,"paleolat"],Triassic[,"genus"],mean)
	> head(MeanTriassicLat)
 	Acaenasuchus  Acallosuchus Acompsosaurus   Actiosaurus Adamanasuchus Adelobasileus 
       		10.116        10.430        10.740        32.120        10.145        10.170 
	3.	> TriassicSurvivors <- subset(Triassic, Triassic[,"genus"]%in%unique(PostTriassic[,"genus"])==TRUE)
		> TriassicSurvivors <- unique(TriassicSurvivors[,"genus"])
		> head(TriassicSurvivors)
		[1] "Clevosaurus"        "Grallator"          "Rhynchosauroides"   "Rotodactylus"      
		[5] "Brachychirotherium" "Coelurosaurichnus" 
		> TriassicVictims <- subset(Triassic, Triassic[,"genus"]%in%unique(PostTriassic[,"genus"])!=TRUE)
		> TriassicVictims <- unique(TriassicVictims[,"genus"])
		> head(TriassicVictims)
		[1] "Icarosaurus"      "Rutiodon"         "Kuehneosuchus"    "Kuehneosaurus"   
		[5] "Trilophosaurus"   "Diphydontosaurus"
	4.	> TriassicSynapsids <- subset(Triassic, Triassic[,"genus"]%in%TriassicSynapsids[,"genus"]==TRUE)
	> TriassicSynapsids <- unique(TriassicSynapsids$genus)
	> TriassicDiapsids<- subset(Triassic, Triassic[,"genus"]%in%TriassicDiapsids[,"genus"]==TRUE)
	> TriassicDiapsids<- unique(TriassicDiapsids$genus)
	5.	> TJ<- array(0, dim=length(TriassicVictims), dimnames=list(TriassicVictims))
	> TJMatrix <- merge(MeanTriassicLat, TJ, all=TRUE, by="row.names")
	> TJMatrix <- transform(TJMatrix, row.names=Row.names, Row.names=NULL)
	> colnames(TJMatrix) <- c("MeanLatitudes", "Survivor/Victim")
	> TJMatrix[is.na(TJMatrix[,"Survivor/Victim"]),] <- 1
	> Regression <- glm(TJMatrix[,"Survivor/Victim"] ~ TJMatrix[,"MeanLatitudes"], 
	family="binomial")
	> summary(Regression)
	
	Call:
	glm(formula = FinalMatrix[, "Survivor/Victim"] ~ FinalMatrix[, 
	    "MeanLatitudes"], family = "binomial")

	Deviance Residuals: 
	    Min       1Q   Median       3Q      Max  
	-0.4474  -0.4411  -0.4385  -0.4308   2.1889  

	Coefficients:
	                                 Estimate Std. Error z value Pr(>|z|)    
	(Intercept)                    -2.3009122  0.1547326  -14.87   <2e-16 ***
	FinalMatrix[, "MeanLatitudes"]  0.0007725  0.0051555    0.15    0.881    
	---
	Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

	(Dispersion parameter for binomial family taken to be 1)

	    Null deviance: 308.10  on 504  degrees of freedom
	Residual deviance: 308.08  on 503  degrees of freedom
	AIC: 312.08

	Number of Fisher Scoring iterations: 5

	Since each degree in latitude only increases T/J survivorship by 0.0007725, latitude is not a good 
	predictor of extinction throughout this time period. 

