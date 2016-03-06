## Lab Exercise 4

> 17/20

## Problem Set 1

1)	Pennsylvanian: 133
	Miocene: 603
	Early Jurassic: 169
	Late Cretaceous: 375
	sum(PresencePBDB[“Miocene”])

2)	29 epochs
	str(PresencePBDB)

3)	Eocene, Paleocene, Oligocene, Miocene, Early Triassic, Pridoli, Early Devonian, Cisuralian, Late Jurassic, Late Cretaceous, Early Cretaceous, Middle Jurassic, Early Jurassic, Pleistocene, Middle Triassic, Pliocene, Late Triassic 
	which(PresencePBDB[,“Mytilus”]==1)

4)	Mississippian, Middle Devonian, Late Devonian, Guadalupian, Lopingian

> Why? - 0.5 Points

## Problem Set #2

1)	0.8279221

> How did you derive this? -0.75 Points

2)	1.0-0.8279221=0.1720779

3)	

distance=0.1720779
````R
vegdist(PresencePBDB[c(“Pleistocene”,”Miocene”),],method=“jaccard”)
````

4) 
````R
vegdist(PresencePBDB[c("Pleistocene","Pliocene","Miocene","Oligocene","Eocene",
	"Paleocene"),],method="jaccard")
          		               
			 Pleistocene   Pliocene    Miocene  Oligocene     Eocene
       	        Pliocene   0.12692967                                            
	       Miocene    0.17207792 0.08496732                                 
                   Oligocene  0.26910299 0.18968386 0.16065574                      
	        Eocene      0.21870048 0.13397129 0.08585056 0.19063005           
	       Paleocene  0.44444444 0.37914692 0.33333333 0.41042345 0.33385827
````

The Paleocene and Pleistocene epochs are the most dissimilar because they have the greatest distance.

## Problem Set #3

1) 
````R
RandomEpochs<-PresencePBDB[c("Pliocene","Oligocene","Paleocene","Early Cretaceous","Late Jurassic","Middle Jurassic"),]
````

2) 
````R
vegdist(RandomEpochs,methods="jaccard")

                  			Pliocene Oligocene Paleocene Early Cretaceous
		Oligocene        0.1047794                                     
		Paleocene        0.2339181 0.2581967                           
	        Early Cretaceous 0.5952663 0.5974843 0.4706685                 
		Late Jurassic    0.7625330 0.7627119 0.6532508        0.3075269
 	         Middle Jurassic  0.7941176 0.7879656 0.6572327        0.3230769

                  	            	Late Jurassic
    		  Oligocene                     
    		  Paleocene                     
     	   Early Cretaceous              
           	          Late Jurassic                 
        	      Middle Jurassic      0.1739130
````

3)	poles: Middle Jurassic, Pliocene
	Pliocene, Oligocene, Paleocene, Early Cretaceous, Late Jurassic, Middle Jurassic

            I ordered the distance values between the epochs from least to greatest.  In other words, the epochs 
	with the most similar values are closer together.  

4)	Temperature change; the Pliocene period had a cool and dry climate while the Middle Jurassic was warm and moist with a greenhouse-like climate. 

> You are correct about this temperature inference, but there are lots of up and downs in temperature over this period of time. An even more direct analysis would be to say that the epochs are ordered temporally from oldest to youngest.

5) Cretaceous-Paleogene (K-Pg) mass extinction event; extinction event eradicated a variety of species, meaning that there were less individuals to fill niches

> What do niches have to do with it?

## Problem Set #5

1)	Ordovician<-downloadPBDB(Taxa="animalia",StartInterval="Ordovician")

2)	Ordivician<-cleanGenus(“Ordovician”)

3)	?

> Come see me if you want a walkthrough of how to do this. -2 Points
