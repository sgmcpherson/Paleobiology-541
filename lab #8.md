> 20/20 Great Job! And thanks for doing it in markdown.

Lab #8

### Problem Set #1

	1.	North America is currently to the West of its position in the Cretaceous period. 
	2.	 This line of code plots a function named ModernMap, in the color red with an opacity of 0.33, and adds it to a previous plot without creating a new one. 
	3.	>AlbianMap<-downloadPaleogeography(Age=110)
	4.	>plot(AlbianMap,col=rgb(0,1,0,0.33),lty=0,add=TRUE)
	5.	Since the Albian, there has been more movement North and South. 
	6.	In the Western Hemisphere, there was been more movement West since the Albian. 

### Problem Set #2

	1.	> PaleoceneEocene<-downloadPaleogeography(Age=56)
		> plot(PaleoceneEocene,col=rgb(1,0,0,0.33),lty=0)
	2.	> Anthozoa<- downloadPBDB("Anthozoa",StartInterval="Paleocene",StopInterval="Eocene")
	3.	2,847
	4.	> colnames(Anthozoa)
 		[1] "occurrence_no"   "record_type"     "reid_no"         "flags"          
 		[5] "collection_no"   "identified_name" "identified_rank" "identified_no"  
 		[9] "difference"      "accepted_name"   "accepted_rank"   "accepted_no"    
		[13] "early_interval"  "late_interval"   "max_ma"          "min_ma"         
		[17] "reference_no"    "paleomodel"      "paleolng"        "paleolat"       
		[21] "geoplate"        "phylum"          "class"           "order"          
		[25] "family"          "genus"       

	occurence_no: a positive integer that uniquely identifies the occurrence 
	record_type: the thy of this object for an occurrence 
	reid_no: if this occurrence was reidentified, a unique reidentification
	flags: a record representing an identification that has been superseded by a more recent identification 		will have the letter R is this field
	collection_no:  the identifier of the collection with which this occurrence is associated 
	identified_name:  the taxonomic name by which this occurrence was identified
	identified_rank:  the taxonomic rank of the identified name, if this can be determined
	difference:  if the identified name is different from the accepted name, this field gives the response why
	accepted_name:  the value of this field will be the accepted taxonomic name corresponding to the 		identified name
	accepted_rank:  the taxonomical rank of the accepted name 
	accepted_no:  the unique identifier of the accepted taxonomic name in this database 
	early_interval:  the specific geological time range association with this occurrence, or the interval that 		begins the range if late_interval is also given
	late interval:  the interval that ends the specific geological time range associated with this occurrence, if 		different from the value of early_interval
	max_ma:  records whose temporal locality is at most this old, specified in Ma
	min_ma:  records whose temporal locality is at least this old, specified in Ma
	reference_no:  the identifier of the reference from which this data was entered
	paleomodel:  the primary model specified by the parameter pgm; included only if more than one model
	paleolng:  the paleolongitude of the collection, evaluated according to the primary model indicated by 		the  pgm
	paleolat:  the paleolatitude of the collection, evaluated according to the primary model indicated by pgm
	geoplate:  the identifier of the geological plate on which the collection lies, evaluated according to the 		primary model indicated by the parameter pgm
	phylum:  the name of the phylum in which the occurrence is classified 
	class: the taxonomical classification of the occurrence-> phylum, class, order, family, genus
	order: specifies the order in which the results are returned 
	family: select only occurrences which are identified to family, genus or species 
	genus: the genus corresponding to each occurrence, if the occurrence has been identified to the genus 		level

	5.	> points(PaleoceneEocene$paleolng,PaleoceneEocene$paleolat,pch=19, col="blue",cex=1.5)
	6.	Eurupe, Turkey; appear to be primarily marine, meaning that some marine environment existed in these areas during this time

### Problem Set #3
	1.	Perissodactyla<-downloadPBDB("Perissodactyla",StartInterval="Paleocene",StopInterval="Oligocene")
	2.	Perissodactyls are odd-toed ungulates that have simple hindgut, fermenting stomachs.  This order includes three extant families: Equidae,Rhinocerotidae and	Tapiridae, more commonly known as horses, donkeys, and zebras, rhinos, and tapirs respectively. 
	3.	> which(Perissodactyla[,"collection_no"]==112723)
	[1] 3949 3951
	4.	This data is associated with geoplate id 501 and corresponds to modern day Pakistan.
	5.	> PerissodactylaX<-Perissodactyla[which(Perissodactyla$geoplate==501),]
		> length(PerissodactylaX)
		[1] 26
	6.	Region X was originally southeastern of Africa and then as time passed, it moved northward until combining with Eurasian continent. 
	7.	Looking at the Paleogene time period using the PB Navigator Tool (as well as the later and former time intervals), it is possible that Perissodactyla could have migrated from region x to China, or the opposite may also be true.  However, it is unlikely that the Perissodactyla species of these regions are unrelated but is does appear that the order first appeared in North America and then moved Eastward across the continents. 
